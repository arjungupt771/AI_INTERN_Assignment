# AI Model Reference Document

**Tekravio Labs AI Intern Assignment - AI Research / LLM Intelligence**  
**Audience:** CTOs, VP Engineering, Heads of L&D, enterprise AI buyers  
**Updated:** 05 June 2026

> **Scope note:** The assignment brief names several 2024-2025 models such as GPT-4o, Claude 3.5 Sonnet, Gemini 1.5, Llama 3.x, and Grok 3. This document covers those models for historical and compatibility context, but updates the recommendation layer to the model landscape visible in official provider docs on 05 June 2026. Always verify exact model IDs, regions, retention terms, and pricing before procurement.

## Executive Summary

The best enterprise AI model is not the one with the highest benchmark score. It is the model that matches the use case, risk, latency, privacy, cost, and workflow integration.

The winning pattern is a **model portfolio**:

- Use a frontier model for complex reasoning, coding, executive analysis, and high-risk review.
- Use a cheaper fast model for routing, support, classification, summarization, extraction, and rewriting.
- Use embeddings plus RAG for internal knowledge instead of trying to fine-tune private facts into a model.
- Use open-weight models when privacy, customization, data residency, or high-volume economics justify infrastructure ownership.
- Use Azure OpenAI, AWS Bedrock, Google Vertex AI, or Hugging Face when governance and procurement matter more than direct-to-provider simplicity.

The practical enterprise rule is: **build an evaluation set from real company tasks, use the cheapest model that passes it, and escalate hard or risky cases to stronger reasoning models.**

## Source Trail

Primary/provider sources used for the 2026 update:

- OpenAI models and pricing: https://platform.openai.com/docs/models and https://platform.openai.com/docs/pricing/
- Anthropic Claude models and pricing: https://docs.anthropic.com/en/docs/about-claude/models/overview and https://docs.anthropic.com/en/docs/about-claude/pricing
- Google Vertex/Gemini models and pricing: https://cloud.google.com/vertex-ai/generative-ai/docs/models and https://cloud.google.com/vertex-ai/generative-ai/pricing
- Meta Llama models: https://www.llama.com/models/
- Mistral models and pricing: https://mistral.ai/en/models and https://mistral.ai/pricing/
- xAI models: https://docs.x.ai/docs/models
- DeepSeek pricing: https://api-docs.deepseek.com/quick_start/pricing
- GitHub Copilot docs: https://docs.github.com/en/copilot
- AWS Bedrock: https://aws.amazon.com/bedrock/
- Azure OpenAI privacy/data handling: https://learn.microsoft.com/en-us/azure/ai-foundry/responsible-ai/openai/data-privacy
- Hugging Face Inference Endpoints: https://huggingface.co/docs/inference-endpoints

## 1. Foundation / General Purpose LLMs

### 2026 Provider Shortlist

| Provider | Current enterprise shortlist | Why it matters |
|---|---|---|
| OpenAI | GPT-5.5, GPT-5.4, GPT-5.4 mini/nano; legacy GPT-4o and o-series where deployed | Strong reasoning, coding, vision, tools, agents, broad ecosystem |
| Anthropic | Claude Opus 4.8, Sonnet 4.6, Haiku 4.5; legacy Claude 3.x | Excellent writing, long context, code, safety-sensitive analysis |
| Google | Gemini 3.1 Pro, Gemini 3.5 Flash, Gemini 3.1 Flash-Lite; legacy Gemini 1.5/2.5 | Long context, multimodal media/document work, Google Cloud integration |
| Meta | Llama 4 Scout/Maverick, Llama 3.3/3.2/3.1 | Open-weight/self-hosting path, customization, private deployment |
| Mistral | Mistral Large 3, Medium 3.5, Small 4, Devstral, Codestral | European vendor, open/premier models, coding and document intelligence |
| xAI | Grok 4.3, Grok Build 0.1; legacy Grok 3 | Search/X-connected assistants and coding workflows |
| DeepSeek | DeepSeek V4 Flash/Pro; legacy R1 | Low-cost reasoning and code-capable APIs, open ecosystem history |

