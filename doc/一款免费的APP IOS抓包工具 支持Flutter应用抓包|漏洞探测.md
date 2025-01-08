#  一款免费的APP IOS抓包工具 支持Flutter应用抓包|漏洞探测   
漏洞挖掘  渗透安全HackTwo   2025-01-08 16:00  
  
0x01 工具介绍   
**ProxyPin** 是一款免费开源的跨平台抓包工具，支持 Windows、Mac、Android、iOS 和 Linux。它可以拦截、检查并重写 HTTP(S) 流量，同时支持 Flutter 应用抓包。核心功能包括扫码连接设备、域名过滤、请求/响应修改（支持 JavaScript 脚本）、请求屏蔽、历史流量记录（支持 HAR 导出/导入），以及正则搜索和常用工具箱。基于 Flutter 开发，界面美观易用，非常适合调试与流量分析。  
  
![](https://mmbiz.qpic.cn/sz_mmbiz_png/RjOvISzUFq66OwelFCiahibUib3AszQRt5x564Q3fHJgIHJaUibzaKFticlttO35KL3EicMbe5efIiap42XV0rKndglEQ/640?wx_fmt=png&from=appmsg "")  
  
**下载地址在末尾**  
  
0x02 功能简介核心特性手机扫码连接: 不用手动配置Wifi代理，包括配置同步。所有终端都可以互相扫码连接转发流量。域名过滤: 只拦截您所需要的流量，不拦截其他流量，避免干扰其他应用。搜索：根据关键词响应类型多种条件搜索请求脚本: 支持编写JavaScript脚本来处理请求或响应。请求重写: 支持重定向，支持替换请求或响应报文，也可以根据增则修改请求或或响应。请求屏蔽: 支持根据URL屏蔽请求，不让请求发送到服务器。历史记录：自动保存抓包的流量数据，方便回溯查看。支持HAR格式导出与导入。其他：收藏、工具箱、常用编码工具、以及二维码、正则等Mac首次打开会提示不受信任开发者，需要到系统偏好设置-安全性与隐私-允许任何来源开源抓包工具 支持iOS/安卓/Windows/Mac/Linux全平台系统应该是目前支持最全的工具，全平台支持，您可以使用它来拦截、检查和重写HTTP（S）流量，ProxyPin基于Flutter开发，UI美观易用。0x03更新说明V1.1.6新增Hosts设置, 支持域名映射工具箱新增时间戳转换编辑请求发送快捷键和发送loading修复脚本编辑键盘弹出安全模式问题修复脚本URL编码问题修复请求屏蔽编辑多出空格问题修复ipad分享点击无效问题修复高级重放次数过多不执行问题修复请求重写bug应用黑白名单增加清除无效应用，添加过滤已存在应用0x04 使用介绍选择对应的版本进行安装即可使用以下操作以Windows为例，打开工具后会默认进行HTTP抓包操作，看到的界面如下图所示默认情况下我们只能抓取HTTP请求，无法抓取HTTPS请求需要点击顶部的【启用HTTPS代理】开关按钮，安装根证书到本机根据软件进一步提示安装根证书  
![](https://mmbiz.qpic.cn/sz_mmbiz_png/RjOvISzUFq66OwelFCiahibUib3AszQRt5xWLbRjzsocpz7zXbFUn9Ml093OCLW7VEPJgiae6CbiaBNTFlnsjHibF8KA/640?wx_fmt=png&from=appmsg "")  
最后再启用HTTPS代理，就能抓取HTTPS请求了  
![](https://mmbiz.qpic.cn/sz_mmbiz_png/RjOvISzUFq66OwelFCiahibUib3AszQRt5xFaTkPZpKYztz3ia84MicKsb7XwOYlgYzEZWGIYJKX2I0iamj9aheHrJ9A/640?wx_fmt=png&from=appmsg "")  
  
0x05 内部星球VIP介绍-V1.3（福利）        如果你想学习更多渗透挖洞技术/技巧欢迎加入我们内部星球可获得内部工具字典和享受内部，每周一至五周更新1day/0day漏洞刷分上分(2025POC更新至3500+)，包含网上一些付费工具BurpSuite漏洞检测插件，Fofa高级会员，CTFshow等各种账号会员共享。详情直接点击下方链接进入了解，觉得价格高的师傅可后台回复" 星球 "有优惠券名额有限先到先得！后续资源会更丰富在加入还是低价！（价格随资源人数进行上涨早加入早享受）👉点击了解加入-->>内部VIP知识星球福利介绍V1.3版本-1day/0day漏洞及内部资源每日更新  
  
  
结尾  
  
# 免责声明  
  
  
# 获取方法  
  
  
**公众号回复20250109获取下载地址**  
  
# 最后必看  
  
  
      
文章中的案例或工具仅面向合法授权的企业安全建设行为，如您需要测试内容的可用性，请自行搭建靶机环境，勿用于非法行为。如  
用于其他用途，由使用者承担全部法律及连带责任，与作者和本公众号无关。  
本项目所有收录的poc均为漏洞的理论判断，不存在漏洞利用过程，不会对目标发起真实攻击和漏洞利用。文中所涉及的技术、思路和工具仅供以安全为目的的学习交流使用。  
如您在使用本工具或阅读文章的过程中存在任何非法行为，您需自行承担相应后果，我们将不承担任何法律及连带责任。本工具或文章或来源于网络，若有侵权请联系作者删除，请在24小时内删除，请勿用于商业行为，自行查验是否具有后门，切勿相信软件内的广告！  
  
> **彩蛋🌟昨日内部星球新增0day/1day漏洞及资源:(已连续更新600天+星球涵盖全网90%资源)**  
  
  
```
瑞友天翼应用虚拟化系统 GetPwdPolicy 存在SQL注入漏洞
用友NC checkekey 存在SQL 注入漏洞
以柔资讯-D-Security终端文件保护系统 logFileName 任意文件读取漏洞
深科特 LEAN MES系统 SMTLoadingMaterial.ashx 存在SQL注入漏洞
蓝凌EIS智慧协同平台 fi_message_receiver.aspx SQL注入漏洞
爱数AnyShare SMTP_GetConfig存在信息泄露漏洞
Four-Faith路由器apply存在未授权命令注入漏洞(CVE-2024-12856)
CS/Webshell等免杀工具分享
全网最全的SRC资产表更新
独眼情报书签情报完整版
SRC漏洞挖掘培训视频更新
```  
  
  
  
  
# 往期推荐  
  
  
**1.内部VIP知识星球福利介绍V1.3版本-‍星球介绍(新增推送0day)**  
  
**2. 最新Nessus2024.10.7版本主机漏洞扫描下载**  
  
**3. 最新BurpSuite2024.7.3专业版中英文版下载**  
  
[4. 最新xray1.9.11高级版下载Windows/Linux](http://mp.weixin.qq.com/s?__biz=Mzg3ODE2MjkxMQ==&mid=2247483882&idx=1&sn=e1bf597eb73ee7881ae132cc99ac0c8e&chksm=cf16a75af8612e4c73eda9f52218ccfc6de72725eb37aff59e181435de095b71e653b446c521&scene=21#wechat_redirect)  
  
  
[5. 最新HCL AppScan Standard 10.2.128273破解版下载](http://mp.weixin.qq.com/s?__biz=Mzg3ODE2MjkxMQ==&mid=2247483850&idx=1&sn=8fad4ed1e05443dce28f6ee6d89ab920&chksm=cf16a77af8612e6c688c55f7a899fe123b0f71735eb15988321d0bd4d14363690c96537bc1fb&scene=21#wechat_redirect)  
  
  
  
###### 渗透安全HackTwo  
  
  
微信号：关注公众号获取  
  
后台回复星球加入：  
知识星球  
  
扫码关注 了解更多  
  
![](https://mmbiz.qpic.cn/sz_mmbiz_png/RjOvISzUFq6qFFAxdkV2tgPPqL76yNTw38UJ9vr5QJQE48ff1I4Gichw7adAcHQx8ePBPmwvouAhs4ArJFVdKkw/640?wx_fmt=png "二维码")  
  
  
  
喜欢的朋友可以点赞转发支持一下  
  
  
