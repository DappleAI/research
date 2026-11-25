# DappleAi Research

Research by [DappleAI](https://dappleai.com) on why powerful AI models still fail everyday users, and the interface infrastructure that fixes it.

Hundreds of millions of people have tried AI, but few use it well. Our research traces that gap to structure, not to user error (e.g. an open prompt box puts the work of framing, context, model choice and iteration on the person least equipped to do it). Dapple's answer is an adaptive orchestration layer between people and models. It frames the task, injects the right context at the right moment, and routes the work to whichever model fits, so users get reliable results without becoming prompt engineers.

This repository indexes the research behind that design; user and market analysis, the architecture we propose, our patent-pending context methods, and the open-source code that implements them.

## Research areas

| Area | Problem | Output |
|---|---|---|
| AI usability | Why adoption stalls even as models improve | [Friction by Design](#friction-by-design-a-structural-analysis-of-ais-usability-crisis) |
| Market structure | Where a crowded, fast-changing AI market leaves everyday users unserved | [The Imperfect, Fast-Growing AI Market](#the-imperfect-fast-growing-artificial-intelligence-market-an-analysis-of-the-current-waves) |
| Interface design | Replacing open-ended prompting with guided, role-aware workflows | [Litepaper](#the-dappleai-litepaper-the-adaptive-orchestration-layer) |
| System architecture | Framing, context injection, task structure and model routing as one stack | [Technical Thesis](#the-adaptive-orchestration-layer-a-multi-layer-technical-stack-for-ai-20), [`dapple-core`](https://github.com/dappleAI/dapple-core) |
| Context engineering | Writing SQL that query planners, DBAs, data pipelines and AI agents can all work with | [Context Engineering for the Database Layer](#context-engineering-for-the-database-layer-structuring-sql-for-planners-pipelines-and-llms), [`sql-composer`](https://crates.io/crates/sql-composer) |

## Papers

Start with the Litepaper for the big picture, then Friction by Design for the evidence. The Technical Thesis and the Context Engineering paper go deeper.

### The DappleAI Litepaper: The Adaptive Orchestration Layer

DappleAI · [PDF](papers/dappleai-litepaper.pdf) · September 2025

AI adoption has soared but real utility hasn't. Most interfaces hand users a blank box, and enterprise tools are built for teams most people aren't on. The litepaper argues that foundation models are raw capacity, like an electrical grid, and that the missing piece is a utility layer that makes them usable. It describes DappleAI's three components: a Zero Friction Interface that turns the blank page into guided steps, a Learning Engine that surfaces what users didn't know to ask, and a Flexible Architecture that routes each task to the right model. It closes with DappleAI's commitments on community-led design, privacy and accountable infrastructure.

### Friction by Design: A Structural Analysis of AI's Usability Crisis

DappleAI · [PDF](papers/friction-by-design.pdf) · 2025

Public access to large language models has scaled faster than any prior technology, but meaningful adoption hasn't followed. Drawing on customer conversations, behavioral patterns and third-party research, this paper identifies four root causes: **time to value, required expertise, lack of awareness, and eroding trust**. It defines two underserved segments, *Frustrated Believers* (motivated users who find the path from prompt to payoff slow and draining) and *Apprehensive Avoidants* (people held back by low awareness and low trust). It concludes that access does not equal activation, that leverage requires literacy, and that interfaces are infrastructure.

### The Imperfect, Fast-Growing Artificial Intelligence Market: An Analysis of the Current Waves

DappleAI · [PDF](papers/ai-market-analysis.pdf) · 2025

AI is entering its platform era. Adoption is unprecedented, but utility is still gated by user fluency. This paper maps the industry along three forces: lots of people, lots of tools, and lots of change. It groups the competitive landscape into four clusters (foundation models, enterprise copilots, domain-specific tools, and the DIY ecosystem) and identifies the missing wedge: a Canva-like surface for everyday AI use. It then sizes the opportunity, examines adoption data showing a gap between exposure and confidence, and considers the implications for capturing the market.

### The Adaptive Orchestration Layer: A Multi-Layer Technical Stack for AI 2.0

DappleAI · [PDF](papers/technical-thesis.pdf) · 2025 · Code: [`dapple-core`](https://github.com/dappleAI/dapple-core)

Most AI interfaces are built on improvisation, which produces cognitive friction and inconsistent results. This technical thesis argues that usability is infrastructure, not a feature, and adapts the model to the user instead of the reverse. It describes four components: **Dual Phase Context Injection (DPCI)**, which frames a task before refining the output; a **Task Ontology** of structured task packets mapped to roles and focus areas; a **Role Swapping System** that applies identity-specific context automatically; and a **model-agnostic backend** with routing that balances quality, latency and cost. Together they eliminate cold starts, reduce drift across long sessions, and insulate users from churn in the underlying models.

### Context Engineering for the Database Layer: Structuring SQL for Planners, Pipelines, and LLMs

Kenny Flegal · [PDF](papers/context-engineering-database-layer.pdf) · 2025 · Code: [`sql-composer`](https://crates.io/crates/sql-composer)

Who do we write SQL for? This architectural proposal names five audiences: the database engine's query planner, the DBA team, SQL strategists, the data pipeline, and, increasingly, AI agents. It argues that keeping SQL in shareable, compile-time-checked files serves all of them. It introduces SQL Composer, a SQL pre-processor published on crates.io. SQL Composer keeps richly commented, reusable query templates that agents and humans can read, while sending clean SQL to production. The paper ends with an open call to developers, DBAs and data teams to help shape it into a shared protocol for an era in which LLMs bring us all into each other's work.

## Core methods (patent pending)

| Method | What it does | Status |
|---|---|---|
| **Dual Phase Context Injection (DPCI)** | Mirrors how people solve problems: first frame the task (goals, constraints, scope), then refine the output (tone, detail, format). Context is selected and delivered only when it improves the result. | Patent pending |
| **Domain Directed Execution and Task Packet Creation (DDE)** | Gathers what a task needs, packages it into a structured Task Packet, and hands that packet to DPCI for delivery to the model. | Patent pending |

Inventors: Ebony Belhumeur[, other inventors exactly as on the filings]. Implementation: [dapple-core › Core methods](https://github.com/dappleAI/dapple-core#core-methods).

## Code

| Repository | Content |
|---|---|
| [`dapple-core`](https://github.com/dappleAI/dapple-core) | Rust engine for structured, model-agnostic LLM workflows: playbooks, guided interviews, prompt rendering and multi-model routing, sandboxed workflow execution, and a PostgreSQL data layer. Apache-2.0. |
| [`sql-composer`](https://crates.io/crates/sql-composer) | SQL pre-processor for composable, commented SQL templates shared across projects (see the Context Engineering paper). [Add the GitHub repo link.] |

## Applications

The research is applied in DappleAI's guided-workflow platform. Users pick a role and a task, answer a short interview, and get results without writing a prompt. The same workflow runs on Claude, a local Mistral model, or a self-hosted model, and the architecture is designed to carry over to new domains, roles and models without a redesign.

## Team

- [Ebony Belhumeur](https://www.linkedin.com/in/ebelhumeur), Operations Lead & Co-Founder. Independent Researcher
- [Kenny Flegal](https://www.linkedin.com/in/kFlegal]), Founding Engineer. Relational Database Expert | Rust, SQL
- [Brian Belhumeur](https://www.linkedin.com/in/[handle]), Technical Advisor & Front-End Architect
- [Elijah Wilson](https://www.linkedin.com/in/elijah-wilson-401140380/), Community Manager

Contact: [info@dappleai.com](mailto:info@dappleai.com) · [dappleai.com](https://dappleai.com) · [LinkedIn](https://www.linkedin.com/company/dappleai/)