### OpenAI Family

OpenAI's official docs now position **gpt-5.5** as the flagship for complex reasoning and coding, with **gpt-5.4-mini** and **gpt-5.4-nano** for lower latency and cost. Latest OpenAI models support text and image input, text output, multilingual capabilities, vision, and tools through the Responses API.

| Model | Context / output | Modalities | Price per 1M tokens | API | Best use | Not good at | Status |
|---|---:|---|---:|---|---|---|---|
| GPT-5.5 | 1M context; 128K max output | Text, image input, tools | $5 input / $30 output; long context $10 / $45 | Yes | Complex reasoning, coding, professional work | Cheap high-volume support | Current flagship |
| GPT-5.5 Pro | Premium long-context | Text, image, tools | $30 input / $180 output; long context $60 / $270 | Yes | Very high-value expert review | Routine automation | Premium |
| GPT-5.4 | 1M context; 128K max output | Text, image, tools | $2.50 input / $15 output; long context $5 / $22.50 | Yes | Balanced enterprise apps | Ultra-low-cost extraction | Current balanced |
| GPT-5.4 mini | 400K context; 128K output | Text, image, tools | $0.75 input / $4.50 output | Yes | Cost-effective coding, assistants, routing | Hardest reasoning | Current small |
| GPT-5.4 nano | Fast low-cost tier | Text, image, tools | $0.20 input / $1.25 output | Yes | Classification, routing, extraction | Complex synthesis | Current cheapest |
| GPT-4o | 128K typical older deployments | Text, image, audio in selected surfaces | Availability/pricing varies | Yes where supported | Multimodal assistant, vision, training content | New procurement vs GPT-5 line | Legacy/compatibility |
| GPT-4o mini | 128K typical | Text, image | Availability/pricing varies | Yes where supported | Low-cost chat/extraction | Top reasoning | Legacy/compatibility |
| GPT-4 Turbo | 128K | Text, vision variants | Legacy | Limited | Existing GPT-4-era apps | New builds | Legacy |
| o1 / o3 / o4-mini | Reasoning-first older line | Text/image/tools depending endpoint | Availability varies | Varies | Math, planning, multi-step reasoning | Commodity chat | Legacy reasoning |

**Enterprise read:** For new 2026 builds, benchmark GPT-5.4 nano/mini for volume, GPT-5.4 for balanced workflows, and GPT-5.5/Pro only where the task value justifies the cost.

### Anthropic Claude Family

Anthropic's current docs list **Claude Opus 4.8**, **Claude Sonnet 4.6**, and **Claude Haiku 4.5**. Current Claude models support text and image input, text output, multilingual capability, and vision, and are available through Claude API plus selected cloud platforms.

| Model | Context / output | Modalities | Price per 1M tokens | API/platform | Best use | Not good at | Status |
|---|---:|---|---:|---|---|---|---|
| Claude Opus 4.8 | 1M context; 128K output | Text, image input; text output | $5 input / $25 output | Claude API; cloud availability varies | Complex reasoning, agentic coding, high-autonomy work | Cost-sensitive support | Current premium |
| Claude Sonnet 4.6 | 1M context; 64K output | Text, image input; text output | $3 input / $15 output | Claude API, Bedrock, Vertex, Foundry | Best speed/intelligence balance, documents, code, L&D writing | Cheapest classification | Current workhorse |
| Claude Haiku 4.5 | 200K context; 64K output | Text, image input; text output | $1 input / $5 output | Claude API/cloud partners | Fast near-frontier support and extraction | Deep premium reasoning | Current fast tier |
| Claude 3.5 Sonnet | 200K typical | Text, image | Legacy/current varies | Yes where supported | Strong writing/code in existing apps | New procurement vs Sonnet 4.6 | Legacy but important |
| Claude 3 Opus | 200K typical | Text, image | Legacy/current varies | Varies | Premium Claude 3-era analysis | Cost-sensitive production | Legacy |
| Claude 3 Haiku / 3.5 Haiku | 200K typical | Text, image | 3.5 Haiku retired except some cloud platforms per docs | Varies | Fast old Claude apps | New builds | Legacy |

