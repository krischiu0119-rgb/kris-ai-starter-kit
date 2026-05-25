<!-- 2026-05-25 -->
# Kris's AI Starter Kit

> Install it. Your AI development practices improve immediately.

A drop-in framework for structured AI-assisted development. Gives your AI agent consistent behavior, quality gates, and a delegation workflow that actually works.

Works with **Kiro IDE**, **Claude Code**, and **Claude CoWork**.

---

## 📦 What's Inside

| Component | What It Does | Level |
|-----------|-------------|-------|
| **AGENTS.md** | Cross-platform agent workflow rules (Planner → Executor → Reviewer) | 🟢 Core |
| **Steering files** | Persistent instructions that shape agent behavior every session | 🟢 Core |
| **Hooks** | Automated triggers (QA after edits, audit logging, deploy verification) | 🔵 Optional |
| **Templates** | Blank AGENTS.md, FILE_MAP.md, PROJECT_BRIEF.md to fill in | 🟢 Core |
| **Privacy rules** | Guardrails to prevent leaking secrets or PII | 🔵 Optional |
| **Database safety** | Rules preventing destructive migrations | 🔵 Optional |
| **Sub-agent workflow** | Full delegation protocol with convergence rules | ⚪ Advanced |
| **Examples** | Filled-in example for a Python FastAPI project | 🟢 Core |

**Legend:** 🟢 Core (everyone should use) · 🔵 Optional (use if relevant) · ⚪ Advanced (power users)

---

## 🚀 Get Started

Two paths. Pick one.

### Quick Start (2 minutes)

Paste this prompt into your AI tool (Kiro, Claude Code, or CoWork):

```
I want to adopt an AI agent workflow framework.

Fetch the content from: https://github.com/krischiu0119-rgb/kris-ai-starter-kit

Then:
1. Read the repo structure and identify which files apply to my tool (Kiro → kiro/ folder, Claude Code → claude-code/ folder)
2. Copy the relevant steering/rules files into my project
3. Copy AGENTS.md to my project root
4. Analyze my project and generate FILE_MAP.md + PROJECT_BRIEF.md
5. Replace all [PLACEHOLDER] values with my project's actual info
6. Create temporary/ and audit_log.md if they don't exist

Give me a summary when done.
```

That's it. The agent handles the rest.

### Full Setup (10 minutes)

For full control over what gets installed:

```bash
# Clone
git clone https://github.com/krischiu0119-rgb/kris-ai-starter-kit.git
cd kris-ai-starter-kit

# For Kiro IDE users:
cp -r kiro/ /path/to/your-project/.kiro/
cp AGENTS.md /path/to/your-project/

# For Claude Code users:
cp claude-code/CLAUDE.md /path/to/your-project/
cp -r claude-code/.claude/ /path/to/your-project/
cp AGENTS.md /path/to/your-project/
```

Then customize:
1. Edit `AGENTS.md` — replace all `[PLACEHOLDER]` values
2. Create `FILE_MAP.md` using `templates/FILE_MAP.template.md`
3. Create `PROJECT_BRIEF.md` using `templates/PROJECT_BRIEF.template.md`
4. Review hooks in `.kiro/hooks/` — disable any you don't need

---

## ⚙️ Variables to Customize

After installation, find and replace these placeholders:

| Variable | Where | Example |
|----------|-------|---------|
| `[PROJECT_NAME]` | AGENTS.md | `my-saas-app` |
| `[TECH_STACK]` | AGENTS.md | `Next.js + Supabase + Tailwind` |
| `[BUILD_COMMAND]` | AGENTS.md, steering files | `pnpm build` |
| `[TEST_COMMAND]` | AGENTS.md, QA hooks | `pytest` or `vitest --run` |
| `[DEPLOY_PLATFORM]` | AGENTS.md, deploy hook | `Vercel` / `AWS CDK` / `Railway` |
| `[MAX_PARALLEL_AGENTS]` | AGENTS.md | `3` (default, adjust for RAM) |

**Steering files to activate/deactivate:**

| File | Activate If... |
|------|----------------|
| `database-safety.md` | Your project has a database |
| `deployment-verification.md` | You deploy to a live environment |
| `code-execution-practices.md` | You want agents to use temp files instead of inline scripts |
| `loop-until-success.md` | You want automated review loops |
| `privacy-guard.md` | Your project handles sensitive data |
| `subagent-workflow.md` | You want full Planner/Executor/Reviewer delegation |

**Hooks to enable/disable:**

| Hook | What It Does | Enable If... |
|------|-------------|---------------|
| `qa-post-edit.kiro.hook` | Runs QA after file edits | Always recommended |
| `qa-full-audit.kiro.hook` | Deep QA before deploy | You deploy from this project |
| `audit-log-writer.kiro.hook` | Logs completed work | You want traceability |
| `housekeeping.kiro.hook` | Cleans temp files, checks FILE_MAP | Weekly maintenance |
| `verify-deploy.kiro.hook` | Confirms deploy succeeded | You deploy to production |

---

## 🧭 How It Works

### Core Concept: Structured Delegation

