# Data Sources Reference — All Free / Open Source

Every agent in this system operates on **100% publicly available data**. No paid subscriptions
required. Here are the prioritized free data sources each agent should use, organized by
agent and data type.

---

## Universal Sources (All Agents Should Know)

### SEC EDGAR (Primary Source of Truth)
- **10-K / 10-Q / 8-K filings**: `https://www.sec.gov/cgi-bin/browse-edgar?action=getcompany&CIK=[TICKER]&type=10-K`
- **XBRL financial data**: `https://efts.sec.gov/LATEST/search-index?q=[TICKER]&dateRange=custom`
- **Full-text search**: `https://efts.sec.gov/LATEST/search-index?q="[COMPANY]"&forms=10-K,10-Q`
- **Exhibit 21 (subsidiaries)**: search 10-K filings for exhibit 21
- **DEF 14A (proxy statements)**: compensation, board, governance data
- **13F filings**: institutional ownership quarterly
- **13D/13G**: activist accumulation / large holders
- **Forms 3/4/5**: insider transactions
- **EDGAR XBRL API**: `https://data.sec.gov/api/xbrl/companyfacts/CIK[10-digit-CIK].json`

### Financial Modeling Prep (FMP) — Free Tier
- **API base**: `https://financialmodelingprep.com/api/v3/`
- **Income statement**: `/income-statement/[TICKER]?period=annual&limit=10`
- **Balance sheet**: `/balance-sheet-statement/[TICKER]?period=annual&limit=10`
- **Cash flow**: `/cash-flow-statement/[TICKER]?period=annual&limit=10`
- **Key metrics**: `/key-metrics/[TICKER]?period=annual&limit=10`
- **Ratios**: `/ratios/[TICKER]?period=annual&limit=10`
- **Profile**: `/profile/[TICKER]`
- **DCF**: `/discounted-cash-flow/[TICKER]`
- **Enterprise value**: `/enterprise-values/[TICKER]?period=annual`
- **Stock price**: `/historical-price-full/[TICKER]?serietype=line`
- **Earnings surprises**: `/earnings-surprises/[TICKER]`
- **Analyst estimates**: `/analyst-estimates/[TICKER]`
- **Institutional holders**: `/institutional-holder/[TICKER]`
- **SEC filings list**: `/sec_filings/[TICKER]?type=10-K`
- **Stock screener**: `/stock-screener?sector=[SECTOR]&limit=20`
- **Industry PE**: `/sector-performance`
- **Note**: Free tier has rate limits (250 calls/day). Use wisely. API key required.

### Yahoo Finance (via web scrape)
- Summary page: `https://finance.yahoo.com/quote/[TICKER]`
- Statistics: `https://finance.yahoo.com/quote/[TICKER]/key-statistics`
- Financials: `https://finance.yahoo.com/quote/[TICKER]/financials`
- Holders: `https://finance.yahoo.com/quote/[TICKER]/holders`
- Options: `https://finance.yahoo.com/quote/[TICKER]/options`
- Sustainability: `https://finance.yahoo.com/quote/[TICKER]/sustainability`

### Macrotrends (Historical Financial Data)
- `https://www.macrotrends.net/stocks/charts/[TICKER]/[COMPANY-SLUG]/revenue`
- Revenue, earnings, margins, ratios — 10+ year history, free

### Stock Analysis (Free Tier)
- `https://stockanalysis.com/stocks/[TICKER]/financials/`
- Financials, estimates, ownership, short interest

---

## Agent-Specific Data Sources

### Agent 1: Forensic Accountant
| Data Need | Free Source | URL Pattern |
|-----------|-----------|-------------|
| Financial statements | SEC EDGAR XBRL API | `data.sec.gov/api/xbrl/companyfacts/` |
| Beneish M-Score inputs | FMP ratios + manual calc | FMP `/ratios/` endpoint |
| Audit reports | SEC EDGAR 10-K filing | Search for "auditor" in 10-K |
| Restatements | SEC EDGAR 10-K/A, 8-K | Filter for amended filings |
| SBC data | DEF 14A proxy | Compensation Discussion section |
| DSO / DIO / DPO | FMP key metrics or manual calc | FMP `/key-metrics/` |
| Accrual ratio | Manual calc from FMP data | (NI - CFO - CFI) / Total Assets |

