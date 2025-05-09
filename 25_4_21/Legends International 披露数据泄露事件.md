# 微软披露Node.js恶意广告活动：网络安全威胁的新形态

## 一、事件概述

近日，微软披露了一场持续进行的恶意广告活动，该活动利用Node.js技术分发能够窃取信息及导致数据泄露的恶意载荷。这场攻击最早于2024年10月被发现，攻击者通过伪装成币安（Binance）或TradingView等合法软件的欺诈网站，以加密货币交易为诱饵，诱骗用户安装恶意安装程序。此次活动不仅展现了攻击者高超的技术手段和伪装能力，还揭示了Node.js这一开源跨平台JavaScript运行时环境在网络安全领域被滥用的新趋势。通过结合社会工程学、持久化驻留技术以及规避检测的策略，攻击者成功窃取受害者敏感数据，甚至针对企业员工展开以人力资源为主题的钓鱼骗局，形成了一场复杂的网络安全威胁。

## 二、事件描述分析

这场恶意广告活动的攻击链条设计精巧，包含多个阶段，充分利用了Node.js的特性以及社会工程学的欺骗手段，其核心目标是窃取用户敏感数据并长期潜伏于目标系统之中。以下是对攻击过程和技术手段的详细分析。

首先，攻击者通过伪装成知名加密货币交易平台（如币安和TradingView）的欺诈网站，诱导用户下载看似合法的安装程序。这些伪装网站的界面设计与真实平台高度相似，甚至通过谷歌赞助广告投放恶意搜索广告，进一步提高可信度。安装程序内嵌了一个动态链接库（CustomActions.dll），该库通过Windows管理规范（WMI）收集系统基本信息，并利用计划任务在受感染主机上实现持久化驻留。为了维持伪装，该动态链接库会启动一个名为“msedge_proxy.exe”的浏览器窗口，显示合法的加密货币交易网站，从而降低用户的怀疑。

其次，攻击者通过计划任务运行PowerShell命令，从远程服务器下载附加脚本。这些脚本具备高度隐蔽性，能够将正在运行的PowerShell进程及当前目录排除在Microsoft Defender for Endpoint的扫描范围之外，从而规避安全检测。此后，系统会执行一条经过混淆的PowerShell命令，从远程URL获取并运行信息收集脚本，详细记录操作系统的版本、BIOS信息、硬件配置以及已安装的应用等数据。所有窃取的数据被转换为JSON格式，并通过HTTPS POST请求发送至命令与控制（C2）服务器。

在攻击链的下一阶段，另一条PowerShell脚本被启动，从C2服务器下载包含Node.js运行时二进制文件及JavaScript编译（JSC）文件的压缩包。Node.js可执行文件会触发JSC文件的运行，建立网络连接，并可能窃取浏览器中的敏感信息，如密码、Cookie等。此外，微软还观察到一种名为“ClickFix”的策略，即通过恶意PowerShell命令直接下载Node.js二进制文件并运行内联JavaScript代码，而非从文件加载。这种方式进一步提高了攻击的隐蔽性。内联JavaScript代码的操作包括通过网络探测识别高价值资产，将C2流量伪装为合法的Cloudflare活动以躲避监测，以及通过修改Windows注册表启动项实现持久化。

值得注意的是，Node.js作为一个开源、跨平台的JavaScript运行时环境，广泛应用于前端和后端开发，因其灵活性和高效性受到开发者青睐。然而，这次恶意活动表明，攻击者正利用Node.js的合法特性，将恶意软件与合法应用混淆，从而绕过传统安全防护机制，长期潜伏于目标环境中。这一趋势对现有的安全防护体系提出了严峻挑战。

此外，微软的披露还提到，类似攻击手段被用于其他场景。例如，安全公司CloudSEK发现了一个仿冒PDF Candy的虚假网站（域名为candyxpdf[.]com或candyconverterpdf[.]com），通过“ClickFix”社会工程学手段诱导受害者运行编码后的PowerShell命令，最终部署宗派RAT（SectopRAT，又名ArechClient2）信息窃取木马。该木马以窃取敏感数据著称，威胁性极高。安全研究员Varun Ajmera在其报告中指出，攻击者精心复制真实平台的用户界面，并注册外观相似的域名以欺骗用户，进一步凸显了社会工程学在此次活动中的核心作用。

