# Prop Trading Firms (Jane Street, Citadel / Citadel Securities, HRT, …): What Regulatory Sources Actually Exist

*Checked 2026-09-26 on EDGAR full-text search, sec.gov/comments and sebi.gov.in.*

## Bottom line

**None of these firms publishes its trading methodology in an SEC filing.** Jane Street, Citadel Securities, Hudson River Trading, Optiver, DRW and Jump are privately held. They do not sell registered funds to the public, so there is no prospectus describing a strategy. What they do file is **financial-condition, holdings and policy material**. Some of it is still useful for research, but none of it can support a "reconstruct their strategy" project the way the four fund filings can. Any project claiming to reconstruct a Jane Street or HRT strategy from SEC filings would fail your own primary-source rule.

## What exists (primary sources)

| Firm | Source | What it contains | Useful for |
|---|---|---|---|
| Jane Street Group, LLC (CIK 1595888) | **Form 13F-HR**, quarterly (e.g. filed 2026-08-14, acc. 0001595888-26-000108) | Long US-listed equity/ETF/option positions at quarter-end | Little for strategy. For a market maker these are hedges and inventory, and shorts are not shown |
| Jane Street Capital, LLC (CIK 1103083); also Jane Street Options, Jane Street Execution Services | **Form X-17A-5** annual audited broker-dealer report (e.g. filed 2026-02-26, acc. 0001103083-26-000004, `jscpublic2025.pdf`) | Statement of financial condition, fair-value hierarchy, derivatives, risk-management and regulatory-capital notes | Balance-sheet/risk literacy. **No methodology** |
| Jane Street Group (India) | **SEBI interim order, 3 July 2025**, "Index manipulation by Jane Street Group" (105 pp.): https://www.sebi.gov.in/enforcement/orders/jul-2025/interim-order-in-the-matter-of-index-manipulation-by-jane-street-group_95040.html (PDF: https://www.sebi.gov.in/sebi_data/attachdocs/jul-2025/1751584518593.pdf) | The most detailed **regulator-authored** description of a prop firm's trading pattern: expiry-day Bank Nifty trades in constituent stocks/futures alongside index-option positions, with trade-level price-impact analysis | Microstructure / surveillance research. **These are allegations in an interim order that Jane Street contests. Check the case's current status before citing.** It is not an SEC filing |
| Citadel Securities | **SEC comment letters** (e.g. Order Competition Rule, File S7-31-22; Best Execution proposal, 2023) | The firm's economic arguments on market structure: auctions, tick sizes, retail order flow | Market-structure literature review; not strategy |
| Jane Street Capital | SEC comment letter on the Order Competition Rule (S7-31-22, 2023) | Same | Same |
| Hudson River Trading | Comment letters on sec.gov/comments (e.g. file 10-222, 2016; SR-NYSE-2023-36) and hudsonrivertrading.com/hrt-comment-letters | Views on exchange fees, tick sizes, market data | Same |
| Citadel Advisors (the hedge fund, separate from Citadel Securities) | 13F-HR; Form ADV (IAPD) | Holdings; adviser registration data | Little |
| **Virtu Financial** (the one *public* HFT market maker; CIK 1592386) | **10-K** FY2025: https://www.sec.gov/Archives/edgar/data/1592386/000159238626000009/virt-20251231.htm ; 2015 S-1 | Business model (spread capture as principal market maker), risk controls, market-risk disclosures, segment revenue. The S-1 is known for its daily-P&L distribution disclosure (verify in the S-1 itself) | The closest thing to an SEC-disclosed HFT *business model*. Still no model detail |
| Market centres incl. Citadel Securities, Jane Street, Virtu | **Rule 605 / 606 reports** (execution quality and order routing; Rule 605 was amended by the SEC in 2024, so check the current format and compliance date) | Monthly effective spreads, price improvement, realised spreads by order size and type | **Real, free microstructure data tied to named firms** |

## Can any of this become a project? Two honest options

### Option A (recommended as an optional 5th mini-project) — Wholesaler Execution Quality from Rule 605 Data
* **Question:** Across retail wholesalers (Citadel Securities, Jane Street, Virtu, G1, …), how do effective spread, price improvement and *realised* spread (a proxy for adverse selection) vary with stock volatility, order size and market conditions? Did the 2024 Rule 605 amendments change the picture?
* **Why it fits:** this is literally the business of Citadel Securities and Jane Street. It adds **market microstructure**, which your four projects lack. The data is public and firm-attributed, and no methodology has to be invented.
* **Methods:** panel regressions with stock and month fixed effects; decomposition of effective spread = realised spread + price impact; heterogeneity by volatility regime.
* **Effort:** MVP about 40 h; strong version about 90 h. The data-wrangling-heavy part is parsing per-firm monthly files.
* **Honest limit:** this is descriptive and econometric, not a trading strategy, and 605 statistics are self-reported aggregates.

### Option B — Expiry-Day Index/Underlying Linkage (motivated by the SEBI order)
* **Question:** On index-option expiry days, how sensitive is the settlement price to trading in constituent stocks late in the day, and what observable signatures does a surveillance system see (e.g. price impact reversal after the close, option open interest concentration)? Framed as **market-integrity measurement**, not as replicating the alleged strategy.
* **Data:** NSE daily bhavcopies (cash and F&O) are free. **Intraday data is not free**, and the research question really needs it, so data feasibility is low.
* **Caution:** Jane Street interviewers will know this case well. A neutral, surveillance-framed empirical study is defensible; anything that reads as "how to do what Jane Street was accused of" is not.

## Recommendation

Keep the four SEC-grounded projects as they are. They are where the verifiable methodology disclosures exist. If you want an explicit prop-firm and microstructure signal on your GitHub, add **Option A** as a smaller fifth repo after Week 8 (it doesn't depend on the others). Treat Option B only as a reading and literature exercise unless you can get intraday NSE data.
