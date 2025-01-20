#  Catcher外网打点指纹识别+Nday漏洞验证工具|指纹识别   
漏洞挖掘  渗透安全HackTwo   2025-01-20 16:01  
  
0x01 工具介绍   
          
Catcher重点系统指纹漏洞验证工具，适用于外网打点，资产梳理漏洞检查。在面对大量的子域名时，Catcher可将其进行指纹识别，将已经识别成功的指纹进行对应的漏洞验证，并对域名进行cdn判断，将未使用cdn域名进行端口扫描，工具包含一些网上已经公布的Nday poc  
。  
  
![](https://mmbiz.qpic.cn/sz_mmbiz_png/RjOvISzUFq49cBQdmNV7iaa0iaeUJWHuYACpWsLBKK0GYv9VUicgJ5FbeGDV4MDfPFW3yP8FVNRib4iaCIpbponPFzA/640?wx_fmt=png&from=appmsg "")  
  
**下载地址在末尾**  
  
0x02 功能简介工具特点Catcher首先会对域名通过finger.json文件进行指纹识别识别成功后会进入poc文件下去找具体对应的poc进行测试比如识别到的指纹为Atlassian Confluence，那么就会进入到 poc文件下的Atlassian Confluence文件下，去运行该文件中所有的poc文件Catcher中内置了许多用于漏洞验证的poc进行完漏洞测试后会将所有域名进行cdn判断（不可能做到绝对准确）判断完cdn后会去获取域名对应的ip，并进行端口扫描运行结束后会将结果保存到results文件下该文件下有7个文件 Cdn.txt: 使用了cdn的域名NoCdn.txt: 没有使用cdn的域名ErrorCdn.txt: 未判断出是否使用cdn的域名Finger.json: 指纹识别到的域名NoFinger.json: 未指纹识别到的域名PocResults.txt: 漏洞测试的结果Ports.txt: 端口扫描结果0x03更新介绍更新指纹以及poc0x04 使用介绍使用工具目录如下domain.txt: 需要进行测试的域名（可直接写入ip和端口的形式如1.1.1.1:80，也可写url: https://www.xxx.com的形式，也可直接写域名www.xxx.com）finger.json: 指纹文件poc : poc文件使用时直接通过命令行运行Catcher.exe即可，不需要使用任何参数在查看结果时推荐使用sublime等编译器打开查看，文本文档直接打开不太友好除了对多个域名进行指纹识别漏洞验证因为domain.txt中也可写入ip端口的形式，并且Catcher中有很多poc。对多个资产、单个资产进行批量的泛微OA、用友OA等漏洞验证也是不错的选择  
0x05 内部星球VIP介绍-V1.3更新啦！  
       学习更多挖洞技巧可加入**内部星球**可获得内部工具和享受内部资源，包含网上一些付费工具。详情直接点击下方链接进入了解，需要加入的直接点击下方链接了解即可，觉得价格高的师傅可后台回复"   
**星球** "有优惠券名额有限先到先得！内部  
包含网上需付费未公开的0day/1day漏洞库，后续资源会更丰富在加入还是低价！  
  
  
**👉点击了解-->>内部VIP知识星球福利介绍V1.3版本-星球介绍**  
  
****  
结尾  
  
# 免责声明  
  
  
# 获取方法  
  
  
**公众号回复20250121获取下载地址******  
  
  
# 最后必看  
  
  
      
文章中的案例或工具仅面向合法授权的企业安全建设行为，如您需要测试内容的可用性，请自行搭建靶机环境，勿用于非法行为。如  
用于其他用途，由使用者承担全部法律及连带责任，与作者和本公众号无关。  
本项目所有收录的poc均为漏洞的理论判断，不存在漏洞利用过程，不会对目标发起真实攻击和漏洞利用。文中所涉及的技术、思路和工具仅供以安全为目的的学习交流使用。  
如您在使用本工具或阅读文章的过程中存在任何非法行为，您需自行承担相应后果，我们将不承担任何法律及连带责任。本工具或文章或来源于网络，若有侵权请联系作者删除，请在24小时内删除，请勿用于商业行为，自行查验是否具有后门，切勿相信软件内的广告！  
  
  
  
> **彩蛋🌟昨日内部星球新增0day/1day漏洞及资源:(已连续更新600天+星球涵盖全网90%资源)**  
  
  
```
如何发现导致账户接管的参数篡改漏洞
针对前端加密爆破的方法及实战案例
百度技术培训中心存在越权取消订单漏洞
记录第一次尝试小程序支付漏洞挖掘
某小程序高危漏洞
勤云科技 abstract 存在SQL注入漏洞
以柔资讯-D-Security终端文件保护系统 logFileName 任意文件读取漏洞
移动应用getPicServlet存在任意文件的读取漏洞
CobaltStrike4.9.1汉化魔改版更新
CS_CounterStrike1.6.1最新版
CS/Webshell等免杀工具分享
全网最全的SRC资产表更新
漏洞情报威胁情报更新
SRC漏洞挖掘培训视频更
```  
  
  
  
# 往期推荐  
  
  
**1.内部VIP知识星球福利介绍V1.3版本-星球介绍**  
  
**2. 最新BurpSuite2023.12.1专业版中英文版下载**  
  
[3. 最新Nessus2023下载Windows/Linux](http://mp.weixin.qq.com/s?__biz=Mzg3ODE2MjkxMQ==&mid=2247484713&idx=1&sn=0fdab59445d9e0849843077365607b18&chksm=cf16a399f8612a8f6feb8362b1d946ea15ce4ff8a4a4cf0ce2c21f433185c622136b3c5725f3&scene=21#wechat_redirect)  
  
  
[4. 最新xray1.9.11高级版下载Windows/Linux](http://mp.weixin.qq.com/s?__biz=Mzg3ODE2MjkxMQ==&mid=2247483882&idx=1&sn=e1bf597eb73ee7881ae132cc99ac0c8e&chksm=cf16a75af8612e4c73eda9f52218ccfc6de72725eb37aff59e181435de095b71e653b446c521&scene=21#wechat_redirect)  
  
  
[5. 最新HCL AppScan Standard 10.2.128273破解版下载](http://mp.weixin.qq.com/s?__biz=Mzg3ODE2MjkxMQ==&mid=2247483850&idx=1&sn=8fad4ed1e05443dce28f6ee6d89ab920&chksm=cf16a77af8612e6c688c55f7a899fe123b0f71735eb15988321d0bd4d14363690c96537bc1fb&scene=21#wechat_redirect)  
  
  
  
###### 渗透安全HackTwo  
  
  
微信号：关注公众号获取  
  
后台回复星球加入：  
知识星球  
  
扫码关注 了解更多  
  
![](https://mmbiz.qpic.cn/sz_mmbiz_png/RjOvISzUFq6qFFAxdkV2tgPPqL76yNTw38UJ9vr5QJQE48ff1I4Gichw7adAcHQx8ePBPmwvouAhs4ArJFVdKkw/640?wx_fmt=png "二维码")  
  
  
  
喜欢的朋友可以点赞转发支持一下  
  
  
