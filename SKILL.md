---
name: hedge-fund-analysis
description: >
  Produce institutional-grade, hedge-fund-quality deep research reports on any public equity.
  Orchestrates 15 specialist AI agents across 80+ analytical dimensions — forensic accounting,
  competitive moat, governance forensics, quant positioning, alternative data, macro scenarios,
  future optionality decoding, narrative forensics, capital structure, corporate structure
  investigation, scuttlebutt research, balance sheet quality, customer unit economics,
  industry & disruption landscape (AI disruption, platform shifts, value chain migration),
  and red-team/pre-mortem analysis. Generates an interactive HTML dashboard deployable
  as a web directory (<TICKER>-YYYYMMDD-HHmmss/). Use this skill for deep stock analysis,
  hedge fund style research, institutional equity research, variant perception analysis,
  investment thesis, or any request implying more than surface-level research.
---

# Hedge Fund-Grade Equity Analysis System

This is a **decomposed multi-skill system**. The parent orchestrator coordinates 14
specialist sub-skills, each with its own SKILL.md containing complete instructions.

## Quick Start

To run this system, read and follow: `skills/orchestrator/SKILL.md`

## Architecture

```
hedge-fund-analysis/
├── SKILL.md                              ← You are here (entry point)
├── skills/
│   ├── orchestrator/SKILL.md             ← Parent orchestrator (read this first)
│   ├── forensic-accountant/SKILL.md      ← Agent 1: Earnings quality, Beneish, accruals
│   ├── competitive-moat/SKILL.md         ← Agent 2: Porter's, supply chain, TAM, channels
│   ├── governance-forensics/SKILL.md     ← Agent 3: Comp, insiders, board, succession
│   ├── quant-positioning/SKILL.md        ← Agent 4: Short interest, options, 13F, crowding
│   ├── alt-data-signals/SKILL.md         ← Agent 5: Web traffic, hiring, patents, sentiment
│   ├── macro-scenarios/SKILL.md          ← Agent 6: Scenarios, reverse DCF, catalysts, kills
│   ├── future-optionality/SKILL.md       ← Agent 7: SOTP, S-curves, real options, flywheels
│   ├── narrative-decoder/SKILL.md        ← Agent 8: Promise tracking, tone, goal posts
│   ├── capital-structure/SKILL.md        ← Agent 9: Dilution, debt wall, covenants, SBC
│   ├── corporate-structure/SKILL.md      ← Agent 10: Hindenburg-style entity forensics
│   ├── scuttlebutt/SKILL.md              ← Agent 11: Customer/employee/supplier intel
│   ├── balance-sheet-quality/SKILL.md    ← Agent 12: Asset risk, goodwill, working capital
│   ├── customer-unit-economics/SKILL.md  ← Agent 13: Cohorts, LTV/CAC, concentration
│   ├── industry-disruption/SKILL.md      ← Agent 14: AI disruption, platform shifts, value chain
│   ├── red-team/SKILL.md                 ← Agent 15: Pre-mortem, thesis destruction
│   └── executive-summary-deployer/SKILL.md ← HTML dashboard generator & deployer
└── references/
    ├── report-template.md                ← HTML report section structure reference
    ├── differentiation-checklist.md      ← Quality checklist vs retail research
    └── agent-prompts.md                  ← Legacy monolithic prompts (superseded by sub-skills)
```

## Execution Flow

1. **Phase 1 — Scoping**: Collect ticker, angle, bias, horizon from user
2. **Phase 2 — Parallel Research**: Launch 14 agents simultaneously (zero cross-dependencies)
3. **Phase 3 — Red Team**: Agent 15 receives all findings and attacks every conclusion
4. **Phase 4 — Synthesis**: Cross-reference, resolve contradictions, build variant perception
5. **Phase 5 — Deploy**: Generate interactive HTML dashboard in `<TICKER>-YYYYMMDD-HHmmss/`

## Working Directory Structure (per analysis run)

Each run creates a timestamped directory with full artifact traceability:

```
<TICKER>-YYYYMMDD-HHmmss/
├── agents/
│   ├── 01-forensic-accountant/
│   │   ├── findings.md
│   │   └── sources.json
│   ├── 02-competitive-moat/
│   │   ├── findings.md
│   │   └── sources.json
│   ├── ... (03 through 13)
│   ├── 14-industry-disruption/
│   │   ├── findings.md
│   │   └── sources.json
│   └── 15-red-team/
│       ├── findings.md
│       └── sources.json
├── synthesis/
│   ├── cross-references.md
│   ├── contradictions.md
│   ├── variant-perception.md
│   └── consolidated-findings.md
└── deploy/
    ├── index.html              ← Interactive dashboard
    ├── executive-summary.md    ← 1-page PM summary
    └── metadata.json           ← Report metadata
```

## Analytical Dimensions (50+)

