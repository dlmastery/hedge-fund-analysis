# Hedge Fund-Grade Equity Research Report Template

Use this exact structure for the final HTML report output. Every section below must appear.
If data is unavailable for a section, include the section header with a note explaining
the data gap and its implications.

---

## HTML Report Structure

The report should be a single self-contained HTML file with embedded CSS and JavaScript.
Use a clean, professional design — think Bloomberg terminal meets modern dashboard.
Dark mode optional but preferred for the "institutional" feel.

### Header Section
```
[COMPANY NAME] ([TICKER]) — Institutional Deep Dive
Report Date: [DATE]
Analyst Team: Automated Multi-Agent System
Classification: INTERNAL USE ONLY — NOT INVESTMENT ADVICE
```

### Executive Dashboard (visible on load, no scrolling needed)

A compact grid showing:

| Metric | Value |
|--------|-------|
| Current Price | $XX.XX |
| Market Cap | $XX.XB |
| 52-Week Range | $XX - $XX |
| Variant View | LONG / SHORT / NEUTRAL |
| Conviction Level | HIGH / MEDIUM / LOW |
| Expected Value (probability-weighted) | $XX.XX (XX% upside/downside) |
| Primary Catalyst | [description] — [date] |
| Primary Risk | [description] |
| Thesis in One Sentence | [sentence] |

### Conviction Heatmap

A visual grid showing each analysis dimension with a color-coded indicator:

- GREEN = Supports thesis / no issues found
- YELLOW = Mixed signals / moderate concern
- RED = Contradicts thesis / significant risk

Display as a compact visual grid, not a long list.

### Section 1: Variant Perception & Thesis

**This is the most important section.** It must answer:
1. What does consensus believe about this stock? (Be specific — cite analyst consensus
   price targets, the narrative on the street)
2. Where specifically is consensus wrong?
3. What is our differentiated view and what evidence supports it?
4. What is the magnitude of the mispricing if we're right?

This section should be 300-500 words max. Dense, specific, no filler.

### Section 2: Forensic Accounting & Earnings Quality

Structure:
- Earnings Quality Score: [1-10 with explanation]
- Beneish M-Score: [calculated value and interpretation]
- Sloan Accrual Ratio: [calculated value and trend]
- Key Findings (3-5 bullet points, each with data)
- Red Flags (if any, with severity rating)
- Detailed Analysis (expandable/collapsible)

### Section 3: Competitive Position & Supply Chain

Structure:
- Moat Rating: [WIDE / NARROW / NONE with justification]
- Supply Chain Risk Score: [1-10]
- Key Findings
- Porter's Five Forces (quantified)
- Supply Chain Map (text-based topology)
- Channel Check Summary
- Competitive Threat Matrix

### Section 4: Governance & Management Quality

Structure:
- Management Quality Score: [1-10]
- Alignment Score: [1-10 — how well are incentives aligned with shareholders?]
- Key Findings
- Comp Structure Analysis
- Insider Transaction Pattern
- Capital Allocation Report Card
- Guidance Accuracy Track Record

### Section 5: Market Positioning & Flows

Structure:
- Positioning Summary (bullish/bearish/neutral based on data)
- Short Interest Analysis
- Institutional Ownership Dynamics
- Options Market Signals
- Factor Exposure Profile
- Technical Regime

### Section 6: Alternative Data & Forward Signals

Structure:
- Signal Direction: [BULLISH / BEARISH / MIXED]
- Leading Indicators Summary
- By Signal Type:
  - Digital Footprint
  - Hiring Signals
  - IP/Patent Activity
  - Regulatory Pipeline
  - Litigation Exposure
  - Geopolitical Risk Map
  - Sentiment Momentum

### Section 7: Future Optionality & Embedded Value Decomposition

**This section is CRITICAL for high-multiple stocks.** A stock at 50+ P/E cannot be
understood through backward-looking analysis alone. This section decodes what the
market is actually paying for.

Structure:
- **Current P/E and what it implies**: "At [X]x earnings, the market is pricing in [Y]"
- **Sum-of-the-Parts Decomposition Table**:

