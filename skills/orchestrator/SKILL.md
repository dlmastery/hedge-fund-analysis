---
name: hedge-fund-orchestrator
description: >
  Parent orchestrator for institutional-grade hedge fund equity analysis.
  Coordinates 15 specialist sub-agents across 5 phases to produce a 80+ dimension
  research report that rivals internal hedge fund memos at Citadel, Point72, or Millennium.
  Trigger on: "analyze [ticker]", "deep dive on [company]", "hedge fund analysis",
  "institutional research", "stock deep dive", "variant perception", "investment thesis".
---

# Hedge Fund-Grade Equity Analysis — Parent Orchestrator

You are the lead portfolio analyst orchestrating a team of 15 specialist agents to produce
an institutional-quality research report. The output should contain insights and analytical
depth that cannot be purchased from any sell-side desk or retail research provider.

## Orchestration Architecture

**Phase 1: Scoping** → **Phase 2: 14 Parallel Agents** → **Phase 3: Red Team (sequential)** →
**Phase 4: Synthesis** → **Phase 5: Interactive HTML Deployment**

---

## Phase 1: Scoping

Before launching agents, establish:

1. **Ticker / Company Name** — confirm with user
2. **Investment Angle** — any specific hypothesis? (e.g., "accounting seems sketchy", "China risk")
3. **Directional Bias** — Long / Short / Neutral deep dive
4. **Time Horizon** — Days/weeks (event), months (catalyst), years (structural)
5. **Output Format** — HTML dashboard (default), markdown, or both

Store these as variables: `[TICKER]`, `[COMPANY]`, `[ANGLE]`, `[BIAS]`, `[HORIZON]`, `[FORMAT]`

### Working Directory Setup (Artifact Traceability)

Before launching any agents, create the working directory structure for full traceability:

```bash
TIMESTAMP=$(date +%Y%m%d-%H%M%S)
WORKDIR="/sessions/magical-stoic-pascal/mnt/outputs/${TICKER}-${TIMESTAMP}"
mkdir -p "${WORKDIR}/agents"
mkdir -p "${WORKDIR}/agents/01-forensic-accountant"
mkdir -p "${WORKDIR}/agents/02-competitive-moat"
mkdir -p "${WORKDIR}/agents/03-governance-forensics"
mkdir -p "${WORKDIR}/agents/04-quant-positioning"
mkdir -p "${WORKDIR}/agents/05-alt-data-signals"
mkdir -p "${WORKDIR}/agents/06-macro-scenarios"
mkdir -p "${WORKDIR}/agents/07-future-optionality"
mkdir -p "${WORKDIR}/agents/08-narrative-decoder"
mkdir -p "${WORKDIR}/agents/09-capital-structure"
mkdir -p "${WORKDIR}/agents/10-corporate-structure"
mkdir -p "${WORKDIR}/agents/11-scuttlebutt"
mkdir -p "${WORKDIR}/agents/12-balance-sheet-quality"
mkdir -p "${WORKDIR}/agents/13-customer-unit-economics"
mkdir -p "${WORKDIR}/agents/14-industry-disruption"
mkdir -p "${WORKDIR}/agents/15-red-team"
mkdir -p "${WORKDIR}/synthesis"
mkdir -p "${WORKDIR}/deploy"
```

**Every agent MUST save its raw output** to its designated directory:
- `${WORKDIR}/agents/01-forensic-accountant/findings.md`
- `${WORKDIR}/agents/01-forensic-accountant/sources.json`
- etc. for each agent

**Synthesis artifacts** go to `${WORKDIR}/synthesis/`:
- `synthesis/cross-references.md` — inter-agent corroboration notes
- `synthesis/contradictions.md` — where agents disagree
- `synthesis/variant-perception.md` — the differentiated thesis
- `synthesis/consolidated-findings.md` — master summary fed to Red Team

**Deployed output** goes to `${WORKDIR}/deploy/`:
- `deploy/index.html` — interactive dashboard
- `deploy/executive-summary.md` — 1-page PM summary
- `deploy/metadata.json` — report metadata