### Agent 2: Competitive Moat & Supply Chain
| Data Need | Free Source | URL Pattern |
|-----------|-----------|-------------|
| Market share data | Statista (limited free), web search | Google: "[INDUSTRY] market share 2025" |
| Competitor financials | FMP profile + comparisons | FMP `/profile/[COMP_TICKER]` |
| Supply chain nodes | SEC 10-K risk factors, supply chain disclosures | EDGAR full-text search |
| Customer concentration | SEC 10-K (major customers note) | Search 10-K for "customer" |
| TAM estimates | Industry reports (free excerpts), company IR | Company investor presentations |
| Industry data | BLS, Census, trade associations | `bls.gov`, `census.gov` |

### Agent 3: Governance & Incentive Forensics
| Data Need | Free Source | URL Pattern |
|-----------|-----------|-------------|
| Executive compensation | SEC DEF 14A proxy | EDGAR proxy filings |
| Insider transactions | SEC Forms 3/4/5 | `sec.gov/cgi-bin/browse-edgar?action=getcompany&type=4` |
| Insider transactions (easy) | OpenInsider | `openinsider.com/screener?s=[TICKER]` |
| Board composition | DEF 14A proxy statement | EDGAR proxy filings |
| Institutional ownership | SEC 13F filings | `sec.gov/cgi-bin/browse-edgar?type=13F` |
| Institutional owners (easy) | FMP API | FMP `/institutional-holder/[TICKER]` |

### Agent 4: Quant & Positioning
| Data Need | Free Source | URL Pattern |
|-----------|-----------|-------------|
| Short interest | FINRA short interest data, Finviz | `finviz.com/quote.ashx?t=[TICKER]` |
| Options data | Yahoo Finance options, CBOE | `finance.yahoo.com/quote/[TICKER]/options` |
| 13F institutional holdings | WhaleWisdom (free tier) | `whalewisdom.com/stock/[TICKER]` |
| 13F holdings (API) | FMP | FMP `/institutional-holder/[TICKER]` |
| Price history | FMP or Yahoo Finance | FMP `/historical-price-full/[TICKER]` |
| Earnings reactions | FMP earnings surprises | FMP `/earnings-surprises/[TICKER]` |
| Factor data | Kenneth French data library | `mba.tuck.dartmouth.edu/pages/faculty/ken.french/data_library.html` |
| Technical indicators | FMP | FMP `/technical_indicator/daily/[TICKER]?type=sma` |

### Agent 5: Alternative Data & Forward Signals
| Data Need | Free Source | URL Pattern |
|-----------|-----------|-------------|
| Google Trends | Google Trends | `trends.google.com/trends/explore?q=[COMPANY]` |
| Job postings | LinkedIn (public), Indeed, Glassdoor | Web search: "[COMPANY] jobs" |
| Patent filings | Google Patents, USPTO | `patents.google.com/?q=[COMPANY]` |
| Litigation | PACER (limited free), CourtListener | `courtlistener.com/` |
| SEC comment letters | SEC EDGAR correspondence | EDGAR filter by "CORRESP" |
| App store reviews | App Store / Google Play web | Web search: "[APP] reviews" |
| Reddit sentiment | Reddit search | `reddit.com/search/?q=[TICKER]` |
| Government contracts | USASpending.gov | `usaspending.gov/search` |
| FDA filings | FDA.gov | `fda.gov/drugs/drug-approvals-and-databases` |
| ESG ratings | Sustainalytics (limited), Yahoo Finance ESG | Yahoo `/sustainability` page |

### Agent 6: Macro Overlay & Scenarios
| Data Need | Free Source | URL Pattern |
|-----------|-----------|-------------|
| Interest rates | FRED (Federal Reserve) | `fred.stlouisfed.org/series/DFF` |
| Currency data | FRED, ECB, FMP | FMP `/historical/forex` |
| Commodity prices | FMP, Trading Economics (limited) | FMP `/historical-price-full/[COMMODITY]` |
| GDP / macro data | FRED, BEA, BLS | `fred.stlouisfed.org` |
| Analyst estimates | FMP | FMP `/analyst-estimates/[TICKER]` |
| Earnings calendar | FMP | FMP `/earning_calendar` |
| M&A data | FMP | FMP `/mergers-acquisitions-rss-feed` |
| Index data | FMP | FMP `/historical-price-full/SPY` |

