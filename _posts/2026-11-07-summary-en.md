---
layout: default
title: "Horizon Summary: 2026-11-07 (EN)"
date: 2026-11-07
lang: en
---

> From 38 items, 8 important content pieces were selected

---

**Technology News**
1. [Baidu Open-Sources ERNIE 5.5 Flash Base MoE Model](#item-tech-news-1) ⭐️ 8.0/10
2. [Libghostty, an open-source terminal-emulation library, reaches 1.0](#item-tech-news-2) ⭐️ 7.0/10
3. [PwnEscape Firecracker Exploit Walkthrough Uses No-Jailer Setup](#item-tech-news-3) ⭐️ 7.0/10
4. [Boson AI announces 45B Higgs Realtime Duplex full-duplex model](#item-tech-news-4) ⭐️ 7.0/10
5. [YMTC plans Wuhan fab with up to 70% domestic equipment](#item-tech-news-5) ⭐️ 7.0/10
6. [EU Accuses TikTok&\#x27;s Algorithm of Harmful &\#x27;Rabbit Hole&\#x27; Effects](#item-tech-news-6) ⭐️ 7.0/10
7. [Taobao MNN open-sources 0.3B on-device model MNN-Pocket-0.3B](#item-tech-news-7) ⭐️ 7.0/10
8. [Anthropic Said to Plan IPO Roadshow and Mid-November Listing](#item-tech-news-8) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Baidu Open-Sources ERNIE 5.5 Flash Base MoE Model](https://www.news.cn/info/20261105/f3bbdb6854f5441ca9fb34062f213875/c.html) ⭐️ 8.0/10

Baidu has open-sourced ERNIE 5.5 Flash Base, a mixture-of-experts base model with 280 billion total parameters and 14 billion active parameters per token. It was pretrained on 33.5 trillion tokens with a 128K-token pretraining context, while fine-tuning and inference support contexts of up to 1 million tokens. Baidu says it optimized attention, expert routing, and training objectives for efficiency; the source did not provide benchmark results or licensing terms.

telegram · zaihuapd · Nov 6, 05:41

**「Background」** A base model is pretrained on broad text and typically serves as the starting point for task-specific fine-tuning rather than as a finished chat product. In a mixture-of-experts model, a router sends each token through only a subset of parameters, so total parameter count and active parameters measure different things; active parameters are the compute-relevant figure per token.

**「Impact」** Teams adopting ERNIE 5.5 Flash Base should plan for post-training: Baidu is publishing it as a pretraining base checkpoint rather than an instruction-tuned assistant, so instruction-following and task-specific behavior must be added before production use. Deployment planning must also account for storing and loading the full 280B-parameter weight set even though only 14B parameters are active per token, meaning lower per-token compute does not by itself reduce weight-memory requirements.

<details><summary>References</summary>
<ul>
<li><a href="https://ernie.baidu.com/release/ernie-5-5-flash-base/">ERNIE 5 . 5 Flash Base · ERNIE</a></li>
<li><a href="https://news.ycombinator.com/item?id=50377078">Baidu released ERNIE 5 . 5 Flash Base | Hacker News</a></li>

</ul>
</details>

**Tags**: `#Baidu ERNIE`, `#open-source LLM`, `#MoE`, `#long context`, `#model release`

---

<a id="item-tech-news-2"></a>
### [Libghostty, an open-source terminal-emulation library, reaches 1.0](https://mitchellh.com/writing/libghostty-1-0) ⭐️ 7.0/10

Libghostty, an open-source terminal-emulation library, has reached version 1.0, announced in a post on Mitchell Hashimoto&\#x27;s site. As a library, it is intended for developers who want to embed terminal emulation in their own applications rather than run a standalone terminal emulator. The supplied material did not include release notes or a changelog, so the specific API guarantees, platform support, and breaking changes attached to the 1.0 designation are not established here.

hackernews · mfiguiere · Nov 6, 23:30 · [Discussion](https://news.ycombinator.com/item?id=50399933)

**「Background」** Libghostty is an embeddable terminal-emulation core that host applications can reuse instead of implementing terminal behavior themselves. Mitchell Hashimoto&\#x27;s October 2024 post announcing Ghostty 1.0 said libghostty was not yet considered stable or available as a standalone public API, though Ghostty used it internally.

**「Impact」** For developers building terminal or editor tooling, the reported practical effect is reuse: commenters say they are using libghostty as the emulation layer for their own terminal project and for Ghostel, an Emacs terminal, instead of writing that layer themselves. The available evidence does not indicate what compatibility or migration work the 1.0 release requires from existing users.

**「Community discussion」** Commenters welcomed the release, with one developer saying they are building a terminal on libghostty and that it &quot;just works&quot; and saves substantial work, and another crediting it for making Ghostel, described as the best terminal for Emacs, possible. These are users&\#x27; reports about their own projects, not independent verification of the 1.0 release&\#x27;s technical claims.

<details><summary>References</summary>
<ul>
<li><a href="https://mitchellh.com/writing/ghostty-is-coming">Ghostty 1 . 0 is Coming – Mitchell Hashimoto</a></li>

</ul>
</details>

**Tags**: `#terminal emulators`, `#libghostty`, `#open source`, `#developer tools`, `#libraries`

---

<a id="item-tech-news-3"></a>
### [PwnEscape Firecracker Exploit Walkthrough Uses No-Jailer Setup](https://pwn.ai/blog/firecracker-escape) ⭐️ 7.0/10

The PwnEscape Part 2 write-up demonstrates practical exploitation of a Firecracker VM escape, but in a configuration that omitted Firecracker&\#x27;s jailer. Firecracker&\#x27;s production containment drops privileges and restricts the VMM process with namespaces and seccomp, and the post states that deployments using those controls need a separate assessment of what an attacker can reach after compromising the VMM. Commenters stress that this is not a new vulnerability: PwnEscape was disclosed weeks earlier, and this article is an exploitation walkthrough.

hackernews · SerCe · Nov 6, 19:33 · [Discussion](https://news.ycombinator.com/item?id=50397219)

**「Background」** PwnEscape \(CVE-2026-99999\) was disclosed in October 2026 after being found during Vercel&\#x27;s sandbox challenge; it lets a KVM guest read host memory by abusing IPv4 checksum handling. This post is a practical exploit walkthrough of that previously reported bug, not a new vulnerability. The demonstrated configuration ran Firecracker as root without the jailer, while production containment relies on privilege dropping, namespaces, and seccomp, so the host-root outcome depends on that deployment choice.

**「Impact」** For Firecracker operators, the write-up makes jailer configuration the dividing line: it illustrates attacker capability after VMM compromise but does not show that the same path reaches the host when privilege dropping, namespaces, and seccomp are active. Security teams should assess post-compromise privileges under their own jailer settings rather than extrapolate from the no-jailer demonstration.

**「Community Discussion」** One commenter criticized the post for not expanding on the no-jailer caveat and asked whether a properly jailed Firecracker instance would contain the compromise. Another emphasized that the piece describes exploitation of the already-disclosed PwnEscape bug, not a new vulnerability.

<details><summary>References</summary>
<ul>
<li><a href="https://sesamedisk.com/firecracker-escape-guest-to-host-root/">Firecracker Escape: From Guest to Host Root - Sesame Disk</a></li>
<li><a href="https://cyberexperts.com/2026-10-16-linux-pwnescape/">Linux PwnEscape CVE-2026-99999: KVM Guest Can Read Host Memory</a></li>

</ul>
</details>

**Tags**: `#Firecracker`, `#virtualization security`, `#VM escape`, `#exploit development`, `#microVMs`

---

<a id="item-tech-news-4"></a>
### [Boson AI announces 45B Higgs Realtime Duplex full-duplex model](https://www.reddit.com/r/MachineLearning/comments/1xpn5pv/higgs_realtime_duplex_a_45b_moe_fullduplex_model/) ⭐️ 7.0/10

Boson AI announced Higgs Realtime Duplex, a 45B mixture-of-experts model that processes audio and video input while generating speech, and runs reasoning, tool calls and delegation as background spans in the same stream. The model works in 160 ms chunks: audio input costs 1 token per chunk, audio output 2 tokens, and video input about 12 tokens every six chunks, for roughly 2.6K tokens per minute and 2.6K–5K with thinking and tool traces. It is not open-weight; the Duplex API is waitlisted, while the earlier turn-based Higgs Realtime is available now. In vendor-reported comparisons, OpenAI&\#x27;s best settings led five of seven benchmarks by 1–5 points, with Boson furthest behind on turn-taking, and no independent benchmarks were provided.

reddit · r/MachineLearning · /u/Cali\_Cobarde · Nov 6, 20:23

**「Why full-duplex matters here」** Conventional voice assistants are turn-based: they wait for the end of the user&\#x27;s turn, then reason, then speak. Thinking Machines Lab outlined the competing approach in a May 2026 post on &quot;Interaction Models,&quot; describing a full-duplex system that processes audio, video and text in roughly 200-millisecond micro-turns so it can listen and speak at the same time, and claiming the best measured turn latency. Boson&\#x27;s own write-up positions Duplex against that design: both keep heavy reasoning off the speech path, but Duplex runs thinking, tool calls and delegation as spans inside the same stream, whereas the Thinking Machines approach routes reasoning and tool use to a background model, which Boson says can mean 10+ seconds per answer and makes cost harder to control.

**「What it means for developers」** Because Higgs Realtime Duplex is closed-weight and gated behind an API waitlist, teams cannot self-host it or benchmark it on their own workloads yet; those needing immediate streaming speech-to-speech must use the earlier turn-based Higgs Realtime, which the company says is generally available. For those who do get access, customization shifts from fine-tuning to deployment-time configuration: a short reference clip for the voice, a single image for the face, and a text prompt for behavior.

<details><summary>References</summary>
<ul>
<li><a href="https://thinkingmachines.ai/blog/interaction-models/">Interaction Models: A Scalable Approach to Human-AI ...</a></li>
<li><a href="https://aiautomationglobal.com/blog/thinking-machines-interaction-models-full-duplex-voice-ai-2026">Thinking Machines Interaction Models: Voice AI That Listens ...</a></li>
<li><a href="https://www.boson.ai/blog/higgs-realtime">Higgs Realtime : cost-efficient, real - time speech-to-speech model...</a></li>

</ul>
</details>

**Tags**: `#full-duplex speech models`, `#multimodal LLMs`, `#mixture-of-experts`, `#real-time audio/video`, `#tool use`

---

<a id="item-tech-news-5"></a>
### [YMTC plans Wuhan fab with up to 70% domestic equipment](https://www.reuters.com/world/china/chinas-top-flash-memory-chipmaker-targets-more-homegrown-tools-new-factory-2026-11-06/) ⭐️ 7.0/10

YMTC plans a fourth fab in Wuhan, expected to begin construction in 2027, targeting domestic equipment at 60–70% of procurement—above the more than 50% level at its third fab, Reuters reported. The plant is intended to produce advanced NAND flash with more than 300 layers for data-center and AI storage. U.S. export controls are driving the localization effort; cleaning, polishing, and etching tools are expected to account for most of the domestic increase, while lithography and inspection equipment would still rely on overseas suppliers. YMTC&\#x27;s share of China&\#x27;s NAND market has reached 38.5%, overtaking Samsung, and its overall capacity could double once all of its new fabs are in production.

telegram · zaihuapd · Nov 6, 08:34

**「Background」** YMTC already operates multiple fabs in Wuhan; the planned facility would be its fourth, and its third fab reportedly sources more than 50% of equipment domestically—the baseline the company aims to raise to 60–70%. U.S. export controls have constrained Chinese chipmakers&\#x27; access to advanced foreign equipment, making domestic tool substitution a central part of YMTC&\#x27;s expansion planning.

**「Impact」** Chinese cleaning, polishing, and etching equipment makers stand to gain the main incremental orders, while the planned fab would remain dependent on overseas suppliers for lithography and inspection despite its domestic-procurement target.

**Tags**: `#semiconductors`, `#NAND flash`, `#YMTC`, `#export controls`, `#supply chain`

---

<a id="item-tech-news-6"></a>
### [EU Accuses TikTok&\#x27;s Algorithm of Harmful &\#x27;Rabbit Hole&\#x27; Effects](https://www.cnbc.com/2026/11/06/eu-charges-tiktok-harmful-algorithmic-rabbit-hole-effects.html) ⭐️ 7.0/10

The European Commission has accused TikTok&\#x27;s recommendation algorithm of creating harmful “rabbit hole” effects and violating the Digital Services Act. It is demanding that TikTok adjust the “For You” feed to rely more on users&\#x27; explicit preferences, improve user controls, and regularly test the algorithm, saying the platform has not taken effective measures to address the risks. If the case is not resolved, parent company ByteDance could face a fine of up to 6% of global annual revenue next year; the commission says repeated similar-content recommendations may affect mental health, and the accusation is part of a broader investigation.

telegram · zaihuapd · Nov 6, 14:03

**「Background」** The accusation is a preliminary finding under the Digital Services Act, the EU rulebook that obliges large platforms to assess and mitigate systemic risks, including those created by their recommender systems; it is not yet a final decision. The European Commission opened its investigation into TikTok&\#x27;s compliance with the DSA more than two years before this step.

**「Impact」** TikTok must now either revise the “For You” feed and its controls—weighting recommendations more toward users’ explicit preferences and testing the algorithm regularly—or contest the charges; if it does neither, ByteDance faces a fine of up to 6% of worldwide annual revenue. The company can inspect the file and reply before any penalty is imposed.

<details><summary>References</summary>
<ul>
<li><a href="https://digital-strategy.ec.europa.eu/en/news/commission-preliminarily-finds-tiktoks-you-feed-breach-digital-services-act-harmful-rabbit-holes">Commission preliminarily finds TikTok’s ‘For You’ feed in ...</a></li>
<li><a href="https://apnews.com/article/tiktok-european-union-brussels-social-media-regulation-f59bbe2045ab842c0a4beef4e9a050e2">EU says ‘rabbit hole’ video feeds on TikTok violate its ...</a></li>
<li><a href="https://reclaimthenet.org/eu-commission-tiktok-algorithm-digital-services-act">European Commission Says TikTok Recommendation Algorithm...</a></li>

</ul>
</details>

**Tags**: `#EU Digital Services Act`, `#TikTok`, `#recommendation algorithms`, `#platform regulation`, `#algorithmic accountability`

---

<a id="item-tech-news-7"></a>
### [Taobao MNN open-sources 0.3B on-device model MNN-Pocket-0.3B](https://www.ithome.com/1/023/212.htm) ⭐️ 7.0/10

Taobao&\#x27;s MNN team has open-sourced MNN-Pocket-0.3B, an approximately 300-million-parameter language model intended for on-device use. The release includes an INT4 deployment file of 173 MB and uses a 28-layer architecture with a vocabulary reduced from 151K to 64K; the team also published multiple versions covering pretraining, post-training, and device deployment. In the reported demo, it runs fully offline on an iPhone 18 Pro and averages about 350 tokens/s decoding, against the team&\#x27;s target of under 300 MB peak memory and more than 200 tokens/s. Those performance and memory figures come from IT之家&\#x27;s secondary report and have not been independently verified.

telegram · zaihuapd · Nov 6, 15:13

**「Background」** Sub-billion-parameter models such as MNN-Pocket-0.3B are positioned for on-device assistants, data extraction, and lightweight agent workflows, not reasoning-heavy tasks such as advanced mathematics or long-horizon code generation. The release is packaged in MNN format and quantized to INT4 so it can run through the MNN inference engine fully offline on phones.

**「Deployment impact」** Developers can download the INT4 deployment files and test fully offline inference on phones, but they should validate the reduced 64K-vocabulary tokenizer and actual memory use in their own app before relying on the team&\#x27;s reported 350 token/s decoding speed, which has not been independently measured.

<details><summary>References</summary>
<ul>
<li><a href="https://huggingface.co/taobao-mnn/MNN-Pocket-0.3B">taobao-mnn/MNN-Pocket-0.3B · Hugging Face</a></li>
<li><a href="https://huggingface.co/taobao-mnn/MNN-Pocket-0.3B-MNN">taobao-mnn/MNN-Pocket-0.3B-MNN · Hugging Face</a></li>

</ul>
</details>

**Tags**: `#on-device LLM`, `#MNN`, `#open-source models`, `#mobile inference`, `#quantization`

---

<a id="item-tech-news-8"></a>
### [Anthropic Said to Plan IPO Roadshow and Mid-November Listing](https://www.theinformation.com/briefings/anthropic-proceed-ipo-roadshow-next-week) ⭐️ 7.0/10

A Telegram digest citing anonymous sources reported that Anthropic plans to begin an IPO roadshow next week and list in the week of November 16, before the U.S. Thanksgiving holiday. The report said the move follows two weeks of sharp volatility in technology stocks. The market had reportedly expected a $1.5 trillion valuation and more than $80 billion raised, but recent concerns about AI stocks and spending may lead the company to seek a lower valuation. The supplied material does not confirm that Anthropic has set those terms or the timetable.

telegram · zaihuapd · Nov 7, 01:27

**「Earlier IPO context」** Anthropic had already moved toward a public listing: an October report on its IPO filing said it generated $16.29 billion in revenue in the first half of 2026 while investors weighed an $80 billion loss and discussed a valuation around $1.5 trillion, with no official price range disclosed. By early November, IPO talk had reportedly slid to about $1.2 trillion as an AI-stock rout hit the sector, giving the roadshow a lower-valuation backdrop.

**「Impact」** If the roadshow proceeds, it would test public-investor demand for Anthropic after the AI-stock volatility, and the reported possibility of a lower valuation could change the pricing expectations investors use. The $1.5 trillion valuation and $80 billion-plus raise should be treated as prior expectations, not confirmed offering terms.

<details><summary>References</summary>
<ul>
<li><a href="https://www.fxstreet.com/news/anthropic-ipo-filing-reveals-rapid-growth-as-investors-weigh-an-80-billion-loss-202610270748">Anthropic IPO filing reveals rapid growth as investors weigh an $ 80 ...</a></li>
<li><a href="https://www.zerohedge.com/markets/haircut-no-2-anthropic-ipo-talk-slides-12-trillion-ai-rout-crushes-odds-november-listing">Haircut No. 2: Anthropic IPO Talk Slides To $ 1 .2 Trillion ... | ZeroHedge</a></li>

</ul>
</details>

**Tags**: `#Anthropic`, `#IPO`, `#AI industry`, `#valuation`, `#market news`

---