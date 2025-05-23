# Inferno Drainer 卷土重来：网络犯罪新威胁的深度剖析

## 一、事件概述

    近期，网络安全公司 Check Point Research 发布了一份重要报告，揭露了名为 Inferno Drainer 的网络犯罪工具的复苏与进化。Inferno Drainer 是一种“Drainer-as-a-Service”（即服务型勒索工具）的典型代表，尽管其开发者曾宣布关闭该项目，但报告显示其不仅仍在运作，还通过技术升级和策略调整变得更加危险，对加密货币用户构成了前所未有的威胁。该工具利用伪装成合法 Web3 项目网站的钓鱼链接，诱导用户进入恶意 Discord 服务器，并通过假冒的 Collab.Land 机器人窃取用户钱包权限。自 2024 年 9 月至 2025 年 3 月，已有超过 3 万个钱包被盗，损失总额超过 900 万美元，部分用户单次损失高达 76.1 万美元。这一事件的持续性和破坏力，凸显了网络犯罪工具在技术与组织模式上的高度进化。

## 二、事件描述分析

    Inferno Drainer 的复苏并不是简单的重启，而是一种全面的技术升级和策略优化。其运作模式展现了现代网络犯罪的高度组织化与智能化特征，具体表现在以下几个方面：

    首先，Inferno Drainer 的攻击链条设计极为精妙。攻击通常始于一个看似合法的 Web3 项目网站上的邀请链接，将用户引导至一个 Discord 服务器。在服务器内，一个伪装成 Collab.Land 的机器人会要求用户进行“钱包验证”。这一步骤利用了用户对常规流程的信任心理，许多加密货币用户习惯于在类似场景中连接钱包并授权签名。然而，用户并未连接至真正的 connect.collab.land 网站，而是被引导至一系列恶意重定向链接，最终到达一个完全仿冒 Collab.Land 界面的钓鱼网站。一旦用户在假网站上点击“批准”，攻击者便通过签名交易获得对用户钱包的完全控制权。Check Point 报告特别指出，即便是经验丰富的加密货币用户，也可能因为疏忽而落入陷阱，因为他们往往会本能地完成授权流程，而未仔细检查链接或界面的真实性。

    其次，Inferno Drainer 的钓鱼基础设施展现了极高的技术复杂性。为了规避传统的 URL 检测机制，该工具使用短寿命的 OAuth2 令牌，使恶意链接难以被追踪和封锁。同时，其智能合约值在币安智能链（Binance Smart Chain）上采用 Base64 和 ROT13 编码，进一步隐藏恶意代码。对于数据传输，Inferno Drainer 还使用了四层 AES 加密的 JSON 负载，确保即便是截获数据也难以解密。此外，其命令与控制（C2）地址被隐藏在区块链合约中，使得传统的网络安全工具难以定位其核心服务器。这种多层次的加密与隐藏技术，不仅提高了攻击的隐蔽性，也让黑名单机制和钱包警告系统几乎失效。

    再者，Inferno Drainer 的后端基础设施同样极具抗打击能力。其核心系统隐藏在 Cloudflare Workers 和客户部署的代理服务器背后，这种分布式架构使得直接攻击或关闭其服务器变得极为困难。在资金转移方面，攻击者通过假冒的 ERC-20 代币合约、接收合约以及一次性使用的临时合约，将被盗资金快速转移。这种“用后即弃”的合约部署策略，使得传统的反钓鱼措施难以通过黑名单机制封锁资金流向。正如 Check Point 报告所指出的，这种策略是攻击者有意为之，旨在通过频繁更换合约地址来绕过任何可能的预警机制。

    此外，Inferno Drainer 的经济模型也显示出其高度商业化的特征。其开发者以“服务提供商”的身份运营，收取 15%-20% 的佣金，而剩余的收益则分配给与其合作的犯罪附属团体。这种地下 SaaS（软件即服务）模式，不仅降低了技术门槛，让更多犯罪分子能够参与其中，也让 Inferno Drainer 的开发者得以专注于工具的开发与优化，而无需直接参与具体的攻击行动。据统计，自 2024 年 9 月至 2025 年 3 月，Inferno Drainer 已导致超过 3 万个钱包被盗，累计损失超过 900 万美元，单笔最高损失记录为 76.1 万美元。这一数据表明，Inferno Drainer 已不再是单一的恶意工具，而是一个成熟的网络犯罪生态系统。

    最后，Inferno Drainer 的进化还体现在其对用户心理的精准把握上。其钓鱼工具与合法服务的界面几乎无异，利用了用户对熟悉流程的信任。报告指出，随着钓鱼工具的伪装能力不断提升，传统钱包安全机制正在逐渐失效，用户自身的警惕性和安全意识成为了最后一道防线。这种趋势表明，网络犯罪已从单纯的技术攻击转向结合社会工程学的综合性威胁。

