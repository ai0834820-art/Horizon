---
layout: default
title: "Horizon Summary: 2026-11-27 (ZH)"
date: 2026-11-27
lang: zh
---

> 从 36 条内容中筛选出 4 条重要资讯。

---

**科技新闻**
1. [英伟达据报暂停对东南亚四国 AI 服务器出货](#item-tech-news-1) ⭐️ 8.0/10
2. [Google 计划让 AI 代理接入 Workspace MCP，Gmail 服务器不能发信](#item-tech-news-2) ⭐️ 7.0/10
3. [Neuralink 获 FDA 批准启动渐冻症脑机接口关键试验](#item-tech-news-3) ⭐️ 7.0/10
4. [荷兰称不接受美国 MATCH Act 限制 ASML 对华销售](#item-tech-news-4) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [英伟达据报暂停对东南亚四国 AI 服务器出货](https://www.ft.com/content/7838a715-07d4-4605-aa60-21f5af2b2370) ⭐️ 8.0/10

据《金融时报》报道，英伟达已要求主要制造伙伴暂停向马来西亚、新加坡、泰国和印度尼西亚发运 AI 服务器；戴尔、美超微等将英伟达芯片组装成整机的厂商已通知四国买家，相关订单不能出厂。三名知情人士称，此次冻结与美国新一轮出口管制有关，但是否为临时措施尚不清楚。美国商务部上周出台的新规要求区域云服务商在 90 天内取得出口许可，并核实客户不包含受限制的中国实体；这四个国家此前是中国 AI 公司获取英伟达最先进处理器的中转地，相关芯片不得直接出口中国大陆。

telegram · zaihuapd · 11月26日 07:38

**「背景」** 此前美国已禁止英伟达最先进处理器直接出口中国大陆，马来西亚、新加坡、泰国和印度尼西亚因此成为中国 AI 公司获取这些芯片的中转地。此次冻结对应美国商务部上周发布的新规：区域云服务商须在 90 天内取得出口许可，并核实客户中不含受限的中国实体。

**「对区域云服务商与买家的直接影响」** 对马来西亚、新加坡、泰国和印度尼西亚的云服务商与服务器买家而言，直接影响是相关 AI 服务器订单无法出厂，且新规要求他们在 90 天内取得出口许可并核实终端客户不包含受限中国实体。由于有云厂商高管称新规“没有执行指引”，这些客户需要预留合规审查与许可等待时间，短期内难以确认交付时间表。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.zerohedge.com/ai/nvidia-halts-ai-chip-shipments-four-southwest-asian-countries">&quot;Causing Sheer Chaos&quot;: Nvidia Halts AI Chip Shipments ... | ZeroHedge</a></li>
<li><a href="https://nypost.com/2026/11/26/business/nvidia-halts-server-shipments-to-4-southeast-asian-countries-report/">Nvidia halts server shipments to 4 Southeast Asian countries: report</a></li>

</ul>
</details>

**标签**: `#export-controls`, `#nvidia`, `#ai-hardware`, `#supply-chain`, `#geopolitics`

---

<a id="item-tech-news-2"></a>
### [Google 计划让 AI 代理接入 Workspace MCP，Gmail 服务器不能发信](https://techstackups.com/articles/google-workspace-ai-agents-mcp/) ⭐️ 7.0/10

Google 计划让 Workspace 的 AI 代理使用其 MCP 服务器，但其中 Gmail 服务器被限制为不能发送邮件。该消息目前只披露了这一能力边界，尚未说明上线时间、版本或具体可用范围，因此应视为计划中的能力，而非已交付功能。

hackernews · ritzaco · 11月26日 09:44 · [社区讨论](https://news.ycombinator.com/item?id=50653477)

**「背景：MCP 与 Gmail 服务器的既有能力」** Model Context Protocol（MCP）是一种让 AI 代理以标准化方式调用外部服务和数据的接口规范，Google 据此为 Workspace 提供 MCP 服务器，使代理能够接入 Gmail 等产品。根据 Google 面向开发者的 Gmail MCP 服务器文档，该服务器对外暴露的能力集中在读取侧：搜索邮件、获取邮件会话和列出标签。也就是说，发送邮件从一开始就不在其公开的工具范围内，这也解释了为何围绕“代理如何发信”会出现 SMTP/IMAP 等替代路径的讨论。

**「影响」** 对需要代理自动发信的用户来说，Gmail MCP 不发信意味着要改用浏览器自动化或 SMTP/IMAP 等外部路径，流程更复杂且可能产生额外成本；这些绕行方案也未必符合平台的使用条款。

**「社区讨论」** 评论对 Gmail MCP 不发信的限制看法不一：有人认为用户会让代理操作浏览器发信，既混乱又浪费；也有人指出 MCP 的 elicitation 已能在工具调用前请求用户确认，因此仅限合作伙伴更像商业决策而非安全需要。另有用户称用 NeoMutt 走 SMTP+IMAP 给代理接入 Gmail，比其试过的 MCP 更可靠。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://developers.google.com/workspace/gmail/api/guides/configure-mcp-server">Configure the Gmail MCP server | Google for Developers</a></li>

</ul>
</details>

**标签**: `#Model Context Protocol`, `#Google Workspace`, `#AI agents`, `#Gmail`, `#API access`

---

<a id="item-tech-news-3"></a>
### [Neuralink 获 FDA 批准启动渐冻症脑机接口关键试验](https://www.bloomberg.com/news/articles/2026-11-25/neuralink-gets-clearance-for-brain-implant-trial-in-als-patients?srnd=phx-technology) ⭐️ 7.0/10

Neuralink 宣布已获 FDA 批准，将在美国启动名为“LINK”的植入式脑机接口关键临床试验，面向渐冻症患者招募，目标是把大脑信号直接转化为计算机控制指令。该公司称，这是美国首个获批的此类关键试验；此前其早期研究已在全球为超过 30 名瘫痪患者植入设备。此次获批意味着进入以未来医疗器械上市许可为目标的关键临床阶段，相关数据将作为申请上市的核心依据，但目前尚属试验授权，并非已公布结果或已上市产品。

telegram · zaihuapd · 11月26日 07:15

**「背景」** 关键临床试验（pivotal trial）通常是医疗器械上市前用于收集主要安全性和有效性证据的人体研究，其结果将进入监管审评。Neuralink 此前通过早期研究已在全球为超过 30 名瘫痪患者植入设备；此次针对渐冻症的试验，是把该植入式脑机接口推进到上市审批所需证据阶段的下一步。

**「对患者的影响」** 对于因渐冻症导致严重瘫痪的患者，LINK 关键试验提供了一条在商业化上市前接受这种植入式脑机接口治疗的受监管途径；但 FDA 此次批准的是试验，并非疗法本身，因此患者目前只能在试验范围内使用该设备，无法将其作为常规治疗获得。该试验产生的数据将作为未来申请上市许可的核心依据，所以受试者招募与随访的进展，将决定这种设备何时可能面向更广泛的患者。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://interestingengineering.com/health/neuralink-fda-approval-link-pivotal-brain-implant-trial">Neuralink gets FDA approval for first pivotal brain implant trial</a></li>

</ul>
</details>

**标签**: `#brain-computer interface`, `#Neuralink`, `#FDA regulation`, `#clinical trials`, `#neurotechnology`

---

<a id="item-tech-news-4"></a>
### [荷兰称不接受美国 MATCH Act 限制 ASML 对华销售](https://www.bloomberg.com/news/articles/2026-11-26/netherlands-plans-to-fight-rollout-of-proposed-us-curbs-on-asml) ⭐️ 7.0/10

荷兰外贸与发展合作大臣 Sjoerd Sjoerdsma 于 11 月 26 日在议会表示，荷兰不会接受美国进一步限制 ASML 对华销售，并反对 MATCH Act 的域外管辖效力。荷兰正与欧盟委员会协调，同时联合德国、法国展开游说，争取把该法案从美国年度国防政策法案中剔除。MATCH Act 由美国两党共同提出，要求荷兰、日本等盟友对华实施更严格的出口管制，否则美方将单方面限制其半导体设备；中国约占 ASML 今年销售额的 20%。外界预计美国国会将在 12 月中旬表决，通过的可能性很大。

telegram · zaihuapd · 11月26日 14:56

**「背景」** MATCH Act 是美国国会提出的对华芯片管制法案，要求荷兰、日本等盟友对华实施更严格的半导体设备出口管制，否则美方将单方面限制相关设备出口；今年 4 月的报道称，该法案为与盟友的谈判设定期限，期限过后即授权美方实施管制。荷兰议会此前也已呼吁政府抵制这一法案。

**「影响」** 若 MATCH Act 按现文通过，荷兰、日本等盟友的半导体设备商对华销售将面临更严格管制，否则可能被美方单方面限制。对 ASML 而言，中国约占其今年销售额的 20%，这一法案及荷兰的游说结果直接关系其对华出货安排。

<details><summary>参考链接</summary>
<ul>
<li>Dutch lawmakers urge government to resist US MATCH bill targeting ASML</li>
<li>U.S. Lawmakers Scale Back Bill Targeting Chinese Chipmaking</li>

</ul>
</details>

**标签**: `#semiconductors`, `#export controls`, `#ASML`, `#US-China relations`, `#tech policy`

---