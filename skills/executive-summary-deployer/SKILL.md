---
name: executive-summary-deployer
description: >
  Generates an interactive HTML executive summary dashboard with Chart.js visualizations,
  packages it for web deployment in format <TICKER>-YYYYMMDD-HHmmss/. Creates a
  self-contained deployable directory with index.html and all assets inline.
---

# Executive Summary Deployer — Interactive HTML Dashboard

You are the final-stage report generator. You receive the synthesized output from all
14 agents and produce a deployable interactive HTML executive summary.

---

## Deployment Format

The output directory MUST be named: `<TICKER>-YYYYMMDD-HHmmss/`

Example: `TSLA-20260309-143022/`

Directory contents:
```
TSLA-20260309-143022/
├── index.html          ← Self-contained interactive dashboard (single file)
├── executive-summary.md ← 1-page text summary for PM quick read
└── metadata.json       ← Report metadata (ticker, date, agents used, confidence)
```

---

## index.html Specification

A **single self-contained HTML file** with ALL CSS and JavaScript inline. No external
dependencies except CDN-hosted Chart.js. Must work offline after initial CDN load.

### Design System
- **Color scheme**: Dark mode institutional (#0d1117 background, #c9d1d9 text)
- **Accent colors**: Green (#3fb950) for bullish, Red (#f85149) for bearish,
  Amber (#d29922) for mixed/warning, Blue (#58a6ff) for neutral data
- **Typography**: System font stack, monospace for financial data
- **Layout**: Responsive grid, works on desktop and tablet

### Required Sections (in order)

#### 1. Executive Dashboard Header (visible without scrolling)
Compact grid showing at-a-glance:
```
[COMPANY NAME] ([TICKER]) — Institutional Deep Dive
Report Date | Analyst: Multi-Agent System (14 Agents)
Classification: INTERNAL USE ONLY — NOT INVESTMENT ADVICE

Current Price: $XX.XX    |  Market Cap: $XX.XB   |  52-Week: $XX - $XX
Variant View: LONG/SHORT |  Conviction: HIGH/MED  |  Expected Value: $XX (XX% upside)
Primary Catalyst: [desc] |  Primary Risk: [desc]
Thesis: [one sentence]
```

#### 2. Conviction Heatmap (Chart.js or CSS Grid)
A visual grid where each analysis dimension is a colored cell:
- **GREEN** = Supports thesis / no issues
- **YELLOW** = Mixed signals / moderate concern
- **RED** = Contradicts thesis / significant risk
- **GRAY** = Insufficient data

Dimensions (14 cells matching agents):
Forensic Accounting | Competitive Moat | Governance | Positioning | Alt Data |
Macro/Scenarios | Future Optionality | Narrative | Capital Structure |
Corporate Structure | Scuttlebutt | Balance Sheet | Customer Economics | Red Team

Each cell clickable to scroll to that section.

#### 3. Scenario Probability Chart (Chart.js Doughnut or Bar)
Visualize the probability-weighted scenarios:
- Bull, Base, Bear, Tail Risk — with probability % and target price
- Expected value overlay line
- Color-coded by scenario type

#### 4. Sum-of-the-Parts Decomposition (Chart.js Horizontal Bar or Stacked Bar)
For high-multiple stocks, show:
- Each business line's estimated value as a bar segment
- "Optionality Premium" as a distinct color
- Current market cap as a reference line
- Percentage labels on each segment

#### 5. S-Curve Position Map (Custom CSS/SVG)
Visual representation of where each business line sits on the adoption curve:
- X-axis: adoption stage (Innovators → Early Majority → Growth → Late → Saturation)
- Each business line plotted as a labeled dot
- Historical analogue overlay if available

#### 6. Catalyst Timeline (Chart.js Timeline or CSS)
Horizontal timeline showing upcoming catalysts:
- Date, event name, direction arrow (up/down), magnitude dot size
- Color-coded by probability
- Current date marker

#### 7. Risk Matrix (CSS Grid or Chart.js Scatter)
2×2 grid: Probability (Low/High) × Impact (Low/High)
- Each risk plotted as a colored dot with label
- Color by category: financial, operational, regulatory, competitive, geopolitical

#### 8. Earnings Reaction History (Chart.js Bar)
Bar chart of last 8 earnings reactions:
- Implied move (gray bar) vs. actual move (colored bar)
- Green for beats, red for misses

#### 9. Share Dilution Waterfall (Chart.js Waterfall/Bar)
Visual of basic shares → fully diluted shares:
- Starting bar: basic shares
- Incremental bars: options, RSUs, convertibles, warrants
- Ending bar: fully diluted count
- Dilution gap % label

#### 10. Promise Tracking Scorecard (HTML Table)
Interactive table from Narrative Decoder:
- Promise | Deadline | Result | Status (✓/✗/⏳)
- Sortable columns
- Color-coded status

#### 11. Pre-Mortem Top 5 (Expandable Cards)
Each failure narrative as a collapsible card:
- Title + probability badge
- Expandable detail with trigger → cascade → outcome

#### 12. Kill Criteria Dashboard (HTML Table)
Numbered criteria with:
- Metric | Threshold | Current Value | Buffer | Status (SAFE/WARNING/TRIGGERED)
- Color-coded proximity to threshold

#### 13. Position Sizing Summary (CSS Card)
- Conviction level badge
- Recommended size
- Entry strategy
- Stop-loss levels
- Hedge recommendation

#### 14. Data Confidence Matrix (CSS Grid)
For each section: data availability, recency, confidence rating, key gaps.
Color-coded cells.

#### 15. Collapsible Detail Sections
Each agent's full analysis in `<details><summary>` tags:
- Collapsed by default for scannability
- Full findings when expanded
- **Each section MUST include a "Sources & Working Documents" footer** with:
  - Link/path to the agent's `findings.md` file
  - Link/path to the agent's `sources.json` file
  - Inline citation count: "Based on X sources"

#### 16. Source Traceability & Citation Index
A dedicated section at the bottom of the report with:
- **Complete source index**: every URL cited across all 14 agents, deduplicated
- **Working document links**: relative paths to all intermediate artifacts:
  ```
  📁 Working Documents
  ├── agents/01-forensic-accountant/findings.md (X sources)
  ├── agents/02-competitive-moat/findings.md (X sources)
  ├── ... (all 14 agents)
  ├── synthesis/cross-references.md
  ├── synthesis/contradictions.md
  ├── synthesis/variant-perception.md
  └── synthesis/consolidated-findings.md
  ```
- **Methodology note**: which agents contributed to each finding
- **Data freshness**: most recent data point date per section
- **Confidence matrix**: data availability × recency × confidence per agent

Every claim in the report should be traceable:
`Finding → Agent findings.md → sources.json → original URL`

#### 17. Floating Table of Contents
Sticky sidebar or top nav with links to each section.
Highlights current section on scroll.

### JavaScript Features
- **Chart.js** loaded from CDN: `https://cdn.jsdelivr.net/npm/chart.js`
- Smooth scroll navigation
- Collapsible sections with toggle animation
- Print-friendly stylesheet via `@media print` (hides nav, expands all sections)
- **Dark/light mode toggle** (optional)
- Responsive breakpoints for mobile/tablet

### Performance Requirements
- Total file size < 500KB
- No external images — use CSS shapes, Chart.js, or inline SVG
- Fast initial render — dashboard visible without waiting for charts

---

## executive-summary.md Specification

A separate markdown file that fits on one printed page. A PM reads it in under 2 minutes
to decide if the full report is worth reading.

Contents:
```
# [COMPANY] ([TICKER]) — Executive Summary
**Date**: [YYYY-MM-DD] | **Conviction**: [HIGH/MED/LOW] | **View**: [LONG/SHORT/NEUTRAL]

## Thesis (1 sentence)
[The single-sentence thesis]

## Variant Perception
[2-3 sentences on what consensus believes and where it's wrong]

## Expected Value
- Probability-weighted target: $XX.XX (XX% upside/downside)
- Bull ($XX, XX%) | Base ($XX, XX%) | Bear ($XX, XX%) | Tail ($XX, XX%)

## Top 3 Catalysts
1. [Event] — [Date] — [Magnitude]
2. ...
3. ...

## Top 3 Risks
1. [Risk] — [Probability] — [Impact]
2. ...
3. ...

## Position Sizing Context
- Size: [Full/Half/Tracking/Pass]
- Entry: [Strategy]
- Stop: [Framework]

## Kill Criteria
1. [Metric] [threshold] for [timeframe] → [action]
2. ...
3. ...

## Data Confidence
[1-2 sentences on overall confidence and key data gaps]
```

---

## metadata.json Specification

```json
{
  "ticker": "[TICKER]",
  "company": "[COMPANY]",
  "reportDate": "YYYY-MM-DDTHH:mm:ssZ",
  "directoryName": "[TICKER]-YYYYMMDD-HHmmss",
  "agentsUsed": 14,
  "dimensions": 50,
  "convictionLevel": "HIGH/MEDIUM/LOW/PASS",
  "variantView": "LONG/SHORT/NEUTRAL",
  "expectedValue": XX.XX,
  "currentPrice": XX.XX,
  "impliedReturn": "XX%",
  "dataConfidence": "HIGH/MEDIUM/LOW",
  "generatedBy": "Hedge Fund Analysis Multi-Agent System v2.0"
}
```

---

## Implementation Notes

1. Generate the directory name using current timestamp:
   ```bash
   DIRNAME="$(echo [TICKER] | tr '[:lower:]' '[:upper:]')-$(date +%Y%m%d-%H%M%S)"
   mkdir -p "/sessions/magical-stoic-pascal/mnt/outputs/$DIRNAME"
   ```

2. Write index.html as a single file with all CSS in `<style>` and JS in `<script>`

3. Use Chart.js for all charts — it's the only external dependency

4. All data for charts should be embedded as JavaScript objects in the HTML

5. Test that the file renders correctly by verifying structure before saving

6. The output directory should be fully deployable — copy to any web server
   (Apache, Nginx, S3 static site) and it works immediately

7. Include the `@media print` stylesheet so the report can be printed cleanly