### Agent 7: Future Optionality Decoder
| Data Need | Free Source | URL Pattern |
|-----------|-----------|-------------|
| Segment revenue | SEC 10-K (segment reporting note) | EDGAR 10-K |
| Industry TAM estimates | Free research excerpts, company IR | Web search + investor decks |
| S-curve analogues | Our World in Data, Statista free | `ourworldindata.org` |
| Company investor presentations | Investor relations pages | `[COMPANY].com/investors` |
| Adoption data | Pew Research, industry associations | Web search |

### Agent 8: Narrative Decoder
| Data Need | Free Source | URL Pattern |
|-----------|-----------|-------------|
| Earnings call transcripts | Motley Fool Transcripts (free) | `fool.com/earnings/call-transcripts/` |
| Earnings call transcripts | Seeking Alpha (limited free) | `seekingalpha.com/symbol/[TICKER]/earnings/transcripts` |
| Press releases | SEC 8-K, company newsroom | EDGAR 8-K filings |
| Guidance history | FMP analyst estimates | FMP `/analyst-estimates/[TICKER]` |

### Agent 9: Capital Structure & Dilution
| Data Need | Free Source | URL Pattern |
|-----------|-----------|-------------|
| Share count detail | SEC 10-K cover page + equity note | EDGAR 10-K |
| Convertible details | SEC 10-K debt footnotes | EDGAR 10-K |
| SBC detail | SEC DEF 14A + 10-K equity note | EDGAR filings |
| Debt maturities | SEC 10-K debt footnotes | EDGAR 10-K |
| Credit ratings | Moody's/S&P press releases (free) | Web search: "[COMPANY] credit rating" |
| Bond prices | FINRA TRACE (free) | `finra-markets.morningstar.com/BondCenter/` |

### Agent 10: Corporate Structure Investigator
| Data Need | Free Source | URL Pattern |
|-----------|-----------|-------------|
| Subsidiary list | SEC 10-K Exhibit 21 | EDGAR Exhibit 21 |
| Related party transactions | SEC 10-K footnotes | EDGAR 10-K search "related party" |
| Beneficial ownership | SEC 13D/13G filings | EDGAR 13D filings |
| Corporate registrations | State SOS databases | `opencorporates.com` |
| Offshore entities | OpenCorporates, ICIJ Offshore DB | `offshoreleaks.icij.org/` |

### Agent 11: Scuttlebutt
| Data Need | Free Source | URL Pattern |
|-----------|-----------|-------------|
| Employee reviews | Glassdoor | `glassdoor.com/Reviews/[COMPANY]-Reviews` |
| Product reviews | G2, Capterra, TrustPilot, BBB | Web search |
| App reviews | App Store / Play Store web | Web search |
| Reddit discussions | Reddit | `reddit.com/search/?q=[COMPANY]` |
| LinkedIn headcount | LinkedIn (public) | Web search: "site:linkedin.com [COMPANY]" |
| Customer complaints | CFPB (financial), FTC, BBB | `consumerfinance.gov/data-research/complaints/` |

### Agent 12: Balance Sheet Quality
| Data Need | Free Source | URL Pattern |
|-----------|-----------|-------------|
| Goodwill detail | SEC 10-K intangibles note | EDGAR 10-K |
| Working capital | FMP key metrics | FMP `/key-metrics/[TICKER]` |
| Peer comparison | FMP stock screener | FMP `/stock-screener?sector=` |
| Reserve details | SEC 10-K footnotes | EDGAR 10-K |
| Real estate values | County assessor records (varies) | Web search |

### Agent 13: Customer Unit Economics
| Data Need | Free Source | URL Pattern |
|-----------|-----------|-------------|
| Customer concentration | SEC 10-K major customers | EDGAR 10-K |
| NRR / retention metrics | Company earnings reports, IR | Investor presentations |
| CAC / LTV | Company earnings reports (if SaaS) | Investor presentations |
| Churn data | Company filings, review sites | EDGAR + web search |

