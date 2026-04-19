# Clean Claude  
![2026 Edition](https://img.shields.io/badge/2026-Edition-orange?style=flat-square)

> I curated this list of tools, SDKs, prompts, tutorials, and community projects for working with **Claude** — Anthropic’s AI assistant. Fully updated for 2026 with Claude 4, 1M token context, Computer Use (GA), and the entire MCP ecosystem.

## Contents
- [Official SDKs & Libraries](#official-sdks--libraries)
- [Models & API Reference](#models--api-reference)
- [Tools & Applications](#tools--applications)
- [Model Context Protocol (MCP)](#model-context-protocol-mcp)
- [Prompt Engineering](#prompt-engineering)
- [Agentic Patterns](#agentic-patterns)
- [Community Projects](#community-projects)
- [Tutorials & Learning Resources](#tutorials--learning-resources)
- [Research & Papers](#research--papers)


## Official SDKs & Libraries
> Maintained by Anthropic or deeply integrated into major AI frameworks.

| Name | Language | Stars | Notes |
|------|----------|-------|-------|
| [anthropic-sdk-python](https://github.com/anthropics/anthropic-sdk-python) | Python | ★ 41.2k | Official. Streaming, tool use, vision, async/await, auto-retry |
| [anthropic-sdk-typescript](https://github.com/anthropics/anthropic-sdk-typescript) | TypeScript | ★ 38.8k | Official. Full type safety, streaming helpers, Edge Runtime |
| [anthropic-sdk-java](https://github.com/anthropics/anthropic-sdk-java) | Java | ★ 9.1k | Official. Spring Boot integration, Project Reactor support |
| [anthropic-sdk-go](https://github.com/anthropics/anthropic-sdk-go) | Go | ★ 7.3k | Official. Idiomatic error handling, zero external dependencies |
| [anthropic-sdk-rust](https://github.com/anthropics/anthropic-sdk-rust) | Rust | ★ 4.2k | Official. Async via Tokio, zero-copy streaming |
| [langchain-anthropic](https://github.com/langchain-ai/langchain) | Python | ★ 22.4k | Chains, agents, LCEL, RAG pipelines, memory |
| [llama-index-anthropic](https://github.com/run-llama/llama_index) | Python | ★ 18.7k | Document loaders, knowledge graphs, query engines |
| [vercel-ai-sdk](https://github.com/vercel/ai) | TypeScript | ★ 31.5k | `useChat`, `useCompletion`, RSC streaming, tool rendering |
| [haystack-claude](https://github.com/deepset-ai/haystack) | Python | ★ 6.9k | Pipeline components for retrieval and summarization |
| [instructor](https://github.com/jxnl/instructor) | Python | ★ 24.1k | Structured outputs from Claude using Pydantic schemas |
| [litellm](https://github.com/BerriAI/litellm) | Python | ★ 19.8k | Unified API wrapper across 100+ LLM providers incl. Claude |


## Models & API Reference
### Claude 4 Model Family (2025–2026)

| Model ID                  | Context     | Best For                              | Speed    |
|---------------------------|-------------|---------------------------------------|----------|
| `claude-opus-4-20260101`  | 1M tokens   | Complex reasoning, research, agentic tasks | Slower   |
| `claude-sonnet-4-20260101`| 200k tokens | Coding, analysis, balanced production | Fast     |
| `claude-haiku-4-20260101` | 200k tokens | Real-time apps, classification, high-volume | Fastest  |

### Key API Features in 2026
- **Extended Thinking** — Budget-controlled internal reasoning (`thinking.budget_tokens`). Available on Opus 4 and Sonnet 4.
- **Computer Use (GA)** — Full GUI control via screenshot + action loop. Sub-second latency, now generally available.
- **1M Token Context** — Opus 4 can process entire codebases or books in one request.
- **Prompt Caching** — Up to 90% cost reduction on repeated large-context calls.
- **Batch API** — Process up to 100k prompts asynchronously with 50% discount.
- **Streaming Tool Use** — Real-time tool call deltas for live UX.
- **Video Understanding** — Opus 4 processes video frames for temporal reasoning (beta).
- **Citations API** — Structured source attribution from documents.

### Quickstart
```python
import anthropic
client = anthropic.Anthropic()

message = client.messages.create(
    model="claude-sonnet-4-20260101",
    max_tokens=1024,
    messages=[{"role": "user", "content": "Explain extended thinking in Claude 4."}]
)
print(message.content[0].text)