| # | Dimension | Agent |
|---|-----------|-------|
| 1 | Beneish M-Score & Sloan Accrual Ratio | Forensic Accountant |
| 2 | Revenue recognition forensics (DSO, deferred revenue) | Forensic Accountant |
| 3 | Off-balance-sheet exposure quantification | Forensic Accountant |
| 4 | Cash flow forensics & CapEx classification | Forensic Accountant |
| 5 | Working capital manipulation detection | Forensic Accountant |
| 6 | Accounting policy choice signals (NEW) | Forensic Accountant |
| 7 | Porter's Five Forces quantified | Competitive Moat |
| 8 | Supply chain topology & single-point failures | Competitive Moat |
| 9 | Supply chain ESG & compliance risk (NEW) | Competitive Moat |
| 10 | Channel check synthesis | Competitive Moat |
| 11 | TAM/SAM/SOM reality check | Competitive Moat |
| 12 | Geographic revenue concentration risk (NEW) | Competitive Moat |
| 13 | Executive comp deconstruction & incentive alignment | Governance |
| 14 | Insider transaction PATTERN analysis | Governance |
| 15 | Board interlocks & succession risk | Governance |
| 16 | Capital allocation track record (words vs. deeds) | Governance |
| 17 | Short interest dynamics & squeeze risk | Quant Positioning |
| 18 | Options intelligence (skew, term structure, unusual activity) | Quant Positioning |
| 19 | 13F institutional flow analysis | Quant Positioning |
| 20 | Crowding analysis — factor-level & position overlap (NEW) | Quant Positioning |
| 21 | Factor exposure decomposition | Quant Positioning |
| 22 | Earnings reaction analysis (implied vs. actual) | Quant Positioning |
| 23 | Web traffic & digital footprint | Alt Data |
| 24 | Job posting & hiring signal analysis | Alt Data |
| 25 | Patent filing & product roadmap signals (NEW) | Alt Data |
| 26 | Litigation pipeline with financial impact | Alt Data |
| 27 | Geopolitical exposure mapping | Alt Data |
| 28 | Micro-transaction & payment signals (NEW) | Alt Data |
| 29 | Macro sensitivity mapping (rates, dollar, commodities) | Macro Scenarios |
| 30 | Probability-weighted scenario analysis | Macro Scenarios |
| 31 | Reverse DCF implied assumptions | Macro Scenarios |
| 32 | Catalyst calendar with probability & magnitude | Macro Scenarios |
| 33 | Historical analogue analysis & base rates | Macro Scenarios |
| 34 | Kill criteria (specific, measurable) | Macro Scenarios |
| 35 | Sum-of-the-parts with optionality pricing | Future Optionality |
| 36 | S-curve positioning for each business line | Future Optionality |
| 37 | TAM bridge analysis per business line | Future Optionality |
| 38 | Real options valuation framework | Future Optionality |
| 39 | Network effects & flywheel mapping | Future Optionality |
| 40 | Comparable optionality pricing (historical analogues) | Future Optionality |
| 41 | Earnings call language evolution & tone dynamics | Narrative Decoder |
| 42 | Promise tracking ledger (3+ years) | Narrative Decoder |
| 43 | Goal post movement detection | Narrative Decoder |
| 44 | Guidance sandbagging score | Narrative Decoder |
| 45 | Fully diluted share count reconstruction | Capital Structure |
| 46 | SBC dilution vs. buyback netting | Capital Structure |
| 47 | Debt maturity wall & refinancing risk (NEW enhanced) | Capital Structure |
| 48 | Covenant headroom analysis | Capital Structure |
| 49 | Share supply calendar | Capital Structure |
| 50 | Hindenburg-style entity structure mapping | Corporate Structure |
| 51 | Related-party transaction deep dive & cash leakage | Corporate Structure |
| 52 | Fraud pattern matching (Enron, Wirecard, Luckin, Adani) | Corporate Structure |
| 53 | Glassdoor/review synthesis & employee morale index | Scuttlebutt |
| 54 | Expert network call design (top 10 calls) | Scuttlebutt |
| 55 | Win/loss pattern analysis (NEW) | Scuttlebutt |
| 56 | Goodwill & intangible impairment risk | Balance Sheet Quality |
| 57 | Working capital quality vs. peer benchmarks (NEW) | Balance Sheet Quality |
| 58 | Reserve adequacy & trend analysis (NEW) | Balance Sheet Quality |
| 59 | Hidden & unrecognized asset discovery | Balance Sheet Quality |
| 60 | Customer concentration dynamics | Customer Unit Economics |
| 61 | Cohort retention & NRR tracking (NEW) | Customer Unit Economics |
| 62 | LTV/CAC forensics (NEW) | Customer Unit Economics |
| 63 | Pricing power assessment (NEW) | Customer Unit Economics |
| 64 | Industry lifecycle stage assessment | Industry & Disruption |
| 65 | Secular trend mapping (5-10 year) | Industry & Disruption |
| 66 | AI/ML disruption analysis (threat + opportunity + infrastructure) | Industry & Disruption |
| 67 | Technology platform shift detection (cloud, edge, quantum, robotics) | Industry & Disruption |
| 68 | Adjacent industry disruption & contagion | Industry & Disruption |
| 69 | Value chain migration analysis | Industry & Disruption |
| 70 | Competitive deep benchmarking matrix (quantitative) | Industry & Disruption |
| 71 | Industry consolidation & M&A cycle | Industry & Disruption |
| 72 | Regulatory regime evolution trajectory | Industry & Disruption |
| 73 | Industry technology roadmap & standards evolution | Industry & Disruption |
| 74 | Geopolitical reshoring & supply chain reorganization | Industry & Disruption |
| 75 | ESG as industry structural force | Industry & Disruption |
| 76 | Industry expert consensus vs. variant view | Industry & Disruption |
| 77 | Pre-mortem failure narratives (top 5) | Red Team |
| 78 | Confirmation bias audit | Red Team |
| 79 | Multi-order risk chain mapping | Red Team |
| 80 | Position sizing & Kelly criterion | Red Team |
| 81 | Monitoring dashboard design | Red Team |

## Installation

See `INSTALL.md` for instructions on installing this skill system on a new machine.