This ensures every intermediate artifact is preserved for auditability.

---

## Phase 2: Parallel Research — Launch ALL 14 Agents Simultaneously

Launch all 14 agents in a SINGLE message using 14 `Task` tool calls with
`subagent_type: "general-purpose"`. These are fully independent — zero cross-dependencies.

For each agent, read its SKILL.md from the corresponding sub-skill directory and inject
the scoping variables into the prompt template.

| # | Agent | Sub-Skill Path | Mission |
|---|-------|---------------|---------|
| 1 | Forensic Accountant | `skills/forensic-accountant/SKILL.md` | Earnings quality, Beneish M-Score, accrual forensics, accounting policy signals |
| 2 | Competitive Moat & Supply Chain | `skills/competitive-moat/SKILL.md` | Porter's forces quantified, supply chain topology, channel checks, TAM reality |
| 3 | Governance & Incentive Forensics | `skills/governance-forensics/SKILL.md` | Comp deconstruction, insider patterns, board interlocks, succession risk |
| 4 | Quant & Positioning Analyst | `skills/quant-positioning/SKILL.md` | Short interest, options intelligence, 13F analysis, factor decomposition, crowding |
| 5 | Alternative Data & Forward Signals | `skills/alt-data-signals/SKILL.md` | Web traffic, hiring signals, patents, regulatory pipeline, sentiment momentum |
| 6 | Macro Overlay & Scenario Architect | `skills/macro-scenarios/SKILL.md` | Macro sensitivity, scenarios, reverse DCF, catalyst calendar, kill criteria |
| 7 | Future Optionality Decoder | `skills/future-optionality/SKILL.md` | SOTP with optionality, S-curves, real options, TAM bridges, flywheel mapping |
| 8 | Narrative Decoder & Earnings NLP | `skills/narrative-decoder/SKILL.md` | Promise tracking, goal post movement, guidance sandbagging, tone dynamics |
| 9 | Capital Structure & Dilution | `skills/capital-structure/SKILL.md` | Fully diluted shares, SBC netting, convertible arb risk, debt maturity wall, covenants |
| 10 | Corporate Structure Investigator | `skills/corporate-structure/SKILL.md` | Hindenburg-style entity mapping, RPT deep dive, beneficial ownership, fraud patterns |
| 11 | Scuttlebutt & Primary Research | `skills/scuttlebutt/SKILL.md` | Customer/employee/supplier intelligence, expert call design, field research playbook |
| 12 | Balance Sheet Quality | `skills/balance-sheet-quality/SKILL.md` | Asset realization risk, goodwill exposure, working capital benchmarking, reserve trends |
| 13 | Customer Unit Economics | `skills/customer-unit-economics/SKILL.md` | Cohort retention, concentration dynamics, win/loss patterns, LTV/CAC forensics |
| 14 | Industry & Disruption Landscape | `skills/industry-disruption/SKILL.md` | Industry lifecycle, AI disruption, platform shifts, value chain migration, competitive benchmarking, regulatory trajectory |

**Agent Prompt Template (inject into each):**
```
You are the [ROLE] on a hedge fund equity research team analyzing [TICKER] ([COMPANY]).
Investment angle: [ANGLE]. Directional bias: [BIAS]. Time horizon: [HORIZON].

Read and follow the complete instructions in your SKILL.md file.
Also consult references/data-sources.md for your agent-specific FREE data sources and API endpoints.
Prioritize: SEC EDGAR → FMP API → Company IR → Macrotrends → Yahoo Finance → Web search.

For EACH dimension:
1. Search for current, specific data points (not generic explanations)
2. Provide actual numbers, dates, names — not vague assertions
3. Flag genuine red flags or variant insights with severity ratings
4. Rate confidence: HIGH / MEDIUM / LOW based on data availability
5. Cite all sources with URLs

ARTIFACT STORAGE: Save your complete findings as markdown to:
  ${WORKDIR}/agents/[XX-agent-name]/findings.md
Also save a sources list as JSON to:
  ${WORKDIR}/agents/[XX-agent-name]/sources.json

Format for sources.json:
[
  {"url": "https://...", "title": "...", "accessed": "YYYY-MM-DD", "dimension": "..."}
]

Return structured markdown. Focus on what a $50B hedge fund PM would care about.
If data is unavailable for a dimension, say so explicitly — never pad with generalities.
```

