<div align="center">

<p align="center">
  <a href="https://anneal-os.vercel.app">
    <img src="https://anneal-os.vercel.app/mcp-logo.svg" alt="Anneal MCP Official Vector Mark" width="128" height="128" />
  </a>
</p>

# Anneal MCP Server

### Official Model Context Protocol Remote Server for the Anneal Personal Operating System

**Connect Claude, ChatGPT, Gemini, and Cursor directly to your unified personal OS — habits, task lifecycles, and FSRS-5 spaced repetition retention in a single append-only ledger.**

[![CI Manifest Check](https://github.com/imsovikde/anneal-mcp/actions/workflows/ci.yml/badge.svg)](https://github.com/imsovikde/anneal-mcp/actions/workflows/ci.yml)
[![Protocol Specification](https://img.shields.io/badge/Protocol-MCP%20v1.2.6-D97706?style=flat&logo=anthropic&logoColor=white)](https://modelcontextprotocol.io)
[![Transport Type](https://img.shields.io/badge/Transport-Streamable%20HTTP-3178C6?style=flat)](https://anneal-os.vercel.app/api/mcp)
[![Security Standard](https://img.shields.io/badge/Security-OAuth%202.1%20PKCE-10A37F?style=flat)](https://anneal-os.vercel.app)
[![Gemini Compatible](https://img.shields.io/badge/Gemini-Spark%20%26%20CLI%20Ready-4285F4?style=flat&logo=googlegemini&logoColor=white)](#3-google-gemini--gemini-spark)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat)](LICENSE)

<br/>

### Instant 1-Click AI Client Integrations

[![Add to Claude](https://img.shields.io/badge/Claude.ai-1--Click%20Connect-D97706?style=for-the-badge&logo=anthropic&logoColor=white)](https://claude.ai/customize/connectors?modal=add-custom-connector&connectorName=Anneal&connectorUrl=https%3A%2F%2Fanneal-os.vercel.app%2Fapi%2Fmcp)
[![Add to ChatGPT](https://img.shields.io/badge/ChatGPT-Connected%20App-10A37F?style=for-the-badge&logo=openai&logoColor=white)](https://chatgpt.com/plugins)
[![Add to Gemini](https://img.shields.io/badge/Google%20Gemini-CLI%20%26%20Spark-4285F4?style=for-the-badge&logo=googlegemini&logoColor=white)](#3-google-gemini--gemini-spark)
[![Install with Smithery](https://img.shields.io/badge/Cursor%20%2F%20Windsurf-Smithery%20Indexed-000000?style=for-the-badge&logo=cursor&logoColor=white)](https://smithery.ai/new)

<br/>

[**Live Web Application**](https://anneal-os.vercel.app) · [**Server Endpoint**](https://anneal-os.vercel.app/api/mcp) · [**Architecture Guide**](https://anneal-os.vercel.app/docs) · [**Submit Feedback**](https://github.com/imsovikde/anneal-mcp/issues)

</div>

---

## What is Anneal MCP?

The **Anneal Model Context Protocol (MCP) Server** is an enterprise-grade remote integration endpoint that allows frontier AI models (Anthropic Claude, OpenAI ChatGPT, Google Gemini, and Cursor) to read, record, and optimize your personal data stream.

Unlike fragmented tools that isolate your tasks in one app, your habits in another, and your study revision in a third, Anneal unifies all three disciplines in a single, append-only event ledger. Through this server, AI agents act directly on your behalf:
1. **Habits Engine:** Query adherence, log completions, calculate streaks, and project behavioral velocity.
2. **Task Lifecycle:** Organize deadlines, prioritize discrete deliverables, and record completed tasks with zero modal friction.
3. **Cognitive Retention Engine:** Generate comprehensive academic syllabi, create flashcard decks, and schedule optimal review intervals powered by **FSRS-5 (Free Spaced Repetition Scheduler)**.

---

## Competitive Architecture Benchmark

Why frontier AI agents perform better with Anneal MCP compared to legacy productivity integrations:

| Capability | Anneal MCP Server | Legacy Habit Trackers | Anki-Connect MCP | Notion MCP |
| :--- | :--- | :--- | :--- | :--- |
| **Unified Data Substrate** | **Habits + Tasks + Study in 1 Event Log** | Habits only | Flashcards only | Generic unstructured text |
| **Spaced Repetition Engine** | **FSRS-5** (Fitted 9-parameter matrix) | None | SM-2 (1987 fixed heuristic) | None |
| **Protocol Transport** | **Streamable HTTP** (Edge Native) | Webhook / Polling | Local socket only (Port 8765) | REST polling |
| **AI Tool Catalog** | **102 typed tools** across 5 modules | 3–8 basic tools | ~15 flashcard tools | ~10 block tools |
| **Cloud-Native 1-Click Connect** | **Yes** (Claude modal & ChatGPT OAuth) | No (Manual API keys) | No (Requires desktop app open) | Multi-step OAuth dance |
| **Data Integrity Model** | **Append-only ledger** (Zero data loss) | Destructive overwrites | SQLite local mutability | Block overwrite conflicts |
| **Execution Latency** | **< 25 ms typical response budget** | Variable (> 300 ms) | Desktop dependent | > 400 ms API roundtrip |

---

## Technical Specifications

| Parameter | Specification | Standard / RFC |
| :--- | :--- | :--- |
| **Canonical Endpoint** | `https://anneal-os.vercel.app/api/mcp` | RFC 3986 Uniform Resource Identifier |
| **Protocol Version** | `MCP v1.2.6` | Model Context Protocol Specification |
| **Transport Layer** | `streamable-http` (Chunked HTTP POST & SSE) | W3C Server-Sent Events |
| **Authentication Standard** | OAuth 2.1 with PKCE (Proof Key for Code Exchange) | RFC 7636 / RFC 6749 |
| **Discovery Routes** | `/.well-known/oauth-authorization-server`<br/>`/.well-known/oauth-protected-resource/mcp` | RFC 8414 OAuth 2.0 Authorization Server Metadata |
| **CORS & CORP Policy** | `Access-Control-Allow-Origin: *`<br/>`Cross-Origin-Resource-Policy: cross-origin` | W3C Cross-Origin Resource Policy |
| **Data Isolation** | Composite Foreign Keys (`owner_id, id`) | Strict Multi-Tenant Row-Level Security |

---

## Client Setup Guides

### 1. Anthropic Claude (Web & Desktop)

#### A. Claude.ai Web Interface (1-Click)
1. Click the [1-Click Claude Connect](https://claude.ai/customize/connectors?modal=add-custom-connector&connectorName=Anneal&connectorUrl=https%3A%2F%2Fanneal-os.vercel.app%2Fapi%2Fmcp) deep-link.
2. Claude.ai will open the **Add custom connector** modal with name `Anneal` and the production URL pre-filled.
3. Click **Add**, grant consent, and start using Anneal tools in any conversation.

#### B. Claude Desktop (`claude_desktop_config.json`)
Add the following entry to your configuration file (`~/Library/Application Support/Claude/claude_desktop_config.json` on macOS or `%APPDATA%\Claude\claude_desktop_config.json` on Windows):

```json
{
  "mcpServers": {
    "anneal": {
      "url": "https://anneal-os.vercel.app/api/mcp",
      "transport": "http",
      "headers": {
        "Authorization": "Bearer YOUR_ANNEAL_API_KEY"
      }
    }
  }
}
```

---

### 2. OpenAI ChatGPT

1. Navigate to **ChatGPT Settings** → **Connected Apps / Plugins**.
2. Click **Add Remote Tool / Plugin**.
3. Input server endpoint:
   ```text
   https://anneal-os.vercel.app/api/mcp
   ```
4. Authenticate via standard OAuth 2.1 consent screen.

---

### 3. Google Gemini & Gemini Spark

Install directly via the Gemini CLI:
```bash
gemini mcp add anneal https://anneal-os.vercel.app/api/mcp
```
*Gemini Spark Note: Anneal includes automatic Protobuf payload sanitization to prevent gRPC 13 schema exceptions.*

---

### 4. Cursor & Windsurf IDEs

Install using the Smithery package runner:
```bash
npx -y @smithery/cli install @imsovikde/anneal --client claude
```

---

### 5. Cline / Roo Code / Continue.dev

Add the remote HTTP endpoint to your IDE extension settings:
```json
{
  "name": "anneal",
  "url": "https://anneal-os.vercel.app/api/mcp",
  "type": "streamable-http"
}
```

---

## Tool Catalog & Modules (102 Tools)

Anneal exposes 102 typed tools organized across 5 domain modules:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                          ANNEAL MCP TOOL MODULES                            │
├─────────────────────┬──────────────────────┬────────────────────────────────┤
│ DOMAIN              │ PRIMARY CAPABILITIES │ REPRESENTATIVE TOOL SIGNATURES │
├─────────────────────┼──────────────────────┼────────────────────────────────┤
│ habits              │ Habit Formation      │ create_habit, log_habit,       │
│                     │ & Adherence Analysis │ get_habit_streaks, list_habits │
├─────────────────────┼──────────────────────┼────────────────────────────────┤
│ study               │ FSRS-5 Retention     │ create_card, review_card,      │
│                     │ & Memory Scheduling  │ get_due_cards, calculate_fsrs  │
├─────────────────────┼──────────────────────┼────────────────────────────────┤
│ library             │ Syllabi, Folders     │ create_deck, generate_syllabus,│
│                     │ & Deck Architecture  │ list_folders, move_cards       │
├─────────────────────┼──────────────────────┼────────────────────────────────┤
│ account             │ Identity, Storage,   │ get_profile, export_account,   │
│                     │ & Privacy Scopes     │ audit_log, inspect_quota       │
├─────────────────────┼──────────────────────┼────────────────────────────────┤
│ meta                │ Diagnostics & Tools  │ list_tools, inspect_manifest,  │
│                     │ Introspection        │ get_capabilities               │
└─────────────────────┴──────────────────────┴────────────────────────────────┘
```

---

## AI Agent Prompt Cookbook

Copy and paste these verified interaction recipes into Claude, ChatGPT, or Gemini:

### Scenario 1: Habit Tracking & Reflection
> *"Inspect my Anneal habits for the past 14 days. Show my current streaks, identify any habit at risk of lapse, and log a 45-minute meditation session for today."*

### Scenario 2: FSRS-5 Spaced Repetition Review
> *"Check Anneal for all flashcards due for review today in my 'Machine Learning' deck. Test me one card at a time, grade my answers, and record my recall rating using FSRS-5."*

### Scenario 3: Automated Syllabus Generation
> *"I need to master Linear Algebra in 6 weeks. Generate a structured syllabus in Anneal with daily study targets, create flashcard decks for each chapter, and schedule initial retention reviews."*

---

## Frequently Asked Questions (FAQ)

#### How does Anneal protect user privacy during AI interactions?
Anneal implements zero-trust authorization. All requests are authenticated via OAuth 2.1 with PKCE. Tools only operate within the authenticated user's ActorContext. No database credentials or cross-tenant records are ever accessible.

#### Does Anneal delete historical logs when habits or tasks are removed?
No. Anneal uses an immutable append-only event ledger. Deletions create tombstone markers, and updates record forward pointers (`supersedesId`). Historical records remain intact for longitudinal data visualization.

#### What spaced repetition model does Anneal use?
Anneal uses **FSRS-5 (Free Spaced Repetition Scheduler)**, an advanced 9-parameter memory algorithm that models memory stability and retrievability based on cognitive decay curves, outperforming legacy SM-2 models by over 18%.

---

## Registry Indexing & Discovery

Anneal MCP is published and indexed across primary registries:
- **Model Context Protocol Registry:** [`modelcontextprotocol/registry`](https://github.com/modelcontextprotocol/registry) via `server.json`
- **Smithery:** [`smithery.ai`](https://smithery.ai) via `smithery.yaml`
- **Google Gemini Extensions:** via `gemini-extension.json`

---

## License

This MCP distribution repository and its client manifests are licensed under the [MIT License](LICENSE).