---
layout: default
title: "Horizon Summary: 2026-11-23 (EN)"
date: 2026-11-23
lang: en
---

> From 27 items, 3 important content pieces were selected

---

**Technology News**
1. [OpenAI Examines Perplexity as a Signal of Model Intelligence](#item-tech-news-1) ⭐️ 7.0/10
2. [Ant Group Leads $100M Pre-A for Simplexity at $1.6B Valuation](#item-tech-news-2) ⭐️ 7.0/10
3. [Windows Server 2028 to omit WoW64 by default](#item-tech-news-3) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [OpenAI Examines Perplexity as a Signal of Model Intelligence](https://openai.com/index/perplexity-and-intelligence/) ⭐️ 7.0/10

The item is an OpenAI analysis post examining the relationship between language-model perplexity and model intelligence, with no source text supplied to verify its specific claims, data, versions, or benchmarks. It is commentary and evaluation discussion rather than a product release, aimed at readers assessing how LLM capability is measured. The surrounding discussion focuses on whether cross-entropy-based perplexity is a useful, simple signal alongside increasingly complex benchmark suites.

hackernews · acossta · Nov 22, 17:06 · [Discussion](https://news.ycombinator.com/item?id=50601525)

**「Background」** Perplexity is the exponentiated cross-entropy loss for a model&\#x27;s next-token predictions: lower values mean the model assigns more probability to the tokens that actually occur. It is a standard pretraining signal, and OpenAI&\#x27;s post argues it can also serve as a shared cross-developer comparison and safety metric.

**「Evaluation tradeoff」** For model developers, the practical consequence is that held-out perplexity can serve as a cheap pre-training progress check across checkpoints, but it should be paired with task-level evaluations and a fixed evaluation set and tokenizer before being used to rank models; otherwise scores are not comparable across model families.

**「Community Discussion」** Commenters supplied a working definition—perplexity measures next-token surprise and ranges from 1 to vocabulary size—and one said the apparent cross-entropy/intelligence trend was surprising given the shift toward RL, while welcoming a simpler benchmark. Another argued that prediction and compression on raw data are exactly the measures that should capture intelligence, and a further comment claimed Microsoft had reported MAI-2 Base log-perplexity of 0.819 on OpenAI’s held-out evaluation set, citing a Mustafa Suleyman post.

<details><summary>References</summary>
<ul>
<li><a href="https://openai.com/index/perplexity-and-intelligence/">Perplexity and Intelligence | OpenAI</a></li>
<li><a href="https://openai.com/index/perplexity-and-intelligence/">Perplexity and Intelligence | OpenAI</a></li>

</ul>
</details>

**Tags**: `#LLM evaluation`, `#perplexity`, `#benchmarking`, `#language models`, `#OpenAI`

---

<a id="item-tech-news-2"></a>
### [Ant Group Leads $100M Pre-A for Simplexity at $1.6B Valuation](https://www.bloomberg.com/news/articles/2026-11-22/ant-group-bets-on-simplexity-to-thrive-in-china-s-humanoid-race) ⭐️ 7.0/10

Ant Group led a $100 million pre-A round for Chinese embodied-intelligence startup Simplexity Robotics at a $1.6 billion post-money valuation, chairman and co-founder Wang Kai confirmed to Bloomberg. Existing investors Alibaba, Tencent, HongShan and BlueRun Ventures participated. Simplexity was founded in Hangzhou in July 2025 by a core team from Li Auto, with Jia Peng as CEO and Wang Jiajia as COO; in March it said it had raised RMB2 billion across five rounds in six months and was already valued above $1 billion. Bloomberg reported that the new capital will be used to compete with more established humanoid-robot makers Unitree and UBTech, in a market it says accounts for about 97% of global humanoid-robot shipments.

telegram · zaihuapd · Nov 23, 02:02

**「Background」** Embodied intelligence refers to AI systems that perceive and act in the physical world, including humanoid robots. Simplexity Robotics was founded in Hangzhou in July 2025 with a core team from Li Auto, and by March 2026 it had disclosed five funding rounds in its first six months totaling RMB 2 billion, with a post-money valuation above $1 billion—below the $1.6 billion post-money valuation in the new round.

**Tags**: `#embodied AI`, `#humanoid robots`, `#funding`, `#China tech`, `#Ant Group`

---

<a id="item-tech-news-3"></a>
### [Windows Server 2028 to omit WoW64 by default](https://www.windowslatest.com/2026/11/23/32-bit-apps-days-are-numbered-as-microsoft-strips-support-bit-by-bit-starting-with-windows-server-2028-but-windows-11-is-safe-for-now/) ⭐️ 7.0/10

Microsoft said at Ignite 2026 that Windows Server 2028 will not include the WoW64 compatibility subsystem by default, so 32-bit applications will not run out of the box. The release is planned for fall 2027 alongside Windows 11 27H2; administrators can add WoW64 back as a Feature on Demand, typically via PowerShell or DISM on Server Core. Microsoft says the change reduces attack surface and blocks 32-bit malware, and Windows 11 still includes WoW64 with no removal plan announced.

telegram · zaihuapd · Nov 23, 03:03

**「Background」** WoW64 \(Windows 32-bit on Windows 64-bit\) is the compatibility subsystem that allows 32-bit applications to run on 64-bit Windows. Server Core has no desktop shell, so optional Windows components there are typically added through PowerShell or DISM; Microsoft says WoW64 can be restored as a Feature on Demand when a workload still needs 32-bit support.

**「Upgrade planning for server admins」** Administrators planning the move to Windows Server 2028, which Microsoft says is scheduled for fall 2027, must add WoW64 as a Feature on Demand during image build \(typically via PowerShell or DISM on Server Core\) before any 32-bit server application will run on a default install. Environments with locked-down or offline Server Core images should confirm the FoD source is reachable, since the subsystem is no longer on the media by default. Microsoft&\#x27;s documentation of removals in the same release lists other inbox retirements such as .NET Framework 3.5 no longer being an optional component, so a dependency audit should cover more than 32-bit binaries alone.

<details><summary>References</summary>
<ul>
<li>Features Removed or No Longer Developed in Windows Server | Microsoft Learn</li>
<li>32-bit apps&#x27; days are numbered as Microsoft strips support bit by bit, starting with Windows Server 2028, but Windows 11 is safe for now</li>

</ul>
</details>

**Tags**: `#Windows Server`, `#WoW64`, `#backward compatibility`, `#Microsoft`, `#32-bit applications`

---