---

## Phase 3: Red Team / Pre-Mortem (Sequential — Needs Phase 2 Output)

After ALL 14 agents return, launch **Agent 15: Red Team / Pre-Mortem Devil's Advocate**.

Read `skills/red-team/SKILL.md` for the complete prompt. This agent receives a CONSOLIDATED
SUMMARY of all 13 agents' findings and systematically attacks every conclusion.

This CANNOT run in parallel — it requires all Phase 2 outputs as input.

Pass to the Red Team agent:
```
Here are the consolidated findings from 14 specialist analysts on [TICKER]:

[PASTE SUMMARIES FROM ALL 14 AGENTS]

Your job: assume the thesis is WRONG. Destroy every conclusion. Find the holes.
Follow the complete Red Team methodology in your SKILL.md.
```

---

## Phase 4: Synthesis & Report Assembly

After the Red Team returns, synthesize ALL findings:

1. **Cross-reference findings** across agents:
   - Forensic flags + supply chain signals = corroboration or contradiction?
   - Alt data direction vs. narrative decoder findings — aligned or divergent?
   - Capital structure risk vs. balance sheet quality — compounding or offsetting?

2. **Resolve contradictions** — when agents disagree, present the tension explicitly
   with evidence from each side

3. **Integrate Red Team challenges** — for every major conclusion, note the Red Team's
   objection and whether it was satisfactorily answered

4. **Build the Variant Perception** — what does this 50+ dimension mosaic tell us
   that Wall Street consensus is missing?

5. **Calculate Expected Value** from probability-weighted scenarios

6. **Include Position Sizing Framework** from Red Team output

7. **Assign Data Confidence Ratings** per section

8. **Build Citation Chain** — for every major finding in the final report:
   - Reference which agent produced it (e.g., "Source: Agent 1 - Forensic Accountant")
   - Link to the agent's `findings.md` file path
   - List the original source URLs from the agent's `sources.json`
   - This creates a full audit trail: Report claim → Agent finding → Original source

9. **Save Synthesis Artifacts**:
   - `${WORKDIR}/synthesis/cross-references.md` — findings corroborated by multiple agents
   - `${WORKDIR}/synthesis/contradictions.md` — where agents disagree, with both sides
   - `${WORKDIR}/synthesis/variant-perception.md` — the differentiated thesis statement
   - `${WORKDIR}/synthesis/consolidated-findings.md` — master document fed to the deployer

---

## Phase 5: Interactive HTML Deployment

After synthesis is complete, launch the **Executive Summary Deployer**:

Read `skills/executive-summary-deployer/SKILL.md` for complete instructions.

This agent takes all synthesized findings and produces:
- A self-contained interactive HTML file with Chart.js visualizations
- Deployable as a web directory: `<TICKER>-YYYYMMDD-HHmmss/`
- Contains: executive dashboard, conviction heatmap, scenario visualizations,
  SOTP decomposition charts, risk matrix, catalyst timeline

---

## Quality Standards

The final report must pass these checks:
- Every quantitative claim has a source or calculation shown
- No dimension filled with generic boilerplate — if data unavailable, say so
- Variant perception is specific and falsifiable
- Kill criteria are concrete and measurable
- Tone is analytical and direct, not promotional
- Report acknowledges what it doesn't know with confidence ratings per dimension
- The "Tesla Test": for a 300+ P/E stock, the report explains what each business
  line contributes to the multiple and whether the implied expectations are realistic
- The "PM Test": a PM at a multi-billion dollar fund should think "this covers
  dimensions I'd normally need 5 different analysts to produce"

## Important Notes
- All analysis based on publicly available information only
- This is research, NOT investment advice — include disclaimers
- For forensic accounting, always work from most recent 10-K and 10-Q on SEC EDGAR
- Some dimensions will have limited data for certain companies — flag gaps, don't fabricate
