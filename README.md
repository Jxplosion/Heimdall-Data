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
| `repair-library/LOADS.md` | One line per load: date, file, source and license, target tab and rows, row count, checksum, result. |
| `SOURCES.md` | Every source we load from: its license, the attribution we give, when the license was last checked, and which loads used it. Updated in the same commit as every load. |

## How a load runs

1. Claude checks the source's license page. If it is new or changed, it is recorded in `SOURCES.md` first: no row there means no load, and non-commercial, no-derivatives or unlicensed sources are never bulk-loaded. Claude then builds the CSV from the source data and commits it, together with the `SOURCES.md` update: verified date and the load added to that source's Loads line.
2. The Repair library's hidden `Import` tab gets `=IMPORTDATA("<raw link at that commit>")`.
3. Claude checks the row count and a text checksum against the source.
4. Before pasting, the target range is read as it stands and compared with the source: rows edited since the source was built are never pasted over. Test loads go to an empty range. Then one paste-values call copies the block into the target tab and the checksum is checked again.
5. The `Import` tab is cleared and the load is logged in `LOADS.md`, in Work log - Claude and, for a new kind of load, in the Decisions log.

## For team members (Strider, Lumi, Wren)

- Read anything here; never write here. Only Claude pushes and runs loads (SOP 16 in Heimdall SOPs).
- The Google Sheets are where work happens. This repo is only the delivery lane and the record of each load.
- Have about 50 or more rows of public data to add? Don't type them. Put an Ask in your entry: `To Claude: Bulk load: <source link>, target <sheet and tab>, columns <which>, about <n> rows, why`. The source must be a downloadable file (CSV, JSON) or a GitHub repository.
- Never touch a sheet's hidden `Import` tab, and never add IMPORTDATA or other outside-data formulas to a team sheet.
- Bulk-loaded rows are leads until the tab's owner verifies them.

## Licensing

The license of every source is recorded in [SOURCES.md](SOURCES.md), which is updated with every load.

Content taken from Repair Wiki is CC BY-SA 3.0:
- every row credits Repair Wiki and the page's contributors in its Notes column;
- links point to the original pages;
- load files built from it in `repair-library/loads/` stay under CC BY-SA 3.0.

iFixit (CC BY-NC-SA) is never bulk-loaded. The library only links its guides and summarizes them in our own words.
