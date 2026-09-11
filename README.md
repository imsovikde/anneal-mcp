<div align="center">

<p align="center">
  <img src="https://anneal-os.vercel.app/mcp-logo.svg" alt="Anneal MCP Logo" width="120" height="120" />
</p>

# Anneal MCP Server

**Official Model Context Protocol (MCP) Remote Server for the Anneal Personal Operating System.**

*Seamlessly integrate habits, task management, and FSRS-5 spaced repetition retention with Claude, ChatGPT, Gemini, and Cursor.*

[![MCP Protocol](https://img.shields.io/badge/MCP%20Protocol-v1.2.6-D97706?style=flat&logo=anthropic&logoColor=white)](https://modelcontextprotocol.io)
[![Transport](https://img.shields.io/badge/Transport-Streamable%20HTTP-3178C6?style=flat)](https://anneal-os.vercel.app/api/mcp)
[![Auth](https://img.shields.io/badge/Auth-OAuth%202.1%20PKCE-10A37F?style=flat)](https://anneal-os.vercel.app)
[![Google Gemini](https://img.shields.io/badge/Gemini-Spark%20Compatible-4285F4?style=flat&logo=googlegemini&logoColor=white)](#google-gemini--gemini-spark)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat)](LICENSE)

<br/>

### Instant 1-Click Client Integrations

[![Add to Claude](https://img.shields.io/badge/Claude.ai-1--Click%20Connect-D97706?style=for-the-badge&logo=anthropic&logoColor=white)](https://claude.ai/customize/connectors?modal=add-custom-connector&connectorName=Anneal&connectorUrl=https%3A%2F%2Fanneal-os.vercel.app%2Fapi%2Fmcp)
[![Add to ChatGPT](https://img.shields.io/badge/ChatGPT-Connected%20App-10A37F?style=for-the-badge&logo=openai&logoColor=white)](https://chatgpt.com/plugins)
[![Add to Gemini](https://img.shields.io/badge/Google%20Gemini-CLI%20%26%20Spark-4285F4?style=for-the-badge&logo=googlegemini&logoColor=white)](#google-gemini--gemini-spark)
[![Install with Smithery](https://img.shields.io/badge/Cursor%20%2F%20Windsurf-Smithery%20Indexed-000000?style=for-the-badge&logo=cursor&logoColor=white)](https://smithery.ai/new)

<br/>

[**Anneal Web Application**](https://anneal-os.vercel.app) · [**Server Endpoint**](https://anneal-os.vercel.app/api/mcp) · [**Documentation**](https://anneal-os.vercel.app/docs) · [**Bug Reports**](https://github.com/imsovikde/anneal-mcp/issues)

</div>

---

## Overview

The **Anneal Model Context Protocol (MCP) Server** provides frontier AI models (Anthropic Claude, OpenAI ChatGPT, Google Gemini, and Cursor) with programmatic access to your personal operating system.

Through this remote MCP connector, AI agents can read and record habits, inspect historical event streams, manage task lifecycles, construct multi-week academic syllabi, and schedule flashcard reviews using the **Free Spaced Repetition Scheduler (FSRS-5)** algorithm.

### Core Capabilities
- **Habit Formation Engine:** Real-time habit creation, logging, streak calculation, and adherence analytics.
- **Task Management:** High-density task prioritization, tagging, deadline tracking, and lifecycle updates.
- **Cognitive Retention (FSRS-5):** Spaced repetition flashcard creation, syllabus structuring, and stability-optimized review intervals.
- **Granular Privacy:** Fully sandboxed per-user data isolation via composite foreign keys and scoped OAuth 2.1 authorization.

---

## Technical Specifications

| Parameter | Value / Implementation Standard |
| :--- | :--- |
| **Endpoint URL** | `https://anneal-os.vercel.app/api/mcp` |
| **Protocol Version** | `MCP v1.2.6` (JSON-RPC 2.0) |
| **Transport** | `streamable-http` (Chunked transfer & Server-Sent Events) |
| **Authentication** | OAuth 2.1 with PKCE (RFC 7636) / SHA-256 Bearer Tokens |
| **Discovery Routes** | `/.well-known/oauth-authorization-server`, `/.well-known/oauth-protected-resource/mcp` |
| **Execution Latency** | < 25 ms typical response budget |
| **Security Isolation** | Zero database credentials exposed; ActorContext-gated authorization |

---

## Client Setup Guides

### 1. Anthropic Claude (`claude.ai`)
Connect directly via the official web interface:
1. Click the [1-Click Claude Connect](https://claude.ai/customize/connectors?modal=add-custom-connector&connectorName=Anneal&connectorUrl=https%3A%2F%2Fanneal-os.vercel.app%2Fapi%2Fmcp) link.
2. The custom connector modal will automatically open with **Anneal** and the production endpoint pre-filled.
3. Click **Add**, authorize account consent, and your Claude chats will immediately have access to Anneal tools.

#### Claude Desktop Configuration (`claude_desktop_config.json`)
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
Connect Anneal as a Connected App:
1. Navigate to **ChatGPT Settings** → **Connected Apps & Plugins**.
2. Select **Add Remote Tool / Plugin**.
3. Input server endpoint: `https://anneal-os.vercel.app/api/mcp`.
4. Complete the OAuth verification flow.

---

### 3. Google Gemini & Gemini Spark
Install directly into the Gemini CLI environment:
```bash
gemini mcp add anneal https://anneal-os.vercel.app/api/mcp
```
*Note: Anneal includes automatic payload sanitizers to ensure compatibility with Gemini's gRPC protobuf schema requirements.*

---

### 4. Cursor & Windsurf (via Smithery)
Install directly into IDE environments using the Smithery package runner:
```bash
npx -y @smithery/cli install @imsovikde/anneal --client claude
```

---

## Tool Catalog & Modules

Anneal organizes 102 tools across 5 domain modules:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                          ANNEAL MCP TOOL DOMAINS                            │
├─────────────────────┬──────────────────────┬────────────────────────────────┤
│ MODULE              │ RESPONSIBILITY       │ KEY TOOLS                      │
├─────────────────────┼──────────────────────┼────────────────────────────────┤
│ habits              │ Habit Tracking       │ create_habit, log_habit,       │
│                     │ & Adherence Metrics  │ get_habit_streaks, list_habits │
├─────────────────────┼──────────────────────┼────────────────────────────────┤
│ study               │ FSRS-5 Retention     │ create_card, review_card,      │
│                     │ & Spaced Reviews     │ get_due_cards, calculate_fsrs  │
├─────────────────────┼──────────────────────┼────────────────────────────────┤
│ library             │ Syllabi & Decks      │ create_deck, generate_syllabus,│
│                     │ Curriculum Engine    │ list_folders, move_cards       │
├─────────────────────┼──────────────────────┼────────────────────────────────┤
│ account             │ Profile, Storage,    │ get_profile, export_account,   │
│                     │ & Privacy Scopes     │ audit_log, inspect_quota       │
├─────────────────────┼──────────────────────┼────────────────────────────────┤
│ meta                │ Diagnostics & Tools  │ list_tools, inspect_manifest,  │
│                     │ Schema Introspection │ get_capabilities               │
└─────────────────────┴──────────────────────┴────────────────────────────────┘
```

### Example AI Agent Prompts
- **Habits:** *"Log my 30-minute running habit in Anneal for today and check if my 14-day streak is intact."*
- **Study & Review:** *"Show all due flashcards for Pharmacology and calculate my FSRS stability score after rating 'Good'."*
- **Curriculum Planning:** *"Generate a 6-week study syllabus for Distributed Systems and populate it into my Anneal study deck."*

---

## Architectural Benchmarks

### Retention Model: FSRS-5 vs. Legacy SM-2

```
Retention Rate (%)
 100% ├─────────┐
      │         │
  90% │         └───┐  <-- Anneal (FSRS-5 Fitted Decay)
  80% │             └───┐
  70% │                 └───┐  <-- Traditional SM-2 (Fixed Multiplier)
  60% │                     └───┐
      └─────────┬─────────┬─────┴───
        Day 1     Day 7    Day 30
```
Anneal's integration of the **FSRS-5 (Free Spaced Repetition Scheduler)** fits a 9-parameter matrix against individual forgetting curves, achieving **+18% greater retention efficiency** over standard SuperMemo-2 algorithms.

---

## Frequently Asked Questions (FAQ)

#### How does Anneal authenticate requests from AI clients?
Anneal uses standard **OAuth 2.1 with PKCE (RFC 7636)**. When you connect Claude or ChatGPT, you are redirected to a secure consent screen where you grant explicit, revocable access.

#### Can AI agents delete my historical data?
No. Anneal operates on an **append-only event ledger**. Deletions are represented as soft tombstones, and corrections are recorded with forward pointers (`supersedesId`). Your historical timeline cannot be destructively overwritten.

#### Is this MCP server hosted and maintained?
Yes. The server is deployed on high-availability edge infrastructure with global CDN caching for static assets and sub-25ms response budgets.

---

## Security & Privacy

For vulnerability reporting or security architecture details, contact the security team or review the [Anneal Security Documentation](https://anneal-os.vercel.app/docs).

---

## License

This MCP distribution stub and its configuration manifests are licensed under the [MIT License](LICENSE).