**Enterprise read:** Sonnet is the safest Claude default for enterprise writing, code, and document workflows. Opus is for hard reasoning and agentic work; Haiku is for volume.

### Google Gemini Family

Google's docs now list newer Gemini 3.x models, including **Gemini 3.1 Pro**, **Gemini 3.5 Flash**, and **Gemini 3.1 Flash-Lite**, while Gemini 1.5/2.5 remain important for compatibility.

| Model | Context | Modalities | Pricing posture | API/platform | Best use | Not good at | Status |
|---|---:|---|---|---|---|---|---|
| Gemini 3.1 Pro | 1M context in docs | Text, image, audio, video, grounding | Verify current Vertex/AI Studio pricing | Vertex/Gemini API | Complex agentic workflows, coding, multimodal reasoning | Cheapest chat | Current premium |
| Gemini 3.5 Flash | 1M context in docs | Multimodal | Flash-tier cost/speed | Vertex/Gemini API | Near-Pro intelligence at speed, high-volume multimodal tasks | Highest-risk review | Current fast/balanced |
| Gemini 3.1 Flash-Lite | Cost-optimized | Multimodal | Lowest Gemini tier | Vertex/Gemini API | Low-latency high-volume traffic | Complex synthesis | Current cheapest |
| Gemini 1.5 Pro | Up to 1M+ in older deployments | Text, image, audio, video | Legacy/current varies | Vertex/AI Studio | Huge-context document/video analysis | New procurement where 3.x exists | Legacy |
| Gemini 1.5 Flash | Up to 1M | Multimodal | Legacy/current varies | Vertex/AI Studio | Fast summarization/extraction | Premium reasoning | Legacy |
| Gemini Ultra | Early premium Gemini generation | Multimodal | Legacy | Limited | Historical reference | New builds | Legacy |
| Gemini Nano | On-device | Device-native | Device/platform | Android/edge | Edge AI where data stays on device | Heavy enterprise reasoning | Edge |

**Enterprise read:** Gemini is strongest for long-context and multimodal pipelines, especially inside Google Cloud, BigQuery, Workspace, or Vertex AI.

### Meta, Mistral, xAI, and DeepSeek

| Provider/model | Context/modalities | Open/proprietary | Price per 1M tokens | Best use | Not good at |
|---|---|---|---:|---|---|
| Llama 4 Scout/Maverick | Open-weight Llama 4 family; multimodal/large-context depending release and host | Open weights with license terms | Hosting/infra cost | Private assistants, open deployment, customization | Plug-and-play SaaS governance |
| Llama 3.3/3.2/3.1 | Widely deployed open-weight models; Llama 3.1 supports 128K in common releases | Open weights | Hosting/infra cost | Private RAG, self-hosting, vendor leverage | Frontier reasoning vs top closed models |
| Mistral Large 3 | Multimodal, multilingual | Open-weight per page | $0.50 input / $1.50 output | General assistant, EU/open deployment | Maximum frontier reasoning |
| Mistral Medium 3.5 | Text, multimodal, coding, reasoning | Open weights under modified license | $1.50 input / $7.50 output | Strong general/coding/reasoning workflows | Cheapest volume |
| Mistral Small 4 | Lightweight/cost-sensitive | Mistral/open-premier varies | Verify current pricing | Cost-sensitive tasks | Complex reasoning |
| Devstral 2 | Agentic coding | Open/labs per page | $0.40 input / $2 output | Autonomous software engineering agents | General business writing |
| Codestral | Code completion | Premier | Verify current pricing | Fill-in-the-middle, IDE/API code completion | General executive prose |
| Grok 4.3 | 1M context | Proprietary | $1.25 input / $2.50 output | Agentic tool calling, search/X-connected assistants | Conservative regulated workflows without review |
| Grok Build 0.1 | 256K context | Proprietary | $1 input / $2 output | Agentic coding | General non-code work |
| DeepSeek V4 Flash | 1M context; thinking/non-thinking | Proprietary API/open ecosystem history | $0.14 cache miss input / $0.0028 cache hit / $0.28 output | Low-cost reasoning and high-volume tasks | Sensitive-data workflows without policy review |
| DeepSeek V4 Pro | 1M context; thinking/non-thinking | Proprietary API/open ecosystem history | $0.435 cache miss input / $0.003625 cache hit / $0.87 output | Better low-cost reasoning | Conservative procurement without review |
| DeepSeek R1 | Earlier open reasoning model | Open/model-host dependent | Host dependent | Reasoning benchmark reference, self-host experiments | Superseded in some API docs by newer V4 modes |

