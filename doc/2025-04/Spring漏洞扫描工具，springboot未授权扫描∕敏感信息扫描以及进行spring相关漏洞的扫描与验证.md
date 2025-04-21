#  Spring漏洞扫描工具，springboot未授权扫描/敏感信息扫描以及进行spring相关漏洞的扫描与验证   
WuliRuler  夜组安全   2025-04-21 00:00  
  
免责声明  
  
由于传播、利用本公众号夜组安全所提供的信息而造成的任何直接或者间接的后果及损失，均由使用者本人负责，公众号夜组安全及作者不为此承担任何责任，一旦造成后果请自行承担！如有侵权烦请告知，我们会立即删除并致歉。谢谢！  
**所有工具安全性自测！！！VX：**  
**baobeiaini_ya**  
  
朋友们现在只对常读和星标的公众号才展示大图推送，建议大家把  
**夜组安全**  
“**设为星标**  
”，  
否则可能就看不到了啦！  
  
  
![](https://mmbiz.qpic.cn/sz_mmbiz_png/icZ1W9s2Jp2WrOMH4AFgkSfEFMOvvFuVKmDYdQjwJ9ekMm4jiasmWhBicHJngFY1USGOZfd3Xg4k3iamUOT5DcodvA/640?wx_fmt=png&from=appmsg "")  
  
## 一、工具概述  
  
**SBSCAN是一款专注于spring框架的渗透测试工具，可以对指定站点进行springboot未授权扫描/敏感信息扫描以及进行spring相关漏洞的扫描与验证。**  
- **最全的敏感路径字典**  
：最全的springboot站点敏感路径字典，帮你全面检测站点是否存在敏感信息泄漏  
  
- **支持指纹检测**  
：  
  
- 支持spring站点指纹匹配：支持启用指纹识别，只有存在spring指纹的站点才进行下一步扫描，节约资源与时间 (无特征的站点会漏报，客官自行决策是否启用)  
  
- 支持敏感路径页面关键词指纹匹配：通过维护敏感路径包含的关键词特征，对检出的页面进行指纹匹配，大大提升了工具检出的准确率，减少了人工去确认敏感页面真实性投入的时间  
  
- **支持指定模块发起检测：**  
 不想跑漏洞，只想检测敏感路径？ 或者只想检测漏洞？ 都可以，通过 -m  
 参数指定即可  
  
- **最全的spring漏洞检测POC：**  
 spring相关cve漏洞的检测poc全部给你集成到这款工具里，同类型最全  
  
- **无回显漏洞解决：**  
 无回显漏洞检测扫描器光看响应状态码不太靠谱？支持--dnslog参数指定dnslog域名，看到dnslog记录才是真的成功验证漏洞存在  
  
- **降噪输出结果：**  
 可通过指定-q  
参数只显示成功的检测结果  
  
- **友好的可扩展性：**  
 项目设计初期就考虑了用户的自定义扩展需求，整个项目尽量采用高内聚低耦合模块化的编程方式， 你可轻松的加上自己的poc、日常积累的敏感路径、绕过语句，轻松优化检测逻辑，具体见下文的“自定义扩展”  
  
- **其他一些常规支持**  
：单个url扫描/ url文件扫描 / 扫描模块选择 / 支持指定代理 / 支持多线程 / 扫描报告生成  
  
## 工具使用  
>   
> 检测效果图, 使用彩色表格打印更直观显示检测结果，**检测报告**  
保存位置将会在扫描结束后控制台显示  
  
  
![](https://mmbiz.qpic.cn/sz_mmbiz_png/icZ1W9s2Jp2VB2vpRwsDLT60uDYG4ibL8iaiczHVF1zKah8QH6xwodOdaq1ialu28VcJFQWf713Kh8OkPloic5qIiaqyg/640?wx_fmt=png&from=appmsg "")  
>   
> **检测时**  
可使用 tail -f logs/sbscan.log  
 实时查看详细的检测情况  
  
  
![](https://mmbiz.qpic.cn/sz_mmbiz_png/icZ1W9s2Jp2VB2vpRwsDLT60uDYG4ibL8iaB4PcIukia3yRlIhpur2Sq9GjH28DqyfvyncVC4ptXvOPA70JleguRVQ/640?wx_fmt=png&from=appmsg "")  
```
## 🧾 已支持检测CVE列表- CVE-2018-1273- CVE-2019-3799- CVE-2020-5410- CVE-2022-22947- CVE-2022-22963- CVE-2022-22965- JeeSpringCloud_2023_uploadfile
```  
  
  
## 工具获取  
  
  
  
点击关注下方名片  
进入公众号  
  
回复关键字【  
250421  
】获取  
下载链接  
  
  
## 往期精彩  
  
  
往期推荐  
  
[AscensionPath一个基于Docker容器化技术的漏洞环境管理系统](http://mp.weixin.qq.com/s?__biz=Mzk0ODM0NDIxNQ==&mid=2247494140&idx=1&sn=23280ef663e551ad564d018f7653375a&chksm=c36bad04f41c241297da6bfeec639c92cf0fafeeadf7a7d5a3bb33b83fcafe169b7f496b2952&scene=21#wechat_redirect)  
  
  
[Rust境虚拟机+Rust编译工具集，助力脚本小子一键免杀。](http://mp.weixin.qq.com/s?__biz=Mzk0ODM0NDIxNQ==&mid=2247494113&idx=1&sn=cc334bafbeb722d10b7df2b377483f20&chksm=c36bad19f41c240f272406d7d4895aab1c0cde18d4b0f77fe989a62189029037f4c9b99a904d&scene=21#wechat_redirect)  
  
  
[Webshell免杀、流量加密传输工具 V2.5 | 免杀冰蝎、哥斯拉等Webshell的ASP、PHP、JSP木马文件](http://mp.weixin.qq.com/s?__biz=Mzk0ODM0NDIxNQ==&mid=2247494103&idx=1&sn=dabd98f3cc04c91128b8bc6e474acf7c&chksm=c36bad2ff41c243946315522a91c109237fb185e885eafba7d42a2a34dd657c6edf4e52a6ce8&scene=21#wechat_redirect)  
  
  
[信息收集、渗透测试工具箱，支持多种工具和资料](http://mp.weixin.qq.com/s?__biz=Mzk0ODM0NDIxNQ==&mid=2247494095&idx=1&sn=47e916b0acbf27c95a522087e82e8883&chksm=c36bad37f41c2421af14cbf4c83bf1c29adf896434cb9b12b7044e89f67b74f6f389b90ce7f0&scene=21#wechat_redirect)  
  
  
[一款全方位扫描工具，具备高效的机器探活，端口探活，协议识别，指纹识别，漏洞扫描等功能](http://mp.weixin.qq.com/s?__biz=Mzk0ODM0NDIxNQ==&mid=2247494044&idx=1&sn=a001baaaa089ff3339dcfe9e2c811276&chksm=c36bad64f41c247289b93cfee382d35e9328e5c9e8dba1e2513824a65e579b1ec1da68d37e01&scene=21#wechat_redirect)  
  
  
![](https://mmbiz.qpic.cn/mmbiz_png/OAmMqjhMehrtxRQaYnbrvafmXHe0AwWLr2mdZxcg9wia7gVTfBbpfT6kR2xkjzsZ6bTTu5YCbytuoshPcddfsNg/640?wx_fmt=other&wxfrom=5&wx_lazy=1&wx_co=1&random=0.8399406679299557&tp=webp "")  
  
  
