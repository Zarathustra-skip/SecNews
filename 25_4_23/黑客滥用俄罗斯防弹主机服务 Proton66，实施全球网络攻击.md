# Proton66网络威胁激增：全球安全挑战与应对策略分析

## 一、事件概述

近期，网络安全研究人员披露了一项与俄罗斯防弹主机服务商Proton66相关的重大网络安全威胁。据Trustwave SpiderLabs发布的两阶段分析报告，自2025年1月8日起，研究人员检测到与Proton66关联的IP地址出现了大规模扫描、凭证暴力破解以及漏洞利用尝试的激增现象。这些活动针对全球范围内的组织机构，涉及多个高危漏洞的利用和恶意软件的传播，包括GootLoader、SpyNote、XWorm、StrelaStealer及新型勒索软件SuperBlack等。这一事件不仅揭示了网络犯罪团伙日益猖獗的技术手段，也对全球网络安全格局构成了严峻挑战。

## 二、事件描述分析

### 1. Proton66网络威胁的背景与关联性

Proton66作为一家俄罗斯防弹主机服务商，以提供难以追踪和关闭的服务器基础设施而闻名，这使其成为网络犯罪分子的理想选择。Trustwave SpiderLabs的报告显示，与Proton66关联的IP段，如45.135.232.0/24和45.140.17.0/24，自2025年初以来表现出异常活跃的恶意行为。这些IP地址中，有的部分此前长期处于休眠状态，甚至超过两年未参与任何恶意活动，但近期突然被激活用于大规模扫描和暴力破解。

进一步调查发现，Proton66与另一俄罗斯自治系统PROSPERO存在密切联系。法国安全公司Intrinsec此前曾披露，这两个系统与俄语网络犯罪论坛中以Securehost和BEARHOST名义销售的防弹服务密切相关。此外，安全记者Brian Krebs揭露，PROSPERO近期通过俄罗斯杀毒软件厂商卡巴斯基实验室运营的网络进行路由，尽管卡巴斯基否认与PROSPERO直接合作，并解释其网络路径可能仅作为技术前缀出现在与之合作的电信供应商网络中。

### 2. 具体的恶意活动与技术手段

Trustwave的最新分析详细记录了Proton66关联IP地址发起的多种恶意活动。首先，研究人员发现自2025年2月起，IP段193.143.1.65试图利用多个高危漏洞，包括Palo Alto Networks PAN-OS的认证绕过漏洞（CVE-2025-0108）、Mitel MiCollab的输入验证不足漏洞（CVE-2024-41713）、D-Link NAS的命令注入漏洞（CVE-2024-10914），以及Fortinet FortiOS的认证绕过漏洞（CVE-2024-55591和CVE-2025-24472）。其中，利用Fortinet漏洞的攻击行为被归因于初始访问中间商Mora_001，该实体还被发现投放新型勒索软件SuperBlack。

其次，Proton66的基础设施被用于托管多个恶意软件家族的命令与控制（C2）服务器和钓鱼页面。例如，IP地址91.212.166.21通过被入侵的WordPress网站，将安卓设备用户重定向至仿冒Google Play应用列表的钓鱼页面，诱导用户下载恶意APK文件。这些攻击活动专门针对法语、西班牙语和希腊语用户，采用复杂的混淆脚本和反检测机制，如通过ipify.org和ipinfo.io验证用户是否使用VPN或代理，并仅在检测到安卓浏览器时实施重定向。

此外，研究人员还在Proton66关联的IP地址中发现针对韩语聊天室用户的的社会工程攻击，攻击者通过ZIP压缩包传播XWorm恶意软件，利用PowerShell和Visual Basic脚本执行多阶段加载，最终加载恶意二进制文件。类似地，针对德语用户的钓鱼邮件活动传播信息窃取软件StrelaStealer，其C2服务器同样托管在Proton66网络中（IP地址193.143.1.205）。另外，勒索软件WeaXor（Mallox的修订版本）也与Proton66的C2服务器（IP地址193.143.1.139）通信。

### 3. Proton66威胁的特征与发展趋势

从技术角度看，Proton66关联的网络威胁呈现出高度组织化和多样化的特征。攻击者不仅利用最新的高危漏洞，还结合社会工程、钓鱼攻击和多阶段恶意软件加载等多种手段，针对不同地区和语言群体的用户实施精准打击。这种攻击模式的复杂性和灵活性表明，背后可能存在专业的网络犯罪团伙支持。

此外，Proton66的基础设施能够长期逃避执法追踪，其与香港服务商Chang Way Technologies的潜在关联也增加了威胁溯源的难度。Trustwave的研究表明，Proton66不仅是恶意软件的托管平台，还充当了网络犯罪的“枢纽”，通过与其他防弹主机服务商和自治系统的协作，为网络犯罪活动提供持续支持。这种趋势显示，未来的网络威胁可能更加隐蔽且难以根除。

## 三、对我国（中国）影响分析研判

### 1. 直接威胁：基础设施与企业的安全性风险

Proton66关联的网络威胁对我国网络安全构成了多方面的直接影响。首先，我国作为全球最大的互联网市场之一，拥有大量的企业、机构和个人用户，极易成为网络犯罪分子的攻击目标。此次披露的恶意活动涉及多个高危漏洞的利用，如Palo Alto Networks、Fortinet和D-Link等设备中存在的漏洞，而这些设备在我国企业中广泛应用。一旦攻击者成功利用这些漏洞，可能导致企业系统被入侵、数据泄露甚至勒索软件感染，造成严重的经济损失和声誉损害。

