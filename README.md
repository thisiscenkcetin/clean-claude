```markdown
# Clean Claude  
![2026 Edition](https://img.shields.io/badge/2026-Edition-orange?style=flat-square)

> I curated this list of tools, SDKs, prompts, tutorials, and community projects for working with **Claude** — Anthropic’s AI assistant. Fully updated for 2026 with Claude 4, 1M token context, Computer Use (GA), and the entire MCP ecosystem.

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

---

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
```

**With Extended Thinking:**
```python
message = client.messages.create(
    model="claude-opus-4-20260101",
    max_tokens=16000,
    thinking={"type": "enabled", "budget_tokens": 10000},
    messages=[{"role": "user", "content": "Solve this step by step..."}]
)
```

---

## Tools & Applications

### Official Tools by Anthropic
- **[Claude.ai](https://claude.ai)** — Web, iOS, Android. Personal AI assistant (Pro / Team / Enterprise).
- **[Claude Code](https://docs.anthropic.com/en/docs/claude-code)** — Terminal agent with full repo context, git integration, and MCP.
- **[Claude in Chrome](https://chrome.google.com/webstore)** (beta) — Browsing agent for web workflows.
- **[Claude in Excel / PowerPoint](https://www.anthropic.com)** (beta) — Native Office add-ins.
- **[Cowork](https://www.anthropic.com)** (beta) — No-code desktop automation.
- **[Anthropic Workbench](https://console.anthropic.com/workbench)** — Prompt IDE for testing and comparison.

### Third-Party Coding Tools
- **[Cursor](https://cursor.sh)** — AI code editor with Claude 4 support.
- **[Aider](https://github.com/paul-gauthier/aider)** ★22k — Terminal pair-programming.
- **[Cline (VS Code)](https://github.com/cline/cline)** ★18.4k — Autonomous coding agent with MCP.
- **[Zed AI](https://zed.dev)** — High-performance editor with native Claude integration.
- **[Continue](https://github.com/continuedev/continue)** ★14.2k — Open-source VS Code & JetBrains extension.
- **[Windsurf](https://codeium.com/windsurf)** — Agentic IDE with Cascade flow.

### Automation & Workflow
- **[n8n](https://n8n.io)** — No-code workflows with native Claude nodes.
- **[Make](https://make.com)** — Visual automation platform.
- **[Zapier AI](https://zapier.com)** — Natural language Zaps.
- **[Activepieces](https://github.com/activepieces/activepieces)** ★9.8k — Open-source, self-hosted automation.

### Observability & Evaluation
- **[LangSmith](https://smith.langchain.com)**
- **[Braintrust](https://braintrustdata.com)**
- **[PromptLayer](https://promptlayer.com)**
- **[Helicone](https://helicone.ai)** — Open-source LLM observability proxy.

---

## Model Context Protocol (MCP)
MCP is the open standard that turns Claude into a secure, composable “USB-C for AI” — connecting it to external data, tools, and services.

### Official MCP Servers
`filesystem` • `github` • `google-drive` • `slack` • `postgres` • `sqlite` • `brave-search` • `fetch` • `memory` • `puppeteer`

### Popular Community MCP Servers
Obsidian, Notion, Linear, Stripe, AWS, Kubernetes, MongoDB Atlas, Raycast

### Build Your Own MCP Server (TypeScript example)
```typescript
import { Server } from "@modelcontextprotocol/sdk/server/index.js";
import { StdioServerTransport } from "@modelcontextprotocol/sdk/server/stdio.js";

const server = new Server(
  { name: "my-server", version: "1.0.0" },
  { capabilities: { tools: {} } }
);
// Define tools and handlers...
await server.connect(new StdioServerTransport());
```

---

## Prompt Engineering
### Core Techniques I Use
- XML tags for structured input
- Chain-of-Thought
- Explicit output format
- Prefilling the assistant response

### My Favorite System Prompts
**Coding assistant:**
```
You are an expert software engineer. When writing code:
- Use modern, idiomatic patterns
- Add error handling unless told otherwise
- Explain non-obvious decisions with short inline comments
- Ask clarifying questions before big architectural changes
```

**Document analysis:**
```
You are a precise document analyst. Extract only what is explicitly written. If something is unclear or missing, say so directly. No speculation.
```

---

## Agentic Patterns
- ReAct (Reason + Act)
- Orchestrator–Subagent
- Prompt Chaining + Validation
- Parallel Specialization

### My Go-To Agent Frameworks
- LangGraph, AutoGen, CrewAI, Agno, Smolagents, Pydantic AI

---

## Community Projects
### Productivity & Knowledge
- NotebookLM-OSS, Quivr, Khoj, mem0, Markprompt

### Coding & Development
- Claude Engineer, claude-coder, repomix, SWE-agent, OpenHands

### Research & Analysis
- Storm, GPT-Researcher, Perplexica, AutoSurvey

### Creative & Multimodal
- Ebook-GPT, Bedrock-Claude-Chat, ClaudeSync

---

## Tutorials & Learning Resources
- Anthropic official docs & free courses
- Anthropic Cookbook
- DeepLearning.AI – Prompt Engineering with Claude
- LLM Bootcamp

---

## Research & Papers
Key Anthropic papers (Constitutional AI, Extended Thinking, Scaling Monosemanticity, Model Specification, etc.) plus major external benchmarks on Claude.

---

**Curated by dev.cenkcetin@gmail.com**  
Last updated: April 2026  
```