| Business Line | Current Rev | Growth Rate | Standalone Value | % of Mkt Cap | Probability of Scale | Status |
|---|---|---|---|---|---|---|
| Core Business | $XB | X% | $XB | X% | HIGH | Proven |
| Growth Line 1 | $XM | X% | $XB | X% | MEDIUM | Scaling |
| Future Bet 1 | $0 | N/A | $XB | X% | LOW | Pre-revenue |
| Future Bet 2 | $0 | N/A | $XB | X% | SPECULATIVE | Concept |
| **Total** | | | **$XB** | **X%** | | |
| **Optionality Premium** | | | **$XB** | **X%** | | Unproven value |

- **S-Curve Position Map**: For each business line, where on the adoption curve:
  - Early Innovators (0-2% penetration)
  - Early Majority (2-16%)
  - Growth Inflection (16-50%)
  - Late Majority (50-84%)
  - Saturation (84%+)

- **Execution Milestone Tracker**: Promise vs. delivery for each growth initiative
- **Network Effects / Flywheel Diagram**: Map the feedback loops visually
- **Optionality Value Summary**: Real options framework assessment
- **Comparable Optionality Pricing**: Historical analogues of similar pricing
- **Implied Expectations Reality Check**: What has to go right for the current price to be justified?

### Section 7B: Management Narrative Decoder

Structure:
- **Narrative Credibility Score**: [1-10]
- **Promise Tracking Ledger** (table of major promises vs. outcomes over 3+ years)
- **Goal Post Movement Tracker** (instances where metrics/definitions were changed)
- **Language Shift Analysis**: Key phrase evolution across recent earnings calls
- **Guidance Sandbagging Score**: Beat rate, average magnitude, trend
- **Competitive Acknowledgment Trend**: How they talk about competition over time
- **Forward Guidance Framing**: Optimism index trend

### Section 7C: Capital Structure & Dilution Risk

Structure:
- **Dilution Risk Score**: [1-10, where 10 = severe dilution risk]
- **Share Count Table**:

| Category | Shares | % of Basic |
|---|---|---|
| Basic Shares Outstanding | X | 100% |
| + Stock Options (in-the-money) | X | X% |
| + RSUs/PSUs (unvested) | X | X% |
| + Convertible Instruments | X | X% |
| + Warrants | X | X% |
| = **Fully Diluted Shares** | **X** | **X%** |
| **Dilution Gap** | | **X%** |

- **SBC Dilution vs. Buyback**: Net share count change trend (is the company actually shrinking shares?)
- **Share Supply Calendar**: Timeline of upcoming dilution events
- **Debt Maturity Wall**: Visual of upcoming maturities
- **Covenant Headroom Analysis**
- **Capital Needs Assessment**: Does the company need to raise? When? How much dilution?

### Section 7D: Corporate Structure & Ownership Forensics

Structure:
- **Structural Complexity Score**: [1-10, where 10 = Enron-level complexity]
- **Entity Map Summary**: Number of entities, jurisdictional breakdown, opacity flags
- **Related-Party Transaction Summary**: Top related-party flows with amounts
- **Beneficial Ownership Flags**: Pledged shares, circular ownership, VIE risks
- **Governance Lock Analysis**: Voting power concentration, anti-takeover provisions
- **Fraud Pattern Match**: Comparison to known fraud structures (flag or clear)

### Section 7E: Scuttlebutt & Ground-Level Intelligence

Structure:
- **Customer Satisfaction Trend**: Glassdoor, reviews, NPS proxies
- **Employee Morale Index**: Glassdoor rating, Blind sentiment, hiring/attrition signals
- **Supplier Relationship Health**: Payment practices, order volume signals
- **Competitive Ground Truth**: What customers and employees say vs. what management claims
- **Primary Research Playbook**: Top 10 expert calls designed, field research opportunities
- **Lynch/Fisher Verdict**: Would customers/employees/suppliers/competitors be bullish?

### Section 8: Scenario Analysis & Valuation

Structure:
- Probability-Weighted Expected Value: $XX.XX
- Scenario Table:

