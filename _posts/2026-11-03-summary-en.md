---
layout: default
title: "Horizon Summary: 2026-11-03 (EN)"
date: 2026-11-03
lang: en
---

> From 46 items, 8 important content pieces were selected

---

**Technology News**
1. [Qwen 3.8 27B reproduces paper&\#x27;s raw-weight game identification on a laptop](#item-tech-news-1) ⭐️ 9.0/10
2. [Postman issue alleges silent AI plugin installs and API data sharing](#item-tech-news-2) ⭐️ 7.0/10
3. [Could modern chess algorithms on a 1996 Pentium have beaten Kasparov?](#item-tech-news-3) ⭐️ 7.0/10
4. [Mac at Any Scale: Workarounds for macOS Infrastructure](#item-tech-news-4) ⭐️ 7.0/10
5. [Aircraft Noise and ADS-B Data Can Geolocate Videos, OSINT Demo Shows](#item-tech-news-5) ⭐️ 7.0/10
6. [Report: DeepSeek V5 planned for pre-training on Huawei Ascend](#item-tech-news-6) ⭐️ 7.0/10
7. [New York Times sues Brave over alleged scraping and resale to AI firms](#item-tech-news-7) ⭐️ 7.0/10
8. [Report: Nvidia Said to Cap Chinese Customers at 49% of Data-Center Business](#item-tech-news-8) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Qwen 3.8 27B reproduces paper&\#x27;s raw-weight game identification on a laptop](https://simonwillison.net/2026/Nov/3/qwen-can-interpret-model-weights/) ⭐️ 9.0/10

A paper by Rikiya Takehi, Jayden Teoh, Alex Zhang and Omar Khattab, “Sparks of Weight-Space Programming,” claims GPT-6 Astra can infer a small network&\#x27;s purpose from raw floating-point weights and edit those weights without training loops; one example edits 0.016% of Qwen3.5-0.8B&\#x27;s weights and raises MATH-500 from 7.9% to 48.1%. Simon Willison tested the paper&\#x27;s public no-tools game-identification prompts and reports that Qwen 3.8 27B—a 17GB Q4\_K\_M GGUF running in LM Studio on his laptop—identified Pac-Man after 46m12s and 43,506 reasoning tokens and Pong after 1h4m54s. Those are single-run, blog-reported results and do not independently validate the weight-editing claims; Matthew Honnibal called the paper misleading for conflating raw-weight reasoning with code-assisted model editing, and Sean Goedecke argued the Qwen math example follows steps a human researcher would take. The excerpt is truncated, so the Pong response and any further tests are only partially reported.

rss · Simon Willison · Nov 3, 16:29

**「Background」** The result Willison replicated comes from &quot;Sparks of Weight-Space Programming&quot; by Rikiya Takehi, Jayden Teoh, Alex Zhang and Omar Khattab, which defines weight-space programming as an LLM reading a network&\#x27;s raw floating-point weights and inferring what the network computes without executing code or calling tools. For the game-identification test, the authors trained reinforcement-learning policy networks on 10x10 grid versions of Breakout, Pong, Pac-Man and Freeway and published four self-contained prompts, one containing 17,253 weights for a single MLP, in a public GitHub repository. Critics including spaCy author Matthew Honnibal and Sean Goedecke argued the paper blurs that no-tools reading task with a separate, code-assisted weight-editing result, which is why Willison limits his laptop test to the reading half.

**「Reproducible, but slow, on consumer hardware」** The tool-free weight-reading task is now reproducible on a laptop: a 17GB Q4-quantized Qwen 3.8 27B answered the Pac-Man prompt after 46 minutes and 43,506 reasoning tokens, and the Pong prompt after about 65 minutes, but only with a context window larger than the default 8,192 and a raised request timeout. For developers that makes local weight inspection a batch job measured in roughly an hour per prompt, not an interactive tool, and the results should be kept distinct from the paper&\#x27;s code-assisted weight-editing claims, which critics argue conflate the two capabilities.

**「Community discussion」** Commenters dispute the paper&\#x27;s framing: x313, who says they work in mechanistic interpretability, argues the Qwen math gain is mainly a reduction in reasoning loops that simple steering can fix, and neom calls the Astra weight-editing result a regurgitation of existing techniques. Other threads debate whether the original write-up already made those limits clear, while bushido describes four to five weeks of conventional training that improved a small model but still left it unusable for their git commit-message task.

<details><summary>References</summary>
<ul>
<li><a href="https://www.startuphub.ai/ai-news/ai-research/2026/llms-can-now-read-and-rewrite-weights-directly">LLMs Can Now Read and Rewrite Weights Directly | StartupHub.ai</a></li>
<li><a href="https://rikiyat.github.io/blog/weight-space-programming/">Sparks of Weight - Space Programming : LLMs can natively read...</a></li>

</ul>
</details>

**Tags**: `#weight-space programming`, `#LLM interpretability`, `#model weights`, `#local LLMs`, `#Qwen`

---

<a id="item-tech-news-2"></a>
### [Postman issue alleges silent AI plugin installs and API data sharing](https://github.com/postmanlabs/postman-app-support/issues/14370) ⭐️ 7.0/10

A GitHub issue in Postman&\#x27;s public support repository \(postman-app-support \#14370\) alleges that the Postman API client silently auto-installs AI plugins and attempts to share all API data. The available material contains no Postman response, no reproduction steps, and no confirmed affected version, so the claims rest on a single unverified report rather than an independently measured result. The thread is drawing attention because Postman is widely used to store API keys, tokens, and request payloads that may include production credentials.

hackernews · sidgarimella · Nov 3, 17:22 · [Discussion](https://news.ycombinator.com/item?id=50354960)

**「Background」** Postman is a widely used API client for building and testing HTTP requests. It has long since expanded from a free desktop utility into a commercial API platform; a $225 million funding round valued the company at $5.6 billion, according to Livemint.

**「Impact」** For teams that keep live API credentials in Postman, the report makes default AI-feature and telemetry settings a concrete thing to audit, since silent plugin installation or data sharing would affect secrets stored in collections and environments. Commenters describe moving request definitions to local-first, git-backed clients such as Bruno and Kreya in response, which changes how teams review and version API tests.

**「Community discussion」** Commenters criticized Postman as slow and bloated and said they had switched to Bruno, the built-in REST client in JetBrains IDEs, or Kreya; several emphasized git-stored request definitions and offline-first operation as the reason. These are individual reported experiences and opinions, not confirmation of the issue&\#x27;s claims, and the thread&\#x27;s engagement does not establish consensus.

<details><summary>References</summary>
<ul>
<li><a href="https://www.livemint.com/companies/start-ups/postman-raises-225-million-valuation-soars-to-5-6-billion-11629297332045.html">Postman raises $225 mn, turns most valuable SaaS unicorn</a></li>

</ul>
</details>

**Tags**: `#privacy`, `#security`, `#developer-tools`, `#api-testing`, `#open-source-alternatives`

---

<a id="item-tech-news-3"></a>
### [Could modern chess algorithms on a 1996 Pentium have beaten Kasparov?](https://nicholas.carlini.com/writing/2026/algorithmic-improvements-chess.html) ⭐️ 7.0/10

Nicholas Carlini&\#x27;s post is a counterfactual analysis rather than a new benchmark: it asks whether modern chess-engine methods—improved search and NNUE-style evaluation—running on 1996 Pentium-era hardware could have defeated Garry Kasparov. The piece uses that question to examine how much engine strength comes from algorithmic improvements versus hardware and data, and whether the result was historically feasible for programmers at the time. The supplied material does not state a definitive verdict, so the exercise is best read as an argument about the sources of progress in computer chess.

hackernews · markusw · Nov 3, 07:56 · [Discussion](https://news.ycombinator.com/item?id=50349276)

**「Background」** The question refers to IBM&\#x27;s Deep Blue, which played then-world champion Garry Kasparov in a six-game match in 1996; Kasparov won 4–2, and Deep Blue won the 1997 rematch 3½–2½. Deep Blue was a purpose-built supercomputer, so the article&\#x27;s premise is whether ordinary Pentium-era hardware running modern search and evaluation methods could have produced a comparable opponent.

**「Community discussion」** Commenters pushed back on parts of the article&\#x27;s framing: one disputed the claim that grandmasters analyze roughly the same number of moves as amateurs, saying observed grandmaster play involves more branches and deeper lines. Another argued that most modern engine strength comes from NNUE, a neural evaluation trained on enormous data, so 1990s programmers could not have reproduced it even with the technique described, because they lacked the teacher model and training corpus. A further comment corrected the post&\#x27;s characterization of the Pentium Pro versus Pentium MMX, noting the Pro introduced the out-of-order P6 microarchitecture rather than being simply inferior to MMX.

<details><summary>References</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Deep_Blue_versus_Garry_Kasparov">Deep Blue versus Garry Kasparov - Wikipedia</a></li>

</ul>
</details>

**Tags**: `#chess engines`, `#algorithmic progress`, `#retrocomputing`, `#performance`, `#NNUE`

---

<a id="item-tech-news-4"></a>
### [Mac at Any Scale: Workarounds for macOS Infrastructure](https://namespace.so/blog/mac-at-any-scale) ⭐️ 7.0/10

The article “Mac at Any Scale” describes the operational problems and workarounds involved in running macOS infrastructure at scale, with particular attention to limitations in Apple’s ecosystem around CI and automation. It is aimed at teams that need Mac hardware for build and test workloads rather than individual desktop users. The Hacker News discussion treats those workarounds as evidence that Apple’s data-center and automation tooling remains cumbersome, while commenters disagree about whether renting Mac capacity is preferable to buying Mac minis.

hackernews · anner\_ · Nov 3, 14:53 · [Discussion](https://news.ycombinator.com/item?id=50352758)

**「Background」** Apple’s macOS license permits virtualization only on Apple-branded hardware, and its Virtualization framework allows at most two macOS guests to run concurrently per Mac. Those restrictions are the baseline constraint for teams that need many macOS build and test environments, which the article addresses through operational workarounds.

**「Impact」** Teams running macOS CI should expect to maintain custom automation and workaround layers around Apple’s tooling; the article’s focus and commenters’ complaints about Xcode Cloud and Apple automation point to a limited turnkey path for data-center Mac operations.

**「Community discussion」** Several commenters agreed that the article exposes workarounds forced by Apple’s ecosystem limits, with one arguing that demand would exist for server-grade Mac hardware and another calling Xcode Cloud and Apple’s automation “a joke.” A separate thread questioned renting versus buying: one commenter calculated that a $599 M4 Mac mini worked out to about six months of rental at the prices under discussion and noted its low power draw.

<details><summary>References</summary>
<ul>
<li><a href="https://juergenkoller.software/en/blog/more-than-two-macos-vms-on-apple-silicon.html">Running More Than Two macOS VMs on Apple Silicon | Juergen Koller</a></li>
<li><a href="https://virtualizationreview.com/articles/2025/04/28/hands-on-with-macstadium-remote-desktop.aspx">Hands On with MacStadium Remote Desktop -- Virtualization Review</a></li>

</ul>
</details>

**Tags**: `#macOS infrastructure`, `#CI/CD`, `#Apple ecosystem`, `#developer tooling`, `#scaling`

---

<a id="item-tech-news-5"></a>
### [Aircraft Noise and ADS-B Data Can Geolocate Videos, OSINT Demo Shows](https://simonwillison.net/2026/Nov/3/a-sound-that-leaks-your-exact-location/) ⭐️ 7.0/10

In a YouTube demonstration highlighted by Simon Willison, Colsto shows that nearly inaudible aircraft sounds in a video&\#x27;s soundtrack can be converted into Doppler curves and matched against ADS-B flight data to infer the footage&\#x27;s exact location from aircraft speed, distance, and gaps between flights. The post presents this as an OSINT technique with privacy implications, but it describes a demonstration rather than a released tool or an independently validated result.

rss · Simon Willison · Nov 3, 05:32

**「How the technique works」** ADS-B \(Automatic Dependent Surveillance-Broadcast\) is the publicly receivable stream of aircraft position and velocity data used by flight-tracking services, while the Doppler effect is the shift in frequency caused by relative motion between a sound source and a listener. The technique works because aircraft passing overhead leave faint, shifting-frequency noise in a recording; in the demonstration, spectrogram measurements constrained each flyover&\#x27;s velocity and closest-approach slant distance, and candidates were then filtered using the 920-second gap between two flyovers plus a silence constraint.

**「Impact」** People who publish video with incidental aircraft noise should treat the audio track as a possible geolocation channel, not only the visuals, because the demonstrated method relies on sound cues rather than visible landmarks.

<details><summary>References</summary>
<ul>
<li><a href="https://www.youtube.com/watch?v=UytYrhYLOKI">I discovered a sound that leaks your exact location ... - YouTube</a></li>

</ul>
</details>

**Tags**: `#OSINT`, `#privacy`, `#geolocation`, `#signal-processing`, `#ADS-B`

---

<a id="item-tech-news-6"></a>
### [Report: DeepSeek V5 planned for pre-training on Huawei Ascend](https://www.reddit.com/r/LocalLLaMA/comments/1xmmadn/deepseek_v5_is_planned_to_be_pretrained_on_huawei/) ⭐️ 7.0/10

An unconfirmed report citing multiple industry supply-chain sources says DeepSeek&\#x27;s next-generation V5 model is planned to be pre-trained on Huawei Ascend chips, shifting from Ascend&\#x27;s prior use primarily for inference. Neither DeepSeek nor Huawei has confirmed the claim, and no training scale, specific Ascend chip model, timeline, or performance details were provided. The report follows DeepSeek&\#x27;s September 30 open-source release of Ascend-targeted infrastructure components and a completed full-parameter post-training run of the 1.6-trillion-parameter V4-Pro on an Ascend 910C cluster, which did not include the initial pre-training phase.

reddit · r/LocalLLaMA · /u/hedgehog0 · Nov 3, 07:07

**「Background」** Pre-training is the compute-intensive stage that builds a model&\#x27;s base capabilities; the report says Huawei Ascend chips have so far been used mainly to run DeepSeek models for inference rather than to pre-train them. DeepSeek&\#x27;s V4, released in April 2026, was supported across Huawei&\#x27;s Ascend &quot;super-node&quot; products, and a project team later completed full-parameter post-training—not pre-training—of the 1.6-trillion-parameter V4-Pro on an Ascend 910C cluster. DeepSeek also open-sourced Ascend-specific infrastructure components on September 30, extending its software alignment beyond inference.

**「Developer impact」** For developers, the report raises a software-stack compatibility question rather than confirming a usable training platform: the V5 claim remains unverified and lacks performance evidence, while DeepSeek&\#x27;s existing Ascend work is already tied to Huawei&\#x27;s CANN stack. Teams should treat Ascend pretraining as unproven until DeepSeek or Huawei confirms it and provides benchmarks or tooling details.

<details><summary>References</summary>
<ul>
<li><a href="https://promptblueprints.tech/leaks/what-the-deepseek-v5-leak-actually-reports/">DeepSeek V 5 Leak: What the Report Says</a></li>
<li><a href="https://whatllm.org/blog/deepseek-v4-preview">DeepSeek V 4 is here: the open model that made... | WhatLLM.org</a></li>

</ul>
</details>

**Tags**: `#DeepSeek`, `#Huawei Ascend`, `#AI hardware`, `#LLM pretraining`, `#China AI`

---

<a id="item-tech-news-7"></a>
### [New York Times sues Brave over alleged scraping and resale to AI firms](https://techcrunch.com/2026/11/02/new-york-times-and-other-outlets-sue-web-browser-brave-over-alleged-content-scraping/) ⭐️ 7.0/10

The New York Times sued the privacy browser Brave on Monday, alleging it scraped copyrighted content and sold it to AI companies including Anthropic, Perplexity, Mistral, xAI and Cohere. The complaint, filed in Manhattan federal court, seeks an injunction and damages. The same day, the New York Daily News, the Chicago Tribune and other outlets filed similar suits. According to the complaint, Brave used an undisclosed crawler to build an index of more than 30 billion web pages, bypassed paywalls and blocked publisher advertisements; Brave has not yet responded, and the allegations have not been tested in court.

telegram · zaihuapd · Nov 3, 06:50

**「Background」** The case hinges on whether a web index assembled for a browser can be reused commercially as a feed for AI companies without separate permission from publishers. The plaintiffs allege that Brave ran an undisclosed crawler to build an index of more than 30 billion web pages, bypassed paywalls, blocked publisher ads, and sold the resulting content to AI developers.

**「Impact」** The suits target crawling performed at the browser level rather than by a standalone AI crawler, so a ruling could determine whether browsers must license the pages they index and resell. Because the outlets are seeking an injunction alongside damages, Brave&\#x27;s data pipeline to AI customers — not just its browser — is the exposure.

**Tags**: `#AI版权`, `#网页抓取`, `#Brave浏览器`, `#AI数据来源`, `#媒体诉讼`

---

<a id="item-tech-news-8"></a>
### [Report: Nvidia Said to Cap Chinese Customers at 49% of Data-Center Business](https://www.tomshardware.com/tech-industry/data-centers/nvidia-tells-data-center-operators-to-limit-business-from-chinese-customers-with-new-global-restrictions-report-claims-allegedly-restricted-to-49-percent-of-the-total-ensuring-51-percent-are-non-chinese-outfits) ⭐️ 7.0/10

According to a Financial Times report relayed by Tom&\#x27;s Hardware, Nvidia has asked data-center operators worldwide to keep business from Chinese companies at or below 49% of the total, ensuring at least 51% comes from non-Chinese customers. The requirement reportedly applies only to newly signed and future contracts, not to existing leases, and was communicated verbally by Nvidia&\#x27;s sales and regional teams with no formal document sighted. Nvidia did not confirm the policy directly, saying that U.S. chips underpin the ability of American model and application vendors to compete globally and that current U.S. policy encourages cloud providers to take on business from everywhere using U.S. infrastructure. The claim rests on unnamed sources in a single report, so both the policy&\#x27;s existence and its scope remain unverified.

telegram · zaihuapd · Nov 3, 16:19

**「Why customer mix matters」** Nvidia&\#x27;s China exposure has so far been shaped mainly by US export controls on advanced AI chips, which limit what the company can sell into the Chinese market. The reported requirement targets a different layer of the supply chain: data-center and cloud operators that buy Nvidia systems and resell compute capacity, whose share of Chinese customers Nvidia would now reportedly ask them to track and cap. The guidance is said to apply worldwide but only to new and future contracts, leaving existing leases unaffected.

**「Impact」** If the reported practice is real, operators negotiating new leases would need to track and limit the share of capacity committed to Chinese customers, even when those customers are outside the United States, since the restriction is described as global. Because the instruction was reportedly given verbally, operators would face compliance ambiguity without a written standard to audit against, while existing leases remain unaffected.

**Tags**: `#Nvidia`, `#data centers`, `#China`, `#export controls`, `#AI infrastructure`

---