### Agent 14: Industry & Disruption Landscape
| Data Need | Free Source | URL Pattern |
|-----------|-----------|-------------|
| Industry data | BLS, Census, BEA | `bls.gov`, `census.gov` |
| Technology trends | Gartner Hype Cycle (free summaries) | Web search: "Gartner hype cycle [INDUSTRY]" |
| Competitor financials | FMP batch | FMP `/profile/[TICKER]` for each competitor |
| M&A activity | FMP, PitchBook (free excerpts) | Web search: "[INDUSTRY] M&A 2025" |
| Patent landscape | Google Patents | `patents.google.com` |
| Regulatory pipeline | Congress.gov, Federal Register | `congress.gov/search?q=[INDUSTRY]` |
| Industry reports (free) | IBIS World (summaries), Statista | Web search excerpts |

### Agent 15: Red Team
| Data Need | Free Source | URL Pattern |
|-----------|-----------|-------------|
| Short thesis research | Hindenburg, Muddy Waters, etc. | Web search: "[TICKER] short thesis" |
| Bull/bear cases | Seeking Alpha (limited free) | Web search: "[TICKER] bear case deep dive" |
| Historical base rates | Academic papers, Damodaran | `pages.stern.nyu.edu/~adamodar/` |
| Kelly criterion inputs | Derived from scenario analysis | Internal calculation |

---

## Free API Keys Required

These free services require registration but cost $0:

1. **Financial Modeling Prep**: `https://financialmodelingprep.com/developer/docs/` — 250 calls/day free
2. **Alpha Vantage**: `https://www.alphavantage.co/support/#api-key` — 25 calls/day free
3. **FRED API**: `https://fred.stlouisfed.org/docs/api/api_key.html` — unlimited free
4. **SEC EDGAR**: No API key needed — fully open
5. **Google Patents**: No API key needed — fully open
6. **OpenCorporates**: Free tier available

## No Login Required

These sources are fully open with no registration:
- SEC EDGAR (all filings, XBRL API)
- FRED (Federal Reserve Economic Data)
- Google Trends
- Google Patents
- USPTO
- Congress.gov / Federal Register
- Yahoo Finance (web)
- Macrotrends.net
- Finviz (basic)
- OpenInsider
- Reddit (public)
- Glassdoor (public reviews)
- Our World in Data
- ICIJ Offshore Leaks Database
- USASpending.gov
- BLS / Census / BEA

---

## Agent 15: CEO / Founder Ecosystem

| Dimension | Free Source | URL Pattern |
|-----------|-----------|-------------|
| Multi-venture map | Wikipedia, Crunchbase | `en.wikipedia.org/wiki/[CEO_NAME]` |
| Venture valuations | PitchBook news, TechCrunch | `techcrunch.com/tag/[company]` |
| Political relationships | OpenSecrets, news | `opensecrets.org/` |
| Political impact | News search | Web search: `[CEO] [COMPANY] political impact` |
| Brand tracking | Brand Finance, Interbrand | Web search: `[COMPANY] brand value [YEAR]` |
| Talent flows | LinkedIn (public), Glassdoor | `glassdoor.com/Reviews/[COMPANY]` |
| Related party transactions | SEC EDGAR DEF 14A | `sec.gov/cgi-bin/browse-edgar?action=getcompany&CIK=[TICKER]&type=DEF+14A` |
| CEO compensation | SEC EDGAR DEF 14A | Same as above |
| CEO time allocation | News, interviews | Web search: `[CEO] time management schedule` |
| Ecosystem synergies | Patent cross-references, news | Web search: `[COMPANY] [SISTER_COMPANY] collaboration` |

---

## Data Quality Hierarchy

When multiple sources exist, prefer in this order:
1. **SEC EDGAR** — primary source of truth for all financial data
2. **Company investor relations** — management's own presentations and data
3. **Financial Modeling Prep API** — structured, consistent, programmatic access
4. **Macrotrends / StockAnalysis** — clean historical data presentation
5. **Yahoo Finance** — broad coverage, easy access
6. **Web search synthesis** — for qualitative data, recent events, sentiment
