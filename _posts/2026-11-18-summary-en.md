---
layout: default
title: "Horizon Summary: 2026-11-18 (EN)"
date: 2026-11-18
lang: en
---

> From 40 items, 13 important content pieces were selected

---

**Technology News**
1. [Java4Shell RCE in OpenJDK Base64 decoding hits Java 17–27 on AVX-512 x86-64](#item-tech-news-1) ⭐️ 8.0/10
2. [Solid 2.0 adds server RPC, live primitives, diagnostics](#item-tech-news-2) ⭐️ 8.0/10
3. [External sandbox pattern isolates coding-agent code execution](#item-tech-news-3) ⭐️ 8.0/10
4. [Datasette Lite Rewritten to Run Full Datasette in Browser](#item-tech-news-4) ⭐️ 8.0/10
5. [Cloudflare casts Quad9&\#x27;s France exit as warning on DNS blocking](#item-tech-news-5) ⭐️ 7.0/10
6. [Microsoft&\#x27;s ONNX Runtime GitHub repository reportedly goes dark without warning](#item-tech-news-6) ⭐️ 7.0/10
7. [OpenAI releases GPT-6.2 Astra and Sol with cheaper Astra pricing](#item-tech-news-7) ⭐️ 7.0/10
8. [Nvidia stops disclosing Singapore sales as subsidiary revenue hits $104B](#item-tech-news-8) ⭐️ 7.0/10
9. [Phrack Issue 73 Released With Docker Escape and SSH1 Exploit History](#item-tech-news-9) ⭐️ 7.0/10
10. [Claude Code team outlines verification practices for AI-assisted coding](#item-tech-news-10) ⭐️ 7.0/10
11. [Microsoft announces MAI Code 2 and Code 2 Flash coding models](#item-tech-news-11) ⭐️ 7.0/10
12. [China Demonstrates 27 Gbps Bidirectional Q/V-Band Wireless Link](#item-tech-news-12) ⭐️ 7.0/10
13. [NVIDIA Board Creates National Security and Export Control Committee](#item-tech-news-13) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Java4Shell RCE in OpenJDK Base64 decoding hits Java 17–27 on AVX-512 x86-64](https://calif.io/java4shell/) ⭐️ 8.0/10

Security researchers published details of CVE-2026-114938, an unauthenticated remote code execution flaw in OpenJDK&\#x27;s Base64 processing, rated 9.2 under CVSS 4.0 and reported to have gone undetected for nearly four years. Affected versions are Java 17 from 17.0.6 onward, plus 21, 25 and 27; standard Java 8 and 11 are generally unaffected, with Oracle&\#x27;s Java 8 Performance Pack cited as an exception. The flaw is limited to x86-64 processors with AVX-512 VBMI — roughly Intel Ice Lake-generation Xeon and later \(2021+\) and AMD Zen 4 and later \(2022+\) — and does not affect ARM64. The write-up states that its network heap-grooming step is sensitive to RTT and jitter and was exercised over public internet addresses rather than only in a lab, so exploit reliability depends on network conditions.

hackernews · werrett · Nov 17, 21:11 · [Discussion](https://news.ycombinator.com/item?id=50538240)

**「Background」** Java&\#x27;s Base64 decoder is a routine entry point for untrusted data in network services, and the reported flaw is tracked as CVE-2026-114938 in that handling path. External coverage lists OpenJDK 17.0.6 and later, Java 21, 25 and 27 before the November 17, 2026 fixes, plus Oracle Java SE 8 Enterprise Performance Pack 8u511b33-perf, as affected; the vulnerable code runs only on x86-64 CPUs with AVX-512 VBMI. Standard Java 8 and 11 builds are generally reported to be unaffected.

**「Patch priority for AVX-512 Java hosts」** Organizations running Java 17.0.6+, 21, 25, or 27 on AVX-512-capable x86-64 servers—including Jenkins, Jira, Confluence, and Keycloak deployments—face unauthenticated remote code execution and should inventory JVMs and apply patches rather than assume standard Java 8 or 11 installations are safe, since Oracle&\#x27;s Java 8 Performance Pack is also affected. Qualys has published find-mitigate-patch guidance for CVE-2026-114938.

**「Community discussion」** A Semgrep engineer published free detection scripts keyed to five conditions, including that only HotSpot-based runtimes \(OpenJDK, Oracle JDK, GraalVM\) generate the relevant stub while OpenJ9 and Azul Prime do not, and another commenter relayed an unconfirmed Twitter claim that the AVX-512 Base64 decoder is at fault and that the -XX:UseAVX=2 flag avoids it. Commenters agreed the exploit conditions are narrow but argued that a large number of hosts still match them.

<details><summary>References</summary>
<ul>
<li><a href="https://orca.security/resources/research/java4shell-critical-openjdk-base64-decoder-flaw-could-allow-unauthenticated-remote-code-execution/">Java 4 Shell CVE - 2026 - 114938 : Affected Versions &amp; Mitigation</a></li>
<li><a href="https://thehackernews.com/2026/11/oracle-to-patch-11-java-flaws-today-as.html">Oracle to Patch 11 Java Flaws Today as Critical OpenJDK RCE...</a></li>
<li><a href="https://www.cyberkendra.com/2026/11/cve-2026-114938-pre-auth-rce-flaw-in-java-17-puts-servers-at-risk.html">Java 4 Shell ( CVE - 2026 - 114938 ): Java Base 64 Flaw... - Cyber Kendra</a></li>
<li><a href="https://blog.qualys.com/vulnerabilities-threat-research/2026/11/17/how-to-find-mitigate-and-patch-the-critical-java4shell-flaw-cve-2026-114938-now">How to Find, Mitigate, and Patch the Critical Java 4 Shell Flaw... | Qualys</a></li>
<li><a href="https://www.bleepingcomputer.com/news/security/critical-java4shell-flaw-allows-rce-attacks-on-major-java-applications/">Critical Java 4 Shell flaw allows RCE attacks on major Java applications</a></li>

</ul>
</details>

**Tags**: `#OpenJDK`, `#Java`, `#RCE`, `#Base64`, `#security research`

---

<a id="item-tech-news-2"></a>
### [Solid 2.0 adds server RPC, live primitives, diagnostics](https://www.solidjs.com/blog/solid-2-0-the-long-hold/) ⭐️ 8.0/10

Solid 2.0 is out, adding server RPC, live and broadcast primitives, and developer diagnostics to the SolidJS framework. The release targets developers building UI and full-stack applications with Solid, though the supplied material does not include migration guidance, compatibility requirements, or release details beyond the 2.0 version.

hackernews · pier25 · Nov 17, 18:56 · [Discussion](https://news.ycombinator.com/item?id=50536387)

**「Background」** Solid is a JavaScript UI framework built on fine-grained reactive primitives, and its 2.0 changes were scoped in public ahead of time: a GitHub discussion titled &quot;The Road to 2.0&quot; outlined the feature areas the team intended to target. Before this announcement, the project&\#x27;s site was already directing visitors to a Solid 2.0 release candidate, so the published release follows a public roadmap and a pre-release period rather than arriving unannounced.

**「Impact」** For Solid developers, the release adds framework-level server RPC and live/broadcast primitives, shifting more client-server and realtime wiring into Solid itself; teams considering an upgrade should check migration and compatibility details, which the supplied material does not provide.

**「Community discussion」** One commenter called the server RPC and live/broadcast design &quot;beautiful&quot; and more seamless than LiveView or htmx/datastar, while another argued the &quot;Built to Be Written by Agents&quot; diagnostics are really general debugging improvements useful for hand-written code too. A third commenter said they are still waiting for Vue 3.6 Vapor.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/solidjs/solid/discussions/2425">The Road to 2 . 0 · solidjs solid · Discussion #2425 · GitHub</a></li>
<li><a href="https://www.solidjs.com/">SolidJS · Reactive Javascript Library</a></li>

</ul>
</details>

**Tags**: `#SolidJS`, `#frontend frameworks`, `#JavaScript`, `#server RPC`, `#developer tooling`

---

<a id="item-tech-news-3"></a>
### [External sandbox pattern isolates coding-agent code execution](https://simonwillison.net/2026/Nov/17/external-sandboxes-for-coding-agents/) ⭐️ 8.0/10

Simon Willison and Prime Radiant have introduced an external sandbox pattern for coding agents in which agent-generated code runs inside a dedicated sandbox while the agent itself remains outside it. They released three server implementations: external-sandbox-v86, a Node.js server running Alpine Linux under v86 in WebAssembly; external-sandbox-container, a Python server using Alpine Linux in an Apple Containers instance; and external-sandbox-quicksand, a Python server using Microsoft&\#x27;s Quicksand, which bundles QEMU and Alpine Linux. All three expose the same localhost API, which can be configured in Pi, Claude Code, or Codex to handle code execution. They also include an optional HTTP/HTTPS allow-list proxy and a credential replacement mechanism that lets agent code make authenticated API calls without receiving the secret.

rss · Simon Willison · Nov 17, 22:52

**「Background」** Agents such as Pi, Claude Code, and Codex normally execute commands directly on the host with the user&\#x27;s own privileges, so a model mistake or a prompt-injection attack can damage the machine. Sandboxing confines that execution, and one library used here, Microsoft&\#x27;s Quicksand, is an async Python API that launches, controls, and snapshots QEMU virtual machines with prebuilt Ubuntu and Alpine images specifically aimed at sandboxing AI agents.

**「Impact」** Users can confine code from local or untrusted coding agents to a separate environment and restrict its network access to approved hosts, reducing exposure to prompt-injection or model mistakes. Using the pattern requires launching one of the sandbox servers and pointing the agent&\#x27;s execution API at its localhost endpoint.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/microsoft/quicksand">GitHub - microsoft / quicksand : Quickly sandbox your AI agent. · GitHub</a></li>

</ul>
</details>

**Tags**: `#AI coding agents`, `#sandboxing`, `#prompt injection`, `#agent security`, `#local models`

---

<a id="item-tech-news-4"></a>
### [Datasette Lite Rewritten to Run Full Datasette in Browser](https://simonwillison.net/2026/Nov/17/datasette-lite/) ⭐️ 8.0/10

Simon Willison has released a complete rewrite of Datasette Lite that runs the full Datasette Python application in the browser using Pyodide and service workers, rather than simulating requests and injecting the resulting HTML. Crafted lite.datasette.io URLs can load SQLite databases, JSON files, CSV files, or SQL scripts; select a Datasette release from PyPI or a GitHub commit, tag, or branch; choose from more than 100 SQLite versions; and install additional plugins from PyPI or wheel URLs. Willison says the result is almost indistinguishable from the server-side application and demonstrates it with the datasette-maplibre plugin, while noting that database and metadata URLs must have open CORS headers.

rss · Simon Willison · Nov 17, 16:48

**「Why the original port was limited」** Datasette Lite first launched in 2022 as a way to run the Datasette Python application entirely in the browser via Pyodide. That first version ran Datasette inside a Pyodide web worker and injected the resulting HTML into the top-level page with innerHTML, so script tags never executed and any feature depending on JavaScript — including additional plugins — failed to work. The rewrite replaces that approach with service workers, which is what allows the browser version to behave like the server-side application.

**「Impact」** Developers can now share a single Datasette Lite URL that pins a specific Datasette reference, plugin, and SQLite version, making it possible to post reproducible bug demonstrations or work-in-progress feature demos without deploying a web server; remote database and metadata files still need to be hosted with open CORS headers.

**Tags**: `#Datasette`, `#Pyodide`, `#WebAssembly`, `#service workers`, `#Python in browser`

---

<a id="item-tech-news-5"></a>
### [Cloudflare casts Quad9&\#x27;s France exit as warning on DNS blocking](https://blog.cloudflare.com/quad9-withdrawal-from-france/) ⭐️ 7.0/10

Cloudflare published an analysis framing Quad9&\#x27;s withdrawal of its public DNS resolver from France as a warning about DNS blocking mandates and their effect on public resolvers and internet freedom. The post is an advocacy argument rather than a disclosure of new technical detail, and it does not commit Cloudflare to withdrawing from any jurisdiction whose courts rule against it. Quad9 CTO John Todd said at IETF 127 that he had so far found unanimous support for Quad9&\#x27;s position there and that attendees felt &quot;general dread&quot; about what is happening with the DNS. The material available here does not include the underlying French order or a Quad9 timeline for the withdrawal.

hackernews · subset · Nov 17, 22:13 · [Discussion](https://news.ycombinator.com/item?id=50538994)

**「Background」** Quad9 is a free global public recursive DNS resolver that blocks domains associated with malware and phishing. The French dispute concerns DNS-level blocking mandates—requirements that public resolvers enforce domain blocks—which Quad9 has resisted and which led to its withdrawal from France.

**「Impact」** Networks and users in France that relied on Quad9 must now select a different resolver, while operators elsewhere have a concrete example of exit as a response to a blocking order. As one commenter noted, Cloudflare is itself contesting a ruling on appeal, and the post does not say whether it would withdraw if it lost — leaving its own users&\#x27; future access unresolved.

**「Community discussion」** Quad9&\#x27;s CTO reported from IETF 127 that support for the organization&\#x27;s position was unanimous among those he had spoken with, and several commenters described the shift as European overregulation eroding earlier internet freedoms. Commenter driverdan pressed Cloudflare to move beyond vague opposition and commit to withdrawing from countries whose rulings went against it.

<details><summary>References</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Quad9">Quad 9 - Wikipedia</a></li>
<li><a href="https://quad9.net/">Quad 9 | A public and free DNS service for a better security and privacy</a></li>

</ul>
</details>

**Tags**: `#DNS`, `#internet governance`, `#privacy`, `#content blocking`, `#Cloudflare`

---

<a id="item-tech-news-6"></a>
### [Microsoft&\#x27;s ONNX Runtime GitHub repository reportedly goes dark without warning](https://github.com/microsoft/onnxruntime) ⭐️ 7.0/10

The microsoft/onnxruntime GitHub repository, which hosts Microsoft&\#x27;s widely used ONNX Runtime inference engine, was reportedly inaccessible as of November 17 with no advance notice or official explanation. A commenter who said their evaluation pipelines began failing that morning described the repository, which they said had roughly 22,000 stars, as having &quot;gone dark.&quot; Neither Microsoft nor GitHub has confirmed a cause, and the supplied discussion contains only speculation, including a possible link to a compromised PyPI package or security cleanup. The removal should be treated as reported and unexplained rather than an established outage or deliberate takedown.

hackernews · nvader · Nov 17, 23:18 · [Discussion](https://news.ycombinator.com/item?id=50539610)

**「Background」** ONNX Runtime is Microsoft&\#x27;s cross-platform, high-performance engine for machine-learning inferencing and training, distributed primarily as an open-source library that applications link against rather than as a standalone service. Because it is widely embedded in production inference pipelines, developers commonly depend on the GitHub repository itself for source, issues, and build artifacts. Reporting on the disappearance describes the repository as no longer accessible, apparently deleted or made private, with no official explanation published so far.

**「Build and evaluation disruption」** ONNX Runtime is documented as powering inference in Microsoft products including Office, Azure, and Bing as well as community projects, so teams that build it from source lose their canonical microsoft/onnxruntime repository; a commenter reported evaluation pipelines failing. The Intel fork cited as an alternative carries OpenVINO modifications, so it should be tested rather than treated as a drop-in replacement.

**「Community discussion」** Commenters focused on workarounds and unverified causes: one pointed to Intel&\#x27;s fork at github.com/intel/onnxruntime, noting it includes Intel&\#x27;s OpenVINO modifications, while another claimed ONNX collects application telemetry unless built from source with telemetry disabled. Others speculated the removal could relate to a compromised PyPI package or model-backdoor research, but no commenter offered evidence connecting those to the repository&\#x27;s disappearance.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/microsoft/onnxruntime">GitHub - microsoft/onnxruntime: ONNX Runtime: cross-platform ...</a></li>
<li><a href="https://agihunt.info/en/p/1a1ebe81991e04a4ffba110460c">Microsoft&#x27;s ONNX Runtime repo has vanished… · AGI Hunt</a></li>
<li><a href="https://onnxruntime.ai/docs/">ONNX Runtime is a cross-platform machine-learning model accelerator</a></li>

</ul>
</details>

**Tags**: `#ONNX Runtime`, `#Microsoft`, `#GitHub`, `#open-source supply chain`, `#AI infrastructure`

---

<a id="item-tech-news-7"></a>
### [OpenAI releases GPT-6.2 Astra and Sol with cheaper Astra pricing](https://openai.com/index/introducing-gpt-6-2-astra-sol/) ⭐️ 7.0/10

OpenAI released GPT-6.2 Astra, its new frontier model for hard projects, and GPT-6.2 Sol, an efficient model for everyday work, both available in the API as \`gpt-6.2-astra\` and \`gpt-6.2-sol\`; Simon Willison&\#x27;s LLM 0.38 adds support. Astra costs $8 per million input tokens and $40 per million output tokens—80% of the $10/$50 GPT-6 Astra price—with cached input at $0.40 per million versus $1 for the older model, while Sol stays at $2/$10, half the price of GPT-5.6 Sol. Early feedback is mixed: Astra is reported not to score as high as Claude Fable 5.2 on various benchmarks, and reviewers cite confusing communication on long agentic tasks, though commenters also report large cost and speed gains.

hackernews · jasondavies · Nov 17, 17:46 · [Discussion](https://news.ycombinator.com/item?id=50535230)

**「Background」** OpenAI’s prior lineup provides the comparison points: GPT-6 Astra was priced at $10 per million input tokens and $50 per million output tokens, while GPT-6.1 Sol and GPT-6 Sol were $2/$10. The new models are positioned as successors to those tiers, with Astra aimed at harder workloads and Sol at everyday work.

**「Impact」** Developers can move to the new models by switching API requests to \`gpt-6.2-astra\` or \`gpt-6.2-sol\`. The practical saving is concentrated in long agentic sessions: Astra’s cached input is priced at $0.40 per million tokens, versus $1 for GPT‑6 Astra, so workflows that repeatedly resend context pay less, while Sol keeps GPT‑6.1 Sol’s $2/$10 token pricing and offers no per-token price cut.

**「Community discussion」** Commenters reported substantial cost savings in a data-analytics exam—Astra falling from about $20 to $4 and Sol from $2.6 to $1.2 with similar accuracy, partly from 20% fewer tokens and fewer tool calls—though some runs finished early and missed answers. Others criticized the office-task examples as poor, and PacBench comparisons put Astra slightly behind Kimi K3.1 Pro \(92 vs 93\) at a higher $2.04 cost, while one commenter highlighted system-card language about greater evaluation awareness and better chain-of-thought evasion.

<details><summary>References</summary>
<ul>
<li><a href="https://openai.com/index/introducing-gpt-6-2-astra-sol/">Introducing GPT - 6 . 2 Astra and Sol | OpenAI</a></li>

</ul>
</details>

**Tags**: `#OpenAI`, `#GPT-6.2`, `#LLM release`, `#AI benchmarks`, `#cost efficiency`

---

<a id="item-tech-news-8"></a>
### [Nvidia stops disclosing Singapore sales as subsidiary revenue hits $104B](https://www.ft.com/content/dbde7a30-548c-4f9d-a4be-7898a0c24dcf) ⭐️ 7.0/10

Nvidia has stopped disclosing Singapore sales even as external revenue at its Singapore subsidiary reached $104 billion, according to a Financial Times report. The change comes amid scrutiny of AI-chip flows and US export controls, affecting investors and regulators trying to trace where Nvidia revenue is booked versus where chips are ultimately used.

hackernews · louiereederson · Nov 17, 17:12 · [Discussion](https://news.ycombinator.com/item?id=50534631)

**「Background」** Megaspeed, the Singapore-based Nvidia customer at the center of the scrutiny, was incorporated in 2015 as 7Road International and renamed Megaspeed International in March 2023, according to business filings cited by Investing.com. U.S. agencies said they began investigating the company in 2024; the New York Times reported that the inquiry was transferred to the Justice Department after a top Nvidia executive contacted Commerce Department officials.

**「Impact」** The reduced geographic disclosure makes it harder to compare reported Singapore sales over time, but the $104 billion subsidiary figure should not be read as local demand: it reflects orders booked through the Singapore entity, not the final location of the chips. Investors and export-control analysts are left relying on subsidiary-level or channel data that does not establish end use.

**「Community Discussion」** Commenters argued the $104 billion figure is easily misread: one said it is external revenue of Nvidia&\#x27;s Singapore subsidiary and includes orders routed through that entity, not local end demand, while another called the disclosure change an accounting-attribution issue rather than evidence of where chips end up. Several cautioned against treating the number as proof of sanctions evasion.

<details><summary>References</summary>
<ul>
<li><a href="https://www.investing.com/news/stock-market-news/factboxwhat-we-know-about-megaspeed-singaporebased-customer-of-nvidia-5014126">What we know about Megaspeed , Singapore -based customer of...</a></li>
<li><a href="https://www.nytimes.com/2026/11/09/business/economy/nvidia-megaspeed-investigation-huang.html">U.S. Commerce Dept. Inquiry Into Megaspeed Was Halted After...</a></li>
<li><a href="https://www.cnbc.com/2026/11/17/megaspeed-investigation-nvidia-jensen-huang.html">U.S. agencies detail probe on Nvidia partner Megaspeed in 2024</a></li>

</ul>
</details>

**Tags**: `#Nvidia`, `#AI hardware`, `#export controls`, `#semiconductor supply chain`, `#corporate disclosure`

---

<a id="item-tech-news-9"></a>
### [Phrack Issue 73 Released With Docker Escape and SSH1 Exploit History](https://phrack.org/issues/73/introduction_md) ⭐️ 7.0/10

Phrack issue 73 has been released at phrack.org. The issue&\#x27;s contents are reported to include a Docker escape discussion and a history of the 2000 SSH1 exploit, along with other security research. The available material does not establish whether the Docker escape technique was responsibly disclosed or assigned a CVE, a question raised by commenters.

hackernews · notmine1337 · Nov 17, 18:31 · [Discussion](https://news.ycombinator.com/item?id=50535992)

**「Background」** Phrack issue 73 includes a retrospective on the 2000 SSH1 CRC32 remote code execution flaw, tracked as CVE-2001-0144, which allowed an attacker to gain root on many exposed SSH servers of that era \(tool-2-2\). The article recounts that earlier exploit rather than disclosing a new SSH vulnerability.

**「Impact」** For security practitioners, the issue is research reading rather than a patching notice: the available material does not state whether the Docker escape was disclosed to the vendor or assigned a CVE. Readers evaluating that article should check for a CVE or vendor advisory before treating it as a current vulnerability.

**「Community Discussion」** Commenters debated disclosure norms, with ashleyn asking whether the Docker escape had been responsibly disclosed or assigned a CVE before publication. Others valued Phrack&\#x27;s unpolished style and pointed to the issue&\#x27;s SSH1 exploit history as a notable read.

<details><summary>References</summary>
<ul>
<li><a href="https://archives.phrack.org/dl/73/the-2000-ssh1-exploit-that-broke-the-internet.pdf">PHRACK-2026-DTP-main-content (1)</a></li>

</ul>
</details>

**Tags**: `#cybersecurity`, `#exploit-development`, `#Phrack`, `#vulnerability-research`, `#SSH`

---

<a id="item-tech-news-10"></a>
### [Claude Code team outlines verification practices for AI-assisted coding](https://claude.dev/blog/how-the-claude-code-team-thinks-about-verification/) ⭐️ 7.0/10

The Claude Code team published an engineering blog post outlining its approach to verification for AI-assisted coding, including per-change checks driven by skill files, use of a &quot;Chrome for Claude&quot; tool to catch regressions, and using failures to decide which changes need human review. The post is vendor guidance rather than a shipped feature or an independently measured result. Commenters disputed its practicality, especially the token cost of running checks and multiple agents in parallel, and questioned whether Claude Code is reliable enough for daily use.

hackernews · craigmart · Nov 17, 10:20 · [Discussion](https://news.ycombinator.com/item?id=50529612)

**「Context」** Claude Code is Anthropic’s agentic coding tool for the terminal and IDE. The Claude Code team says roughly 90% of its own code is now written and reviewed by Claude, which makes “verification loops”—checks that give the agent evidence its changes work—central to delegating more work to it.

**「Impact」** For teams using Claude Code, the post offers a process template rather than a built-in capability, so verification steps and failure-based triage would need to be implemented in project workflows. The practical constraint raised is token spend: developers should weigh token-heavy per-change agent checks against deterministic browser automation such as Playwright, which one commenter says can catch regressions without spending model tokens.

**「Community discussion」** Commenters criticized the guidance as suited to unlimited token budgets, arguing that existing tools such as Playwright can catch regressions more cheaply, and one reported spending about $2,000 per month on tokens with only one or two agents. Others debated whether every diff needs human review, with one commenter arguing that breaking changes into small enough pieces keeps review feasible and another asking whether Claude Code has become reliable enough for daily use.

<details><summary>References</summary>
<ul>
<li><a href="https://claude.dev/blog/how-the-claude-code-team-thinks-about-verification/">How the Claude Code team thinks about verification / claude .dev Blog</a></li>
<li><a href="https://claude.com/product/claude-code">Claude Code by Anthropic | AI coding agent and assistant</a></li>

</ul>
</details>

**Tags**: `#AI coding agents`, `#software verification`, `#developer tooling`, `#LLM reliability`, `#code review`

---

<a id="item-tech-news-11"></a>
### [Microsoft announces MAI Code 2 and Code 2 Flash coding models](https://microsoft.ai/news/introducing-mai-code-2-and-mai-code-2-flash/) ⭐️ 7.0/10

Microsoft announced MAI Code 2 and MAI Code 2 Flash, two coding-focused models, on its corporate AI news site. The announcement body was not available for review, so Microsoft&\#x27;s benchmark figures, availability terms, pricing, and specific capability claims could not be verified. This is a vendor announcement rather than an independent technical evaluation.

hackernews · lemonish97 · Nov 17, 18:25 · [Discussion](https://news.ycombinator.com/item?id=50535885)

**「Background」** Microsoft&\#x27;s MAI family is the company&\#x27;s in-house model line, and Microsoft says MAI Code 2 is intended for everyday enterprise coding and is becoming the workhorse behind Microsoft products. GitHub&\#x27;s changelog lists both MAI Code 2 and the lighter MAI Code 2 Flash in GitHub Copilot, positioning Flash for code explanations, targeted edits, routine fixes, and rapid iteration.

**「Copilot availability and pricing caveat」** Developers using GitHub Copilot can select MAI Code 2 or MAI Code 2 Flash for coding and agentic tasks. However, published headline cost comparisons rely on a 50% promotional price, and API access differs between the two models, so teams should check current per-token pricing and availability before switching production workflows.

**「Community discussion」** One commenter reported that GitHub Copilot offered MAI Code 2 at a 50% discount and that, after switching, it resolved tricky Python build issues in Windows WSL/Ubuntu and Azure Bicep deployment problems while feeling comparable to Claude Opus — a single-user, unverified hands-on report. Other commenters argued that OpenAI&\#x27;s and Anthropic&\#x27;s lead may be only months deep and debated whether the benchmarks would hold up in practice, with one speculating, without evidence, that distillation from GPT models explained Microsoft&\#x27;s progress.

<details><summary>References</summary>
<ul>
<li><a href="https://microsoft.ai/news/introducing-mai-code-2-and-mai-code-2-flash/">MAI Code 2 and Code 2 Flash : Everyday coding at... | Microsoft AI</a></li>
<li><a href="https://github.blog/changelog/2026-11-17-mai-code-2-and-mai-code-2-flash-in-github-copilot/">MAI Code 2 and MAI Code 2 Flash in GitHub... - GitHub Changelog</a></li>
<li><a href="https://github.blog/changelog/2026-11-17-mai-code-2-and-mai-code-2-flash-in-github-copilot/">MAI Code 2 and MAI Code 2 Flash in GitHub Copilot</a></li>
<li><a href="https://techscurrent.com/2026/11/microsoft-mai-code-2-copilot-benchmark-promotional-pricing/">Microsoft MAI Code 2 Reaches Copilot: The Pricing Caveat ...</a></li>

</ul>
</details>

**Tags**: `#coding models`, `#Microsoft AI`, `#LLM competition`, `#developer tools`, `#GitHub Copilot`

---

<a id="item-tech-news-12"></a>
### [China Demonstrates 27 Gbps Bidirectional Q/V-Band Wireless Link](https://www.news.cn/tech/20261117/d6323540dccf4e2a976c48a762795956/c.html) ⭐️ 7.0/10

Researchers from the Chinese Academy of Sciences Aerospace Information Research Institute and partner organizations demonstrated a bidirectional Q/V-band wireless link at 27 Gbps at the Lijiang China Remote Sensing Satellite Ground Station, which the source describes as China&\#x27;s highest verified bit rate in that band. The experiment tested modulation from 64QAM through 512QAM; 512QAM reached 6.75 Gbps bidirectional on a single channel, and dual carriers plus polarization multiplexing raised the total to 27 Gbps. The team says it will next aim for more than 50 Gbps, but the result is an experimental ground-station verification, not a commercial deployment.

telegram · zaihuapd · Nov 17, 08:45

**「What Q/V band and 512QAM mean here」** Q/V band sits above Ka-band in the millimeter-wave spectrum, offering wide contiguous bandwidth for satellite and backhaul links but with greater sensitivity to atmospheric and rain loss, so links need more margin. 512QAM is a high-order modulation format that carries nine bits per symbol, raising throughput only when the received signal-to-noise ratio is high enough to distinguish the denser constellation — the reason the demonstration paired it with dual carriers and polarization multiplexing.

**「Impact」** For 6G and satellite-communications developers, the demonstration provides a domestic Q/V-band benchmark showing that 512QAM can be combined with dual carriers and polarization multiplexing to scale a link from 6.75 Gbps to 27 Gbps. The reported figures apply to this experimental ground-station setup, so they do not yet establish commercial terminal or operational satellite performance.

<details><summary>References</summary>
<ul>
<li><a href="https://www.rfwireless-world.com/terminology/understanding-qam-512-qam-vs-1024-qam-vs-2048-qam-vs-4096-qam">QAM: 512 - QAM vs 1024-QAM vs 2048-QAM vs ... | RF Wireless World</a></li>

</ul>
</details>

**Tags**: `#6G`, `#Q/V-band`, `#satellite communications`, `#wireless communications`, `#512QAM`

---

<a id="item-tech-news-13"></a>
### [NVIDIA Board Creates National Security and Export Control Committee](https://nvidianews.nvidia.com/news/nvidia-board-of-directors-establishes-national-security-and-export-control-oversight-committee) ⭐️ 7.0/10

NVIDIA&\#x27;s board has established a National Security and Export Control Oversight Committee to oversee the company&\#x27;s national-security policy, export-control compliance and global trade risk. The committee is composed of three directors, meets at least quarterly, and has engaged independent outside experts in law and trade compliance. NVIDIA&\#x27;s existing national-security and global trade compliance teams will report directly to the new committee and to the interim CEO. The board chair said advanced silicon technology and the emergence of AI and superintelligence present unprecedented national-security challenges.

telegram · zaihuapd · Nov 17, 10:57

**「Background」** NVIDIA&\#x27;s advanced AI chips sit inside a U.S. export-control regime that has sought to limit China&\#x27;s access not only through direct chip sales but also through third countries and cloud computing. A January 2025 BIS “AI diffusion” rule proposed a global licensing framework to curtail PRC access via third countries, and by August 2026 reports said Chinese AI firms had accessed Nvidia compute overseas, with lawmakers weighing how to close the cloud-access gap.

**「Impact」** The direct reporting line gives the new board committee a formal channel to oversee the teams handling NVIDIA&\#x27;s national-security and export-control matters, with those teams also reporting to the interim CEO. The committee&\#x27;s use of independent legal and trade-compliance experts adds external input to that oversight structure.

<details><summary>References</summary>
<ul>
<li><a href="https://www.cnbc.com/2026/08/19/china-ai-nvidia-chips-us-export-controls.html">China AI firms tap Nvidia power overseas as U.S ... - CNBC</a></li>
<li><a href="https://www.congress.gov/crs_external_products/R/PDF/R48642/R48642.5.pdf">U.S. Export Controls and China: Advanced Semiconductors</a></li>

</ul>
</details>

**Tags**: `#NVIDIA`, `#export controls`, `#AI governance`, `#semiconductors`, `#corporate governance`

---