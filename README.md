# awesome-ai-mlops

> A curated list of modern MLOps, LLMOps, AgentOps, and AI infrastructure resources for building, evaluating, deploying, governing, and scaling AI systems in 2026.

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](#contributing)
[![License: CC0-1.0](https://img.shields.io/badge/License-CC0--1.0-lightgrey.svg)](#license)

## Why this list exists

The AI stack changed meaningfully in 2025 and early 2026.

The old MLOps mental model centered on training pipelines, feature stores, model registries, and batch deployment. That still matters, but the center of gravity has shifted. Modern teams now need to operate:

- non-deterministic LLM and agent systems
- evaluation suites and trace-based debugging
- cost-aware inference platforms
- prompt, retrieval, and tool-call lineage
- governance and observability for production AI
- autonomous multi-agent workflows with guardrails

This repository organizes the ecosystem around **what teams actually need to do**, not just around vendor categories.

## Table of contents

- [2026 principles](#2026-principles)
- [Awesome repositories](#awesome-repositories)
- [MLOps foundations](#mlops-foundations)
- [Evaluation and testing](#evaluation-and-testing)
- [Observability and tracing](#observability-and-tracing)
- [Experiment tracking and lineage](#experiment-tracking-and-lineage)
- [Workflow orchestration and CI/CD](#workflow-orchestration-and-cicd)
- [Model serving and inference](#model-serving-and-inference)
- [AgentOps](#agentops)
- [Governance, security, and policy](#governance-security-and-policy)
- [Data and feature infrastructure](#data-and-feature-infrastructure)
- [Inference economics](#inference-economics)
- [Research infrastructure](#research-infrastructure)
- [Learning resources](#learning-resources)
- [Architecture patterns](#architecture-patterns)
- [Contributing](#contributing)
- [License](#license)

## 2026 principles

1. **Evals are release gates.**
   - Treat eval suites like software tests for non-deterministic systems.
   - Include quality, latency, safety, and cost in every evaluation run.
   - Start small. Expand continuously.

2. **Tracing is mandatory.**
   - You need visibility into prompts, retrieval, tool calls, latency, cost, and failure paths.
   - Standardize on OpenTelemetry-based instrumentation.

3. **Lineage must cover more than models.**
   - Track code, data, prompts, traces, evaluations, judge configs, and deployments.
   - The minimum versioned surface in 2026 includes infra-as-code, data schemas, retrievers, and eval sets.

4. **Inference economics are architecture.**
   - Batching, caching, quantization, routing, autoscaling, and speculative decoding are core design decisions.
   - Track TTFT, throughput, GPU utilization, token cost, and cache efficiency as platform metrics.

5. **Governance shifts left.**
   - Auditability, approval flows, and policy checks belong in development and CI/CD pipelines.
   - Policy-as-code for model, prompt, and data access boundaries.

6. **Research and production are different operating modes.**
   - Production optimizes reliability, controls, and fleet economics.
   - Research optimizes iteration speed, reproducibility, and experiment breadth.

7. **Agents require their own operational discipline.**
   - Multi-agent systems need proactive guardrails, scoped tool access, and specialized monitoring.
   - AgentOps extends LLMOps with resilience patterns, feedback loops, and governance for autonomous actions.

8. **Cost is a governed metric.**
   - Budget ceilings, per-route model policies, and graceful degradation belong in the platform layer.
   - Model routing and fallbacks ensure expensive frontier models handle only the traffic that requires them.

---

## Awesome repositories

### General MLOps

- [visenger/awesome-mlops](https://github.com/visenger/awesome-mlops) — One of the broadest MLOps reference maps, covering deployment, monitoring, governance, papers, and communities. 13.7k+ stars.
- [kelvins/awesome-mlops](https://github.com/kelvins/awesome-mlops) — A practical baseline list spanning CI/CD, catalogs, versioning, and infrastructure.
- [umitkacar/awesome-mlops](https://github.com/umitkacar/awesome-mlops) — Newer production-oriented catalog emphasizing 2024–2025 tools and workflows.
- [ashishpatel26/Awesome-MLOps-Course-Outline](https://github.com/ashishpatel26/Awesome-MLOps-Course-Outline) — Structured learning path for MLOps fundamentals.

### LLMOps and AI infrastructure

- [tensorchord/Awesome-LLMOps](https://github.com/tensorchord/Awesome-LLMOps) — Strong taxonomy for serving, observability, data, security, and large-scale deployment. 5.6k+ stars.
- [InftyAI/Awesome-LLMOps](https://github.com/InftyAI/Awesome-LLMOps) — Inference-heavy view of the stack: engines, routers, gateways, runtimes, and training workflows.
- [KennethanCeyer/awesome-llmops](https://github.com/KennethanCeyer/awesome-llmops) — Lightweight index of LLMOps projects and ecosystem tools.
- [ashishpatel26/awesome-open-source-llmops](https://github.com/ashishpatel26/awesome-open-source-llmops/) — Curated open-source LLMOps tools for data scientists.

---

## MLOps foundations

### Core references

- [Google — Practitioners Guide to MLOps](https://cloud.google.com/architecture/mlops-continuous-delivery-and-automation-pipelines-in-machine-learning)
- [Made With ML](https://madewithml.com/)
- [Full Stack Deep Learning](https://fullstackdeeplearning.com/)
- [DataTalksClub MLOps Zoomcamp](https://github.com/DataTalksClub/mlops-zoomcamp)
- [ML in Production](https://mlinproduction.com/)
- [Databricks — MLOps Best Practices](https://www.databricks.com/blog/mlops-best-practices-mlops-gym-crawl)

### Core engineering ideas

- problem framing before modeling
- versioning code, data, configs, prompts, and artifacts
- reproducible environments (pin packages, capture seeds)
- automated training, validation, and evaluation
- staged deployment, canary releases, and rollback
- continuous monitoring, drift detection, and retraining strategy
- cost tracking and budget governance

### The modern Python toolchain

- [uv](https://github.com/astral-sh/uv) — Extremely fast Python package and project manager, superseding pip/conda for many teams.
- [Ruff](https://github.com/astral-sh/ruff) — High-speed linting and formatting.
- [Hatch](https://hatch.pypa.io/) — Modern Python project management.

### Data and model versioning

- [DVC](https://dvc.org/) — Ties data and model versions to Git commits.
- [lakeFS](https://lakefs.io/) — Git-like branching/merging for petabyte-scale object storage.

---

## Evaluation and testing

### Why this category matters

In 2026, evaluation is the center of gravity for AI reliability. Agent and LLM systems are non-deterministic software; eval suites are the equivalent of automated tests for these systems.

### Tools and frameworks

- [MLflow GenAI Evaluations](https://mlflow.org/genai/)
- [Arize Phoenix](https://phoenix.arize.com/)
- [Langfuse](https://github.com/langfuse/langfuse)
- [promptfoo](https://github.com/promptfoo/promptfoo)
- [OpenAI Evals](https://github.com/openai/evals)
- [Ragas](https://github.com/explodinggradients/ragas)
- [DeepEval](https://github.com/confident-ai/deepeval)

### Key metrics for LLM evaluation

| Metric | Description |
|:-------|:-----------|
| Faithfulness | Degree to which output aligns with retrieved context |
| TTFT | Time to First Token — critical latency metric |
| ITL | Inter-Token Latency — generation smoothness |
| Context precision | Relevance of retrieved context to the query |
| Human-in-the-loop | Qualitative assessment by domain experts |

### Recommended practice

- maintain a **golden set** of representative tasks
- separate **offline evals** (pre-release regression) and **online monitoring** (post-release drift)
- include quality, latency, safety, and cost in every evaluation run
- run multi-trial evals for stochastic systems
- store evaluation datasets and judge configs as versioned artifacts
- use outcome-oriented rubrics, not fixed-path checks, for agent systems
- distinguish benchmark variance from actual gains

---

## Observability and tracing

### Standards and foundations

- [OpenTelemetry](https://opentelemetry.io/) — Emerging standard for AI observability instrumentation.
- [OpenInference](https://github.com/Arize-ai/openinference) — Semantic conventions for AI/ML traces.
- [OpenTelemetry AI Agent Observability](https://opentelemetry.io/blog/2025/ai-agent-observability/) — GenAI/agentic semantic conventions.

### Tools

- [Langfuse](https://github.com/langfuse/langfuse)
- [Arize Phoenix](https://github.com/Arize-ai/phoenix)
- [Helicone](https://github.com/Helicone/helicone)
- [MLflow Tracing](https://mlflow.org/genai/)
- [OpenLIT](https://github.com/openlit/openlit)

### What to capture

- prompts and responses
- retrieval inputs and outputs
- tool calls and their results
- latency breakdown and token usage
- model routing decisions
- cache hit rates
- user feedback and downstream success signals
- guardrail triggers and policy violations
- cost per request and per route

---

## Experiment tracking and lineage

### Tools

- [MLflow](https://mlflow.org/) — MLflow 3 widened lineage to include runs, prompts, traces, and evaluations.
- [Weights & Biases](https://wandb.ai/site)
- [DVC](https://dvc.org/)
- [DAGsHub](https://dagshub.com/)
- [ClearML](https://clear.ml/)

### Best practice — define one lineage graph

Track under a common run or release identifier:

- source code revision
- dataset snapshot
- config, seed, and environment
- model or checkpoint ID
- prompt version
- retriever configuration
- judge configuration
- evaluation dataset version
- deployment artifact
- rollback and approval history

---

## Workflow orchestration and CI/CD

### Orchestration

- [Dagster](https://dagster.io/)
- [Prefect](https://www.prefect.io/)
- [Airflow](https://airflow.apache.org/)
- [Kubeflow Pipelines](https://www.kubeflow.org/docs/components/pipelines/)
- [Metaflow](https://metaflow.org/)

### CI/CD for ML

- [CML](https://github.com/iterative/cml)
- [KitOps](https://github.com/kitops-ml/kitops)
- GitHub Actions
- GitLab CI
- Terraform
- Helm

### Recommended pipeline

```text
lint → unit tests → data checks → integration tests → training/build → eval suite → package artifact → canary/shadow deploy → monitor → promote or rollback
```

### CI/CD best practices

- run static checks, data validation, unit tests, lightweight training tests, and eval suites in CI
- promote artifacts through environments rather than rebuilding ad hoc
- use Infrastructure-as-Code for clusters, gateways, secrets, and deployment policies
- automate rollback based on quality + SLO signals

---

## Model serving and inference

### Serving platforms

- [KServe](https://kserve.github.io/website/) — CNCF incubating project, unified predictive + generative AI serving.
- [Ray Serve](https://docs.ray.io/en/latest/serve/index.html)
- [BentoML](https://www.bentoml.com/)
- [Seldon Core](https://github.com/SeldonIO/seldon-core)
- [Knative](https://knative.dev/)

### Inference engines

- [vLLM](https://github.com/vllm-project/vllm) — High-throughput LLM serving with continuous batching.
- [SGLang](https://github.com/sgl-project/sglang) — Structured generation and efficient serving.
- [TensorRT-LLM](https://github.com/NVIDIA/TensorRT-LLM) — NVIDIA-optimized inference.
- [llama.cpp](https://github.com/ggerganov/llama.cpp) — CPU/edge inference for GGUF models.
- [DeepSpeed-MII](https://github.com/deepspeedai/DeepSpeed-MII)

### Gateways and routing

- [LiteLLM](https://github.com/BerriAI/litellm) — Unified API for 100+ LLM providers.
- [Envoy AI Gateway](https://aigateway.envoyproxy.io/) — Cloud-native AI traffic management.
- [Portkey](https://github.com/Portkey-AI/gateway) — AI gateway with caching, fallbacks, and load balancing.

### Inference best practices

- continuous batching and prefix caching
- quantization (FP4/INT8) for memory and cost reduction
- speculative decoding for latency reduction on structured outputs
- canary and shadow traffic for safe rollouts
- fallback routing across model tiers
- LoRA/multi-adapter serving from a single base model
- explicit cost budgets and latency SLOs
- GPU utilization tracking and autoscaling
- snapshot-based CUDA graph restore for fast cold starts

---

## AgentOps

### Why this category exists

As agents increasingly act independently, AgentOps has emerged to provide the observability, evaluation, and governance that autonomous systems require. AgentOps extends LLMOps with resilience, feedback, and governance for systems that make decisions and take actions without human intervention.

### Frameworks and tools

- [LangGraph](https://github.com/langchain-ai/langgraph) — Stateful multi-actor agent orchestration.
- [CrewAI](https://github.com/crewAIInc/crewAI) — Multi-agent collaboration framework.
- [AutoGen](https://github.com/microsoft/autogen) — Microsoft's multi-agent conversation framework.
- [NVIDIA NeMo Guardrails](https://github.com/NVIDIA/NeMo-Guardrails) — Programmable guardrails for LLM-powered agents.
- [Langfuse](https://github.com/langfuse/langfuse) — Tracing and evaluation for agentic workflows.
- [Arize Phoenix](https://github.com/Arize-ai/phoenix) — Agent trace visualization and debugging.

### Foundational pillars

AgentOps is grounded in five pillars: **observability** (reasoning traces, tool calls, context flow), **evaluation** (output quality, faithfulness, task performance), **governance** (guardrails, policy compliance, auditability), **feedback** (user signals, approvals, corrections), and **resilience** (retries, fallbacks, graceful degradation).

### Multi-agent risks and mitigations

| Risk | Mitigation |
|:-----|:-----------|
| Infinite loops | Time-boxed loops, step count caps, backoff and auto-shutdown |
| Unintended actions | Human-in-the-loop checkpoints for high-risk operations |
| Data exfiltration | Policy-as-code, scoped tool access, data minimization |
| Hallucination | Grounding with golden tasks, benchmark against ideal datasets |
| Circular handoffs | Full decision chain monitoring, correlated traces |

### Recommended practice

- use specialized agents with narrow responsibilities, not monolithic agents
- define proactive guardrails before deployment — they are the system, not optional
- agents should only access explicitly allowed tools
- instrument agents with OpenTelemetry GenAI/agentic semantic conventions
- monitor task start/end, reasoning steps, tools invoked, data queried, guardrails triggered
- implement circuit breakers and automatic escalation to human operators

---

## Governance, security, and policy

### Tools

- [Open Policy Agent](https://www.openpolicyagent.org/)
- [TruLens](https://github.com/truera/trulens)
- [Fiddler](https://www.fiddler.ai/)
- [Lakera Guard](https://www.lakera.ai/)
- [NVIDIA NeMo Guardrails](https://github.com/NVIDIA/NeMo-Guardrails)

### Controls to implement

- approval workflows for promoted artifacts (models, prompts, datasets)
- access controls for data, prompts, and model endpoints
- PII and secret redaction in prompts and outputs
- audit logs for deployments, evaluations, data access, and rollback history
- policy-as-code for unsafe tools and actions
- human override for high-impact operations
- explainability (XAI) paths where outputs influence decisions
- privacy protection via differential privacy and federated learning
- secure decommissioning of retired models and data

### Regulatory alignment

| Regulation / Standard | Core Requirement |
|:----------------------|:-----------------|
| EU AI Act | High-risk system transparency, mandatory automated logging |
| GDPR | Right to rectification of personal data within models |
| NIST AI RMF | Systematic TEVV (Test, Eval, Verify, Validate) |
| ISO/IEC 42001:2023 | AI management system organizational controls |
| MITRE ATLAS | Adversarial testing for prompt injection and tool misuse |

---

## Data and feature infrastructure

### Data quality and contracts

- [Great Expectations](https://github.com/great-expectations/great_expectations)
- [Evidently](https://github.com/evidentlyai/evidently)

### Feature stores

- [Feast](https://github.com/feast-dev/feast)
- [Tecton](https://www.tecton.ai/)

### Metadata and discovery

- [DataHub](https://github.com/datahub-project/datahub)
- [OpenMetadata](https://github.com/open-metadata/OpenMetadata)

### Drift monitoring

- [Evidently](https://github.com/evidentlyai/evidently) — Data and model drift detection.
- [Arize](https://arize.com/) — ML observability and drift monitoring.
- [WhyLabs](https://whylabs.ai/) — Real-time data and model monitoring.

### Recommended practice

- define data contracts between producers and consumers
- validate schemas continuously
- preserve data lineage across the full pipeline
- separate feature logic from serving logic
- snapshot training data used for every promoted model
- monitor feature distributions for drift and trigger retraining
- ensure feature stores supply identical transformations for training and inference

---

## Inference economics

### Why this category matters

In 2026, inference cost is a first-class architectural constraint. The true cost per million tokens dictates AI system profitability, and compounding optimizations can yield order-of-magnitude savings.

### Key optimization techniques

| Technique | Impact | Description |
|:----------|:-------|:-----------|
| Quantization (FP4/INT8) | ~4x cost reduction | Reduces model memory footprint while maintaining accuracy |
| Continuous batching | ~2x cost reduction | Dynamically groups requests, maximizes GPU utilization |
| Speculative decoding | ~2x latency reduction | Draft model predicts, large model verifies in parallel |
| Prefix caching | Variable | Reuses computation for shared prompt prefixes |
| Model routing | Variable | Routes to cheapest capable model per request |
| LoRA/multi-adapter serving | Variable | Multiple fine-tuned variants from one base model |

### Metrics to track

- TTFT (Time to First Token)
- throughput (tokens/second)
- GPU utilization
- token cost per request
- cache hit/miss ratios
- tail latency (p95/p99)

---

## Research infrastructure

### For university labs and open research groups

- [Weights & Biases](https://wandb.ai/site)
- [MLflow](https://mlflow.org/)
- [DVC](https://dvc.org/)
- [Slurm](https://slurm.schedmd.com/)
- [PyTorch Distributed](https://pytorch.org/tutorials/beginner/dist_overview.html)
- [DeepSpeed](https://github.com/deepspeedai/DeepSpeed)
- [FSDP](https://pytorch.org/docs/stable/fsdp.html)
- [Hydra](https://github.com/facebookresearch/hydra)

### Recommended practice

- pin exact environments and capture package versions
- archive configs, seeds, and dataset snapshots
- checkpoint often and test resume behavior before long runs
- validate failure recovery before committing to multi-day runs
- capture dataset snapshots and filtering code
- write experiment manifests that another lab can rerun
- report variance (mean ± std), not only best-run numbers
- report confidence intervals for stochastic evaluations
- distinguish benchmark variance from actual gains
- package model cards, inference recipes, tokenizer details, quantization notes, and benchmark harnesses for research-to-production handoff

---

## Learning resources

### Newsletters and communities

- [MLOps Community](https://mlops.community/)
- [The ML Engineer](https://machinelearning.substack.com/)
- [Decoding AI Magazine](https://decodingml.substack.com/)
- [MLOps.wtf](https://www.mlops.wtf/)
- [MLOps World](https://mlopsworld.com/)
- [Marvelous MLOps](https://www.marvelousmlops.io/)
- [Ahead of AI](https://magazine.sebastianraschka.com/) — Sebastian Raschka

### Blogs worth following

- [Anthropic Engineering](https://www.anthropic.com/engineering)
- [AWS Machine Learning Blog](https://aws.amazon.com/blogs/machine-learning/)
- [vLLM Blog](https://blog.vllm.ai/)
- [PyTorch Blog](https://pytorch.org/blog/)
- [Hugging Face Blog](https://huggingface.co/blog)
- [CNCF Blog](https://www.cncf.io/blog/)
- [OpenTelemetry Blog](https://opentelemetry.io/blog/)

### Key engineering references

- [Anthropic — Demystifying evals for AI agents](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents)
- [Anthropic — How we built our multi-agent research system](https://www.anthropic.com/engineering/multi-agent-research-system)
- [vLLM — Anatomy of a high-throughput inference system](https://blog.vllm.ai/2025/09/05/anatomy-of-vllm.html)
- [CNCF — Building a scalable, flexible, cloud-native GenAI platform](https://www.cncf.io/blog/2025/08/28/building-a-scalable-flexible-cloud-native-genai-platform-with-open-source-solutions/)
- [AWS — Operationalizing Generative AI](https://aws.amazon.com/blogs/machine-learning/operationalizing-generative-ai-how-it-differs-from-mlops/)

---

## Architecture patterns

### Industry production stack

```text
data contracts
  → feature/data validation
  → training / fine-tuning
  → registry + lineage
  → eval suite
  → artifact promotion
  → gateway / routing
  → inference engine
  → tracing + monitoring
  → feedback loop
```

### Academic research stack

```text
dataset snapshot
  → config + launcher
  → cluster scheduler
  → checkpointing
  → experiment tracker
  → benchmark harness
  → artifact archive
  → reproducibility bundle
```

### MLOps maturity levels

| Level | Description |
|:------|:-----------|
| Level 0 | Manual processes, minimal automation, siloed workflows |
| Level 1 | Partial automation, continuous training, modular pipelines |
| Level 2 | Full CI/CD automation, rapid scalable deployment and retraining |
| Level 3 | LLMOps-ready: prompt versioning, multi-model orchestration, guardrails |
| Level 4 | Full AgentOps: autonomous agent governance, self-healing systems, fleet economics |

---

## Contributing

Contributions are welcome.

Please open a pull request if you want to add:

- high-signal open-source tools
- major engineering references
- production case studies
- research infrastructure resources
- AgentOps tools and patterns
- better categorization

### Contribution rules

- prefer primary sources over marketing pages
- prefer tools with clear docs and active maintenance
- explain **why** a resource belongs here
- avoid dead links and duplicate categories
- use concise descriptions

---

## License

This repository is released under **CC0-1.0** unless otherwise stated.

If you reuse this list, attribution is appreciated.
