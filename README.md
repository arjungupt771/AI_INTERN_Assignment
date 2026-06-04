# Tekravio Labs AI Intern Assignment

This repository contains a complete AI Model Reference submission for the Tekravio Labs AI Intern Assignment.

## Files

- `AI_Model_Reference_Document.md` - the main enterprise-facing model reference document.
- `ai_comparison_tool.html` - bonus interactive model recommendation tool.
- `README.md` - submission guide, mindset answers, source notes, and suggested email text.

## How to Read

Start with `AI_Model_Reference_Document.md`. It is structured for a CTO, VP Engineering, or Head of L&D who needs to choose models by use case, not by hype. The most practical section is **Enterprise AI Platforms & Decision Framework**, especially the use-case table and procurement workflow.

Then open `ai_comparison_tool.html` in a browser. It is an offline tool that recommends model options based on use case, budget, and privacy requirement.

## Mindset Questions

### 1. If a mid-size Indian enterprise asked: "Should we use OpenAI or build on open-source models?" what would I tell them?

I would not start with "OpenAI vs open source." I would start with risk, data, and volume.

For most mid-size Indian enterprises, I would recommend using a managed proprietary model first, usually through Azure OpenAI, AWS Bedrock, Google Vertex AI, or direct OpenAI depending on their cloud stack. The reason is simple: the fastest business value comes from solving the workflow, not from operating GPUs. For customer support, document summarization, L&D content, sales enablement, internal search, and reporting, managed APIs will usually be cheaper than hiring and running the infrastructure team needed to self-host properly.

But I would recommend open-source/open-weight models when one of these is true: the data cannot leave a controlled environment, per-token cost becomes too high at scale, the company needs deep customization, or procurement wants vendor leverage. In India, this matters for BFSI, healthcare, legal, public sector, and companies with strict customer-data contracts. A practical roadmap would be: start with managed APIs and strong evaluation, build RAG around internal data, measure real usage and cost for 2-3 months, then move stable high-volume workloads to Llama/Mistral/DeepSeek-style open models if the economics and compliance case is strong.

My short answer: **use a managed frontier model to learn fast; use open-source when privacy, scale, or customization proves it is worth the operational cost.**

### 2. Which single model surprised me most during the research, and why?

DeepSeek R1 and the newer DeepSeek V4 pricing surprised me most. I expected open reasoning models to be interesting but clearly behind premium proprietary systems. What surprised me was how quickly an open reasoning model changed the cost and strategy conversation. Even if a company does not deploy DeepSeek directly, R1 proved that reasoning capability is no longer only a closed-lab luxury feature.

The surprise was not just benchmark performance. It was the strategic pressure it created: every enterprise buyer now has to ask which tasks truly need expensive frontier APIs and which can be handled by cheaper reasoning models with evaluation and guardrails.

### 3. What is one thing that is genuinely confusing or unclear in the AI model landscape right now?

The most confusing thing is that model names no longer map cleanly to capabilities. A name like Pro, Flash, Sonnet, mini, nano, Turbo, or thinking does not tell you enough. The same model family may have different context windows, tool support, prices, or availability depending on whether it is accessed directly, through Azure, Bedrock, Vertex, GitHub Copilot, or a consumer chat product.

To understand it better, I would want a live model registry that tracks exact model IDs, context windows, modalities, pricing, retention terms, regions, deprecation dates, and supported tools by platform.

### 4. If I had to pick one model to bet Tekravio's AI strategy on for the next 2 years, what would it be and why?

I would bet on **Claude Sonnet 4.6-class models** as the primary premium model, while keeping OpenAI GPT-5.x, Gemini, Mistral, DeepSeek, and open-weight alternatives in the architecture.

For Tekravio's likely enterprise use cases - L&D content, document analysis, policy interpretation, code assistance, internal knowledge workflows, and executive communication - Claude Sonnet 4.6 offers a strong balance of writing quality, long-context reasoning, code ability, and user trust. It is rarely the cheapest model, but it is often the model I would trust for the first premium version of a high-value workflow.

That said, the real strategy should not depend on one vendor. Tekravio should build model abstraction, evaluation harnesses, and fallback routing so it can switch between models as prices and capabilities change.

### 5. What is missing from this assignment?

The assignment asks for model coverage and decision-making, but it should also ask for **evaluation design**. Enterprise AI is not won by reading model cards alone. It is won by testing models on the company's actual documents, code, tickets, policies, and user workflows.

I would add a required section: build a 30-case evaluation set for one enterprise use case, score 3-5 models, and explain the trade-offs. I would also add security topics: prompt injection, data leakage, audit logging, model deprecation planning, and human approval for agentic actions.

## Research Sources and Notes

The main document was updated on 05 June 2026 to include current official model families such as OpenAI GPT-5.5/GPT-5.4, Claude Opus 4.8/Sonnet 4.6/Haiku 4.5, Gemini 3.x, Mistral Large 3/Medium 3.5, Grok 4.3, and DeepSeek V4. Older assignment-specified models such as GPT-4o, Claude 3.5, Gemini 1.5, Llama 3.x, and Grok 3 are still covered as legacy/compatibility context.

Sources used:

- OpenAI models and pricing: https://platform.openai.com/docs/models and https://platform.openai.com/docs/pricing/
- Anthropic Claude models and pricing: https://docs.anthropic.com/en/docs/about-claude/models/overview and https://docs.anthropic.com/en/docs/about-claude/pricing
- Google Gemini / Vertex AI models: https://cloud.google.com/vertex-ai/generative-ai/docs/models and https://cloud.google.com/vertex-ai/generative-ai/pricing
- Meta Llama models: https://www.llama.com/models/
- Mistral models and pricing: https://mistral.ai/en/models and https://mistral.ai/pricing/
- xAI model docs: https://docs.x.ai/docs/models
- AWS Bedrock: https://aws.amazon.com/bedrock/
- Azure OpenAI data/privacy information: https://learn.microsoft.com/en-us/azure/ai-foundry/responsible-ai/openai/data-privacy
- Hugging Face Inference Endpoints: https://huggingface.co/docs/inference-endpoints
- GitHub Copilot documentation: https://docs.github.com/en/copilot
- DeepSeek documentation and pricing: https://api-docs.deepseek.com/ and https://api-docs.deepseek.com/quick_start/pricing

Important limitation: AI model details change weekly. Before production procurement, verify exact current model IDs, regional availability, data retention terms, and prices from the provider contract or official pricing page.

