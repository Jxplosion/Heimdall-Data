# Loads

| Date (ET) | File | Target | Rows | Text checksum | Result |
|---|---|---|---|---|---|
| 2026-10-13 21:22 | loads/2026-10-13-test-guides-RG0047-RG0051.csv (commit 69e12f7) | Guides A48:X52 (same rows, test) | 5 | 2711 = 2711 | Mechanics PASS (IMPORTDATA, paste-values, checksum). Correction 22:30: it overwrote Lumi's 19:52 verification of these 5 rows (rows changed after the source was built); Lumi re-verifies them. Rule added: read target rows before any paste. |
