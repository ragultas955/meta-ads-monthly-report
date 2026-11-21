---
name: meta-ads-monthly-report
description: Create a client-ready monthly Meta Ads (Facebook and Instagram) performance report from an Ads Manager export or a connected Meta Ads account, delivered either as an editable PowerPoint (.pptx) or as a single-file HTML report. Covers overall performance, a campaign list table, age, gender, device and placement analysis, and an observed-results-only summary. Use whenever the user asks for a monthly Meta Ads report, ad performance PPT or deck, monthly review, campaign performance table, or age/gender/placement analysis for any advertiser. Reporting month, advertiser name, data source, and output format are runtime inputs, so the skill is reusable every month and for any account.
---

# Monthly Meta Ads Performance Report

Produce a polished, data-led report that explains what happened in Meta Ads during one reporting month. The audience is management or a client, so the report must be accurate, scannable, and free of speculation.

Read these files before building (if your environment cannot open them, follow the "Core rules" section below, which is enough to produce a correct report):

- `references/report-spec.md`: section-by-section layout, charts, tables, design standards, final checklist.
- `references/insight-and-data-rules.md`: data integrity and insight-writing rules. Read before writing any number or sentence.
- `references/data-fields.md`: how to map Meta Ads Manager export columns to the metrics used here.
- `references/output-formats.md`: how to build the PowerPoint or the HTML report, plus notes for Claude and ChatGPT.

## Runtime inputs

Ask only for what is missing. Never ask the user to edit or paste these instructions.

1. **Reporting period**: `Month YYYY` (use the full calendar month) or an explicit date range.
2. **Advertiser / brand name**: shown on the cover. Never invent or assume one.
3. **Data source**, any one of:
   - an uploaded Meta Ads Manager export (CSV or XLSX) containing the needed breakdowns,
   - tables pasted into the chat,
   - a connected Meta Ads account (ask for the ad account ID, and use it only for the query; do not print it in the report).
4. **Output format**: `PowerPoint (.pptx)` or `HTML report` (a single self-contained page, also called an artifact). If the user does not say, ask once. If there is still no answer, deliver the PowerPoint.
5. **Optional**: previous-month data (enables month-over-month deltas; otherwise omit them), brand colours or logo.

If there is no data at all, stop and ask for an export or a connected account. Never produce sample or placeholder numbers as if they were real.

## Workflow

1. Normalize the period (start date, end date, label such as "September 2026"). Use the same period, currency, and attribution setting everywhere.
2. Collect six views: account-level totals, campaign-level rows, age, gender, device, placement.
3. Validate: Frequency = Impressions ÷ Reach, CPM = Cost ÷ Impressions × 1,000, CPR = Cost ÷ Results for a single result type. Record anything missing as `N/A`.
4. Draft insights using `references/insight-and-data-rules.md`, then build the report using `references/report-spec.md` and `references/output-formats.md`.
5. Render and inspect every slide or section for overlap, clipping, misalignment, and unreadable labels. Fix and re-render until clean.
6. Run the final checklist in the spec, then deliver the file (or the HTML artifact).

If a breakdown is missing or a connection fails, say exactly which view is missing and mark it `N/A`. Do not fill it in.

## Output structure

Seven core sections, 16:9 for PowerPoint, same order for the HTML report:

1. Cover
2. Overall Performance Insights
3. Campaign List (reach, impressions, CPR, results, CPC, CPM, frequency, cost for every campaign)
4. Age Analysis
5. Gender Analysis
6. Device and Placement Analysis
7. Overall Performance Summary

The Campaign List continues onto extra slides or rows only when there are more campaigns than fit (see the spec). PowerPoint charts and tables must be native and editable, not pictures.

## Core rules (always apply)

- Report observed performance only. No recommendations, action plans, optimization ideas, budget suggestions, next-month strategy, or calls to action. Before delivery, search the text for "should", "consider", "opportunity", "next month", "scale", "test", "optimize".
- The provided data is the only source of truth. Do not estimate or fabricate. Missing value → `N/A`.
- Reach is not additive across breakdowns or campaigns. Use the account-level reach for totals; show segment reach as per-segment values only.
- CPR is only comparable within one result type. Name the result type next to every CPR and never rank across different result types.
- Keep device and placement as separate dimensions. Never merge them.
- Show every category in the data, including unknown or unspecified. Do not drop one silently.
- Describe frequency, do not judge it ("the average reached account saw ads about three times").
- Do not explain why performance changed unless the data shows it.
- Do not include the ad account ID, access tokens, or any other identifier in the report unless the user explicitly asks.

## Final reply

Keep it short: the file or artifact, the period and data source used, and any `N/A` metrics or caveats (for example, reach not summable across breakdowns). Do not restate the report's contents.