**Enterprise read:** Llama and Mistral are the strongest open-weight strategic options. xAI is compelling for search-connected and coding workflows. DeepSeek is price-performance disruptive, but procurement teams should evaluate data handling, region, and geopolitical risk carefully.

## 2. Code-Specific Models

| Model/tool | What it is | Strengths | Limitations | When to choose |
|---|---|---|---|---|
| GitHub Copilot | IDE, GitHub, CLI, and agentic development product using model selection across multiple providers | Best developer adoption, IDE completion, PR summaries, code review, agent sessions, enterprise controls | Underlying models and request pricing change | Microsoft/GitHub-heavy engineering teams |
| OpenAI GPT-5.5 / GPT-5.4 | Frontier coding and agentic work models | Strong coding, tools, computer use, professional reasoning | More expensive than code-only small models | Code agents, complex refactors, test generation |
| Claude Sonnet 4.6 / Opus 4.8 | Claude coding/document models | Strong code explanation, long-context repo analysis, agentic coding | Opus cost; Sonnet still needs evals | Code review automation, repo reasoning, careful explanations |
| Mistral Devstral 2 | Agentic coding model | Built for autonomous software engineering | Newer ecosystem; benchmark locally | Coding agents and cost-controlled automation |
| Codestral | Code completion model | Fill-in-the-middle, multilingual code completion | Not the best general chat model | IDE autocomplete/API code completion |
| Code Llama | Meta open-weight code family | Self-hosting, privacy, fine-tuning | Older than latest coding models | Regulated/self-hosted code assistants |
| StarCoder / StarCoder2 | BigCode open code models | Open weights and transparent research lineage | Behind frontier coding agents | Internal experiments, education, private code tooling |
| DeepSeek Coder / V4 | Low-cost code-capable models | Strong price-performance, FIM support in non-thinking mode | Procurement/geopolitical/privacy review | Cost-sensitive coding tasks where policy permits |
| Amazon Q Developer / CodeWhisperer | AWS-native coding assistant | AWS service knowledge, IAM/CloudFormation help, IDE support | Less useful outside AWS | AWS-first engineering teams |
| Grok Build 0.1 | xAI coding model | Agentic coding workflows, 256K context | Newer enterprise maturity | xAI ecosystem coding agents |

**Code model rule:** If developers use it every day, integration often beats benchmark score. Use Copilot or Amazon Q when the IDE/cloud workflow fit dominates. Use Claude/GPT/Grok/Mistral/DeepSeek APIs for backend code automation where you can evaluate outputs on real repositories.

## 3. Reasoning & Agentic Models

Reasoning models spend more compute on decomposition, planning, verification, and tool-aware execution. They are not automatically better for every task; they are better when mistakes are expensive and the task has multiple dependent steps.

| Model/framework | Role | Best use | Watch-outs |
|---|---|---|---|
| GPT-5.5 / GPT-5.4 | OpenAI reasoning-configurable frontier models | Complex reasoning, coding, tools, professional work | Cost grows quickly if used for all traffic |
| OpenAI o1/o3/o4-mini | Earlier explicit reasoning line | Math, planning, multi-step analysis in existing stacks | Availability/deprecation varies by surface |
| Claude Opus 4.8 | Premium Claude reasoning/agentic work | Long-horizon coding and complex reasoning | Premium cost |
| Claude Sonnet 4.6 with thinking | Balanced reasoning + writing + code | Long docs, code review, strategy memos | More tokens/time when thinking is enabled |
| DeepSeek V4 Flash/Pro | Low-cost model with thinking/non-thinking modes | Cost-efficient reasoning experiments | Data policy and provider review required |
| DeepSeek R1 | Earlier open reasoning model | Self-hosted/open reasoning reference | Superseded in some API docs by newer V4 modes |
| Gemini 3.1 Pro | Google reasoning-first model | Multimodal complex workflows, coding, grounding | Verify pricing and quotas by platform |
| Grok 4.3 | Tool-calling/reasoning model | Search-connected agents and conversational reasoning | Compliance review required |
| LangGraph | Agent framework | Stateful, auditable agent workflows | Requires engineering discipline |
| CrewAI | Multi-agent framework | Role-based business process prototypes | More agents can mean more failure modes |
| AutoGPT | Early autonomous-agent framework | Historical/demo value | Less production-control than graph-based systems |

