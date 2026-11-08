---
layout: default
title: "Horizon Summary: 2026-11-08 (EN)"
date: 2026-11-08
lang: en
---

> From 37 items, 10 important content pieces were selected

---

**Technology News**
1. [SemiAnalysis Visits Envision’s 800MW Galaxy AI Campus in Inner Mongolia](#item-tech-news-1) ⭐️ 8.0/10
2. [Microsoft Research&\#x27;s AI Frontiers group reportedly ends as John Langford exits](#item-tech-news-2) ⭐️ 7.0/10
3. [Committed Claude Code settings exposed secrets in 1,122 public GitHub files](#item-tech-news-3) ⭐️ 7.0/10
4. [A $10 OpenStick Homelab Built Around Lightweight Self-Hosting](#item-tech-news-4) ⭐️ 7.0/10
5. [Asahi Linux report cites same-day Fedora Asahi Remix, licensing concerns](#item-tech-news-5) ⭐️ 7.0/10
6. [Coldframe Honeypot Mimics Danfoss and Dixell Fridge Controllers](#item-tech-news-6) ⭐️ 7.0/10
7. [MaxxBench tests whether DeepSWE scores survive task-spec changes](#item-tech-news-7) ⭐️ 7.0/10
8. [Undocumented Apple Intelligence daemons on macOS build a personal knowledge graph](#item-tech-news-8) ⭐️ 7.0/10
9. [Claude Code Reportedly Leaks Login Email During Web Searches](#item-tech-news-9) ⭐️ 7.0/10
10. [GitHub&\#x27;s Rubicon Git storage targets AI-agent concurrency, hits 7,200 pushes/sec in tests](#item-tech-news-10) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [SemiAnalysis Visits Envision’s 800MW Galaxy AI Campus in Inner Mongolia](https://newsletter.semianalysis.com/p/we-visited-chinas-stargate-in-inner) ⭐️ 8.0/10

A SemiAnalysis site visit to Inner Mongolia’s Galaxy datacenter campus documents a large Chinese AI infrastructure buildout in Ulanqab, planned for up to 800MW of IT capacity. The first 120MW phase was delivered within a year at a fifth of U.S. costs, and all four phases are built-to-suit for two unnamed internet giants. Owner Envision Group supplies the campus with its own wind farms and a dedicated power line, and it designed or manufactured key electrical equipment including the 800V system, battery storage, low-voltage power modules and a prefabricated substation. SemiAnalysis compares the site with Stargate Abilene, but the excerpt gives no details on compute hardware, tenants or utilization, so the comparison concerns datacenter delivery and cost rather than AI performance.

rss · Semianalysis · Nov 7, 19:01

**「Background」** Stargate Abilene — a gigawatt-scale campus in Texas built for OpenAI — has become the symbolic benchmark for US AI infrastructure. China has comparable-scale datacenter campuses, but few people outside the country have seen inside them, which makes SemiAnalysis&\#x27;s on-site visit to Ulanqab&\#x27;s Galaxy campus a rare direct look at China&\#x27;s buildout.

**「Impact」** For datacenter operators and the two tenant internet companies, Galaxy sets a concrete infrastructure benchmark: 120MW delivered in about a year at roughly one-fifth of U.S. costs, with power supply bundled by the landlord. Matching that cost structure would require similar vertical integration, and the excerpt does not establish whether the campus has secured accelerators or is running production AI workloads.

**Tags**: `#AI datacenters`, `#China AI infrastructure`, `#datacenter economics`, `#compute infrastructure`, `#Inner Mongolia`

---

<a id="item-tech-news-2"></a>
### [Microsoft Research&\#x27;s AI Frontiers group reportedly ends as John Langford exits](https://hunch.net/?p=13764006) ⭐️ 7.0/10

Microsoft Research&\#x27;s AI Frontiers group is reportedly being shut down, and researcher John Langford is exiting, according to a Hacker News link post pointing to an archived article. The supplied material does not include a Microsoft statement, an effective date, or details on what happens to the group&\#x27;s staff and projects, so the change is not independently confirmed here. The report concerns an internal exploratory AI research group, not Microsoft Research as a whole.

hackernews · srean · Nov 7, 18:02 · [Discussion](https://news.ycombinator.com/item?id=50406563)

**「Background」** AI Frontiers was a Microsoft Research group that John Langford, a partner researcher manager at Microsoft Research New York, described as trying to organize coherent research efforts somewhere between top-down and bottom-up direction. Langford announced the group&\#x27;s end in a November 6 post on his Machine Learning \(Theory\) blog.

**「Impact」** For Microsoft Research staff and external collaborators tied to AI Frontiers, the reported closure would remove an institutional home for exploratory AI work without a stated path for ongoing projects; the supplied account does not specify whether work will continue, move to another group, or end.

**「Community discussion」** Commenters argued over whether the closure signals a broader retreat from exploratory AI research: one said large companies are concentrating on transformer scaling and discouraging alternative approaches, while another argued that research and scaling are both necessary and should not be starved of resources. Another commenter described Microsoft Research&\#x27;s implicit “do good work and good things happen” bargain as broken under current leadership, an opinion rather than a confirmed account.

<details><summary>References</summary>
<ul>
<li><a href="https://businessexaminer.ca/victoria-articles/item/microsoft-researcher-john-langford-exits-as-ai-frontiers-group-is-declared/">Microsoft Researcher John Langford Exits as AI Frontiers Group ...</a></li>
<li><a href="https://hunch.net/?p=13764006">The End of AI Frontiers – Machine Learning (Theory)</a></li>

</ul>
</details>

**Tags**: `#Microsoft Research`, `#AI research strategy`, `#organizational changes`, `#transformer scaling`, `#John Langford`

---

<a id="item-tech-news-3"></a>
### [Committed Claude Code settings exposed secrets in 1,122 public GitHub files](https://apiiro.com/blog/coding-agents-leaking-secrets-github-dont-ask-again) ⭐️ 7.0/10

A security report identified 1,122 files in public GitHub repositories where developers had committed Claude Code&\#x27;s .claude/settings.local.json, and some approved commands in those files contained passwords or keys. The exposure is not caused by pressing “Don&\#x27;t Ask Again” alone: it requires committing the local settings file after approving a command that embeds a secret. Boris from the Claude Code team said the tool has not done secret scrubbing but is investigating prevention; the file is meant to stay local and is automatically gitignored when Claude creates it, though these files were manually created and checked in.

hackernews · shmulc · Nov 7, 20:45 · [Discussion](https://news.ycombinator.com/item?id=50407882)

**「Background」** Claude Code&\#x27;s permission settings support allow, ask, and deny rules; choosing &quot;Don&\#x27;t Ask Again&quot; records an allow decision in a settings file, which can be the project-local \`.claude/settings.local.json\`. That file is meant to stay local and is automatically gitignored when Claude Code creates it, but a manually checked-in copy publishes the saved command text.

**「What to check」** Because Claude Code gitignores \`.claude/settings.local.json\` only when it writes the file itself, repositories where the file was created and committed manually can retain approved commands with inline secrets; owners should scan committed \`.claude/\` directories and rotate any credentials found. A separate April 2026 study cited by a security vendor found 33 of 428 npm packages shipping this file contained live Anthropic credentials, indicating the pattern is not confined to one project.

**「Community discussion」** Commenters criticized the headline as misleading, emphasizing that exposure requires committed local settings with secrets embedded in approved commands. Others described stricter safeguards, such as using an ephemeral VM with restricted API access per task or retrieving credentials through a password-manager CLI.

<details><summary>References</summary>
<ul>
<li><a href="https://gist.github.com/melodykoh/7bfbba44fc20b98dda34e40d69e9e92e">Claude Code Permissions &amp; Settings Guide — Three-tier permissions...</a></li>
<li><a href="https://code.claude.com/docs/en/settings">Claude Code settings - Claude Code Docs</a></li>
<li><a href="https://securie.ai/leak/anthropic-key-in-claude-config">Leaked Anthropic key in `. claude / settings . local . json ` — committed...</a></li>

</ul>
</details>

**Tags**: `#Claude Code`, `#AI coding agents`, `#secrets management`, `#GitHub security`, `#developer tooling`

---

<a id="item-tech-news-4"></a>
### [A $10 OpenStick Homelab Built Around Lightweight Self-Hosting](https://blog.bosscher.ch/posts/openstick/) ⭐️ 7.0/10

The author describes running a self-hosted homelab on a $10 OpenStick USB device, arguing that careful software choices let a very cheap gadget serve as a low-cost way to start self-hosting, particularly as RAM prices remain high. The post is a personal setup write-up rather than a benchmark or product announcement, and the author invites suggestions for additional software.

hackernews · LaurensBER · Nov 7, 18:12 · [Discussion](https://news.ycombinator.com/item?id=50406670)

**「Background」** A homelab is a personal setup for running self-hosted services on hardware you control rather than renting cloud instances. This post applies that idea to a $10 USB-stick-format OpenStick, with the author arguing that choosing lightweight software is what makes such low-cost, memory-limited hardware usable for self-hosting.

**「What to check before copying this setup」** Anyone replicating the build needs an MSM8916-based 4G LTE USB modem — the OpenStick community guide lists the UZ801, UFI003, UFI001B/C, HMUF02-V05 and SP970 — and must flash Debian Linux onto it before it works as a server. The 512 MB of RAM is the practical ceiling: the reported ad blocking, monitoring, AI agent and self-hosted apps fit only because they are lightweight, so each additional service should be checked against available memory before deployment.

**「Community Discussion」** Commenters compared the OpenStick with Raspberry Pi Zero-class boards, discussed lighter alternatives to apps such as Fusion and miniflux, and one proposed a PoE Ethernet-stick form factor for plug-and-play clustering. Another asked where to buy the hardware, while one reported that 512 MB of RAM is enough for many workloads if software is chosen carefully.

<details><summary>References</summary>
<ul>
<li><a href="https://news.lavx.hu/article/laurens-bosscher-runs-a-homelab-on-a-10-openstick">Laurens Bosscher runs a homelab on a $10 OpenStick</a></li>
<li><a href="https://openstick.org/">OpenStick (Open Stick) — 1-Click Debian Linux for MSM8916 4G ...</a></li>

</ul>
</details>

**Tags**: `#homelab`, `#self-hosting`, `#openstick`, `#embedded-linux`, `#low-cost-hardware`

---

<a id="item-tech-news-5"></a>
### [Asahi Linux report cites same-day Fedora Asahi Remix, licensing concerns](https://asahilinux.org/2026/11/progress-report-7-3/) ⭐️ 7.0/10

Asahi Linux&\#x27;s 7.3 progress report says Fedora Asahi Remix shipped on the same day as Fedora Linux 45, which was released on 3 November; a quoted passage calls it the first time the remix has matched an upstream Fedora release on day one. The report also addresses licensing concerns, describing multiple attempts to exploit Asahi&\#x27;s permissive licensing to hijack the project and monetize Linux on Apple Silicon. The supplied discussion does not indicate whether Asahi plans to change its license or what enforcement steps it might take.

hackernews · ackyshake · Nov 7, 05:20 · [Discussion](https://news.ycombinator.com/item?id=50401867)

**「Background」** Asahi Linux is the project that brings Linux to Apple Silicon Macs, and Fedora Asahi Remix is its Fedora-based distribution. The project had used a permissive MIT license across its repositories; the 7.3 report says that permissiveness was repeatedly exploited by efforts to take over the work and monetize Linux on Apple Silicon, and that all repositories are being relicensed to GPL-2.0-or-later.

**「Impact」** Fedora Asahi Remix users get a Fedora 45-based remix at the same time as Fedora 45 itself, reducing the version lag between upstream Fedora and the Apple Silicon build.

**「Community discussion」** Commenters praised the same-day release. One MacBook Air user said missing USB-C display support remains a blocker and questioned why newer CPU support is prioritized, while another asked whether the licensing warning referred to Omarchy and was surprised Asahi had used MIT rather than GPL.

<details><summary>References</summary>
<ul>
<li><a href="https://www.linux.org.hk/archive/20261107-9177-asahi-linux-relicenses-all-repositories.html">Hong Kong Linux User Group - 香港Linux用家協會 (HKLUG) &gt; Archi...</a></li>
<li><a href="https://daily.dev/posts/asahi-linux-7-3-progress-report-gnbddoj5h">Asahi Linux 7.3 progress report - daily.dev</a></li>

</ul>
</details>

**Tags**: `#Asahi Linux`, `#Apple Silicon`, `#Fedora`, `#Linux hardware support`, `#open-source licensing`

---

<a id="item-tech-news-6"></a>
### [Coldframe Honeypot Mimics Danfoss and Dixell Fridge Controllers](https://github.com/hedgerow-dev/coldframe) ⭐️ 7.0/10

Coldframe is a newly published open-source Python honeypot that impersonates Danfoss AK-SM 800A and Dixell XWEB supermarket refrigeration controllers, giving ICS/OT researchers a way to observe attacks against exposed cooling equipment. The single-file, standard-library tool uses Shodan fingerprints to match header order, page titles, certificate fields, and TLS versions; the author says both personas have been indexed as real devices, with the Danfoss profile sending nginx headers in a real unit&\#x27;s order and the Dixell profile omitting the Server header and padding its page to 8,202 bytes. It recognizes CVE-2025-41450, the Danfoss &quot;code of the day&quot; login bypass, records whether a submitted code is correct for the day, and tags attempts against three other Danfoss CVEs and XWEB vulnerabilities; default logins open a fake store dashboard with defrost buttons. Two instances had been live for a day and had logged only generic scanners and Shodan&\#x27;s crawler, refrigerator.census.shodan.io.

hackernews · hedgerow-dev · Nov 7, 17:27 · [Discussion](https://news.ycombinator.com/item?id=50406292)

**「Background」** Coldframe&\#x27;s Danfoss persona targets the AK-SM 800A, a supermarket refrigeration controller whose &quot;code of the day&quot; login mechanism can be bypassed under CVE-2025-41450. The project reuses and extends the earlier eppser/danfoss-ak-sm-decoy, drawing on public research by Synacktiv, Claroty and Ironhackers into these controllers, and was prompted by recent attacks on industrial refrigeration installations. Shodan fingerprint data for real Danfoss and Dixell XWEB units supplied the header, TLS and page-size details the honeypot imitates.

**「Impact」** Coldframe gives ICS/OT defenders a low-setup way to collect post-authentication attacker behavior against refrigeration-controller personas, not just initial scan traffic. Because default logins lead to a fake dashboard, deployments can record what an intruder tries after gaining access, but nothing behind the dashboard is real and it should not be treated as a production monitoring tool.

**「Community discussion」** Commenters questioned the use of Shodan records as fingerprinting ground truth: supriyo-biswas said that when replicating Wi-Fi cameras, almost all exposed units found were honeypots or already compromised, and recommended probing a physical vulnerable device instead. xrd asked whether the refrigeration incidents were definitively confirmed as a large-scale hack or could have been a simultaneous software update, while the author argued supermarkets lack security teams and need vendor- or installer-supplied patching, VPNs, and strong passwords by default.

**Tags**: `#honeypots`, `#ICS/OT security`, `#IoT security`, `#CVE-2025-41450`, `#open-source tools`

---

<a id="item-tech-news-7"></a>
### [MaxxBench tests whether DeepSWE scores survive task-spec changes](https://maxxbench.unlap.ai/research/why-maxxbench/) ⭐️ 7.0/10

MaxxBench published an analysis testing whether DeepSWE benchmark scores remain stable when task specifications are varied, rather than treating a single score as evidence of general capability. The work focuses on benchmark validity and evaluation practice, not a new model release. In the Hacker News thread, commenters also flag apparent bugs in DeepSWE and debate whether score changes reflect model capability or sensitivity to evaluation setup.

hackernews · antiuniverse · Nov 7, 17:19 · [Discussion](https://news.ycombinator.com/item?id=50406222)

**「Benchmark context」** DeepSWE is a benchmark of 113 original, long-horizon software-engineering tasks for coding agents, designed to avoid the GitHub-mined fixes that can make benchmark scores reflect pretraining recall rather than problem-solving. MaxxBench builds on that benchmark by changing the instructions or starting code of 89 DeepSWE tasks to test whether models adapt their usual approach.

**「Impact」** For teams using DeepSWE to compare models, the practical implication is to audit or re-run evaluations under altered task specifications before relying on a leaderboard result. One commenter summarized the takeaway as avoiding “max mode,” while others noted that smaller models appeared most affected—observations from the discussion, not confirmed findings from the analysis.

**「Community discussion」** Commenters broadly welcomed the robustness test: one called varying a task parameter a useful default for checking whether a benchmark score generalizes. Another argued the results show smaller models collapsing most and speculated that sloppy reinforcement-learning environments and overfitting to simple tasks explain the pattern. Others said DeepSWE’s apparent bugs increased their skepticism of widely used benchmarks.

<details><summary>References</summary>
<ul>
<li><a href="https://arxiv.org/abs/2607.07946">[2607.07946] DeepSWE: Measuring Frontier Coding Agents on ...</a></li>
<li><a href="https://maxxbench.unlap.ai/research/why-maxxbench/">Introducing MaxxBench: Benchmarking Task Adaptation and ...</a></li>

</ul>
</details>

**Tags**: `#LLM benchmarks`, `#evaluation methodology`, `#DeepSWE`, `#model robustness`, `#AI/ML`

---

<a id="item-tech-news-8"></a>
### [Undocumented Apple Intelligence daemons on macOS build a personal knowledge graph](https://8rank.ai/game/apple-intelligence-personal-knowledge-graph) ⭐️ 7.0/10

An 8rank.ai investigation reports that macOS ships a pair of undocumented Apple Intelligence daemons whose purpose is to build a personal knowledge graph about the user: who they are, who they know, how those contacts relate to each other, how they communicate, where they go and with whom. The author, posting as infwhispers, states that Macs have included these components since 2022, citing a follow-up piece on the knowledge graph as well. The finding is the researcher&\#x27;s own analysis of platform internals rather than an Apple disclosure or an independently verified audit, so the scope of the data collected and whether it leaves the device are not established in the supplied material.

hackernews · infwhispers · Nov 7, 09:46 · [Discussion](https://news.ycombinator.com/item?id=50403097)

**「Context: on-device knowledge graphs」** Apple Intelligence features on macOS lean on local context — resolving which &quot;James&quot; a request means, or who someone&\#x27;s boss is — rather than sending everything to a server. The 8rank.ai investigation reports that the two daemons it examined ship on macOS 13 and later, on both Intel and Apple silicon Macs, so the graph-building it describes predates the Apple Intelligence branding and is not restricted to newer Apple-silicon hardware.

**「Impact」** Because the daemons are undocumented, Mac users have no Apple-published description of what relationship data is inferred or how to inspect or disable it, which complicates privacy reviews for anyone using a Mac for sensitive contact or client information. The most concrete audit step the research supports is starting from the named daemons and their on-disk artifacts rather than from System Settings privacy panes.

**「Community Discussion」** Commenter aetherspawn argues the graph is the context local models need for requests like distinguishing which &quot;James&quot; to text or identifying someone&\#x27;s boss, framing it as functional rather than gratuitous. thomascountz counters with a social concern rather than a moral one: people converse on the assumption that not everything will be remembered, and ambient summarization erodes that. elgertam says the capability is unsurprising given that Photos already recognizes names, faces and even pets, while consumer451 quotes Steve Jobs&\#x27; 2010 remarks on telling users plainly what will be done with their data, set against the lack of such disclosure here.

<details><summary>References</summary>
<ul>
<li><a href="https://8rank.ai/game/apple-intelligence-personal-knowledge-graph">Anatomy of Apple &#x27;s Personal Knowledge Graph — Eighth Rank</a></li>

</ul>
</details>

**Tags**: `#Apple Intelligence`, `#privacy`, `#macOS internals`, `#personal knowledge graph`, `#undocumented APIs`

---

<a id="item-tech-news-9"></a>
### [Claude Code Reportedly Leaks Login Email During Web Searches](https://github.com/anthropics/claude-code/issues/107757) ⭐️ 7.0/10

Claude Code has been reported to inject users&\#x27; login email addresses into outbound web requests, including requests to Wikipedia and the U.S. Securities and Exchange Commission, according to a GitHub issue. An Anthropic engineer said the email was previously placed in the model context to stop Claude from inventing author names; the issue was reported in July. Version 2.1.317 adds an interception intended to block the behavior, but the report says a Python script can bypass it. Anthropic has promised to remove the login email from the context in the next version, so the exposure is not fully resolved in 2.1.317.

telegram · zaihuapd · Nov 7, 08:09

**「Why the email was in requests at all」** Claude Code sends HTTP requests when it searches the web or fetches pages, and those requests carry a User-Agent header identifying the client; the bug report at the center of this item says the user&\#x27;s account email was appearing in that header \(tool-1-1\), a behavior an October 22 write-up also documented along with a user-side workaround \(tool-1-2\). According to the source, Anthropic engineers said the login email had been placed in the model context to stop Claude from inventing author names, after which it surfaced in outbound requests to sites including Wikipedia and the U.S. Securities and Exchange Commission.

**「Exposure persists despite patch」** Claude Code users remain exposed to their login email reaching third-party sites, where it can be harvested for phishing, because the 2.1.317 interception can be bypassed by Python scripts. Until the promised next release removes the email from the model context, users should not treat the current patch as complete protection for agent workflows that run arbitrary scripts.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/anthropics/claude-code/issues/107757">Bug Report: Privacy violation in User-Agent header · Issue ...</a></li>
<li><a href="https://explainx.ai/blog/claude-code-leaks-your-email-user-agent-header-how-to-stop-it-2026">Claude Code Leaks Your Email in Headers: 5-Min Fix - explainx.ai</a></li>
<li><a href="https://cybersecuritynews.com/claude-code-leaks-user-email/">Anthropic’s Claude Code Reportedly Leaks User Email Addresses ...</a></li>
<li><a href="https://privacysavvy.com/news/privacy/claude-code-privacy-flaw-email-exposure/">Anthropic Fixes Claude Code Privacy Flaw that Exposed Users ...</a></li>

</ul>
</details>

**Tags**: `#privacy`, `#security`, `#claude-code`, `#ai-coding-agents`, `#vulnerability`

---

<a id="item-tech-news-10"></a>
### [GitHub&\#x27;s Rubicon Git storage targets AI-agent concurrency, hits 7,200 pushes/sec in tests](https://github.blog/engineering/architecture-optimization/inside-githubs-new-git-storage-architecture/) ⭐️ 7.0/10

GitHub has detailed a new Git storage architecture, codenamed Rubicon, designed for the case of many AI agents operating concurrently on a single repository. In internal tests, the system supported 5,000 agents collaborating at once and processed 7,200 pushes per second while keeping read latency low, according to GitHub&\#x27;s engineering post. The design stores Git objects in Azure Blob Storage, manages reference state through Ref-CAS, and uses virtual replicas to handle reads and writes while background nodes compress packfiles. Rubicon is currently in limited private preview, and GitHub says it will expand the rollout gradually; the source gives no general-availability date, pricing, or migration details.

telegram · zaihuapd · Nov 7, 14:12

**「Background」** GitHub&\#x27;s earlier Git storage design, known internally as Spokes, coordinated writes across replicas using a three-phase commit that serialized reference updates, limiting how many writers a single repository could absorb. Rubicon splits that model: immutable Git objects live in Azure Blob Storage while mutable refs are ordered by a new Ref-CAS log service, a separation reported to yield up to 35x higher write throughput than Spokes. Coverage of the project also places its announcement at GitHub Universe.

**「Impact」** The scenario Rubicon targets — many automated agents pushing to the same repository — is where ref contention and object-storage throughput matter most, so teams running agent fleets now have GitHub&\#x27;s own internal figures \(5,000 agents, 7,200 pushes/sec\) as a reference point. Those teams cannot adopt it yet: the architecture is confined to a limited private preview, with no stated timeline or migration path for broader access.

<details><summary>References</summary>
<ul>
<li><a href="https://hermes-ai.net/news/github-s-rubicon-rewrites-git-storage-to-handle-7-200-ai-agent-pushes-per-second/">GitHub&#x27;s Rubicon Rewrites Git Storage to Handle 7,200 AI ...</a></li>
<li><a href="https://lumienai.com/news/github-project-rubicon-new-git-storage-architecture">GitHub’s “Project Rubicon”: A New Git Storage Built for…</a></li>

</ul>
</details>

**Tags**: `#GitHub`, `#Git storage`, `#AI agents`, `#Azure Blob Storage`, `#software infrastructure`

---