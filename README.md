# Heimdall-Data

Public data drop for OmniSolution's Repair library. Claude builds data files here; the library's Google Sheet pulls them in with `IMPORTDATA`, so bulk loads never have to be written row by row.

## Rules

- **Public repair data only.** Repair guides, device facts, component data from open sources.
- **Never here:** prices, costs or markups; customer, ticket or device-serial data; supplier data; anything from Argus or the server; names, emails, addresses, keys, tokens or passwords.
- Every load is a new file. Files are never edited after they are loaded, so each one stays an exact record of what went in.
- Every load is pulled by its commit hash (`raw.githubusercontent.com/<owner>/<repo>/<commit>/<path>`), so the sheet always gets exactly that version and never a cached older copy.

## Layout

| Path | What it holds |
|---|---|
| `repair-library/loads/` | One CSV per load: `YYYY-MM-DD-<what>.csv`. The columns match the target tab exactly (Guides: 24 columns, ID through Notes). |
| `repair-library/LOADS.md` | One line per load: date, file, target tab and rows, row count, checksum, result. |

## How a load runs

1. Claude builds the CSV from the source data and commits it here.
2. The Repair library's hidden `Import` tab gets `=IMPORTDATA("<raw link at that commit>")`.
3. Claude checks the row count and a text checksum against the source.
4. One paste-values call copies the block into the target tab; the checksum is checked again.
5. The `Import` tab is cleared and the load is logged in `LOADS.md`, in Work log - Claude and, for a new kind of load, in the Decisions log.

## For team members (Strider, Lumi, Wren)

- Read anything here; never write here. Only Claude pushes and runs loads (SOP 16 in Heimdall SOPs).
- The Google Sheets are where work happens. This repo is only the delivery lane and the record of each load.
- Have about 50 or more rows of public data to add? Don't type them. Put an Ask in your entry: `To Claude: Bulk load: <source link>, target <sheet and tab>, columns <which>, about <n> rows, why`. The source must be a downloadable file (CSV, JSON) or a GitHub repository.
- Never touch a sheet's hidden `Import` tab, and never add IMPORTDATA or other outside-data formulas to a team sheet.
- Bulk-loaded rows are leads until the tab's owner verifies them.

## Licensing

Content taken from Repair Wiki is CC BY-SA 3.0: every row credits Repair Wiki and the page's contributors in its Notes column, and adaptations stay under the same license. Links point to the original pages.