### Tool Use / Function Calling

Tool use lets a model call external systems: search, databases, CRMs, calculators, code execution, ticketing systems, document stores, or workflow APIs. This is the bridge from chatbot to agent. Major providers now support some form of function/tool calling, including OpenAI, Anthropic, Google, Mistral, xAI, DeepSeek, and many hosted open models.

### Decision Tree: Reasoning Model vs Standard LLM

1. **Is the task high-volume and low-risk?**  
   Use a standard small/fast model: GPT-5.4 nano/mini, Claude Haiku 4.5, Gemini Flash/Flash-Lite, Mistral Small, or Llama/Gemma small.

2. **Does it require several dependent steps, calculations, trade-off analysis, or planning?**  
   Use a reasoning model: GPT-5.4/5.5, Claude Sonnet/Opus with thinking, Gemini Pro, DeepSeek thinking mode, or Grok 4.3.

3. **Does it need to act in software systems?**  
   Use a model plus tools inside an agent framework, with logs, permissions, and human approval.

4. **Is the action regulated, irreversible, expensive, or customer-facing?**  
   Use reasoning plus human review. Do not fully automate the final decision.

5. **Can the answer be verified cheaply with tests, retrieval, rules, or calculators?**  
   Use a cheaper model and escalate failures.

## 4. Multimodal & Specialized Models

### Image Generation

| Model | Strengths | Commercial/use-rights notes | Enterprise fit |
|---|---|---|---|
| OpenAI image models / DALL-E lineage / GPT Image | API integration, prompt adherence, editing | Verify current OpenAI business terms and safety policy | Marketing drafts, product mockups, internal visuals |
| Stable Diffusion / Stability models | Open ecosystem, local deployment, LoRA customization | License depends on exact model/version | Private creative workflows, custom styles |
| Midjourney | High aesthetic quality | Paid commercial terms and public/private generation rules matter | Creative direction, concept art, brand exploration |
| FLUX | Strong open image model ecosystem | Schnell/Dev/Pro licensing differs | High-quality open/local image generation |
| Ideogram | Strong text rendering and design-style prompts | Verify brand/commercial terms | Posters, social media, text-heavy graphics |
| Gemini image models | Conversational image generation/editing | Google Cloud terms | Workspace/Vertex creative pipelines |
| xAI Imagine API | Image/video generation through xAI | xAI terms | Fast social/product creative prototypes |

### Vision Models

| Model | Best use | Notes |
|---|---|---|
| GPT-5/GPT-4o vision | OCR plus reasoning, screenshots, charts, forms | Strong general-purpose multimodal assistant |
| Claude Vision | Careful image/document interpretation | Strong paired with long-context document review |
| Gemini Vision | Video/image/document/audio understanding | Strong for large multimodal context on Google Cloud |
| Mistral OCR | Document extraction | Mistral pricing lists OCR/page pricing; useful for document intelligence |

### Audio / Speech

| Model/tool | Best use | Enterprise caution |
|---|---|---|
| Whisper / OpenAI transcribe | Transcription and translation | Test Indian accents, noise, and domain vocabulary |
| GPT realtime / voice models | Realtime voice assistants | Latency, privacy, and cost controls |
| ElevenLabs | TTS, dubbing, voice cloning | Consent, fraud controls, likeness rights |
| Suno / Udio | Music generation | Copyright and brand-safety review |
| Mistral Voxtral | TTS/transcription/audio input | Check exact language/support/pricing |
| xAI Voice API | Agent, STT, TTS | Verify enterprise controls and usage pricing |

