# GES M&A Advisory — Project Instructions

This project supports senior leadership at GES (Global Experience Specialists, ges.com) in
finding, evaluating and integrating acquisition targets. The work is advisory: the output is
decision-ready analysis for executives, not production software.

## Before any analysis
- Read `context/ges-profile.md` (company, ownership, industry, strategic theses).
- If a deal folder exists for the target, read everything in `deals/<target-slug>/` first.

## The agent team (`.claude/agents/`)
| Agent | Use it for |
|---|---|
| `corp-dev-orchestrator` | Running a target end to end; routing work to the others |
| `deal-sourcing-analyst` | Long lists, screening, target profiles |
| `exhibitions-industry-analyst` | Market sizing, trends, competitive landscape |
| `event-tech-specialist` | Registration, lead retrieval, event apps, data platforms |
| `commercial-dd-customer-voice` | Organizer and exhibitor buying behaviour, customer risk |
| `labor-venue-specialist` | Union jurisdictions, venue exclusives, show-floor operations |
| `valuation-analyst` | DCF, comps, precedent deals, accretion, offer range |
| `qoe-financial-diligence` | Quality of earnings, normalized EBITDA, working capital |
| `legal-contracts-antitrust` | Contract terms, change-of-control, antitrust, deal terms |
| `cyber-tech-diligence` | Security, privacy (attendee data), tech stack, tech debt |
| `integration-synergy-lead` | Synergy cases, 100-day plan, integration risk |
| `cfo-lens` | Funding, leverage, covenants, earnings impact |
| `pe-sponsor-lens` | Fit with the sponsor's value-creation plan and exit |
| `devils-advocate` | The strongest case against the deal |
| `chief-of-staff-synthesizer` | One-page executive recommendation |

To run the whole team from one session: `claude --agent corp-dev-orchestrator`.

## Conventions for every agent
- **Write outputs to files.** Per target: `deals/<target-slug>/<NN>-<agent-name>.md`
  (e.g. `deals/acme-events/03-valuation-analyst.md`). Market/theme work goes in `research/`.
- **Cite sources** (URL, document, or "management estimate"). Never invent figures. When a
  number is an assumption, label it `ASSUMPTION` and show the range.
- **State confidence** (High / Medium / Low) on each key finding.
- **End every output** with: *Open questions* and *Hand-offs* (which agent should look next and why).
- Use plain business English for executives; define any jargon on first use.

## Deal room discussion (how agents talk to each other)
Each deal has a shared conversation log: `deals/<target-slug>/discussion.md`.
- **Before working**, read `discussion.md` and answer every open message addressed to you.
- **After writing your memo**, append to `discussion.md` (never edit others' entries):
  ```
  ### [round N] <your-agent-name> → <recipient-agent-name(s) | all>
  **Type:** Finding | Challenge | Question | Reply | Agree | Concede
  <2–6 sentences. Quote the number or claim you are responding to and its file.>
  **Needs answer from:** <agent-name> (or "none")
  ```
- Challenge other agents directly when your evidence conflicts with theirs (e.g. the
  `cfo-lens` disputing the `integration-synergy-lead`'s timing). Be specific, cite files,
  and change your own view when the evidence warrants — say so with **Concede**.
- Open items stay open until the addressed agent replies or the orchestrator closes them.

## Confidentiality
- Deal names, financials and data-room content are confidential and may be material
  non-public information. Do not put them into web searches, external tools or third-party
  services. Use web research only for public information about markets and companies.
- Do not commit data-room documents unless the user confirms the repository is approved for them.
