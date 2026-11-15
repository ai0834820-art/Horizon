---
layout: default
title: "Horizon Summary: 2026-11-15 (EN)"
date: 2026-11-15
lang: en
---

> From 37 items, 7 important content pieces were selected

---

**Technology News**
1. [Lovable-built apps exposed passport data and 200K+ messages](#item-tech-news-1) ⭐️ 8.0/10
2. [EFF Warns Tech Companies Are Reframing Privacy Again](#item-tech-news-2) ⭐️ 7.0/10
3. [Project Zero to adopt 90-day vulnerability disclosure, then 60 and 30](#item-tech-news-3) ⭐️ 7.0/10
4. [DeepSeek V3 inference reimplemented in about 200 lines of JAX](#item-tech-news-4) ⭐️ 7.0/10
5. [Cloudflare open-sources Kitesurf, a stateless browser for AI agents](#item-tech-news-5) ⭐️ 7.0/10
6. [Italy fines Meta €805 million over Facebook Android photo access](#item-tech-news-6) ⭐️ 7.0/10
7. [FAA ground stop traced to router fault in copper-to-fiber upgrade](#item-tech-news-7) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Lovable-built apps exposed passport data and 200K+ messages](https://www.crissyfield.de/research/lovable-en/) ⭐️ 8.0/10

A security report on crissyfield.de says apps built with Lovable exposed passport details and more than 200,000 private messages because of insufficient Row-Level Security. Lovable&\#x27;s head of security, commenting as igorandri, said insufficient RLS was the root cause and that Lovable scans every app automatically before publishing, offers a free deeper SAST scan, and gives users fix, auto-fix, and publishing-block options. The report identifies a specific exposure at scale, but the supplied material does not say how many apps or users were affected.

hackernews · armcat · Nov 14, 17:43 · [Discussion](https://news.ycombinator.com/item?id=50499017)

**「Background」** The affected Lovable-built apps use Supabase, a hosted Postgres development platform that gives application frontends access to the database. Supabase&\#x27;s Row-Level Security policies determine which rows a user can read or write, so missing or overly permissive policies can let frontend requests return records the app never intended to expose.

**「Impact」** For developers using Lovable and Supabase, the concrete task is to audit RLS policies on every exposed table and verify what a client can read before publishing; a pre-publish scan or one-click fix does not by itself prove the app&\#x27;s data is closed off.

**「Community Discussion」** Commenters debated where responsibility lies, with one pointing to a Supabase discussion that said an unsafe default was supposedly fixed on October 30 while reports suggested existing projects still retained it. Others argued that platforms need deny-by-default databases and automated authorization tests so AI-generated apps are harder to deploy insecurely.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/supabase/supabase">GitHub - supabase / supabase : The Postgres development platform. ...</a></li>

</ul>
</details>

**Tags**: `#security`, `#vulnerabilities`, `#Supabase`, `#AI code generation`, `#privacy`

---

<a id="item-tech-news-2"></a>
### [EFF Warns Tech Companies Are Reframing Privacy Again](https://www.eff.org/deeplinks/2026/11/tech-companies-are-trying-shift-entire-concept-privacy-again) ⭐️ 7.0/10

The EFF has published an analysis arguing that technology companies are trying to shift the concept of privacy again, with the supplied summary pointing to AI meeting recorders, surveillance norms, and accessibility trade-offs. The item does not include the article body, so its specific claims and any named companies or proposals are not available here.

hackernews · gslin · Nov 14, 12:45 · [Discussion](https://news.ycombinator.com/item?id=50496602)

**「From user consent to bystander exposure」** EFF&\#x27;s argument draws on a recurring theme in digital-rights writing: that &quot;privacy&quot; is being recast from an individual choice — accepting a setting, toggling a preference — into a question about the people who never agreed to be recorded. Summaries of the piece describe EFF&\#x27;s Thorin Klosowski pointing to camera-equipped smart glasses from Meta and Google, Apple&\#x27;s Audio Intelligence transcription on Apple Watch, and Amazon&\#x27;s Bee recorders as devices that relocate the privacy problem from the wearer to the bystanders around them.

**「Impact」** Meeting participants have limited room to decline: one commenter describes every professional meeting, including 1:1s with managers, being recorded and uploaded by AI notetakers, with no practical way to opt out and stay employed. For teams that do choose the tooling, the concrete levers are where audio is processed, who keeps the recording, and whether it is used for model training — the criteria vendor comparisons now grade notetakers on — so requesting that transcription be disabled for a given conversation, or selecting a locally processing tool, is the actionable step available.

**「Community discussion」** Commenters describe AI notetakers as increasingly unavoidable in professional meetings, including one-on-one conversations, and ask whether workers can establish a norm of requesting that transcription be turned off; one says opting out may be practically impossible without risking employment. Others argue that assistive live transcription can be transformative for deaf and hard-of-hearing users and could run locally without retention, while another invokes UN human-rights language on arbitrary interference with privacy.

<details><summary>References</summary>
<ul>
<li><a href="https://aiweekly.my/items/46520/tech-companies-are-trying-to-shift-the-concept-of-privacy-again">Tech Companies Are Trying to Shift the Concept of Privacy (Again )</a></li>
<li><a href="https://www.speechmark.co/articles/best-private-meeting-notetakers-mac">Best Private Meeting Notetakers for Mac ( 2026 ) — Speechmark</a></li>

</ul>
</details>

**Tags**: `#privacy`, `#AI notetakers`, `#digital rights`, `#workplace surveillance`, `#tech policy`

---

<a id="item-tech-news-3"></a>
### [Project Zero to adopt 90-day vulnerability disclosure, then 60 and 30](https://projectzero.google/2026/11/disclosure-policy.html) ⭐️ 7.0/10

Google Project Zero is reportedly moving to a 90-day vulnerability disclosure policy, with the window scheduled to shrink to 60 days on February 2, 2027 and to 30 days on January 3, 2028, according to a policy statement quoted in the discussion. Under the quoted policy, Project Zero will disclose vulnerabilities 90 days after reporting them to vendors, then apply the shorter windows on those dates. The item supplies no source text, so exceptions, extensions, or vendor-notification details are not established.

hackernews · hacb · Nov 14, 11:13 · [Discussion](https://news.ycombinator.com/item?id=50496051)

**「Prior policy」** Project Zero previously followed a &quot;90+30&quot; disclosure deadline: a vendor had 90 days after notification to make a patch available to users, with an additional 30-day grace period before full technical details were published. The new schedule drops that extra 30 days for a &quot;Full 90&quot; deadline and stages further reductions to 60 days on February 2, 2027, and 30 days on January 3, 2028.

**「Impact」** Vendors and open-source maintainers that receive Project Zero reports will need patch and release cycles that fit a 90-day deadline now and a 30-day deadline by early 2028, leaving less room for long review or backport queues.

**「Community discussion」** Commenters disagreed about whether the timetable is workable: one said Ubuntu &quot;will need a LOT more time than that,&quot; while another argued for immediate disclosure on the grounds that nothing else compels vendors to fix reported bugs. A separate comment raised whether companies using AI to find vulnerabilities should give vendors equivalent access to those tools, warning that disclosure could otherwise become leverage to drive LLM adoption.

<details><summary>References</summary>
<ul>
<li><a href="https://googleprojectzero.blogspot.com/p/vulnerability-disclosure-policy.html">Project Zero : Vulnerability Disclosure Policy</a></li>
<li><a href="https://projectzero.google/vulnerability-disclosure-faq.html">Vulnerability Disclosure FAQ - Project Zero</a></li>
<li><a href="https://www.escoffer.com/2025/08/16/google-tightens-security-timelines-through-faster-alerts/">Google Tightens Security Timelines Through Faster Alerts</a></li>

</ul>
</details>

**Tags**: `#vulnerability disclosure`, `#Project Zero`, `#security policy`, `#open source maintenance`, `#Google`

---

<a id="item-tech-news-4"></a>
### [DeepSeek V3 inference reimplemented in about 200 lines of JAX](https://github.com/Vaibhaav-Tiwari/deepseek-v3-jax) ⭐️ 7.0/10

A Show HN project by VaibhaavTiwari reimplements DeepSeek V3 inference in roughly 200 lines of pure JAX, presented as a compact educational reference rather than a production release. The implementation is reported to work on AMD hardware via ROCm; one commenter says it ran end-to-end on an RX 7600 XT 16GB, though that is a user report rather than an independently verified benchmark. Its small size makes the model structure and inference flow easier to study, but the supplied material provides no performance, accuracy, or broad compatibility guarantees.

hackernews · VaibhaavTiwari · Nov 14, 15:04 · [Discussion](https://news.ycombinator.com/item?id=50497589)

**「Context: JAX and DeepSeek V3」** JAX is the array-computation and automatic-differentiation framework used for this implementation, while DeepSeek V3 is the large language model being reimplemented for inference. A roughly 200-line version is intended as a compact, readable reference for tracing the model&\#x27;s inference path rather than as a production serving stack.

**「Impact」** Developers learning LLM inference gain a readable first-principles reference, while those trying it on ROCm should expect hardware-specific setup; an RX 7600 XT user reported needing environment overrides such as HSA\_OVERRIDE\_GFX\_VERSION=11.0.0.

**「Community discussion」** Commenters largely welcomed the from-scratch implementation as a learning resource, with one saying it motivated them to revisit JAX and another asking for a roadmap to build intuition. A ROCm user reported it as the first project that ran end-to-end on their RX 7600 XT 16GB after earlier local setup struggles, while noting required environment variables.

**Tags**: `#JAX`, `#DeepSeek V3`, `#LLM inference`, `#model reimplementation`, `#ROCm`

---

<a id="item-tech-news-5"></a>
### [Cloudflare open-sources Kitesurf, a stateless browser for AI agents](https://www.phoronix.com/news/Cloudflare-Kitesurf-Open-Source) ⭐️ 7.0/10

Cloudflare has open-sourced Kitesurf under the Apache 2.0 license, describing it as a stateless browser for AI agents built on Cloudflare Workers. According to Cloudflare, it can parse HTML, apply CSS, and execute JavaScript without requiring a browser container, and it uses less CPU and memory than Chromium while scaling on demand across the global Workers network. The code has been published on GitHub. The resource- and performance-comparison claims are vendor statements; the source provides no benchmarks or independent measurements.

telegram · zaihuapd · Nov 14, 09:33

**「Background」** Cloudflare Workers is a serverless platform that runs code on Cloudflare&\#x27;s edge network without requiring users to manage servers or containers. Conventional browser automation generally relies on a full headless browser such as Chromium; Kitesurf&\#x27;s premise is to parse HTML, process CSS and execute JavaScript directly inside a Worker, avoiding the CPU and memory overhead of a separate browser container.

**「Impact」** For agent developers, Kitesurf provides a Workers-native path that runs in V8 isolates rather than requiring a Chromium container, reducing resource overhead for browsing tasks. Because it is not Chromium-based, teams should test target sites for missing browser behavior before replacing an existing Chromium-based automation path.

<details><summary>References</summary>
<ul>
<li><a href="https://www.eesel.ai/blog/cloudflare-kitesurf">Cloudflare Kitesurf : the agent browser that trades speed... | eesel AI</a></li>

</ul>
</details>

**Tags**: `#Cloudflare`, `#AI agents`, `#browser automation`, `#open source`, `#Cloudflare Workers`

---

<a id="item-tech-news-6"></a>
### [Italy fines Meta €805 million over Facebook Android photo access](https://www.garanteprivacy.it/home/docweb/-/docweb-display/docweb/10321080) ⭐️ 7.0/10

Italy&\#x27;s privacy regulator, Garante Privacy, fined Meta €805 million after finding that the Facebook Android app accessed the photos, videos, and metadata of about 20 million Italian users without specific consent. The disputed feature, a photo-recommendation function rolled out in 2023, was enabled by default and presented users with only a generic authorization prompt. Meta must change the setting to off by default and obtain separate user consent within 60 days; otherwise, the feature may not be enabled for users who have not validly authorized it.

telegram · zaihuapd · Nov 14, 14:37

**「Background」** The case concerns a Facebook Android album-recommendation feature that Meta introduced in 2023. According to the Italian regulator’s account summarized in the source, the feature was enabled by default and relied on a broad authorization prompt rather than specific consent to read photos, videos, and metadata.

**「Impact」** Meta must rework the feature&\#x27;s default and consent flow for its Italian user base within 60 days, meaning roughly 20 million users would need to opt in separately before photo and video access resumes. The decision also puts the default-on, bundled-consent pattern used in Android app permissions under direct regulatory scrutiny.

**Tags**: `#隐私监管`, `#Meta`, `#用户同意`, `#Android应用`, `#科技行业`

---

<a id="item-tech-news-7"></a>
### [FAA ground stop traced to router fault in copper-to-fiber upgrade](https://www.theverge.com/transportation/1033898/faa-ground-stop-sean-duffy-faa-copper-wire) ⭐️ 7.0/10

U.S. Transportation Secretary Sean Duffy said on Nov. 14 that the FAA&\#x27;s nationwide ground stop ordered on Friday stemmed from routine maintenance replacing old copper wiring with fiber at a remote facility, after which a newly installed router ran into problems and thousands of flights were grounded. Duffy said the root cause remains unclear and could be a hardware fault, a configuration error, or a mistake by contractor L3Harris; the router sent more than 1,000 connection requests every 4 to 5 seconds to other routers, disrupting radar signals and aircraft communications. He cited the incident in calling on Congress to approve additional funding for air-traffic-control modernization.

telegram · zaihuapd · Nov 15, 02:10

**「Background」** The FAA has long outsourced operation of its air-traffic communications network: Harris Corp., the predecessor to L3Harris, won a contract in July 2002 to modernize, operate, and manage it. L3Harris separately holds a modernization contract covering more than 700 FAA ground stations and the national aircraft-tracking network through 2045.

**「Impact」** Airlines and passengers faced a nationwide ground stop and thousands of canceled or delayed flights. For the FAA, the unresolved cause means the copper-to-fiber rollout requires diagnosis across hardware, configuration, and contractor work before similar maintenance can be treated as routine.

<details><summary>References</summary>
<ul>
<li><a href="https://www.cbsnews.com/news/faa-issues-nationwide-ground-stop/">FAA lifts nationwide ground stop that disrupted thousands... - CBS News</a></li>
<li><a href="https://www.ainonline.com/aviation-news/air-transport/2026-06-01/faa-dashboard-provides-view-atc-modernization">FAA Dashboard Provides View into ATC Modernization | Aviation ...</a></li>

</ul>
</details>

**Tags**: `#FAA`, `#network outage`, `#router failure`, `#critical infrastructure`, `#aviation`

---