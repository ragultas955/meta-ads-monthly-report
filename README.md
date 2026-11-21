# Meta Ads Monthly Report Skill

A reusable, advertiser-neutral skill that turns a Meta Ads (Facebook and Instagram) export, or a connected Meta Ads account, into a client-ready monthly performance report.

It works with Claude and ChatGPT. The reporting month, advertiser name, data source, and output format are all asked at run time, so nothing client-specific is stored in this repository.

## What you get

Seven sections, in this order:

1. Cover
2. Overall Performance Insights
3. Campaign List: campaign name, reach, impressions, CPR, results, CPC, CPM, frequency, cost
4. Age Analysis
5. Gender Analysis
6. Device and Placement Analysis
7. Overall Performance Summary

The report states observed results only. It contains no recommendations, next steps, or budget advice.

## Output formats

| Format | What it is |
|---|---|
| PowerPoint (`.pptx`) | 16:9 deck with native, editable charts and tables |
| HTML report (artifact) | One self-contained page with the same sections; prints to PDF from the browser |

## Inputs

- Reporting period (a month or a date range)
- Advertiser name for the cover
- Data: Ads Manager export (CSV/XLSX), pasted tables, or a connected Meta Ads account
- Output format: PowerPoint or HTML
- Optional: previous-month data for comparisons, brand colours or logo

## Folder layout

```
meta-ads-monthly-report/
├── SKILL.md                              Entry point: inputs, workflow, core rules
├── README.md
└── references/
    ├── report-spec.md                    Section layouts, design standards, checklist
    ├── insight-and-data-rules.md         Data integrity and insight-writing rules
    ├── data-fields.md                    Export column mapping
    └── output-formats.md                 PPTX and HTML build notes, platform notes
```

## Use with Claude

Zip the `meta-ads-monthly-report` folder and add it as a custom skill, or place the folder in your skills directory for Claude Code. Then ask, for example: "Create the monthly Meta Ads report for September 2026" and attach the export.

## Use with ChatGPT

Copy the contents of `SKILL.md` (without the front matter) into your Custom GPT or Project instructions, and upload the files in `references/` as knowledge files. Then attach the export and ask for the monthly report. If your ChatGPT plan supports skills, you can load the folder as a skill instead.

## Privacy

- Do not commit exports, decks, or reports to this repository. The `.gitignore` blocks common data and report file types.
- The skill never prints the ad account ID or access tokens in the report.

## License

Add the license of your choice (for example MIT) before publishing.