### Video Generation

| Model/tool | Best use | Current limitations |
|---|---|---|
| OpenAI Sora / video models | High-quality generative video where available | Availability/API terms change; verify current status |
| Google Veo 3 / 3.1 | Text-to-video, image-to-video, video editing | Cost and safety limits; Google Cloud workflow fit |
| Runway | Production-oriented AI video editing/generation | Consistency and licensing review |
| Pika | Short-form creative generation | Less reliable for precise training material |
| Kling | High-quality creator video workflows | Procurement/regional review |
| xAI Imagine video | Fast image/video generation | Verify enterprise terms |

### Embedding Models

Embeddings convert text or media into vectors so content can be searched semantically. They are core to RAG, semantic search, clustering, deduplication, recommendations, memory, and personalization.

| Model family | Best use | Notes |
|---|---|---|
| OpenAI embeddings | General semantic search/RAG | Managed default for OpenAI stacks |
| Cohere Embed + Rerank | Enterprise retrieval | Strong search/reranking ecosystem |
| BGE / BAAI | Self-hosted retrieval | Good open/private option |
| Gemini Embedding | Google Cloud RAG | Strong Vertex integration |
| Mistral / Codestral Embed | Mistral ecosystem retrieval/code retrieval | Useful in Mistral-centric stacks |

### Domain-Specific Models

| Domain | Models/tools | Where they fit | Caution |
|---|---|---|---|
| Healthcare | Med-PaLM lineage, healthcare-tuned systems, clinical copilots | Clinical QA support, summarization, patient/admin workflow assistance | Must not replace licensed medical judgment; compliance burden is high |
| Finance | BloombergGPT, FinGPT, domain-tuned models | Filings analysis, research support, risk narratives | Data licensing, auditability, hallucination risk |
| Legal | Harvey, Lexis+ AI, legal-tuned LLMs | Contract review, legal research, clause extraction | Jurisdiction, privilege, citation accuracy |
| Education/L&D | Frontier LLMs + RAG + assessment systems | Training content, quizzes, simulations, learner support | Needs pedagogy, bias review, and source grounding |
| Software engineering | Copilot, Claude Code, Codex, Devstral, Codestral, Q Developer | Code generation/review/refactoring | Security review and test execution required |

## 5. Enterprise AI Platforms & Decision Framework

### Platform Selection

| Platform | What it offers | Choose it when |
|---|---|---|
| AWS Bedrock | Managed access to multiple model providers, IAM, private networking, agents, knowledge bases | AWS-first organization needing multi-model governance |
| Azure OpenAI / Azure AI Foundry | OpenAI models through Azure controls, networking, compliance, enterprise procurement | Microsoft/Azure/M365-first organization |
| Google Vertex AI / Model Garden | Gemini, Claude, Mistral, Grok, DeepSeek, Llama/Gemma and open models, MLOps, data integration | Google Cloud/data-heavy organization; long multimodal context |
| Hugging Face Enterprise / Inference Endpoints | Open model hub, private endpoints, Spaces, enterprise controls | Need open model flexibility without fully self-managing |
| Direct provider APIs | Fastest path to latest model releases | Governance is manageable and speed matters |
| Self-hosted open models | Maximum technical control | Data cannot leave environment, high steady volume, customization required |

### Open Source vs Proprietary Matrix

| Factor | Proprietary / managed model | Open-weight / self-hosted model |
|---|---|---|
| Time to value | Fast | Slower |
| Quality ceiling | Usually highest | Strong, but varies |
| Data control | Contract/platform controls | Stronger technical control |
| Customization | Prompting, RAG, limited fine-tuning | Fine-tuning, architecture/deployment control |
| Cost | Easy to start, can rise with scale | Infra-heavy; cheaper at high utilization |
| Compliance | Easier through Azure/AWS/GCP | Easier only with mature internal controls |
| Talent needed | App/API engineering | GPU/MLOps/security/evals |
| Vendor leverage | Lower | Higher |

