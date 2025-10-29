# Zapier Finance Agent — Revenue vs Budget (GBP) — Sheets → OpenAI → Notion → Slides → PPTX → Slack

This repo is a **copy‑paste GitHub package** to build a Zapier AI Agent that produces a monthly *Revenue vs Budget* pack from Google Sheets data, writes a Notion log, creates a Google Slides deck, exports to **PowerPoint (.pptx)**, and posts a summary in **Slack**.

> Uses: Google Sheets, Notion, Google Slides, Google Drive, Slack, OpenAI (ChatGPT: Conversation).

---

## Repo Structure

```
zapier-finance-agent-rev-vs-budget/
├─ data/
│  ├─ budget.csv
│  ├─ actuals.csv
│  └─ expected_monthly_totals.csv
├─ agent/
│  └─ agent_instructions.md
├─ notion/
│  └─ database_fields.md
├─ slides/
│  └─ README.md
├─ zapier/
│  ├─ mappings.json
│  └─ SLACK_MESSAGE_TEMPLATE.md
├─ screenshots/
│  ├─ SCREENSHOT_PLAN.md
│  ├─ 01_sheets_data_tabs.png
│  ├─ 02_zapier_tools_config.png
│  ├─ 03_zapier_instructions_panel.png
│  ├─ 04_zapier_run_activity.png
│  ├─ 05_google_slides_generated_deck.png
│  └─ 06_slack_summary_message.png
└─ README.md  ← you are here
```

---

## Quick Start (10–20 min)

1. **Google Sheets**
   - Create a sheet named **Finance_Variance_Exercise**.
   - Add two tabs: **Budget** and **Actuals**.
   - Import the CSVs from `/data` into each tab (File → Import → Upload CSV → *Replace data*).
   - Headers must be exact: `month, department, budget_gbp` and `month, department, actual_gbp`.

2. **Notion**
   - Create a database called **Monthly Finance Reports** using `notion/database_fields.md`.

3. **Slides**
   - Build a template named **Rev_vs_Budget_Template** per `slides/README.md` and share as “Anyone with link — Viewer”.

4. **Zapier Agent**
   - Create an Agent, paste `agent/agent_instructions.md` as the role text.
   - In **Tools/Capabilities**, add:
     - Slack: *Send Channel Message*
     - ChatGPT (OpenAI): *Conversation*
     - Google Sheets: *Lookup Spreadsheet Rows (Advanced)*
     - Google Slides: *Create Presentation From Template*
     - Google Drive: *Export File*
     - Notion: *Create Database Item*
   - Connect app accounts when prompted (Google, Notion, Slack, OpenAI key).

5. **Run it**
   - In the Agent chat input, type: **Create a revenue vs budget report for 2025-09**.
   - The Agent will read Sheets, aggregate, draft a narrative, write to Notion, create Slides, export PPTX, and post to Slack.

> If you want to test **only** the Slides action first, temporarily create a single‑step Zap “Google Slides → Create Presentation From Template” and hardcode values using `zapier/mappings.json` keys to verify placeholder replacement.

---

## Troubleshooting

- **Slides didn’t populate**: Ensure the template name matches exactly and the placeholders are verbatim. Share the template as “Anyone with link — Viewer”. Re‑authorise the Google Slides connection.
- **Agent lacks permissions**: From the Agent, run a trivial step (e.g., list Drive files) to trigger an OAuth prompt, then re‑run.
- **Slack message missing links**: Make sure you captured the Slides file URL and PPTX export URL; optionally update the Notion item to store both URLs before posting.
- **CSV import**: In Sheets use *File → Import → Upload → Replace data*. Copy‑paste also works but watch for number formatting (use plain numbers).

---

## Screenshot Plan

Add real screenshots using these filenames (placeholders included in `/screenshots`):
1. `01_sheets_data_tabs.png` — Sheets Budget/Actuals tabs
2. `02_zapier_tools_config.png` — Agent tools list
3. `03_zapier_instructions_panel.png` — Instructions visible
4. `04_zapier_run_activity.png` — Successful run steps
5. `05_google_slides_generated_deck.png` — Filled deck
6. `06_slack_summary_message.png` — Slack summary

---

## License

MIT — use freely for demos and learning.
