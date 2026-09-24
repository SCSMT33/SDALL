# Shootday Sales Dashboard — Plan

Owner: Chase Anderson (SDR Team Lead). Local dashboard opened in Chrome.
Data comes in by drag-and-drop: one **Airtable** export (leads) and one **Aircall** export (calls).
Nothing is uploaded anywhere — the files stay in the browser.

## The 4 top numbers (always at the top)
1. **Revenue** — money from closed deals
2. **AOV** — average order value (revenue ÷ deals)
3. **Lead→Deal %** — closed deals ÷ leads
4. **Meeting Done %** — leads with Meeting Status = "Meeting Done" ÷ leads

Each has a view switch: **Whole team / SDRs / AEs**
- Whole team = every lead
- SDRs = SDR-led leads (`SDR Owner` filled in)
- AEs = AE-direct leads (`SDR Owner` empty)

## Switches (change every number)
All filters are dropdowns in the top bar.
- **People:** checkbox list of every SDR and AE (+ former team members). Unticked people's leads and deals are removed from every number, chart and table.
- **View:** Whole team / SDR-led / AE-direct (Overview tab)
- **Date range:** this month / last month / last 90 days / this year / all / custom / This year + projection / Next 12 months
- **Leads:** B2B only (default) / All leads
- **Desk:** All / US / OUS
- **Refunds:** leave out (default) / include
- **Repeat clients:** include (default) / leave out
- **Chart split:** none / SDR-led vs AE-led / US vs OUS / New vs repeat client (stacked bars on revenue)
- **Chart grouping:** by week / by month / by quarter

## Tabs
**1. Overview (whole team)**
- The 4 top numbers + view switch
- History chart for whichever top number is selected
- Revenue by month: "Last year" Show/Hide toggle adds a faded bar for the same month last year (same filters and split)
- Revenue projection (green bars, stacked on actuals) whenever the date range reaches today; Revenue tile shows the projected total ± accuracy; explainer box under the chart
- Funnel: Leads → Called → Meeting Done → Closed
- Top Lost and Disqualified reasons

**2. SDRs** (SDR-led leads)
- Tiles: Meeting Done % (main), Lead→Deal %, Non-Response %, SDR-led leads
- Monthly chart (one line per SDR + SDR team), then per-SDR table (leads, revenue, AOV, AE-rejected %)
- Calls & cadence: coverage, median time to first call, second-day call %, "not responsive" never called, cadence (reserved) — tiles, monthly chart, per-SDR table
- Bottom: Why leads drop out, Lost / Disqualified switch

**3. AEs** (grouped by desk, Andrew flagged)
- Leads switch: AE-direct (default) / From SDRs / All leads — applies to everything on the tab
- Tiles: Revenue, AOV, Meeting Done %, Lead→Deal %
- Monthly chart (one line per AE + All AEs; Revenue, AOV, Meeting Done %, Lead→Deal %, Meeting→Close %), then per-AE table
- Calls & cadence: same as SDRs, for AEs
- Bottom: Why leads drop out, Lost / Disqualified switch

(The separate Habits tab was removed; its content lives on the SDRs and AEs tabs.)

## Projection method (Overview revenue)
1. Seasonality: each month ÷ the centred 12-month average (removes growth), averaged per calendar month, shrunk toward 1 when few years exist (1 year = half strength).
2. Run-rate: last 3 complete months, seasonality removed. Trend: slope of last 6 such months, capped ±5%/month, fading 20% per month ahead.
3. Forecast = run-rate × (1 + faded trend) × seasonality. Done per chart split group (seasonality shared).
4. Current month = actual so far + forecast × share of month left after the file's last lead.
5. Accuracy = average miss predicting each of the last 6 complete months one month ahead; shown as ±%.

## Rules
- Every % shows its count next to it, e.g. "22% (of 41)".
- Revenue and AOV use the **close date**. Percentages use the **lead creation date**.
- Meeting = "Meeting Done" only.
- SDR-led revenue shows for both the SDR and the AE, counted once in totals.
- People who left (e.g. Mateo Pautasso) count in totals, hidden from people tables.
- `Price AED` is in the deal's own currency (`Currency` column). Converted to USD with a fixed, editable rate table (`FX_RATES` in index.html).
- Airtable times are UTC+3; Aircall is UTC. Subtract 3h before joining.
- Calls join to leads on the last 9 digits of the phone number.
- SDR vs AE calls are told apart by the Aircall `user` name.

## Repeat clients
- Uses a "new customer" style column if the Airtable export has one (auto-detected).
- Otherwise: repeat = the same email already had an earlier closed deal.
- Revenue tile shows the share of revenue from repeat clients.

## Status buckets (`Sales status`)
| Bucket | Raw values |
|---|---|
| Closed | Closed |
| Lost | Lost |
| Non-Response | Disqualified + reason "Not responsive" |
| Disqualified | Disqualified (other reasons), Disqualified AE (wrong SDR qualification) |
| Still open | Pending, Pending to Quote, Qualified_SDR, Cold, Warm, Hot, Non respondant, blank |
| Refunded | Deposit refund, Full refund, Partial refund (not a sale unless Refunds switch = include) |

## People
| Name | Role | Desk |
|---|---|---|
| MJ Montero | SDR | US |
| Gospel Lim | SDR | US |
| Mark Paolo Santos (Aircall: Mark Santos) | SDR | OUS |
| Levi Ceballos | SDR | OUS |
| Andrew Thomas | AE | US (senior, biggest deals + repeat — not comparable) |
| Khalil Khodor | AE | US |
| Savio Obeid | AE | US |
| Stephan Moubarak | AE | US |
| Firas Azar | AE | OUS (benchmark) |
| Elie El Khoury | AE | OUS (not Elie Terzian) |
| Sinar Knayzeh | AE | OUS |

## Open
- Cadence adherence definition (SDR and AE).
- How AEs are paid.