最后，微软还指出部分活动与名为“薪资海盗”（Payroll Pirates）的黑客组织有关。该组织通过以人力资源（HR）为主题的钓鱼骗局，针对企业员工展开攻击。攻击者仿冒人力资源页面，诱骗受害者提交账户凭证及双因素认证（2FA）代码，甚至未经授权访问薪资门户，修改受害者银行账户信息，将资金转移至攻击者控制的账户。这一系列攻击手法表明，攻击者不仅技术手段高超，还对目标群体的心理和社会行为有深入研究。

综上所述，此次恶意广告活动展现了攻击者的高超技术能力和复杂策略，Node.js的滥用、社会工程学的广泛应用以及多层次的攻击链条，使其成为当前网络安全领域的一大威胁。若不及时采取有效应对措施，这类攻击可能进一步扩散，给个人和企业带来更大损失。

## 三、对我国（中国）影响分析研判

这场由Node.js驱动的恶意广告活动对我国网络安全形势具有重要影响。我国作为全球最大的互联网市场之一，拥有庞大的网民群体和快速发展的数字化经济，网络安全威胁的潜在后果不容忽视。以下从多个维度分析此次事件对我国的影响，并研判其可能的演变趋势。

首先，从用户群体角度看，我国拥有大量加密货币交易用户和Node.js开发者，这为攻击者提供了广阔的目标池。此次活动以币安等知名交易平台为诱饵，而我国用户对加密货币交易的热情和对知名平台的信任，可能导致部分用户因缺乏足够的网络安全意识而落入陷阱。此外，我国网民中仍有相当一部分人对钓鱼网站和恶意软件的辨别能力不足，尤其是在面对伪装精良的欺诈网站时，容易被社会工程学手段所迷惑。这可能导致个人信息泄露、资金损失，甚至身份盗用等问题。

其次，从企业和组织角度看，我国大量企业和开发者在使用Node.js进行前后端应用开发。Node.js的开源特性和广泛应用，使其成为攻击者利用的理想工具。此次活动中，攻击者通过Node.js运行恶意JavaScript代码，窃取敏感信息并实现持久化驻留，这种技术手段可能对我国企业的网络安全防护体系构成挑战。特别是针对人力资源主题的钓鱼攻击，可能对企业内部薪资系统和员工信息安全造成威胁。我国中小企业在网络安全投入和防护能力上普遍较为薄弱，一旦成为攻击目标，可能面临数据泄露、财务损失以及声誉受损的风险。

再次，从网络安全技术发展的角度看，此次活动显示出攻击者对传统防护机制的规避能力日益增强。攻击者通过PowerShell命令、混淆代码以及C2流量伪装等手段，成功绕过Microsoft Defender for Endpoint等主流安全软件的检测。我国网络安全技术和产品的研发虽然近年来取得显著进步，但在面对新型攻击手段时，仍存在一定滞后性。此次活动中Node.js的滥用，可能促使更多攻击者效仿类似技术路径，进一步增加我国网络安全防护的难度。此外，攻击者利用谷歌赞助广告投放恶意搜索广告的手段，也可能在我国搜索引擎和广告平台上复制，加大监管和防护的复杂性。

最后，从社会经济影响角度看，网络安全威胁的扩散可能对我国数字化经济发展造成不利影响。随着“数字中国”战略的推进，互联网经济在国民经济中的比重日益增加，网络安全成为保障经济稳定发展的重要基础。此次恶意活动不仅针对个人用户，还涉及企业员工和薪资系统，若大规模扩散，可能引发公众对数字化服务和平台安全的信任危机，进而影响数字经济相关行业的增长。此外，网络攻击导致的资金损失和数据泄露，还可能对金融系统和企业运营造成连锁反应，进一步放大社会经济损失。

综合以上分析，此次Node.js恶意广告活动对我国的潜在影响主要体现在个人用户信息安全、企业网络防护能力、网络安全技术发展以及社会经济稳定等多个方面。我国作为网络大国，面临的网络安全威胁复杂且多样，若不及时采取针对性措施，这类攻击可能进一步升级，演变为更具破坏性的网络犯罪活动。因此，亟需从技术、政策和意识等多个层面展开应对。