### Use Case -> Model Decision Table

| Use case | Recommended model/tool | Why | Alternative |
|---|---|---|---|
| Customer support chatbot | GPT-5.4 nano/mini or Claude Haiku 4.5 | Low cost and fast enough for volume | Gemini Flash-Lite, Mistral Small, Llama small |
| Legal document review | Claude Sonnet 4.6 | Long context, careful analysis, strong writing | GPT-5.4/5.5, Gemini Pro |
| Code review automation | Claude Sonnet 4.6 / GPT-5.4 / Copilot | Strong code reasoning plus workflow fit | Devstral 2, Codestral, Grok Build |
| Internal knowledge search (RAG) | Embeddings + GPT-5.4 mini / Claude Haiku / Llama | Separates retrieval from answer generation | Azure OpenAI, Bedrock Knowledge Bases, Vertex RAG |
| Complex multi-step reasoning | GPT-5.5 / Claude Opus 4.8 / Gemini Pro | Highest reasoning quality | DeepSeek V4 thinking, Grok 4.3 |
| Image extraction from documents | GPT vision / Claude Vision / Mistral OCR | OCR plus reasoning | Gemini Vision |
| Training content generation | Claude Sonnet 4.6 or GPT-5.4 | Quality writing and reasoning | Gemini Pro for very large source material |
| Real-time transcription | Whisper/OpenAI transcribe or cloud speech | Mature speech-to-text options | Azure Speech, Google Speech, xAI Voice |
| Sales email personalization | GPT-5.4 nano/mini | Cheap generation with CRM context | Claude Haiku, Gemini Flash-Lite |
| Executive strategy memo | Claude Sonnet 4.6 / Opus 4.8 | Strong prose and nuanced analysis | GPT-5.5 |
| Video-based training summary | Gemini Pro/Flash | Long multimodal context | GPT/Claude with extracted frames/transcripts |
| Private on-prem assistant | Llama 4 / Llama 3.3 / Mistral Large 3 | Open-weight data control | Hugging Face managed endpoint |
| Marketing image concepts | Midjourney / OpenAI image / FLUX | Creative quality and iteration speed | Ideogram for text-heavy visuals |
| AWS cloud migration helper | Amazon Q Developer | AWS-native code/cloud assistance | Copilot, Claude, GPT |
| Agentic back-office workflow | GPT-5.4/5.5 + LangGraph | Tool use, planning, auditability | Claude Sonnet/Opus, Gemini Pro |

### Concrete Cost Comparison

Prices below are direct/provider list examples from official docs where available. Cloud marketplace, batch, priority, caching, data residency, and negotiated enterprise discounts can change the final bill.

| Provider/model | Input per 1M tokens | Output per 1M tokens | Notes |
|---|---:|---:|---|
| OpenAI GPT-5.5 | $5.00 | $30.00 | Long context listed at $10/$45 |
| OpenAI GPT-5.5 Pro | $30.00 | $180.00 | Premium model |
| OpenAI GPT-5.4 | $2.50 | $15.00 | Balanced model |
| OpenAI GPT-5.4 mini | $0.75 | $4.50 | Cost-efficient workhorse |
| OpenAI GPT-5.4 nano | $0.20 | $1.25 | High-volume routing/extraction |
| Claude Opus 4.8 | $5.00 | $25.00 | Premium Claude model |
| Claude Sonnet 4.6 | $3.00 | $15.00 | Balanced Claude workhorse |
| Claude Haiku 4.5 | $1.00 | $5.00 | Fast Claude tier |
| Mistral Large 3 | $0.50 | $1.50 | Current Mistral pricing page listing |
| Mistral Medium 3.5 | $1.50 | $7.50 | Strong general/coding/reasoning model |
| Mistral Devstral 2 | $0.40 | $2.00 | Agentic coding |
| xAI Grok 4.3 | $1.25 | $2.50 | 1M context per xAI docs |
| xAI Grok Build 0.1 | $1.00 | $2.00 | Coding model |
| DeepSeek V4 Flash | $0.14 cache miss / $0.0028 cache hit | $0.28 | 1M context; thinking/non-thinking modes |
| DeepSeek V4 Pro | $0.435 cache miss / $0.003625 cache hit | $0.87 | 1M context; thinking/non-thinking modes |

