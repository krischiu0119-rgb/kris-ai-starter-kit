<!-- 2026-05-25 -->
# Roadmap

> Where this project is heading.

This starter kit began as a personal collection of steering files. It's evolving into something more useful.

---

## Current State (v1)

✅ Cross-platform agent workflow (AGENTS.md)  
✅ Kiro steering files + hooks  
✅ Claude Code rules  
✅ Templates for quick adoption  
✅ Privacy guardrails for public repos  
✅ Examples  

---

## Near-Term (Q3 2026)

### Department-Specific Starter Packs

Instead of one generic kit, teams get a customized version:

| Pack | Audience | Includes |
|------|----------|----------|
| **Engineering** | Developers | Full sub-agent workflow, DB safety, deploy verification |
| **Operations** | Ops / non-technical | Simplified steering, CoWork-focused, no hooks |
| **Strategy** | Leadership / BD | Research patterns, document generation, privacy rules |
| **Design** | Designers | Brand steering, HTML/PDF rules, design system references |

Each pack is a subset of the full kit, pre-configured for that team's workflow.

### MCP-Based Distribution

Instead of copying Markdown files from GitHub:
- Install steering rules via MCP server
- Agent pulls latest rules on-demand
- Version-controlled updates without manual file copying
- Per-project configuration via a single config file

---

## Mid-Term (Q4 2026)

### Agent Catalog / Registry

A searchable registry of reusable agent configurations:
- Browse by use case ("code review", "deploy", "research")
- One-click install into any project
- Community contributions welcome
- Quality ratings based on real usage

### Access Control & Versioning

- Pin steering files to specific versions (avoid breaking changes)
- Role-based access (some rules only for senior devs, some for everyone)
- Changelog per steering file
- Rollback capability

---

## Long-Term Vision

### Shared Intelligence Layer

Every team member's AI agent draws from the same knowledge base:
- Company-wide rules (coding standards, security policies)
- Team-specific rules (frontend patterns, API conventions)
- Personal preferences (formatting, communication style)

Layered like CSS: company → team → personal, with later layers overriding earlier ones.

### Self-Improving Rules

When an agent makes a mistake:
1. The fix gets captured as a new rule
2. The rule propagates to all team members automatically
3. The mistake never happens again, for anyone

This turns individual learning into organizational learning.

---

## How to Contribute Ideas

Open an issue with the `roadmap` label, or submit a PR to this file.

---

*This is aspirational. Timelines are estimates, not commitments.*