Instead of one long conversation doing everything, work is split:

| Role | Responsibility |
|------|---------------|
| **Planner** | Breaks tasks into steps, assigns to executors |
| **Executor** | Implements one focused task, verifies with build |
| **Reviewer** | Checks output quality, runs QA layers |

### 3-Layer QA

| Layer | When | What |
|-------|------|------|
| **Smoke** | After every task | Build passes, no type errors |
| **Regression** | After feature complete | Full test suite, nothing broken |
| **Full Audit** | Before deploy | Edge cases, a11y, security |

### Safety Rails

- **Convergence rules**: Review loops cap at 5 iterations, escalate to user if stuck
- **File placement**: Agents must check FILE_MAP.md before creating files
- **Database safety**: Migrations are additive-only by default
- **Deploy verification**: `git push` ≠ deployed — agents verify the live URL

---

## 📚 Progressive Learning Path

Don't enable everything on Day 1.

| Phase | You Do | Agent Does | Weekly Cost |
|-------|--------|-----------|-------------|
| **Week 1-2: Observer** | Break tasks, write prompts, review everything | Execute single tasks only | ~$5-15 |
| **Week 3-4: Co-Pilot** | High-level direction + final review | Plan + execute + self-check | ~$15-40 |
| **Week 5+: Delegation** | Strategic decisions only | Full Planner → Executor → Reviewer | ~$40-100+ |

---

## 🔗 Ecosystem & Alternatives

This kit isn't the only option. These repos offer excellent approaches:

| Repo | Focus | Best For |
|------|-------|----------|
| [shanraisshan/claude-code-best-practice](https://github.com/shanraisshan/claude-code-best-practice) | From vibe coding to agentic engineering | Comprehensive CLAUDE.md patterns |
| [hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) | Curated commands, files, workflows | Discovery & reference |
| [SuperClaude-Org/SuperClaude_Framework](https://github.com/SuperClaude-Org/SuperClaude_Framework) | Cognitive personas + slash commands | Power users |
| [anthropics/skills](https://github.com/anthropics/skills) | Anthropic's official Agent Skills | Official patterns |
| [gsd-build/get-shit-done](https://github.com/gsd-build/get-shit-done) | Lightweight meta-prompting | Minimalists |
| [mksglu/context-mode](https://github.com/mksglu/context-mode) | Saves 98% context via FTS5 indexing | Token-constrained users |

### Author's Private Config

For the author's personal (de-identified) steering files, hooks, and accumulated learnings from daily use:
→ [krischiu0119-rgb/dotpilot](https://github.com/krischiu0119-rgb/dotpilot) — a private configuration repo containing real-world steering rules refined over months of AI-assisted development. Useful as a reference for what a mature setup looks like.

---

## 📁 Directory Structure

```
kris-ai-starter-kit/
├── AGENTS.md                  # Cross-platform agent workflow (shared by all tools)
├── MIGRATION_GUIDE.md         # Adoption guide for existing projects
├── PRIVACY_RULES.md           # What's safe to include in public repos
├── ROADMAP.md                 # Future direction
├── README.md                  # You are here
│
├── kiro/                      # For Kiro IDE → copy to .kiro/
│   ├── steering/              # Persistent agent instructions
│   │   ├── subagent-workflow.md
│   │   ├── database-safety.md
│   │   ├── deployment-verification.md
│   │   ├── code-execution-practices.md
│   │   ├── code-quality.md
│   │   ├── executor-prompt-template.md
│   │   ├── loop-until-success.md
│   │   ├── privacy-guard.md
│   │   └── mcp-guide.md           # TODO: MCP configuration guide
│   └── hooks/                 # Automated triggers
│       ├── audit-log-writer.kiro.hook
│       ├── housekeeping.kiro.hook
│       ├── qa-full-audit.kiro.hook
│       ├── qa-post-edit.kiro.hook
│       └── verify-deploy.kiro.hook
│
├── claude-code/               # For Claude Code → copy to project root
│   ├── CLAUDE.md
│   └── .claude/rules/
│
├── templates/                 # Blank templates to customize
│   ├── AGENTS.template.md
│   ├── FILE_MAP.template.md
│   ├── PROJECT_BRIEF.template.md
│   └── audit_log.template.md
│
└── examples/                  # Filled-in examples
    └── minimal-project/       # Python FastAPI example
```

---

## 🔧 Compatibility

| Tool | Support | Notes |
|------|---------|-------|
| **Kiro IDE** | ✅ Full | Steering + hooks + specs |
| **Claude Code** | ✅ Full | CLAUDE.md + .claude/rules/ |
| **Claude CoWork** | ✅ Full | Uses AGENTS.md directly |
| **Cursor** | ⚠️ Partial | AGENTS.md works, no hooks |
| **Windsurf** | ⚠️ Partial | AGENTS.md works, no hooks |

---

## Contributing

This is a living framework. Every time an agent makes a mistake:
1. Identify the root cause
2. Add a rule to prevent recurrence
3. Update AGENTS.md or the relevant steering file

Good rules come from real mistakes.

## License

MIT