## 四、应对策略

针对此次Node.js恶意广告活动及其对我国的潜在威胁，需制定多层次、全方位的应对策略，涵盖技术防护、政策监管、用户教育和国际合作等方面，以有效降低攻击风险，保障网络安全。以下是具体的应对措施。

第一，在技术层面，需加强针对Node.js相关攻击的检测和防护能力。网络安全企业应加速研发针对Node.js恶意代码的检测工具，识别其运行时异常行为，并建立基于行为的动态防御机制。同时，应升级现有防病毒软件和端点安全产品，增强对PowerShell命令执行、混淆代码和C2流量伪装的识别能力。对于攻击者利用的“ClickFix”社会工程学手段，可通过实时 monitoramento 浏览器行为和脚本执行，及时拦截恶意代码的运行。此外，建议企业在内部网络中部署入侵检测系统（IDS）和入侵防御系统（IPS），加强对异常网络流量的监测，阻断与可疑C2服务器的通信。

第二，在政策和监管层面，国家相关部门应加强对网络广告平台和搜索引擎的监管力度，打击利用赞助广告投放恶意内容的违法行为。针对伪装网站的域名注册和传播，可联合域名管理机构和网络服务提供商，建立快速响应机制，及时下线恶意域名。同时，针对企业内部网络安全管理，可出台强制性政策，要求企业定期更新安全补丁、加强员工身份认证，并对敏感系统实施严格的访问控制。对于涉及人力资源和薪资系统的钓鱼攻击，可加强相关行业的网络安全标准制定，推动企业建立完善的应急响应机制。

第三，在用户教育层面，需加大网络安全意识的宣传和普及力度。针对加密货币交易用户，可通过媒体、社交平台和行业协会发布安全警示，提醒用户谨慎下载安装程序，验证网站域名真实性，避免访问不明链接。对于普通网民，应普及识别钓鱼网站和恶意软件的基本技能，例如检查网站URL是否包含拼写错误、避免点击可疑广告等。此外，可通过学校、社区和企业开展网络安全培训，提升公众对社会工程学攻击的防范意识，降低被骗概率。

第四，在企业内部管理层面，企业应加强对员工的网络安全培训，尤其是在人力资源和财务部门，需建立严格的操作规范，避免员工因误操作泄露凭据或执行恶意代码。企业还应定期进行网络安全演练，模拟钓鱼攻击场景，测试员工的应对能力。同时，建议企业采用零信任架构（Zero Trust Architecture），对内部网络访问实施严格验证，防止攻击者在获取初始访问权限后进一步扩散。此外，企业可引入第三方安全服务，通过渗透测试和威胁情报共享，及时发现潜在漏洞和攻击迹象。

第五，在国际合作层面，我国应加强与国际网络安全组织和企业的协作，共同应对跨国网络威胁。此次活动中涉及的C2服务器和恶意域名可能分布于多个国家，需通过国际执法合作追踪攻击源头，打击幕后黑客组织。同时，可参与国际网络安全标准制定，推动Node.js等开源技术的安全规范，遏制其被恶意利用的趋势。此外，通过国际威胁情报共享平台，获取最新攻击技术和趋势信息，提升国内安全防护的针对性。

## 五、结论

总的来说，微软披露的Node.js恶意广告活动揭示了网络安全威胁的新形态，攻击者通过利用开源技术的合法特性，结合社会工程学和多层次攻击链条，对个人用户、企业组织乃至整个社会经济构成了严重威胁。对我国而言，此次事件可能影响广大网民的个人信息安全、企业网络防护体系以及数字化经济的发展信心。为应对这一威胁，我国需从技术创新、政策监管、用户教育、企业管理和国际合作等多方面入手，构建全面的网络安全防御体系。只有通过多方协同努力，才能有效遏制类似攻击的扩散，保障网络空间的安全与稳定。随着网络攻击技术的不断演进，网络安全将成为我国数字化转型和经济发展的核心挑战，需持续加大投入和重视，以应对未来更为复杂的威胁形势。

**出处来源**：HackerNews 编译，转载请注明出处：  
消息来源：thehackernews；  
本文由 HackerNews.cc 翻译整理，封面来源于网络；  
转载请注明“转自 HackerNews.cc”并附上原文链接。