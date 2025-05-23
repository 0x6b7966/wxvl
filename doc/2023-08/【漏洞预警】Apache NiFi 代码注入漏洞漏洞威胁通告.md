#  【漏洞预警】Apache NiFi 代码注入漏洞漏洞威胁通告   
安识科技  SecPulse安全脉搏   2023-08-04 10:02  
  
##   
  
1. **通告信息**  
  
  
  
近日，  
安识科技A-Team团队  
监测到一则Apache NiFi组件存在代码注入漏洞的信息，漏洞编号：CVE-2023-36542，漏洞威胁等级：中危。  
  
该漏洞是由于  
Apache NiFi 0.0.2至1.22.0版本中包含支持HTTP URL引用以索引驱动程序的处理器和控制器，这允许经过身份认证的用户通过此功能注入恶意代码，最终可利用该漏洞执行任意命令。  
  
对此，安识科技建议广大用户及时升级到安全版本，并做好资产自查以及预防工作，以免遭受黑客攻击。  
##   
  
2. **漏洞概述**  
  
  
  
CVE  
：  
CVE-2023-36542  
  
简述：  
Apache NiFi是一个开源的数据流处理工具，用于可靠地收集、聚合、转换和路由大规模数据流。它提供了一个可视化的用户界面，使用户能够以图形化方式设计和管理数据流。该漏洞是由于Apache NiFi 0.0.2至1.22.0版本中包含支持HTTP URL引用以索引驱动程序的处理器和控制器，这允许经过身份认证的用户通过此功能注入恶意代码，最终可利用该漏洞执行任意命令。  
##   
  
3. **漏洞危害**  
  
  
  
允许经过身份认证的用户通过此功能注入恶意代码，最终可利用该漏洞执行任意命令。  
##   
  
4. **影响版本**  
  
  
  
目前受影响的  
Apache NiFi版本：  
  
0.0.2 ≤ Apache NiFi < 1.23.0  
##   
  
5. **解决方案**  
  
  
  
当前官方已发布最新版本，建议受影响的用户及时更新升级到最新版本。链接如下：  
  
	  
https://nifi.apache.org/download.html  
##   
  
6. **时间轴**  
  
  
  
【  
-  
】2023年  
0  
8月02日 安识科技A  
-T  
eam团队监测到Apache NiFi 代码注入漏洞信息  
  
【  
-  
】  
2  
02  
3年  
0  
8月03日 安识科技A-Team团队根据漏洞信息分析  
  
【  
-  
】  
2  
02  
3年  
0  
8月04日 安识科技A-Team团队发布安全通告  
  
  
  