## 三、对中国的影响分析研判

    Inferno Drainer 的复苏与进化，对包括中国在内的全球加密货币用户构成了严重威胁。作为全球加密货币交易和区块链技术应用的重要市场，中国用户和企业在这一事件中面临多重风险，具体影响可以从以下几个方面进行分析：

    首先，中国加密货币用户的直接经济损失风险不容忽视。尽管中国在国内对加密货币交易实施了严格监管，但仍有大量用户通过海外平台或去中心化金融（DeFi）应用参与加密货币投资与交易。这些用户往往通过 VPN 等工具绕过区域限制，访问国际 Web3 项目和 Discord 社区，而这正是 Inferno Drainer 攻击的主要目标场景。考虑到中国用户在全球加密货币市场中的重要占比，一旦大规模用户钱包被盗，不仅会造成个人经济损失，还可能引发对国内相关行业的信心危机。根据 Check Point 的数据，全球已有 3 万个钱包被盗，损失超 900 万美元，而中国用户的具体受损规模虽未明确，但可以推测占比不小。此外，部分中国用户可能因缺乏足够的网络安全知识，更容易成为攻击目标，进一步加剧损失风险。

    其次，Inferno Drainer 的攻击模式可能对中国区块链企业和技术生态造成间接冲击。中国近年来大力发展区块链技术，尤其是在数字人民币和供应链金融等领域。然而，Inferno Drainer 利用区块链智能合约隐藏恶意代码、实施资金转移的技术手段，可能对区块链技术的公信力产生负面影响。尤其是其针对 Web3 项目和 DeFi 应用的攻击，可能让部分中国用户和企业对区块链技术的安全性产生疑虑，进而影响相关技术在国内的推广与应用。此外，若有中国背景的 Web3 项目或 Discord 社区被攻击者伪装或利用，不仅会损害项目方的声誉，还可能引发国际合作中的信任问题。

    再者，Inferno Drainer 的地下 SaaS 模式可能对中国网络安全形势带来新的挑战。其高度组织化的运作方式和低门槛的参与条件，可能吸引国内一些不法分子加入其附属犯罪网络。特别是在当前国内网络安全监管力度不断加强的背景下，这种跨境网络犯罪工具可能成为监管盲区。一方面，攻击者利用 Cloudflare Workers 和代理服务器隐藏核心基础设施，增加了国内执法机构追踪和打击的难度；另一方面，其资金转移依赖区块链合约的匿名性，传统的金融监管手段难以有效应对。这种新型网络犯罪模式，可能进一步加剧国内网络安全环境的复杂性。

    最后，Inferno Drainer 的复苏还可能对中国用户的数字安全意识和教育提出更高要求。尽管中国在网络安全宣传方面已取得一定成效，但加密货币和区块链领域的安全教育仍显不足。许多用户对钓鱼攻击的伪装手法缺乏足够认识，容易因信任惯性而授权恶意链接。此外，国内网络安全工具和钱包应用在应对此类新型攻击时，可能因缺乏针对性更新而显得力不从心。若不及时加强用户教育和技术防护，类似的攻击可能在国内用户中引发更广泛的损失。