### Rough Monthly Cost Examples

| Scenario | Volume assumption | Sensible model tier | Planning lesson |
|---|---:|---|---|
| FAQ chatbot | 1M conversations, 1K input + 200 output each | GPT-5.4 nano or Gemini/Claude fast tier | Small models keep token cost manageable; RAG/support operations dominate |
| Legal review | 5,000 documents, 40K input + 2K output each | Claude Sonnet / GPT-5.4 / Gemini Pro | Accuracy and liability matter more than token cost |
| Developer assistant | 100 engineers | Copilot/Claude/GPT/Devstral | Seat productivity ROI matters more than token arithmetic |
| Internal search | 10M docs indexed | Embeddings + cheap answer model | Indexing, retrieval quality, and permissions dominate |
| Strategy/reasoning tasks | 1,000 tasks/month | GPT-5.5 / Claude Opus / Gemini Pro | Premium model cost is small compared with decision value |

### Privacy & Compliance

- **GDPR/data protection:** define controller/processor roles, lawful basis, deletion process, DPA/SCCs, cross-border transfer, and data minimization.
- **Data residency:** hyperscaler deployments may offer regional processing; direct APIs may be global unless data residency is explicitly contracted.
- **Training use:** verify whether prompts/outputs are used for training for the exact product/plan. Enterprise/API terms usually differ from consumer chat products.
- **Logging/retention:** request zero-retention or modified abuse monitoring where available for sensitive workflows.
- **Self-hosting:** improves technical control but shifts security, patching, monitoring, access control, and evaluation responsibility to the enterprise.
- **Prompt injection:** any RAG or agent workflow must treat retrieved content as untrusted input.

### Fine-Tuning vs RAG vs Prompt Engineering

| Approach | Use when | Example | Avoid when |
|---|---|---|---|
| Prompt engineering | Task behavior can be clearly instructed | Support reply format, tone, structured JSON | The model needs private/current facts |
| RAG | Model needs current or private knowledge | HR policy search, SOP assistant, product docs | Retrieval quality is poor or permissions are unclear |
| Fine-tuning | You need repeated style/label behavior across many examples | Ticket taxonomy, regulated answer style | You only need the model to know documents |
| Agent/tool use | System must take actions or query live systems | CRM updates, inventory checks, test execution | Actions are risky and unaudited |
| Model distillation/routing | You have stable high-volume tasks | Premium model labels data for small model | Task changes constantly |

## Recommended Procurement Workflow

1. Define the use case in one sentence.
2. Classify risk: low, medium, high, regulated.
3. Build 30-100 representative test cases from real company data.
4. Shortlist cheap, balanced, and premium models.
5. Score accuracy, latency, cost, privacy fit, refusal behavior, and maintainability.
6. Deploy the cheapest model that passes the threshold.
7. Add human review for risky outputs.
8. Monitor drift, cost, and failures.
9. Re-evaluate quarterly because model economics change fast.

## Final Recommendation

For Tekravio-style enterprise work, I would design a **model-router architecture** instead of betting everything on one model:

- **Default premium:** Claude Sonnet 4.6 or GPT-5.4.
- **Hard reasoning:** GPT-5.5, Claude Opus 4.8, Gemini Pro, or DeepSeek thinking mode after evaluation.
- **High-volume low-risk:** GPT-5.4 nano/mini, Claude Haiku 4.5, Gemini Flash/Flash-Lite, or Mistral Small.
- **Private/self-hosted:** Llama 4/3.3 or Mistral open-weight models.
- **Coding:** GitHub Copilot for developers, Claude/GPT/Devstral/Codestral for automation.
- **RAG:** OpenAI/Cohere/Gemini/BGE embeddings plus a cheap answer model, with permission-aware retrieval.

The enterprise winner is not the company with the most expensive model. It is the company with the best evaluation loop, routing logic, governance, and user workflow integration.
