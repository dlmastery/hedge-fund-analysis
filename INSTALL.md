# Installation Guide — Hedge Fund-Grade Equity Analysis System

## Prerequisites

- Claude Desktop App with Cowork mode OR Claude Code CLI
- Web search and web fetch tool access enabled
- Ability to spawn sub-agents via Task tool

## Installation Steps

### Option A: Install as a Cowork Skill (Recommended)

1. Copy the entire `hedge-fund-analysis/` directory to your Claude skills folder:
   ```bash
   # On macOS:
   cp -r hedge-fund-analysis/ ~/Library/Application\ Support/Claude/skills/hedge-fund-analysis/

   # On Windows:
   xcopy /E hedge-fund-analysis\ "%APPDATA%\Claude\skills\hedge-fund-analysis\"

   # On Linux:
   cp -r hedge-fund-analysis/ ~/.config/claude/skills/hedge-fund-analysis/
   ```

2. Restart Claude Desktop or reload skills

3. The skill will trigger automatically on phrases like:
   - "analyze TSLA"
   - "deep dive on Apple"
   - "hedge fund analysis of NVDA"
   - "institutional research on Microsoft"
   - "what's the real story with [stock]?"

### Option B: Install as a Claude Code Skill

1. Copy the directory into your project's `.claude/skills/` folder:
   ```bash
   cp -r hedge-fund-analysis/ .claude/skills/hedge-fund-analysis/
   ```

2. Claude Code will automatically discover and use the skill.

### Option C: Manual Usage

1. Open the orchestrator: `skills/orchestrator/SKILL.md`
2. Follow the Phase 1-5 workflow manually
3. For each agent, read its `SKILL.md` and execute the research dimensions

## Directory Structure

```
hedge-fund-analysis/
├── SKILL.md                              ← Entry point & overview
├── INSTALL.md                            ← This file
├── skills/
│   ├── orchestrator/SKILL.md             ← Parent orchestrator (start here)
│   ├── forensic-accountant/SKILL.md      ← Agent 1
│   ├── competitive-moat/SKILL.md         ← Agent 2
│   ├── governance-forensics/SKILL.md     ← Agent 3
│   ├── quant-positioning/SKILL.md        ← Agent 4
│   ├── alt-data-signals/SKILL.md         ← Agent 5
│   ├── macro-scenarios/SKILL.md          ← Agent 6
│   ├── future-optionality/SKILL.md       ← Agent 7
│   ├── narrative-decoder/SKILL.md        ← Agent 8
│   ├── capital-structure/SKILL.md        ← Agent 9
│   ├── corporate-structure/SKILL.md      ← Agent 10
│   ├── scuttlebutt/SKILL.md              ← Agent 11
│   ├── balance-sheet-quality/SKILL.md    ← Agent 12
│   ├── customer-unit-economics/SKILL.md  ← Agent 13
│   ├── red-team/SKILL.md                 ← Agent 14 (runs after 1-13)
│   └── executive-summary-deployer/SKILL.md ← HTML output generator
└── references/
    ├── report-template.md                ← Report structure reference
    ├── differentiation-checklist.md      ← Quality checklist
    └── agent-prompts.md                  ← Legacy prompts (superseded)
```

## Output Structure (per analysis run)

Each analysis creates a timestamped directory:

```
TSLA-20260309-143022/
├── agents/                    ← Raw agent outputs (traceability)
│   ├── 01-forensic-accountant/
│   │   ├── findings.md
│   │   └── sources.json
│   ├── 02-competitive-moat/
│   │   └── ...
│   └── 14-red-team/
│       └── ...
├── synthesis/                 ← Cross-referencing artifacts
│   ├── cross-references.md
│   ├── contradictions.md
│   ├── variant-perception.md
│   └── consolidated-findings.md
└── deploy/                    ← Web-deployable output
    ├── index.html             ← Interactive dashboard
    ├── executive-summary.md   ← 1-page PM summary
    └── metadata.json          ← Report metadata
```

## Deploying the HTML Dashboard

The `deploy/` directory is a self-contained static website. Deploy it anywhere:

```bash
# Copy to any web server
scp -r TSLA-20260309-143022/deploy/ user@server:/var/www/html/TSLA-20260309-143022/

# Or upload to S3 as static site
aws s3 sync TSLA-20260309-143022/deploy/ s3://your-bucket/TSLA-20260309-143022/

# Or serve locally
cd TSLA-20260309-143022/deploy && python3 -m http.server 8080
```

## Customization

- **Add/remove agents**: Edit `skills/orchestrator/SKILL.md` to add/remove from the agent table
- **Modify dimensions**: Edit any agent's `SKILL.md` to add/remove research dimensions
- **Change output format**: Edit `skills/executive-summary-deployer/SKILL.md`
- **Adjust quality bar**: Edit `references/differentiation-checklist.md`

## Notes

- All analysis is based on publicly available information only
- This is research, NOT investment advice
- Some dimensions may have limited data for certain companies — gaps are flagged, not fabricated
- The system uses web search extensively — analysis quality depends on search result quality
- Typical analysis takes 15-30 minutes depending on data availability and model speed
