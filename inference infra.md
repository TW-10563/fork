Certainly! Here is the English translation of your document:

Advanced Internal AI Coding Agent

Background / Business Challenges

In recent years, many companies—including Amazon, ByteDance, Microsoft, and major domestic IT firms—have strengthened their management of AI coding usage and shifted to a policy of “using internal-only AI coding tools without sending code to external clouds.”
Behind this are the following critical risks and requirements.
(*ref: https://www.zen-tech.co.jp/blog/code-generation-ai-adoption-japanese-enterprises)

[Figure]

(1) Protection of Source Code and Intellectual Property (IP) is Essential

Corporate code is the most important confidential asset, including:

Core algorithms
Business logic
Internal APIs
System vulnerabilities
Configuration information & secret keys
Sending these to an external cloud LLM is equivalent to “handing over the company's heart to a third party.”

Management and legal departments will always ask:

“Why do we need to send all our source code to OpenAI / Google / AWS?”

From this perspective, on-premise inference is the only compliant solution.

[Figure]

(2) Risks of Information Leakage, Retraining, and Cross-border Legal Regulations

When using cloud LLMs:

Input data may be used for model improvement
Data may become subject to logging or monitoring
Data may remain as cache on the service side
Cross-border legal risks such as CLOUD Act
In the context of AI coding:
Code leakage = direct fatal blow to business continuity
Confidential information leakage = major security incident
Exposure of internal structure = expanded attack surface

With on-premise inference infrastructure:

Data never leaves the corporate DMZ and can be processed entirely within a closed internal environment.

[Figure]

(3) AI Coding Requires Access to Internal Context

To achieve high accuracy in AI coding, full access is necessary for:

Hundreds of internal Git repositories
Company-specific frameworks / SDKs
Internal microservice structures
REST / GraphQL / gRPC schemas
Configuration assets like config/helm/compose files
CI/CD pipelines
In-house code guidelines/naming conventions
These cannot be obtained with external cloud LLMs.

With on-premise LLMs:

Inference using an internal knowledge graph
Accurate code generation with RAG + CodeGraph
Executable code generation that understands internal APIs
Automatic analysis of company-specific bugs
Consistent security boundaries

With cloud LLMs:

Cannot access internal information; inference accuracy drops significantly.

[Figure]

(4) Latency Greatly Affects Development Experience

Use cases for AI coding require real-time performance:

Code completion
Inline explanation
Automated test generation
Automatic error correction
Code review

For cloud models:

Round-trip latency 200–500ms
Sometimes delays extend over several seconds
→ Real-time experience as an IDE collapses

On-prem GPU (A6000 Ada/DGX Spark):

Low latency at 2–10ms per token
High-speed completion possible
Achieves next-gen IDE-level responsiveness

This is why Cursor/Windsurf/Copilot Enterprise also adopt local cache models.

Project Goals

Integrate with internal Git/API/CI/CD systems and utilize it as an "enterprise-specialized coding agent" that understands company-specific codebases.

Provide highly accurate code generation/modification/analysis capabilities.

Deliver a "real-time development assistance experience" by seamless integration with IDEs (VSCode/JetBrains IDE etc.).

Strengthen in-house development processes such as code reviews/test generation with a target productivity boost of 30–50%.

Establish an internally standardized AI coding platform that meets compliance and information security standards.

Project Scope

(Included)

Development of main AI Coding Agent (based on OSS CLINE AGENT)
Integration with in-house repositories (GitHub Enterprise/GitLab etc.)
Code search & structural analysis (RAG + CodeGraph)
Reference functions for APIs/schemas/configuration info
Functions for code generation/refactoring/bug analysis
Assistance for code review (including lint integration)
Internal authentication & RBAC linkage
IDE plugin design (VSCode/JetBrains etc.; considering partnerships or outsourcing)

(Not Included)

Procurement/optimization operation for GPU infrastructure (handled by another project)
Improvements to basic corporate network infrastructure
General natural language chat features (not central focus here)

Project Objectives & Deliverables

Main body MVP for AI Coding Agent (API/inference logic)
Modules for code search/dependency analysis
Internal authentication linkage module (RBAC/log mechanisms)
Implementation reflecting dev rules/coding guides based on company policy automatically applied
User manuals & operational guidelines
Security specification documents (data handling/access rights design)
IDE plugins (VSCode version; JetBrains version optional)

Project Team & Roles

Product Owner (PO): Requirement definition, priority management, coordination with in-house clients
Technical Lead (TL): Architecture design, selection of AI models, technical decisions
Backend Engineer: Implementation of inference API/code search engine/authentication integration
AI/ML Engineer: Building RAG & CodeGraph; optimizing code generation
QA/Security Lead: Test planning/vulnerability assessment
Project Manager(PM): Schedule/risk/release management
Frontend/IDE Engineer: IDE plugins/UIUX design (optional)

Key Stakeholders

Digital Creation Divisions 1 & 3
Company-wide Project Team (“mini-project”)
Infrastructure/SRE team
Systems Department(auth/RBAC)
Business units(users)

Key Project Timeline – POC Phase

Phase	Duration	Content
Requirement Def., Architecture Design	1 week	Hearings/specification finalization
Overall/System Integration Design		
Core Function Implementation	1 week	Code search/generation/fix engines
In-House Data Integration	0.5 months	Mechanisms acquiring Git/CI/CD/API/config
Testing/Security	1 week	Vulnerability/load tests
Production Rollout	0.5 months	User adoption/start operations
Risks & Mitigation Measures

Risk	Description	Mitigation
Insufficient Code Analysis Accuracy	Weak understanding of dev rules	Build rule DB; continuous learning
Changes in Internal API Specs	High frequency microservice updates	Automated API schema sync mechanism
Excessive Expectations	Misunderstood as "all-powerful" AI	Clearly state scope/use limitations
Authentication/RBAC Complexity	Multi-layered access rights	Standardize authority mapping
Dev Team Usage Burden	Learning cost for new tool	Training materials/provide PoC
Prerequisites

Corporate GPU cluster available(DGX Spark/A6000 Ada)
Network segmentation(DMZ/internal net) set up beforehand
Permission acquired for using Cloud-side APIs
Access permissions arranged for Git/APIs
Aviary-v4 prepared
Unified access possible across in-house Git repositories
Environment allowing reference access to API schemas/config files provided
In-house permission secured regarding IDE deployment
Coding guidelines/security requirements(log mgmt/auth req.) presented beforehand
Constraints

No confidential data sent externally whatsoever
All data used for training/improvement strictly limited internally
Avoid excessive dependence on external cloud LLM
Respect/integrate existing corporate dev processes(Git Flow/CI-CD/etc.)
Designed keeping future extensibility(agentization/multi-IDEs support) in mind