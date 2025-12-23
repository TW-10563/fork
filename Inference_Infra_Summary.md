**Inference Infrastructure — Core Technical Overview**

- **Purpose:** Provide an on-premise inference infrastructure that supports low-latency, secure AI coding use cases inside the corporate network.
- **Design Principles:**
  - Keep all confidential data and inference inside the corporate DMZ; avoid sending any confidential source code to external clouds.
  - Deliver low-latency inference to enable real-time IDE experiences for code completion, inline explanation, automated test generation, and error correction.
- **Infrastructure Components & Specs:**
  - Corporate GPU cluster (examples referenced: DGX Spark / A6000 Ada) as the primary inference platform.
  - Network segmentation (DMZ/internal net) to ensure data never leaves the internal environment.
  - Integration with internal knowledge graph, RAG, and CodeGraph to enrich model context from internal repositories, APIs, and configuration assets.
- **Performance & Latency:**
  - On-prem GPUs deliver low latency (document references: 2–10ms per token) compared to cloud round-trips (document references: 200–500ms); this difference is critical for IDE responsiveness.
- **Security & Data Handling:**
  - No confidential data sent externally; all training/improvement and logs remain strictly internal.
  - Controls for logging, monitoring, and RBAC are required to satisfy management and legal concerns.
- **Operational Requirements & Prerequisites:**
  - Corporate GPU cluster availability.
  - Network segmentation and DMZ set up beforehand.
  - Permissions for accessing internal Git/APIs and unified access to repositories.
  - Aviary-v4 prepared (referenced in project prerequisites).
- **Constraints:**
  - Avoid excessive dependence on external cloud LLMs.
  - All data used for improvements must remain internal and comply with corporate policies.

**Inference Infrastructure — User Quick-Start & Parody**

- **Quick-Start (practical steps):**
  - Confirm GPU cluster resources are provisioned and reachable inside the DMZ/internal network.
  - Verify network segmentation and platform deployment within the corporate DMZ.
  - Ensure access permissions for repositories, API schemas, and CI/CD pipelines are in place.
  - Enable internal logging, RBAC, and audit mechanisms before allowing developer access to the agent endpoint.
  - Connect the agent and IDE integrations to the internal inference endpoint to begin using low-latency completions and related features.

- **Parody (lighthearted, 3–4 sentences):**
  - The infra engineer proudly boots the GPU nodes; the developer types a half-line and the agent finishes the function before the coffee cools. The security lead checks the RBAC log with a satisfied nod, and the project manager ticks the POC milestone. The cluster hums, completions fly, and everyone agrees that internal-only AI is both comforting and impressively fast.