其次，Proton66基础设施针对安卓用户的钓鱼攻击也对我国个人用户构成威胁。我国安卓设备用户数量庞大，且部分用户对网络安全意识相对较弱，容易成为仿冒Google Play应用列表等钓鱼攻击的受害者。这些攻击可能导致用户隐私数据被窃取，甚至设备被远程控制，进一步威胁个人财产安全。

### 2. 间接影响：国际合作与产业信任危机

从间接影响来看，Proton66网络威胁可能对我国与国际社会的网络安全合作产生不利影响。尽管此次威胁源于俄罗斯的基础设施，但其攻击目标遍及全球，包括我国在内的多个国家。这种跨国网络犯罪活动可能加剧国际间在网络安全问题上的信任危机，尤其是在网络攻击溯源和责任划分方面存在争议的情况下，可能导致国际合作机制受阻。

此外，考虑到Proton66与卡巴斯基等俄罗斯企业的潜在关联，尽管卡巴斯基否认直接合作，但这一事件可能进一步动摇国际社会对俄罗斯网络安全企业的信任。我国企业在与俄罗斯相关企业开展技术合作或采购安全产品时，可能面临额外的审查和风险，从而影响相关产业的发展。

### 3. 长期影响：网络安全态势的复杂化

从长期来看，Proton66网络威胁的持续活跃凸显了防弹主机服务在网络犯罪中的关键作用。这种难以追踪和关闭的基础设施可能刺激更多犯罪团伙效仿，进一步加剧全球网络安全态势的复杂性。对于我国而言，这意味着网络安全防御需要不断升级，不仅要应对已知的漏洞和恶意软件，还要预防未知威胁和新型攻击手段。

同时，我国作为“一带一路”倡议的推动者，积极参与国际互联网治理和数字经济合作，网络安全问题直接关系到国家形象和国际影响力。如果国内企业或机构因Proton66相关威胁遭受重大损失，可能对我国在国际网络空间中的话语权和信誉造成不利影响。

## 四、应对策略

### 1. 技术层面的防御措施

针对Proton66关联的网络威胁，我国应采取多层次的技术防御措施。首先，建议各组织和企业根据Trustwave的建议，封锁所有与Proton66及疑似关联的香港服务商Chang Way Technologies相关的无类别域间路由（CIDR）范围，以阻止潜在的恶意流量。其次，加强对关键基础设施和设备的漏洞管理，及时修补Palo Alto Networks、Fortinet、D-Link等设备中的已知漏洞，防止攻击者利用这些漏洞实施入侵。

此外，针对安卓用户面临的钓鱼威胁，应推动安全厂商和应用商店加强恶意应用的检测与拦截，同时通过公共宣传提高用户的安全意识，提醒用户避免下载来源不明的APK文件。对于企业内部网络，应部署入侵检测系统（IDS）和入侵防御系统（IPS），实时监控网络流量，及时发现并阻止扫描、暴力破解等异常行为。

### 2. 政策与法律层面的应对

在政策层面，我国应进一步完善网络安全法律法规，加大对网络犯罪的打击力度，特别是针对防弹主机服务等灰色产业的监管。通过与国际执法机构的合作，共同打击跨境网络犯罪，切断类似Proton66的基础设施支持。同时，可考虑制定更严格的网络安全标准，要求企业在采购网络安全产品和服务时，进行充分的安全评估，避免引入潜在风险。

### 3. 国际合作与信息共享

网络威胁的全球化特性决定了单一国家难以独自应对此类问题。我国应积极参与国际网络安全合作，加强与国际组织和其他国家的 Threat Intelligence（威胁情报）共享，及时获取Proton66及类似威胁的最新动态。此外，可通过多边平台如联合国框架下的网络安全工作组，推动制定针对防弹主机服务的国际规范，遏制其在网络犯罪中的作用。

### 4. 提升全民网络安全意识

针对社会工程和钓鱼攻击的特点，我国应加大网络安全教育力度，通过媒体、社区和学校等多种渠道，向公众普及网络安全知识。例如，针对安卓用户，可以制作简短的教育视频，教导用户如何识别钓鱼网站和恶意应用；针对企业.employee，可以定期开展网络安全培训，提升员工对恶意邮件和社交工程攻击的警惕性。

### 5. 推动自主技术研发

从长期战略角度，我国应加快网络安全领域的自主技术研发，减少对国外安全产品和服务的依赖。通过支持国产网络安全企业的发展，构建独立的网络安全生态系统，提升对新型威胁的响应能力。同时，鼓励产学研结合，加大对网络威胁情报分析、恶意软件逆向工程等前沿技术的研究，为应对未来类似Proton66的威胁奠定技术基础。

## 五、结论

Proton66关联的网络威胁事件揭示了网络犯罪团伙在技术手段和组织形式上的高度复杂性，其针对全球组织和个人的攻击活动对网络安全构成了严峻挑战。对于我国来说，这一事件不仅直接威胁到企业和个人的数据安全，还可能对国际合作和国家形象产生深远影响。为此，我国需要从技术、政策、国际合作和公众教育等多个层面采取综合措施，强化网络安全defense能力，防范类似威胁的进一步扩大。同时，应以此次事件为契机，加快自主网络安全技术的发展，构建更加坚韧的网络安全体系，为数字经济和国家安全保驾护航。只有通过多方协作和持续努力，才能有效应对日益复杂的网络威胁，维护网络空间的和平与稳定。

**出处来源：**  
消息来源：thehackernews；  
本文由 HackerNews.cc 翻译整理，封面来源于网络；  
转载请注明“转自 HackerNews.cc”并附上原文链接。