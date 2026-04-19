# ✦ Clean Claude
![2026 Edition](https://img.shields.io/badge/2026-Edition-orange?style=flat-square)

> I curated this clean list of tools, SDKs, prompts, tutorials, and community projects for working with **Claude** — Anthropic’s AI assistant. Fully updated for 2026 with Claude 4, 1M token context, Computer Use (GA), and the entire MCP ecosystem.

---

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

---

## Official SDKs & Libraries
> Maintained by Anthropic or deeply integrated into major AI frameworks.

| Name                          | Language     | Stars   | Notes |
|-------------------------------|--------------|---------|-------|
| [anthropic-sdk-python](https://github.com/anthropics/anthropic-sdk-python) | Python | ★ 41.2k | Official. Streaming, tool use, vision, async, auto-retry |
| [anthropic-sdk-typescript](https://github.com/anthropics/anthropic-sdk-typescript) | TypeScript | ★ 38.8k | Official. Full type safety, Edge Runtime |
| [anthropic-sdk-java](https://github.com/anthropics/anthropic-sdk-java) | Java | ★ 9.1k | Official. Spring Boot + Reactor |
| [anthropic-sdk-go](https://github.com/anthropics/anthropic-sdk-go) | Go | ★ 7.3k | Official. Zero dependencies |
| [anthropic-sdk-rust](https://github.com/anthropics/anthropic-sdk-rust) | Rust | ★ 4.2k | Official. Tokio + zero-copy |
| [langchain-anthropic](https://github.com/langchain-ai/langchain) | Python | ★ 22.4k | Chains, agents, LCEL, RAG |
| [llama-index-anthropic](https://github.com/run-llama/llama_index) | Python | ★ 18.7k | Document loaders & query engines |
| [vercel-ai-sdk](https://github.com/vercel/ai) | TypeScript | ★ 31.5k | `useChat`, RSC streaming |
| [instructor](https://github.com/jxnl/instructor) | Python | ★ 24.1k | Pydantic structured outputs |
| [litellm](https://github.com/BerriAI/litellm) | Python | ★ 19.8k | 100+ LLM unified wrapper |

---

## Models & API Reference

### Claude 4 Model Family (2025–2026)

| Model ID                   | Context     | Best For                              | Speed    |
|----------------------------|-------------|---------------------------------------|----------|
| `claude-opus-4-20260101`   | 1M tokens   | Complex reasoning, research, agents   | Slower   |
| `claude-sonnet-4-20260101` | 200k tokens | Coding, analysis, production          | Fast     |
| `claude-haiku-4-20260101`  | 200k tokens | Real-time, classification, high-volume| Fastest  |

### Key 2026 Features
- **Extended Thinking** (`thinking.budget_tokens`)
- **Computer Use (GA)** – GUI kontrolü
- **1M Token Context**
- **Prompt Caching** (%90’a varan maliyet düşüşü)
- **Streaming Tool Use**
- **Video Understanding** (Opus 4)

**Hızlı başlangıç örneği:**
```python
import anthropic
client = anthropic.Anthropic()

message = client.messages.create(
    model="claude-sonnet-4-20260101",
    max_tokens=1024,
    messages=[{"role": "user", "content": "Claude 4’teki Extended Thinking nedir?"}]
)
print(message.content[0].text)