## 四、应对策略

    面对 Inferno Drainer 带来的新型网络犯罪威胁，中国需要在用户教育、技术防护、监管合作以及国际协作等多层面采取综合应对措施，以降低风险并保护用户与行业利益。以下是具体的应对策略：

    首先，加强用户安全教育，提升公众的数字安全意识。针对加密货币和 Web3 领域的特殊性，政府和相关机构应加大宣传力度，通过线上课程、短视频、社区活动等形式，向用户普及钓鱼攻击的常见手段和防范技巧。例如，提醒用户在连接钱包或授权签名时，务必核对链接地址和界面细节，避免因惯性操作而落入陷阱。此外，可鼓励加密货币相关社区和平台发布安全指南，定期更新最新的攻击模式和防护建议。对于普通用户而言，建立“多重验证”的操作习惯，例如使用硬件钱包或多重签名机制，也能在关键时刻提供额外保护。

    其次，强化技术防护措施，开发更智能的安全工具。国内网络安全企业应针对 Inferno Drainer 的技术特点，升级现有的反钓鱼和钱包保护系统。例如，开发能够实时检测短寿命 OAuth2 令牌和多重加密数据包的工具，同时加强与区块链节点的协作，监测异常合约部署和资金流向。此外，钱包应用开发者应内置更严格的授权审核机制，例如在用户签名时弹出详细的权限说明，降低误授权的风险。政府还可支持区块链安全实验室的建设，鼓励企业与高校合作研究新型网络犯罪技术，以便及时更新防护手段。

    再者，完善国内监管机制，填补跨境网络犯罪的监管空白。尽管加密货币交易在国内受到严格限制，但对于跨境网络犯罪的监管仍需进一步加强。相关部门可与国内互联网企业合作，建立专门的网络安全情报共享平台，实时监控钓鱼网站和恶意链接的传播动态。同时，针对区块链资金转移的匿名性特点，可探索与区块链分析公司合作，利用链上数据追踪被盗资金的流向，为受害用户追回损失提供支持。此外，针对地下 SaaS 模式的特点，可通过加强网络实名制和跨境支付监管，切断不法分子参与此类犯罪网络的经济动机。

    最后，积极参与国际合作，共同打击新型网络犯罪。Inferno Drainer 的全球性威胁表明，单一国家难以独自应对此类问题。中国应加强与国际网络安全组织和其他国家的合作，共同制定反网络钓鱼和区块链犯罪的国际标准。例如，通过参与国际刑警组织（Interpol）或亚太经合组织（APEC）框架下的网络安全工作组，共享威胁情报和技术资源，联合打击 Inferno Drainer 的核心基础设施。此外，可与 Cloudflare 等国际服务提供商开展对话，要求其加强对恶意代理服务器的审核力度，压缩攻击者的活动空间。

## 五、结论

    Inferno Drainer 的复苏与进化，不仅标志着网络犯罪工具在技术与组织模式上的重大升级，也为全球加密货币用户和区块链行业敲响了警钟。其精妙的攻击链条、高度隐蔽的基础设施以及商业化的 SaaS 模式，充分体现了现代网络犯罪的复杂性和破坏力。对于中国而言，这一事件可能带来直接的经济损失、区块链技术信任危机以及网络安全监管挑战等多重影响。为有效应对这一新型威胁，中国需要在用户教育、技术防护、国内监管和国际合作等方面采取综合措施，构建全方位的安全防线。只有通过多主体协同努力，才能最大程度降低类似攻击的风险，保护用户权益和数字经济的安全发展。未来的网络安全博弈将更加复杂，中国应以此次事件为契机，加速提升网络安全能力，为数字时代的长远发展奠定坚实基础。

**出处**：本文基于 Check Point Research 发布的关于 Inferno Drainer 的报告撰写，部分数据和描述直接引用或改编自报告内容。