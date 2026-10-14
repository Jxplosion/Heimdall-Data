# Sources and licenses

Every source whose data is loaded through this repository is listed here with its license and how we meet it. This file is updated **in the same commit as every load** that pulls a source's data (Jonathan, 2026-10-13 11:11 PM ET; SOP 16 item 8). A load whose source has no row here, or whose license was not checked that day, is not run.

This is a working record kept by Claude, not legal advice.

## Rules

1. **Allowed for bulk loads:** public domain or CC0; CC BY; CC BY-SA. Plain facts written in our own words, such as model numbers, release dates or which part fits which model, may also be loaded from an official source.
2. **Never bulk-loaded:** non-commercial (NC) or no-derivatives (ND) licenses, sites whose terms forbid reuse or scraping, and content with no license stated. From these sources the library holds only a link and a summary in our own words, added by hand. iFixit (CC BY-NC-SA) is in this group.
3. **Attribution:** every row from a source names it in its Source column and links the original page. Every share-alike row also credits the source and its contributors in its Notes column.
4. **Share-alike:** files in `repair-library/loads/` that adapt CC BY-SA content stay under that same license. See the per-source notes below.
5. **Before every load:**
   - open the source's license page and confirm it is unchanged;
   - set "Verified on" in the register below;
   - add the load to that source's "Loads" line;
   - give the load's row in LOADS.md the source and license.
   All of it goes in the load's commit.
6. **If a source's license changes:**
   - stop loading from it;
   - mark it **Suspended** here;
   - tell Jonathan in the next entry;
   - leave rows already loaded in place until he decides.

## Register

| Source | What we use | License | Attribution we give | Verified on | Status | Loads |
|---|---|---|---|---|---|---|
| Repair Wiki (repair.wiki), via its weekly GitHub mirror github.com/repairwiki/repair-wiki-mirror | Repair guides and device pages: titles, links, device, component, repair type, level, difficulty, tools, parts, symptoms (rewritten in own words by Lumi) | CC BY-SA 3.0 | Source "Repair Wiki", link to the original page, Notes "CC BY-SA, credit Repair Wiki + contributors" | 2026-10-13 | Active | 2026-10-13 import (Guides RG-0047 to RG-1050, 401 Devices rows; written to the sheet directly, before this lane existed); 2026-10-13 test load (Guides RG-0047 to RG-0051) |
| iFixit (ifixit.com) | Links and own-words summaries only, added by hand | CC BY-NC-SA 3.0 | Source "iFixit", link to the guide | 2026-10-12 | Links only, never bulk-loaded | None |

## Per-source notes

### Repair Wiki

- **License:** Creative Commons Attribution-ShareAlike 3.0, checked on 2026-10-13. It is recorded in the Repair library's Sources tab (SOP 12 item 6).
- **What it requires:**
  - credit Repair Wiki and the page's contributors, with a link to the page;
  - say what was changed;
  - keep adaptations under the same license.
- **How we comply:**
  - every row links its page and names Repair Wiki;
  - Notes reads "RW import 10/13, CC BY-SA, credit Repair Wiki + contributors";
  - Watch-outs are rewritten in our own words.
- **Share-alike:** the load files built from Repair Wiki in `repair-library/loads/` are licensed CC BY-SA 3.0, with credit to Repair Wiki and its contributors.
- **How we read it:** repair.wiki refuses automated fetches, so we read it through the public mirror's raw markdown and `build/pages.jsonl`. The mirror is the repairwiki organization's own weekly copy of the site.
