---
layout: default
title: "Horizon Summary: 2026-11-10 (EN)"
date: 2026-11-10
lang: en
---

> From 44 items, 8 important content pieces were selected

---

**Technology News**
1. [E-means claims k-means-quality clustering in one-tenth the epochs](#item-tech-news-1) ⭐️ 8.0/10
2. [watched.earth maps satellite passes and their real imagery](#item-tech-news-2) ⭐️ 8.0/10
3. [Google announces TPU 8tx and 8i Max AI chips](#item-tech-news-3) ⭐️ 8.0/10
4. [Consumer Gemini alleged to send Drive and email data to human reviewers](#item-tech-news-4) ⭐️ 7.0/10
5. [Beep Locator triangulates a mystery beep with browser devices and Claude Code](#item-tech-news-5) ⭐️ 7.0/10
6. [LingBot-Touch tactile pretraining favors latent prediction over reconstruction](#item-tech-news-6) ⭐️ 7.0/10
7. [OPPO, vivo, Xiaomi, Honor launch mutual Android sideload verification](#item-tech-news-7) ⭐️ 7.0/10
8. [Leaked EU Digital Fairness Act Targets Addictive Design and Game Currency](#item-tech-news-8) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [E-means claims k-means-quality clustering in one-tenth the epochs](https://e-means.github.io/) ⭐️ 8.0/10

E-means is presented as a clustering method that reportedly matches or outperforms k-means while requiring one-tenth as many epochs. The project targets practitioners running centroid-based clustering, but the available evidence is a project claim plus early community experiments rather than broad independent validation. In comments, one developer reports a 146x GPU speedup after adapting the method to an IVF index, and another reports 2.5x faster bulk rebuilds of existing indexes while noting overall insertion time changed little because incremental clustering is a small part of CPU time. A separate practitioner found it not better than Lloyd&\#x27;s algorithm for relaxing an icosahedral equal-area sphere mesh, so the benefit appears workload-dependent.

hackernews · porridgeraisin · Nov 9, 18:45 · [Discussion](https://news.ycombinator.com/item?id=50429734)

**「Why Lloyd&\#x27;s algorithm is the baseline」** Lloyd&\#x27;s k-means has long been the standard clustering method for data analysis, retrieval, quantization, and data curation, and it works by repeatedly assigning points to their nearest centroids and recomputing those centroids, which requires many full passes over the dataset. E-means recasts that update as an exponential moving average optimization with mini-batch updates, borrowing machinery from deep-learning training, and the accompanying paper derives scaling laws for how decay rate and batch size affect convergence.

**「Payoff concentrated in full rebuilds, not incremental inserts」** Commenters&\#x27; adaptations suggest the gains land in batch clustering rather than incremental indexing: one reports a 146× GPU speedup after fitting e-means to an IVF index, and another reports bulk reindexing for cases like shard splits running 2.5× faster while overall insertion times barely moved, since incremental clustering is a small fraction of CPU time. Teams weighing a swap from Lloyd&\#x27;s algorithm should benchmark their own workload first — the project site reports validation across 24 datasets and 234 configurations, but one practitioner found it clearly worse for relaxing an icosahedral sphere mesh.

**「Community discussion」** Commenters largely treated E-means as promising, citing reported gains on IVF indexing and bulk reindexing, while the sphere-mesh experiment found it not better for that use case. One commenter framed the update rule as potentially an expectation-maximization variant with a friction term, emphasizing that it keeps centroids inside the convex hull.

<details><summary>References</summary>
<ul>
<li><a href="https://arxiv.org/abs/2611.09501">e-means : outperforming k-means (in one-tenth the epochs )</a></li>
<li><a href="https://arxiv.org/pdf/2611.09501">e-means : outperforming k-means (in one-tenth the epochs )</a></li>
<li><a href="https://e-means.github.io/">Modern optimization and scaling laws for k- means clustering</a></li>
<li><a href="https://mbrenndoerfer.com/writing/ivf-index-clustering-vector-search-partitioning">IVF Index : Clustering -Based Vector Search &amp; Partitioning - Interactive</a></li>

</ul>
</details>

**Tags**: `#clustering algorithms`, `#k-means`, `#machine learning`, `#performance optimization`, `#GPU acceleration`

---

<a id="item-tech-news-2"></a>
### [watched.earth maps satellite passes and their real imagery](https://www.watched.earth/) ⭐️ 8.0/10

The Show HN project watched.earth finds every satellite that passed over a chosen place in the last seven days and displays actual Sentinel-2, Landsat, and NASA images from those passes. Its pass search runs SGP4 against the CelesTrak catalog in the browser in about half a second; the author reports validation against brute force at the poles, antimeridian, and tiny swaths with zero missed passes. The site renders roughly 17,000 objects on the GPU while solving Kepler&\#x27;s equation each frame, and it marks a location as &quot;watched&quot; only when a real image exists. The author notes Sentinel-2 timestamps can be 5–10 minutes off from the actual crossing and says the site does not store the user&\#x27;s location.

hackernews · a585gupt · Nov 9, 17:51 · [Discussion](https://news.ycombinator.com/item?id=50428907)

**「Background」** Satellite pass prediction relies on SGP4, the standard propagation model that turns two-line element sets from public catalogs such as CelesTrak into orbital positions over time. Sentinel-2 and Landsat are openly accessible Earth-observation missions whose imagery is normally browsed through portals organized by scene rather than by observer location.

**「What it changes for imagery users」** Because the pass search runs entirely in the browser and the Sentinel-2, Landsat, and NASA scenes it surfaces are free public data \(NASA distributes Landsat data and products at no charge\), users can check which sensors imaged a specific place in the past week without first working through portals such as Copernicus or Earth Explorer. One commenter already applies it that way for backpacking trip planning, saying it covers more sources and is easier to access than Copernicus; anyone needing the raw scenes can still download them from the public archives. The stated privacy behavior — the site does not store your location — is the detail that matters for people searching a home address, and the &quot;watched&quot; label appears only where a real image exists.

**「Community discussion」** Commenters largely praised the execution, with one geospatial professional highlighting the ability to see the exact image a satellite took and a backpacking user saying it offers more coverage and easier access than Copernicus. No substantive criticism or disagreement appears in the supplied comments.

<details><summary>References</summary>
<ul>
<li><a href="https://science.nasa.gov/mission/landsat/data-overview/">Data Overview - NASA Science</a></li>

</ul>
</details>

**Tags**: `#satellite imagery`, `#SGP4`, `#geospatial`, `#GPU rendering`, `#Show HN`

---

<a id="item-tech-news-3"></a>
### [Google announces TPU 8tx and 8i Max AI chips](https://blog.google/innovation-and-ai/infrastructure-and-cloud/global-network/tpu-8i-max-and-8tx/) ⭐️ 8.0/10

Google announced two new TPUs: TPU 8tx for government agencies and tightly regulated industries handling sensitive data, designed to work alongside AMD chips, and TPU 8i Max for ultra-long-context AI workloads, which integrates two TPU chips in a single package for more compute and memory. The move expands Google&\#x27;s TPU lineup beyond its prior roughly two-year cadence; Apple, Meta, Oracle, and Anthropic are named as customers. Google did not disclose pricing, power efficiency, availability, or independent benchmarks, so comparisons with Nvidia remain unverified.

hackernews · \_benx\_ · Nov 9, 21:56 · [Discussion](https://news.ycombinator.com/item?id=50432831)

**「Context: Google&\#x27;s TPU lineup and release cadence」** TPUs are Google&\#x27;s in-house accelerators for machine-learning workloads, made available through Google Cloud rather than sold as standalone parts, so access and pricing are set by Google rather than by retail hardware channels. According to the source, Google had been on a roughly two-year cadence for new TPU generations before widening the lineup this year with application-specific parts, of which the 8tx and 8i Max are the latest additions.

**「Mixed-vendor deployments」** Government and regulated buyers of TPU 8tx will run a mixed Google–AMD environment, since Google says the chip works alongside AMD accelerators; cross-vendor software integration and procurement therefore become part of the deployment rather than an optional add-on. The supplied announcement also omits watt/token and dollar/token figures, so teams cannot yet benchmark TPU 8i Max against Nvidia GPUs on efficiency from Google&\#x27;s published material.

**「Community discussion」** Commenters questioned why Google does not sell the chips directly and asked for watts-per-token and dollars-per-token figures compared with Nvidia equivalents. One user reported that Colab still offers only v6e-1 TPUs, which they said is too small for serious work.

**Tags**: `#TPU`, `#Google Cloud`, `#AI infrastructure`, `#AI hardware`, `#agentic AI`

---

<a id="item-tech-news-4"></a>
### [Consumer Gemini alleged to send Drive and email data to human reviewers](https://github.com/thisisme6598/gemini_files/) ⭐️ 7.0/10

A Hacker News post alleges that consumer Google Gemini with Connected Apps can load personal Gmail and Drive data and route it to human annotators; no product change or independent verification was provided in the supplied material. Commenters said the issue is specific to consumer Gemini, citing Google Workspace documentation that Workspace Gemini is not subject to human review. The discussion focuses on whether connected-app permissions and Google&\#x27;s data-use terms adequately disclose that possibility.

hackernews · gf74918 · Nov 9, 18:24 · [Discussion](https://news.ycombinator.com/item?id=50429426)

**「Context: Gemini&\#x27;s connected apps」** Consumer Gemini can use a &quot;Connected Apps&quot; setting to draw on personal Google services such as Gmail, Photos, Search, and YouTube history so it can answer questions about the user&\#x27;s own activity. Users can review or disconnect those services under Settings &gt; Personal Intelligence &gt; Connected Apps.

**「Impact」** Consumer Gemini users who have authorized Gmail or Drive through Connected Apps should review those permissions and Google&\#x27;s data-use disclosures before treating the account as private; the discussion indicates that consumer and Workspace settings should be evaluated separately.

**「Community Discussion」** Commenters disagreed about whether the exposure is consumer-specific or systemic: bri3d said Workspace Gemini still claims no human review, while hek2sch alleged that manual reviewers affect all Gemini and NotebookLM. rustyhancock reported Gemini answers that seemed tuned to an email without disclosing that it had read the message.

<details><summary>References</summary>
<ul>
<li><a href="https://memx.app/fix/gemini-reading-my-gmail/">Gemini Reading My Gmail : How to Turn It Off | MemX</a></li>
<li><a href="https://blog.osintph.info/google-gmail-ads-asterisk/">Google ’s Gmail Ads Promise Now Has an Asterisk | OSINTPH</a></li>

</ul>
</details>

**Tags**: `#privacy`, `#Google Gemini`, `#AI data governance`, `#human review`, `#consumer AI`

---

<a id="item-tech-news-5"></a>
### [Beep Locator triangulates a mystery beep with browser devices and Claude Code](https://simonwillison.net/2026/Nov/9/mysterious-beeps/) ⭐️ 7.0/10

Simon Willison has published Beep Locator, an open-source Python web app that turns several browser-equipped phones, tablets, and laptops into listening devices to locate an intermittent beep. Devices join via QR code or URL, record a rolling 60-second audio buffer, and run an FFT-based detector; the server then has one device play a chirp and aligns uploaded clips around it to triangulate the sound. In Willison&\#x27;s test with two iPads, a phone, a MacBook Pro, and a Surface Ultra, the system located the beep within about 40 cm, leading him to an old carbon monoxide detector with failing batteries. The project was built with Claude Code, including an early cloud session on an iPhone using Opus 5.5 in Extra thinking mode.

rss · Simon Willison · Nov 9, 23:57

**「Background」** The project draws on the 2007 BeepBeep paper, which Claude found while drafting the problem statement; it describes high-accuracy acoustic ranging on commodity devices using two-way sensing, self-recording, and sample counting. Willison says the paper&\#x27;s description matched what the project needed to build.

**「Impact」** For developers, Beep Locator is a working reference implementation of browser microphone capture, WebSocket coordination, and chirp-based acoustic alignment, but Willison reports that automatic device-to-device location estimation &quot;didn&\#x27;t work particularly well.&quot; Reusing it therefore requires a rough manual placement mode, after which device positions can be adjusted from the sounds they play to each other.

**Tags**: `#AI-assisted development`, `#Claude Code`, `#audio triangulation`, `#open source`, `#practical project`

---

<a id="item-tech-news-6"></a>
### [LingBot-Touch tactile pretraining favors latent prediction over reconstruction](https://www.reddit.com/r/MachineLearning/comments/1xs05uo/latent_prediction_beats_reconstruction_for/) ⭐️ 7.0/10

Robbyant has introduced LingBot-Touch, a self-supervised tactile encoder pretrained JEPA-style to predict latent representations of masked contact rather than reconstruct raw sensor signals, with inference code and checkpoints public. In reported comparisons against same-size MAE and VAE baselines on the same data, tactile-to-video top-5 recall at 1K hours was 32.1% for JEPA versus 5.6% for MAE and 4.4% for VAE; at 4K hours JEPA reached 49.3%, MAE stayed below 9%, and VAE fell to 3.1%. The encoder feeds magnetic, piezoresistive and visuotactile sensors into one shared Transformer through canonical fingertip coordinates with 5D RoPE, and a masking ratio warmed from 40% to 80% over 300 steps avoids hiding every contacting taxel in sparse signals.

reddit · r/MachineLearning · /u/Zealousideal-War7154 · Nov 9, 18:52

**「Why the JEPA-versus-reconstruction comparison matters」** JEPA \(joint-embedding predictive architecture\) is a self-supervised recipe that trains an encoder to predict the latent representation of a masked input region, rather than regenerating the missing raw pixels or signals as a masked autoencoder \(MAE\) or VAE does. LingBot-Touch ports that objective from vision to touch, where sparse contact and long stretches of near-zero signal make raw reconstruction an easy target that can be minimized without learning contact structure. The paper&\#x27;s headline comparison is therefore between two pretraining objectives applied to identical tactile data and model sizes, not between two sensor hardware designs.

**「Impact」** For robotics teams, the practical claim is that a frozen LingBot-Touch encoder can serve as a reusable tactile backbone: its features scored highest in 89 of 104 policy-and-task combinations across 26 real robot tasks and four policies, and on a magnetic hand never seen in pretraining LingBot-VLA improved from 57.21 to 75.04. Teams adopting it should account for the paper&\#x27;s sensor-coordinate preprocessing and validate on their own hardware, since these are author-reported results in a Reddit announcement rather than independent replication.

**Tags**: `#self-supervised learning`, `#tactile sensing`, `#robotics`, `#JEPA`, `#representation learning`

---

<a id="item-tech-news-7"></a>
### [OPPO, vivo, Xiaomi, Honor launch mutual Android sideload verification](https://mp.weixin.qq.com/s/ZiKBASSLzvsZ6WR2AUmFeg) ⭐️ 7.0/10

OPPO, vivo, Xiaomi, and Honor have launched an Android developer identity verification \(ADV\) mechanism for sideloaded apps in mainland China, with each vendor recognizing the others&\#x27; verification results. Apps already registered and listed on the four vendors&\#x27; open platforms are submitted automatically and do not need a separate application. Apps that have not completed verification will trigger an “unverified” prompt when sideloaded, requiring the user to confirm manually before installation continues. The mechanism is intended to create a trusted link between developers and their apps and help users identify app origin and safety.

telegram · zaihuapd · Nov 9, 11:44

**「What developer identity verification adds to sideloading」** Sideloading means installing an app package outside an official app store, which previously gave users little beyond the package itself to judge who published it. Developer identity verification addresses that gap by tying an app to a verified developer account, and the four vendors&\#x27; mutual recognition means a result validated through one of their open platforms is accepted by the others rather than requiring separate submissions to each. The source does not describe the underlying technical specification or how the checks are enforced at the system level.

**「Impact」** Developers who distribute sideloaded builds outside the four open platforms face an additional user-confirmation step on these devices until their apps are verified, while apps already registered on those platforms are auto-submitted without a separate application.

**Tags**: `#Android sideloading`, `#developer verification`, `#mobile security`, `#app distribution`, `#China tech ecosystem`

---

<a id="item-tech-news-8"></a>
### [Leaked EU Digital Fairness Act Targets Addictive Design and Game Currency](https://www.mlex.com/mlex/articles/2546584/digital-businesses-face-addictive-design-controls-under-draft-eu-consumer-law) ⭐️ 7.0/10

A leaked draft of the EU Digital Fairness Act would require digital companies to let users disable design features such as autoplay and continuous-use rewards, and would impose subscription safeguards including cancellation buttons, renewal reminders, human customer service, and explicit consent before a free trial becomes paid. For games, it would ban paid random draws, pay-to-win mechanics, and profiling advertising aimed at minors, and require in-game currency to display its real-currency value. The European Commission is due to present the proposal on November 11, with violations carrying fines of up to 6% of global turnover; it is not yet adopted and must be agreed by the European Parliament and member-state governments.

telegram · zaihuapd · Nov 9, 16:42

**「Background」** The Digital Fairness Act is a new EU consumer-protection proposal, not an amendment to a single existing rule. The European Commission is scheduled to publish its first draft on 11 November, and part of the aim is to turn the Consumer Protection Cooperation network&\#x27;s concerns into binding law, according to GamesIndustry.biz.

**「Impact」** Game and subscription companies serving EU users would need to rework user-interface and storefront flows by adding opt-outs from engagement features, cancellation and renewal controls, and real-money labels for virtual currency if the text survives the legislative process. The 6% global-turnover penalty would apply only after adoption, so the leaked draft signals intended compliance obligations rather than an enforceable rule.

<details><summary>References</summary>
<ul>
<li><a href="https://www.gamesindustry.biz/a-guide-to-six-regulatory-risks-shaping-games-in-2026">A guide to six regulatory risks shaping games in... | GamesIndustry.biz</a></li>

</ul>
</details>

**Tags**: `#EU regulation`, `#consumer protection`, `#dark patterns`, `#game virtual currency`, `#subscription traps`

---