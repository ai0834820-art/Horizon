---
layout: default
title: "Horizon Summary: 2026-11-14 (EN)"
date: 2026-11-14
lang: en
---

> From 39 items, 5 important content pieces were selected

---

**Technology News**
1. [TorchTitan Scales 1T-Parameter MoE to 1,300 Tokens/s per GPU on 384 GH200s](#item-tech-news-1) ⭐️ 8.0/10
2. [Orcas Airband streams GPU-decoded airband transcripts during Vancouver ground stop](#item-tech-news-2) ⭐️ 7.0/10
3. [Microsoft 365 outage hits Outlook, Teams and Copilot for over 12 hours](#item-tech-news-3) ⭐️ 7.0/10
4. [DeepSeek opens app APIs for search, files, OCR and speech](#item-tech-news-4) ⭐️ 7.0/10
5. [OpenAI launches ChatGPT Wallet for tokenized agent payments](#item-tech-news-5) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [TorchTitan Scales 1T-Parameter MoE to 1,300 Tokens/s per GPU on 384 GH200s](https://www.reddit.com/r/MachineLearning/comments/1xvce5h/scaling_to_1t_moe_on_torchtitan_p/) ⭐️ 8.0/10

A Reddit post from an engineering team working with TorchTitan and PyTorch maintainers reports training a ~1T-parameter mixture-of-experts model at ~1,300 tokens/s per GPU on 384 GH200 GPUs, a 14X improvement over its starting point. The setup used 384-way FSDP plus 4-way expert parallelism kept strictly inside each node, deliberately skipping pipeline parallelism because its bubbles require many microbatches and long steps; JUPITER&\#x27;s InfiniBand supplies only ~25 GB/s per GPU, and the baseline step spent 68 of 84 seconds waiting on the network. Reported gains include full activation checkpointing with offload over the 900 GB/s Grace-Hopper link, Muon instead of Adam to reach 64k-token sequences, FlexShard expert sharding with GPU-side Newton-Schulz cutting the optimizer step from 42 s to ~2 s \(+35% throughput\), attention-cost bucketing that reduced the worst-rank imbalance from 7.9X to 1.15X \(+13%\), bf16 all-to-all expert-gradient reduction with local fp32 accumulation, FP8 expert all-gather \(+18%\), and moving collective temporaries to the compute stream via FSDP2&\#x27;s private unshard\_async\_op flag \(+21%, 13.5 GiB less peak reserved memory\). The poster notes group-limited routing gave +7% but may hurt training quality, with the verdict still open. These are the team&\#x27;s own measurements from a Reddit summary pointing to longer Domyn and PyTorch blog posts, not independently verified results.

reddit · r/MachineLearning · /u/f14-bertolotti · Nov 13, 16:28

**「Background」** TorchTitan is the PyTorch training library used for this run, and the reported setup shards the model with FSDP plus expert parallelism rather than pipeline parallelism; the authors say PP&\#x27;s many microbatches make steps long and failures slow to diagnose. The hardware is JUPITER&\#x27;s GH200 partition, where inter-node InfiniBand is roughly 25 GB/s per GPU—well below NVLink—so communication volume and overlap are the central constraints.

**「What developers can reuse」** Engineers training large MoEs on TorchTitan can adopt whole-expert sharding via FlexShard and the contributed GPU-side Newton-Schulz path for host-offloaded optimizers, which the authors report cut their optimizer step from 42 seconds to about 2 seconds and raised throughput 35% on 384 GH200 GPUs. The 21% throughput gain and 13.5 GiB peak-memory reduction from moving collective temporaries onto the compute stream currently depend on FSDP2&\#x27;s private \`unshard\_async\_op\` flag, so teams needing that fix must either use the private flag or wait for the public API the post says is in progress.

<details><summary>References</summary>
<ul>
<li><a href="https://pytorch.org/blog/training-a-1t-parameter-moe-on-eu-public-infrastructure-with-pytorch-and-torchtitan/">Training a 1T-Parameter MoE on EU public ... - PyTorch</a></li>
<li><a href="https://cctest.ai/en/articles/how-pytorch-scaled-a-near-1t-moe-on-europe-s-public-supercomputer">How PyTorch Trained a Near-1T MoE on Public Compute - CCTest</a></li>

</ul>
</details>

**Tags**: `#MoE`, `#TorchTitan`, `#PyTorch`, `#distributed training`, `#GH200`

---

<a id="item-tech-news-2"></a>
### [Orcas Airband streams GPU-decoded airband transcripts during Vancouver ground stop](https://orcasairband.com/) ⭐️ 7.0/10

Orcas Airband, a hobbyist software-defined-radio project, is publishing live monitoring and raw transcripts of the full airband from KORS. The operator says the setup uses an Ettus B210 receiver and two RTX 4090 GPUs, with CUDA code acting as a polyphase channelizer to split the band, demodulate transmissions, detect activity, and generate transcripts. The feed drew attention during a Vancouver ground stop; the operator posted unedited excerpts including a weak 2143Z Victoria Ground transmission and a 2151Z Vancouver Centre exchange. The transcripts are not independently verified and include unintelligible audio, and the project is a specialized hobby deployment rather than an official aviation feed.

hackernews · mmaunder · Nov 13, 22:04 · [Discussion](https://news.ycombinator.com/item?id=50490593)

**「Background」** The Ettus USRP B210 is a dual-channel software-defined radio transceiver with continuous coverage from 70 MHz to 6 GHz, which includes the civil airband VHF frequencies used for these transmissions. A polyphase channelizer is the DSP technique that splits one wideband capture into many narrow, evenly spaced channels simultaneously, letting a single receiver watch the whole band at once instead of retuning frequency by frequency.

**「Public transcripts widen access, but the setup stays hardware-bound」** The transcripts are published raw and unedited on a public web page, so anyone with a browser could follow exchanges such as Victoria Ground reporting traffic stopped and Vancouver Centre discussing alternates, without owning a receiver. That reach matters most during disruptions like the one on the posting day, when an FAA notice imposed a nationwide ground stop with more than 3,500 aircraft airborne, according to The Guardian. Reproducing the chain still requires an Ettus B210 and CUDA-capable Nvidia GPUs, so full-airband live monitoring remains a well-resourced hobbyist setup rather than an off-the-shelf tool.

**「Community discussion」** Commenters pointed to a timestamped exchange confirming the Vancouver ground stop and the operator said the feed was unexpectedly useful for following local pilot chatter; one reader said many transmissions were so garbled they could understand only about half. Another compared the project with a prior effort that decoded ship DSC signals from public KiwiSDR receivers.

<details><summary>References</summary>
<ul>
<li><a href="https://www.ettus.com/all-products/ub210-kit/">USRP B 210 USB Software Defined Radio ( SDR ) - Ettus Research</a></li>
<li><a href="https://www.theguardian.com/world/2026/nov/13/faa-nationwide-ground-stop-flights">US aviation agency lifts nationwide ground stop ... | The Guardian</a></li>

</ul>
</details>

**Tags**: `#software-defined radio`, `#GPU signal processing`, `#CUDA`, `#airband monitoring`, `#speech transcription`

---

<a id="item-tech-news-3"></a>
### [Microsoft 365 outage hits Outlook, Teams and Copilot for over 12 hours](https://www.reuters.com/technology/microsoft-365-outlook-down-thousands-us-users-downdetector-shows-2026-11-12/) ⭐️ 7.0/10

Microsoft&\#x27;s Outlook, Teams and Copilot services remained down for more than 12 hours, disrupting communications for enterprises and governments worldwide, according to a Reuters-sourced report. Microsoft attributed the disruption to a server problem, said it found no evidence of malicious activity, and reported that it had widened remediation efforts and was seeing signs of stabilization. Government agencies in Australia, Japan and parts of the United States were affected, Euronext&\#x27;s email was disrupted, and some Taiwanese financial institutions switched to fax to confirm trades. The report describes this as the second Microsoft 365 service interruption this year; the aggregator post dates the outage to Nov. 13 while the linked Reuters URL carries a Nov. 12 date, so the exact start time is unclear.

telegram · zaihuapd · Nov 13, 12:21

**「Background」** Microsoft 365 bundles Outlook, Teams, Copilot and other cloud services under one subscription, so a shared server-side fault can disrupt many organizations at once. The source notes that this was the second Microsoft 365 service disruption this year, without detailing the earlier outage.

**「Impact」** The outage forced affected organizations onto fallback channels — Euronext&\#x27;s email was blocked and some Taiwanese financial firms confirmed trades by fax — showing that continuity plans for dependence on a single cloud productivity suite still rely on manual workarounds during multi-hour disruptions. Microsoft has not published a full root-cause account, so customers have no confirmed timeline for when remediation will be complete beyond the reported signs of stabilization.

**Tags**: `#Microsoft 365`, `#cloud outage`, `#service reliability`, `#enterprise software`, `#Microsoft Teams`

---

<a id="item-tech-news-4"></a>
### [DeepSeek opens app APIs for search, files, OCR and speech](https://mp.weixin.qq.com/s/78KBHc4-4N5b2vfL9SkutQ) ⭐️ 7.0/10

DeepSeek has opened a suite of application APIs that let developers enable search, file input, link reading and speech in existing API calls, with the server handling tool invocation and context assembly. The V4.1-Flash model is supported across three interfaces, and Search, Fetch, OCR, ASR and TTS can each be called separately, according to the post. DeepSeek also open-sourced a chat frontend demo that can import prior conversations and be deployed locally using the API. The post did not provide benchmarks, pricing, rate limits, or independent verification.

telegram · zaihuapd · Nov 13, 14:27

**「Prior DeepSeek model work」** DeepSeek had already published the V4.1-Flash model and a technical report for it, so this announcement exposes existing model capabilities through new API parameters rather than introducing a new model. The change is that tool invocation and context assembly now happen on DeepSeek&\#x27;s servers instead of being coordinated by the developer&\#x27;s own code.

**「Impact」** Developers can call Search, Fetch, OCR, ASR and TTS separately rather than only through a bundled chat flow, and the open-source demo provides a starting point for deploying a DeepSeek-style chat interface locally.

<details><summary>References</summary>
<ul>
<li><a href="https://api-docs.deepseek.com/news/news261113/">The full DeepSeek App experience, now via API | DeepSeek API Docs</a></li>
<li><a href="https://huggingface.co/deepseek-ai/DeepSeek-V4.1-Flash/blob/main/DeepSeek_V41_Tech_Report.pdf">DeepSeek _ V 41_Tech_Report.pdf...</a></li>

</ul>
</details>

**Tags**: `#DeepSeek`, `#AI APIs`, `#tool calling`, `#multimodal AI`, `#open source`

---

<a id="item-tech-news-5"></a>
### [OpenAI launches ChatGPT Wallet for tokenized agent payments](https://openai.com/index/introducing-chatgpt-wallet/) ⭐️ 7.0/10

OpenAI announced ChatGPT Wallet, a payment feature that lets its AI agents complete purchases without receiving the user&\#x27;s real card number, built in partnership with American Express, Mastercard and Visa. Starting today it is available in the US to ChatGPT Pro subscribers aged 18 and older who hold US-issued cards, according to the company&\#x27;s announcement. For each transaction the user reviews the item and amount and confirms with Face ID or a fingerprint, while the card networks issue a payment token in place of the real card number. The details come from a brief Telegram repost of OpenAI&\#x27;s announcement and have not been independently confirmed.

telegram · zaihuapd · Nov 13, 15:43

**「Tokenization behind agent payments」** ChatGPT Wallet rests on card-network tokenization: rather than handing a merchant the user&\#x27;s real card number, the payment network issues a substitute payment token tied to that card. OpenAI&\#x27;s setup layers a per-purchase check on top, so the agent initiates the transaction while the user reviews the item and amount and confirms with Face ID or a fingerprint before the token is used.

**「What it means」** For US ChatGPT Pro subscribers, using ChatGPT Wallet requires a US-issued card and a per-purchase review of the item and amount followed by Face ID or fingerprint approval. That means agent-initiated checkout still depends on a user handoff for every transaction, so agent-commerce flows cannot run unattended under these terms.

<details><summary>References</summary>
<ul>
<li><a href="https://openai.com/index/introducing-chatgpt-wallet/">Introducing ChatGPT Wallet | OpenAI</a></li>

</ul>
</details>

**Tags**: `#OpenAI`, `#agentic payments`, `#ChatGPT Wallet`, `#payment tokenization`, `#fintech`

---