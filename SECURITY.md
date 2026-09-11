# Security Policy

## Security Architecture

The Anneal Model Context Protocol (MCP) remote server is engineered with zero-trust architectural boundaries:

1. **RFC 7636 PKCE OAuth 2.1:** All third-party AI clients authenticate via proof key for code exchange. Secrets are never exposed to client-side scripts.
2. **ActorContext Enforcement:** Tool execution is strictly isolated per authenticated user identity. Cross-tenant access is structurally prevented via composite foreign keys at the database layer.
3. **Append-Only Immutability:** Event mutations append new log rows with forward pointers (`supersedesId`). Historical records cannot be silently rewritten or destructively deleted.

## Reporting a Vulnerability

If you discover a potential security vulnerability in the Anneal MCP server or connector manifests, please report it privately:

- **Email:** `security@anneal.app` (or open a confidential security advisory on GitHub)
- **Response SLA:** Vulnerability reports are triaged within 24 hours.
- Please do **not** open public GitHub issues for sensitive security vulnerabilities.