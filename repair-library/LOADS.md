# Loads

One row per load. The Source and license column must match that source's row in [SOURCES.md](../SOURCES.md), and both are updated in the same commit (SOP 16 item 8).

| Date (ET) | File | Source and license | Target | Rows | Text checksum | Result |
|---|---|---|---|---|---|---|
| 2026-10-13 21:22 | loads/2026-10-13-test-guides-RG0047-RG0051.csv (commit 69e12f7) | Repair Wiki, CC BY-SA 3.0 (license column added 2026-10-13 23:12) | Guides A48:X52 (same rows, test) | 5 | 2711 = 2711 | Mechanics PASS (IMPORTDATA, paste-values, checksum). Correction 22:30: it overwrote Lumi's 19:52 verification of these 5 rows (rows changed after the source was built); Lumi re-verifies them. Rule added: read target rows before any paste. |
