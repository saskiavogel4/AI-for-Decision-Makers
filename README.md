# AI for Decision-Makers — GES M&A Agent Team

A team of 15 AI agents that advise GES (Global Experience Specialists) senior leadership on
acquisitions in the trade show, exhibition and events industry. The agents are scoped to
this project: they live in `.claude/agents/` and are only available when you work in this
repository.

## What's here
```
.claude/agents/        15 agent definitions (one Markdown file each)
CLAUDE.md              Project rules every agent follows (outputs, citations, confidentiality)
context/ges-profile.md Shared GES + industry context - review and correct this first
deals/<target>/        Created per target; each agent writes its numbered memo here
research/              Market and thesis research not tied to one target
```

## The agents
| # | Agent | Role |
|---|---|---|
| 1 | `corp-dev-orchestrator` | Head of Corp Dev; runs a deal and delegates |
| 2 | `deal-sourcing-analyst` | Long lists, screening, target profiles |
| 3 | `exhibitions-industry-analyst` | Market, trends, competitors |
| 4 | `event-tech-specialist` | Registration, lead retrieval, event apps, data |
| 5 | `commercial-dd-customer-voice` | Organizer / exhibitor view, customer risk |
| 6 | `labor-venue-specialist` | Union labor, venue exclusives, operations |
| 7 | `valuation-analyst` | DCF, comps, precedents, offer range |
| 8 | `qoe-financial-diligence` | Normalized EBITDA, working capital, debt-like items |
| 9 | `legal-contracts-antitrust` | Contracts, change of control, antitrust, deal terms |
| 10 | `cyber-tech-diligence` | Security, privacy, tech stack |
| 11 | `integration-synergy-lead` | Synergies, 100-day plan |
| 12 | `cfo-lens` | Funding, leverage, covenants |
| 13 | `pe-sponsor-lens` | Value-creation plan, returns, exit |
| 14 | `devils-advocate` | The case against the deal |
| 15 | `chief-of-staff-synthesizer` | One-page executive recommendation |

## How to use them (Claude Code)
Open this repository in Claude Code (terminal, desktop app, or claude.ai/code). Then either:

- **Ask naturally** — Claude picks the right agent from its description:
  "Build a long list of event-tech companies GES could acquire."
- **Name the agent** — "Use the devils-advocate agent on deals/acme-events."
- **Run the whole team** — start the session as the orchestrator, which delegates to the others:
  ```bash
  claude --agent corp-dev-orchestrator
  ```
  Then: "Evaluate Acme Events as an acquisition target."

Type `/agents` in Claude Code to view or edit them.

## Using them from the Claude Agent SDK
The Agent SDK can load the same project agents and `CLAUDE.md` when you enable project
settings (`setting_sources=["project"]` in Python, `settingSources: ['project']` in
TypeScript) and set the working directory to this repository. See the
[Agent SDK docs](https://docs.claude.com/en/docs/agent-sdk/overview).

## Before first use
1. Review `context/ges-profile.md` and correct anything marked **VERIFY** (ownership,
   business units, size band for targets).
2. Decide whether confidential deal documents may be stored in this repository. If not,
   keep `deals/` local or add it to `.gitignore`.