| Scenario | Probability | Target Price | Key Assumptions |
|----------|-------------|-------------|-----------------|
| Bull | XX% | $XX | [assumptions] |
| Base | XX% | $XX | [assumptions] |
| Bear | XX% | $XX | [assumptions] |
| Tail Risk | XX% | $XX | [assumptions] |

- Reverse DCF Implied Assumptions
- Comparable Transaction Multiples
- Historical Analogue Analysis
- Visual: Outcome distribution chart (can be text-based bar chart)

### Section 9: Catalyst Calendar

Chronological list:

| Date | Event | Direction | Magnitude | Probability |
|------|-------|-----------|-----------|-------------|
| [date] | [event] | UP/DOWN/UNCERTAIN | LOW/MED/HIGH | XX% |

### Section 10: Risk Matrix

2x2 grid: Probability (Low/High) vs. Impact (Low/High)

Place each identified risk in the appropriate quadrant. Color-code by category
(financial, operational, regulatory, geopolitical, competitive).

### Section 11: Red Team / Pre-Mortem Challenge

**This section contains the DEVIL'S ADVOCATE analysis.** Every bull and bear argument
gets stress-tested. This is the section that prevents groupthink.

Structure:
- **Pre-Mortem Narratives**: 5 plausible "what killed the investment" stories
- **Confirmation Bias Audit**: For each major finding, the counter-evidence
- **Thesis Destruction**: Bull and bear arguments systematically attacked
- **Crowded Trade Assessment**: Is this a consensus position?
- **Risk Chain Analysis**: 3 multi-order risk chains mapped out
- **Model Sensitivity**: 3 most sensitive assumptions and what happens if wrong
- **Base Rate Reality Check**: Historical success rates for similar theses
- **Senior PM Skepticism Triggers**: Top 5 things that would make a PM skeptical

### Section 12: Position Sizing & Risk Framework

Structure:
- **Conviction Level**: HIGH / MEDIUM / LOW / PASS
- **Recommended Position Size**: Full / Half / Tracking / None (with rationale)
- **Kelly Criterion Estimate** (if sufficient data)
- **Liquidity-Adjusted Max Position**: Based on ADV and market impact
- **Entry Strategy**: Immediate / scale-in / wait-for-catalyst
- **Stop-Loss Framework**: Price-based, thesis-based, and time-based triggers
- **Hedging Recommendations**: Options overlay, pair trade, sector hedge specifics
- **Monitoring Dashboard**: What to check daily / weekly / quarterly / per earnings

### Section 13: Kill Criteria

Numbered list of 3-5 specific, measurable conditions that would invalidate the thesis.
Each must include:
- The metric
- The threshold
- The monitoring frequency
- What action to take if triggered

Example: "If organic revenue growth falls below 3% for 2 consecutive quarters
(monitored quarterly via 10-Q), exit the position regardless of price action."

### Section 14: Data Confidence Assessment

For each major section, rate:
- Data availability: HIGH / MEDIUM / LOW
- Data recency: [most recent data point date]
- Confidence in conclusions: HIGH / MEDIUM / LOW
- Key data gaps: [what we couldn't find]

### Section 15: Sources & Methodology

Complete list of all sources cited in the report, organized by section.
Include URLs, dates accessed, and brief description of what was sourced.

---

## Formatting Notes

- Use collapsible `<details>` tags for detailed analysis sections so the report
  is scannable at the summary level
- Include a floating table of contents for navigation
- Use monospace font for financial data and tables
- Color scheme: dark background (#1a1a2e or similar), green for positive signals,
  red for negative, amber for mixed
- All charts/visualizations should be CSS-based or inline SVG — no external dependencies
- Total report should render in a single HTML file under 500KB
- Include a print-friendly stylesheet via @media print

## Executive Summary (separate file)

Generate a separate markdown file called `executive-summary.md` that contains:
- Company name, ticker, date
- One-sentence thesis
- Variant perception (2-3 sentences)
- Expected value and key scenario outcomes
- Top 3 catalysts
- Top 3 risks
- Conviction level and recommended position sizing context
- Kill criteria summary

This should fit on one printed page. A PM should be able to read it in under 2 minutes
and decide whether to read the full report.
