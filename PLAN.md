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
- **Date range:** this month / last month / last 90 days / this year / all / custom
- **Leads:** B2B only (default) / All leads
- **Desk:** All / US / OUS
- **Refunds:** leave out (default) / include
- **Repeat clients:** include (default) / leave out
- **Chart split:** none / SDR-led vs AE-led / US vs OUS
- **Chart grouping:** by week / by month

## Tabs
**1. Overview (whole team)**
- The 4 top numbers + view switch
- History chart for whichever top number is selected
- Funnel: Leads → Called → Meeting Done → Closed
- Top Lost and Disqualified reasons

**2. SDRs** (one row per SDR, click for detail)
- Meeting Done % (main), Lead→Deal %, Non-Response %
- Breakdown: leads, revenue from their leads, AOV, AE-rejected %

**3. AEs** (grouped by desk, Andrew flagged)
- Revenue, AOV, Meeting Done % (direct leads), Lead→Deal % (direct leads)
- Breakdown: Meeting→Close % (incl. SDR handoffs), lost reasons

**4. Habits** (per person, SDRs and AEs — needs Aircall file)
- Call coverage % (leads called at least once)
- Median time to first call (speed to lead)
- Second-day call % (called again on a later day)
- "Not responsive" but never called %
- Cadence adherence — reserved spot, definition TBD

## Rules
- Every % shows its count next to it, e.g. "22% (of 41)".
- Revenue and AOV use the **close date**. Percentages use the **lead creation date**.
- Meeting = "Meeting Done" only.
- SDR-led revenue shows for both the SDR and the AE, counted once in totals.
- People who left (e.g. Mateo Pautasso) count in totals, hidden from people tables.
- `Price AED` is actually USD. No conversion.
- Airtable times are UTC+3; Aircall is UTC. Subtract 3h before joining.
- Calls join to leads on the last 9 digits of the phone number.
- SDR vs AE calls are told apart by the Aircall `user` name.

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
