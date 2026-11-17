---
layout: default
title: "Horizon Summary: 2026-11-17 (EN)"
date: 2026-11-17
lang: en
---

> From 41 items, 10 important content pieces were selected

---

**Technology News**
1. [vLLM v0.34.0 drops Model Runner V1, turns on extensible KV cache](#item-tech-news-1) ⭐️ 8.0/10
2. [Optimizely reportedly compromised, served malware via scripts on Zoom and GitLab](#item-tech-news-2) ⭐️ 8.0/10
3. [Jiff 1.0: A new datetime library for Rust](#item-tech-news-3) ⭐️ 8.0/10
4. [US extends AI chip export controls to remote access](#item-tech-news-4) ⭐️ 8.0/10
5. [Carnegie Mellon Launches Free CS Course Lectures on YouTube](#item-tech-news-5) ⭐️ 7.0/10
6. [Linebender&\#x27;s Squircles page explains smooth curve geometry](#item-tech-news-6) ⭐️ 7.0/10
7. [Marimba reuses one ASR encoder for calibrated speech queries](#item-tech-news-7) ⭐️ 7.0/10
8. [US and Nine Countries Sign San Francisco Declaration on AI Supply Chain](#item-tech-news-8) ⭐️ 7.0/10
9. [Amazon says Artex-driven agents pooled stolen API keys to fund LLM calls](#item-tech-news-9) ⭐️ 7.0/10
10. [Alibaba Withholds Qwen Weights as Chinese AI Firms Curb Offensive Cyber Capabilities](#item-tech-news-10) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [vLLM v0.34.0 drops Model Runner V1, turns on extensible KV cache](https://github.com/vllm-project/vllm/releases/tag/v0.34.0) ⭐️ 8.0/10

vLLM v0.34.0, released with 1,061 commits from 412 contributors, adds support for 10 new models including Mistral Large 4 and Nemotron-3.5-Transcribe and makes extensible KV cache sizing the default on CUDA and ROCm. The release removes Model Runner V1 entirely—Model Runner V2 is now the only GPU runner—and drops ROCm 7.2 artifacts in favor of ROCm 10.0. It also changes the default block size from 16 to 64 and requires huggingface\_hub &gt;= 2.0.0, so existing deployments need flag or dependency updates before upgrading. The release reports up to 1.95× faster decode on GB200 and 1.6× output throughput for GLM-5.3-Flash, while noting that per-token decode latency can rise 6–18% on some H200 models at concurrency 128 with the new KV cache defaults.

github · khluu · Nov 16, 23:22

**「Background」** vLLM&\#x27;s GPU Model Runner is the execution component that performs the model forward pass and sampling; before v0.34.0, users could fall back to the older V1 runner with \`VLLM\_USE\_V2\_MODEL\_RUNNER=0\`, an option that now fails at startup. The \`--block-size\` setting controls how many tokens each paged KV-cache block holds; vLLM had defaulted to 16 tokens per block, and this release changes that default to 64.

**「Impact」** Upgrading teams must remove VLLM\_USE\_V2\_MODEL\_RUNNER=0 or startup will fail, and must either accept the new 64-token block size and 1.0 gpu\_memory\_utilization default or pass --block-size 16 and --gpu-memory-utilization 0.9 to preserve prior behavior. ROCm 7.2 users must move to ROCm 10.0 wheels and images, since -rocm72 artifacts are no longer published.

**Tags**: `#vLLM`, `#LLM inference`, `#KV cache`, `#GPU performance`, `#release engineering`

---

<a id="item-tech-news-2"></a>
### [Optimizely reportedly compromised, served malware via scripts on Zoom and GitLab](https://blog.report-uri.com/worlds-largest-brands-infected-with-malware-via-optimizely/) ⭐️ 8.0/10

Optimizely was reportedly compromised and served malware through its script delivery on high-profile sites including Zoom and GitLab. The reported supply-chain incident affected a widely used third-party optimization and tagging vendor, so sites that embed its scripts may have exposed visitors to attacker-controlled code. The supplied material does not establish how the attacker obtained write access, how many customers were affected, or whether the malicious delivery has been fully contained.

hackernews · kristjansson · Nov 16, 23:00 · [Discussion](https://news.ycombinator.com/item?id=50524767)

**「Background」** Optimizely Web is an experimentation and personalization platform that customers embed on their pages through a JavaScript snippet loaded from Optimizely&\#x27;s CDN. That architecture means a compromise at the vendor can execute on every participating site at once, rather than requiring attackers to breach each customer individually. According to Report URI&\#x27;s analysis as summarized in coverage of the incident, malicious code was written into the Project JavaScript field of 188 Optimizely Web snippets, reaching visitors of 178 organizations on November 16, 2026, and was served with a valid certificate from Optimizely&\#x27;s own CDN.

**「Exposure and remediation」** For site operators, the incident shows that allowlisting an Optimizely domain is not a sufficient trust boundary: a commenter&\#x27;s analysis says the malicious code came from Optimizely&\#x27;s own delivery and also appeared on login.optimizely.com, so teams that load the snippet should audit what was served and review their CSP and tag-manager allowlists. Self-hosting external scripts would eliminate the CDN supply-chain risk, but it shifts update and security-patching work in-house.

**「Community discussion」** Commenters focused on accountability and third-party script architecture: one argued that tag managers such as Google Tag Manager let marketing add scripts without engineering involvement, producing heavy third-party JavaScript that sites should now re-evaluate, while another called the incident avoidable and urged providers and large publishers to use staged rollouts and security checks. Another commenter stressed that Optimizely&\#x27;s CDN served exactly the code it was given—not a cache-poisoning attack—and that how the attacker gained cross-customer write access remains unexplained.

<details><summary>References</summary>
<ul>
<li><a href="https://cybersecuritynews.com/optimizely-websites-hijacked/">Hackers Infect 178 Major Websites via Optimizely to Steal ...</a></li>
<li><a href="https://blog.tmcnet.com/blog/rich-tehrani/msp/optimizelys-trusted-script-hit-178-companies-visitors-your-vendors-vendor-is-now-your-attack-surface.html">Optimizely’s Trusted Script Hit 178 Companies’ Visitors. Your ...</a></li>
<li><a href="https://www.systemshardening.com/articles/cross-cutting/cdn-third-party-script-supply-chain/">CDN and Third - Party Script Supply Chain Security: Lessons from...</a></li>

</ul>
</details>

**Tags**: `#supply chain security`, `#third-party scripts`, `#web security`, `#Optimizely`, `#malware`

---

<a id="item-tech-news-3"></a>
### [Jiff 1.0: A new datetime library for Rust](https://burntsushi.net/jiff/) ⭐️ 8.0/10

Jiff 1.0 is a new date and time library for Rust from Andrew Gallant, known as burntsushi, positioned as an alternative to existing Rust datetime APIs. The release is drawing attention for its design and its treatment of timezone handling, a domain where Rust developers have relied on crates such as chrono. The supplied material does not detail API compatibility, migration support from chrono, or the minimum supported Rust version.

hackernews · burntsushi · Nov 16, 16:53 · [Discussion](https://news.ycombinator.com/item?id=50519744)

**「Background」** Jiff is a new Rust library for working with dates, times, and time zones, and version 1.0 is its first major release. It arrives in an ecosystem where the older \`chrono\` crate has long been a common choice; in the discussion, a former chrono maintainer says its API was stable but difficult to change, framing Jiff as an alternative rather than an incremental revision.

**「What changes for Rust developers」** Because Jiff puts time zone handling into the API itself rather than leaving it to callers, Rust developers using it for local-time and scheduling logic can rely on the library to handle daylight saving transitions instead of writing those adjustments by hand. The trade-off is ecosystem adoption: switching from chrono means replacing existing datetime types and call sites, and commenters frame wider adoption as a hope rather than something already achieved.

**「Community discussion」** Commenters welcomed Jiff as a professional, focused library, with one noting that its documentation openly says it is not the right tool for every use case. A former chrono maintainer described burnout from trying to improve chrono’s API against demands for stability, while another user asked how Jiff handles time scales such as TAI and UT1 for long-span astronomy simulations.

<details><summary>References</summary>
<ul>
<li><a href="https://burntsushi.net/jiff/">A datetime library for Rust - Andrew Gallant&#x27;s Blog</a></li>
<li><a href="https://news.ycombinator.com/item?id=50519744">Jiff 1 . 0 : A datetime library for Rust | Hacker News</a></li>

</ul>
</details>

**Tags**: `#Rust`, `#datetime`, `#open-source`, `#libraries`, `#timezones`

---

<a id="item-tech-news-4"></a>
### [US extends AI chip export controls to remote access](https://www.reuters.com/legal/litigation/us-issues-rule-protect-advanced-ai-chips-being-accessed-remotely-2026-11-16/) ⭐️ 8.0/10

The US Commerce Department issued an interim final rule on Nov. 16 extending export controls on advanced AI chips and servers to remote access, aiming to prevent access through third-country data centers. The rule requires licenses for reexports of AI chips to Indonesia, Malaysia, Singapore, Thailand and Brazil, according to The Verge, and the source says the Treasury and National Security Council led its drafting.

telegram · zaihuapd · Nov 16, 14:44

**「Background」** US export controls on advanced AI chips and servers have primarily targeted physical shipments and reexports. Remote access through data centers in third countries created a route to use restricted hardware without moving it to the end user, which the new rule is intended to close.

**「Licensing burden lands on third-country data centers」** Data-center and cloud operators in Indonesia, Malaysia, Singapore, Thailand and Brazil must now obtain BIS licenses to reexport advanced AI chips and servers, including where the hardware is only reached remotely by an end user in China, so existing capacity or hosting arrangements with Chinese-linked customers need compliance review before workloads continue. Bloomberg describes the rule as specifically aimed at cutting off Chinese firms&\#x27; remote access to Nvidia&\#x27;s AI chips through third-country data centers, which means the five named countries can no longer be treated as a routing workaround.

<details><summary>References</summary>
<ul>
<li><a href="https://qz.com/us-ai-chip-reexport-licenses-five-countries-111626">U . S . is requiring licenses to reexport AI chips to five countries</a></li>
<li><a href="https://www.bloomberg.com/news/articles/2026-11-16/us-moves-to-limit-remote-access-to-advanced-ai-chips">US Moves to Curb China’s Remote Access to Nvidia’s AI Chips</a></li>
<li><a href="https://wccftech.com/the-u-s-shuts-chinas-access-to-advanced-chips-via-singapore-brazil-indonesia-malaysia-and-thailand-as-scott-bessent-gives-nvidia-10-days-to-show-it-did-not-goose-its-revenues/">The U . S . Shuts China&#x27;s Access To Advanced Chips Via Singapore ...</a></li>

</ul>
</details>

**Tags**: `#AI chips`, `#export controls`, `#semiconductor policy`, `#data centers`, `#US-China tech`

---

<a id="item-tech-news-5"></a>
### [Carnegie Mellon Launches Free CS Course Lectures on YouTube](https://www.cs.cmu.edu/learn/) ⭐️ 7.0/10

Carnegie Mellon&\#x27;s CS Learn launched with full-semester lecture videos from current CMU computer science courses, posted free on YouTube. One course is scheduled to premiere each day this week, and more courses are planned for January, according to the project&\#x27;s organizer. The initial lineup includes courses such as ML Systems and 15-259 Probability and Computing. The release centers on lectures; whether assignments and homework will be included was asked in the discussion but not confirmed.

hackernews · pcompeau · Nov 16, 20:43 · [Discussion](https://news.ycombinator.com/item?id=50522980)

**「Background」** CS Learn is a new platform from CMU&\#x27;s Kenneth C. Griffin School of Computer Science, and its YouTube playlists are organized as complete semesters of real CMU courses rather than isolated lectures. In the discussion thread, organizer Phillip Compeau acknowledged that MIT&\#x27;s OpenCourseWare arrived about 25 years earlier and pointed to student-built tooling as a difference in CMU&\#x27;s approach.

**「Impact」** Self-directed learners can access current CMU course lectures without enrolling, but the release as described does not establish credit, grading, or assignment access.

**「Community Discussion」** Commenters welcomed specific courses such as 15-259 Probability and Computing and Tianqi Chen&\#x27;s ML Systems, while asking for core courses including 15-122, 15-150, 15-151, 15-251, and 15-451 and whether assignments would be released. One commenter argued that learning fundamentals remains valuable because it makes AI a power tool rather than a replacement.

<details><summary>References</summary>
<ul>
<li><a href="https://www.youtube.com/channel/UCqvooOJo8792T83va7LMMSA">CS Learn at Carnegie Mellon - YouTube</a></li>
<li><a href="https://www.pressreleasepoint.com/cmu-opens-access-top-computer-science-classes-through-free-cs-learn-platform">CMU Opens Access to Top Computer Science Classes Through Free ...</a></li>

</ul>
</details>

**Tags**: `#computer science education`, `#open courseware`, `#CMU`, `#online learning`, `#YouTube`

---

<a id="item-tech-news-6"></a>
### [Linebender&\#x27;s Squircles page explains smooth curve geometry](https://linebender.org/wiki/curves/squircle/) ⭐️ 7.0/10

Linebender&\#x27;s “Squircles” is a technical reference on squircles, superellipses, and smooth curve geometry aimed at graphics and UI engineers. The supplied item has no source body, release notes, version numbers, benchmarks, or availability details, so specific implementation claims could not be verified here. Its value is as an implementation reference rather than a product or industry announcement.

hackernews · raphlinus · Nov 16, 07:55 · [Discussion](https://news.ycombinator.com/item?id=50515151)

**「Background」** A squircle is a superellipse-based shape between a square and a circle, and its visual advantage over a rounded rectangle comes from curvature continuity: the curve avoids abrupt changes in curvature at the corners. Apple popularized the form for iOS app icons and hardware and UI elements, which is why graphics and UI engineers treat squircle geometry as a practical rendering and authoring problem.

**「Practical consequence」** Apple&\#x27;s iOS app icons use the squircle rather than a traditional rounded rectangle, so engineers recreating that geometry in CSS need a superellipse-based approach — via CSS \`corner-shape\` or a library such as \`figma-squircle\` — instead of a simple rounded corner.

**「Community discussion」** Commenters added practical context: one praised the Zune 2nd-generation squircle d-pad as a satisfying physical control, and another shared an in-progress spline and superellipse authoring demo. One commenter argued that curves avoiding derivative discontinuities matter when interfaces interact with physical reality, framing squircles as one part of smooth-curve geometry.

<details><summary>References</summary>
<ul>
<li><a href="https://elsolitario.org/en/2026/11/16/squircle-css-ios-icon-superellipse/">Squircle in CSS: What It Is and How to Build One</a></li>
<li><a href="https://squircle.js.org/blog/math-behind-squircles">The Squircle Formula: Superellipse Math Explained</a></li>
<li><a href="https://squircle.js.org/blog/squircles-in-apple-design">How Apple Uses Squircles in iOS Design - Squircle.js</a></li>
<li><a href="https://squircle.js.org/blog/squircles-in-apple-design">How Apple Uses Squircles in iOS Design - Squircle.js</a></li>
<li><a href="https://elsolitario.org/en/2026/11/16/squircle-css-ios-icon-superellipse/">Squircle in CSS: What It Is and How to Build One</a></li>

</ul>
</details>

**Tags**: `#squircles`, `#superellipses`, `#curve-geometry`, `#graphics-rendering`, `#ui-design`

---

<a id="item-tech-news-7"></a>
### [Marimba reuses one ASR encoder for calibrated speech queries](https://www.reddit.com/r/MachineLearning/comments/1xxsqro/marimba_a_system_one_model_for_speech_r/) ⭐️ 7.0/10

A preprint introduces Marimba, which makes one frozen Qwen3-ASR-0.6B encoder pass per 8-second audio window and returns a calibrated probability for each typed query about that window. Term detection is zero-shot over decoder hypotheses, while language ID, turn end, speaker change, and speaker count use the model&\#x27;s scores or small readouts on frozen layers. The authors report matching or beating Qwen3-Omni \(30B-A3B\) on 6 of 9 shared tests, but losing to Smart Turn v3.2 on turn-end detection \(AUROC 0.930 vs 0.982\) and failing on CochlScene, where every head is at chance. Code and Apache-2.0 weights are released.

reddit · r/MachineLearning · /u/solanotodesch · Nov 16, 15:47

**「Context: frozen ASR features for typed speech decisions」** The post is a follow-up to an earlier Reddit thread on the same project and now points to the arXiv preprint \(2611.18330\), which frames the work as an interface for typed speech decisions built on frozen Qwen3-ASR 0.6B features rather than a task-specific model per question. In the paper&\#x27;s description, lexical questions are scored zero-shot from the decoder&\#x27;s greedy and four beam-search hypotheses and calibrated with Platt scaling, while non-lexical questions use a question-conditioned head plus a separate layer-18 turn-end readout.

**「Impact」** Developers can answer several audio questions from one 8-second encoder pass rather than train separate models per task, but the reported CochlScene result means they should validate any new query type rather than assume the shared representation transfers; the authors also flag their turn-end result as in-distribution because that readout was trained on Smart Turn data.

<details><summary>References</summary>
<ul>
<li><a href="https://arxiv.org/html/2611.18330v1">marimba: A System One Model for Speech - arXiv.org</a></li>

</ul>
</details>

**Tags**: `#speech-recognition`, `#asr`, `#model-calibration`, `#efficient-inference`, `#machine-learning-research`

---

<a id="item-tech-news-8"></a>
### [US and Nine Countries Sign San Francisco Declaration on AI Supply Chain](https://www.state.gov/releases/office-of-the-spokesman/2026/11/the-san-francisco-declaration-on-the-secure-foundations-of-enduring-prosperity/) ⭐️ 7.0/10

On November 15, the United States and nine other countries — Australia, India, Israel, Japan, South Korea, Qatar, Singapore, the UAE, and the UK — signed the San Francisco Declaration, affirming that economic security underpins national security and committing to jointly protect sensitive technologies and critical infrastructure in the superintelligence \(SI\) supply chain. The declaration establishes five working groups covering innovation policy frameworks, SI applications in critical sectors, full-stack SI supply-chain collaboration, safe harbors and a supply-chain security hub, and SI security and resilience. The source describes a declaration rather than a binding agreement, and reports no specific commitments, technical standards, or implementation timelines.

telegram · zaihuapd · Nov 16, 10:40

**「Background」** The declaration’s focus is the superintelligence \(SI\) supply chain—specifically the sensitive technologies and critical infrastructure that support SI. It treats protecting those inputs as a matter of economic security, the premise for the five working groups it proposes.

**「Impact」** For companies across the ten signatory countries, the declaration&\#x27;s practical channel is its five working groups — covering innovation policy frameworks, SI use in critical sectors, full-stack supply chain cooperation, safe harbors and supply-chain security hubs, and SI security and resilience — which the State Department frames as a step toward reducing reliance on U.S. adversaries for critical minerals, AI models, and semiconductors. The announcement discloses no binding commitments or deadlines, so firms in chips, minerals, and AI model development should treat the working groups, not immediate rule changes, as the near-term mechanism to watch.

<details><summary>References</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/San_Francisco_Declaration_on_the_Secure_Foundations_of_Enduring_Prosperity">San Francisco Declaration on the Secure Foundations of Enduring Prosperity</a></li>
<li><a href="https://www.state.gov/releases/office-of-the-spokesman/2026/11/the-san-francisco-declaration-on-the-secure-foundations-of-enduring-prosperity/">The San Francisco Declaration on the Secure Foundations of ...</a></li>
<li><a href="https://www.state.gov/pax-silica/">Pax Silica - United States Department of State</a></li>

</ul>
</details>

**Tags**: `#AI governance`, `#AI supply chain`, `#geopolitics`, `#technology policy`, `#superintelligence`

---

<a id="item-tech-news-9"></a>
### [Amazon says Artex-driven agents pooled stolen API keys to fund LLM calls](https://cybernews.com/security/amazon-autonomous-cybercrime-artex-framework/) ⭐️ 7.0/10

Amazon says attackers used the open-source Artex penetration-testing framework to direct AI agents to steal API keys from internet-exposed LiteLLM and Dify applications, validate them, and pool them to pay for additional LLM calls. The campaign ran from October 3 to November 5, when Amazon&\#x27;s MadPot decoy network disrupted it, according to the company. Amazon attributed the activity to a China-related threat group with medium confidence, said not all listed targets were compromised, and notified AWS customers that may have been affected.

telegram · zaihuapd · Nov 16, 13:00

**「Background」** ARTEX is an open-source agentic AI penetration-testing framework that can orchestrate AI agents to perform offensive security tasks. Amazon&\#x27;s threat-intelligence team described MadPot as a globally distributed network of decoy threat sensors, which it used to capture the agents&\#x27; requests and campaign records.

**「Impact」** Organizations running internet-exposed LiteLLM or Dify instances should treat their API keys as potentially compromised, rotate them, and check LLM usage and billing for unauthorized calls, because Amazon says stolen keys were pooled to fund more model requests. Limiting public reachability and setting per-key spend caps address the exposure and cost-abuse path described in the report.

<details><summary>References</summary>
<ul>
<li><a href="https://aws.amazon.com/blogs/security/amazon-threat-intelligence-observes-threat-actors-running-cybercrime-campaigns-with-artex-ai-agents/">Amazon Threat Intelligence observes threat actors running ...</a></li>

</ul>
</details>

**Tags**: `#AI security`, `#API keys`, `#autonomous agents`, `#cybercrime`, `#open-source security`

---

<a id="item-tech-news-10"></a>
### [Alibaba Withholds Qwen Weights as Chinese AI Firms Curb Offensive Cyber Capabilities](https://www.bloomberg.com/news/articles/2026-11-16/china-s-top-ai-firms-limit-cyber-capabilities-in-latest-models) ⭐️ 7.0/10

Alibaba, Tencent, and Moonshot have reportedly reduced offensive cyber capabilities in their new models while improving defensive performance, according to a Telegram post summarizing a Bloomberg report. Alibaba&\#x27;s latest flagship Qwen is not being released with open weights, so users cannot download and customize the full version, and Tencent cut cyber functions before releasing Hy4 this month. The moves are linked to a draft export-control rule published by China&\#x27;s Commerce Ministry last month that would ban exports of AI tools capable of attacking critical infrastructure or government networks; the report&\#x27;s details have not been independently verified.

telegram · zaihuapd · Nov 17, 02:20

**「Context: draft export rule and misuse concerns」** The model changes come as China&\#x27;s Commerce Ministry, which published a draft export-control rule last month, proposes banning exports of AI tools capable of attacking critical infrastructure and government networks. Concern about model misuse has been building: Bloomberg-sourced coverage reported that DeepSeek&\#x27;s models were used in attacks across 14 countries, part of the backdrop for vendors trimming offensive cyber features.

**「Impact」** For developers, the reported withholding of full Qwen weights removes the option to download and locally customize the flagship model, so workflows built on open-weight Qwen releases would need earlier versions or alternative models. If the draft export controls are finalized, companies would also face a compliance limit when exporting models that can attack critical infrastructure or government networks.

<details><summary>References</summary>
<ul>
<li><a href="https://www.bloomberg.com/news/articles/2026-11-16/china-s-top-ai-firms-limit-cyber-capabilities-in-latest-models">China’s Top AI Firms Limit Cyber Capabilities in Latest ...</a></li>
<li><a href="https://www.kucoin.com/news/flash/china-s-top-ai-firms-limit-cyber-capabilities-in-latest-models">China&#x27;s Top AI Firms Limit Cyber Capabilities in Latest ...</a></li>

</ul>
</details>

**Tags**: `#China AI`, `#AI policy`, `#cybersecurity`, `#open weights`, `#export controls`

---