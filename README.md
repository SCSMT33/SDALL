# Shootday Sales Pulse

Sales dashboard for the Shootday SDR and AE teams. See `PLAN.md` for what it tracks and why.

## Open it
1. Download `index.html` (or the whole repo) to your computer.
2. Double-click `index.html`. It opens in Chrome.
3. Drag your exports onto the page (several at once is fine). **Data files** at the top shows what's loaded:
   - **Airtable** leads export (required)
   - **Aircall** call history, and the Aircall **SMS drilldown**
   - **Respond.io** messages, contacts and users (all three, for WhatsApp)
   - **Email activity**: one file per month. Drop every month you have; overlapping files are de-duplicated.

The files are read in your browser only and never uploaded. The page remembers the last files you loaded.

## Exchange rates
Prices are converted to USD with the `FX_MONTHLY` table (ECB monthly averages) near the top of the `<script>`. Add months in the same format to extend it.

## Change the team
Edit the `ROSTER` list near the top of the `<script>` in `index.html`. Each person's `email` is their mailbox in the email activity files.
