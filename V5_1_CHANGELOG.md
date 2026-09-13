# V5.1 — Market Intelligence Edition

## Major changes

1. **Removed Bond Valuation**
   - The former Bond Valuation tab is removed.
   - Replaced with **Investment Thesis** based on aggregated news flow for each stock.
   - Thesis separates Bull case, Bear case, Catalysts, Risks and confidence level.

2. **Market / Industry / Macro synthesis**
   - The dashboard now aggregates supplied articles into a common market view.
   - Summary covers Vietnam vs international news, dominant sectors, positive catalysts and major risks.
   - The same synthesis is included at the top of urgency email digests.

3. **Broad-market scanner**
   - No `WATCH_TICKERS` is required.
   - Background scanner covers broad listed-company news, HOSE/HNX/UPCoM market news, Vietnam macro/policy, major sectors, corporate/legal risk and international market drivers.
   - Tickers are detected from articles rather than being restricted to a predefined user watchlist.

4. **Resend instead of Gmail SMTP**
   - Removed `GMAIL_USER` and `GMAIL_APP_PASSWORD`.
   - Added `RESEND_API_KEY` and `RESEND_FROM`.
   - Email schedule remains 07:00, 09:00, 12:00 and 17:00 Asia/Ho_Chi_Minh.

5. **Database enrichment**
   - Articles now store `region`, `market_topic` and `stream`.
   - `supabase_schema.sql` contains safe `ADD COLUMN IF NOT EXISTS` migration lines for V5 databases.

## Alert architecture

Google News broad market streams → dedupe → ticker extraction → sector/region detection → urgency scoring → Supabase → user threshold → Resend digest.

## Important Resend note

`onboarding@resend.dev` is for testing and can only send to the email address associated with the Resend account. For a public multi-user app, verify a domain in Resend and set `RESEND_FROM` to an address at that domain.
