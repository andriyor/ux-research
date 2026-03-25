# pagination


## Best practices

- [ ] scroll to top after click on page

[UI cheat sheet: pagination, infinite scroll and the load more button | by Tess Gadd | UX Collective](https://medium.com/p/e5c452e279a8)

## Should changing the items per page preserve the current page, or reset and redirect to the first page?

**Why preserving fails:**

- Page meaning changes. Page 5 at 10 items ≠ page 5 at 50 items.
- You can land past the dataset end → empty or confusing results.
- Cursor-based pagination breaks completely since cursors are tied to a specific slice.
- Mental model mismatch: user expects “show more/less”, not “jump somewhere random”.

**When preserving _can_ work (rare):**

- You translate position, not page number:  
    `newPage = floor(((oldPage - 1) * oldSize) / newSize) + 1`
- Dataset is stable (no inserts/deletes affecting order).
- Offset-based pagination only (not cursor).

**Better UX pattern:**

- Reset to page 1 on page size change.
- Optionally show a subtle hint like “Showing more items per page”.
- If continuity matters (e.g., long browsing), use infinite scroll instead of pages.

**Verdict:** default to reset. Preserve only if you explicitly remap position and accept edge-case drift.

Example:

- [https://www.ebay.com/sch/i.html?_from=R40&_nkw=cats&_sacat=0&_ipg=240](https://www.ebay.com/sch/i.html?_from=R40&_nkw=cats&_sacat=0&_ipg=240)


Gmail: separate setting

![](Attachments/Pasted%20image%2020260318231717.png)



## Loader after pagination 

[Loader](Loader.md)

### Without loaders:

https://www.ebay.com/sch/i.html?_from=R40&_nkw=cats&_sacat=0&_pgn=1

### With loader:

Activity indicator, hourglass, spin: 
https://www.amazon.com/s?k=cats&qid=1774463465&xpid=z7xx7-W6lyp0h&ref=sr_pg_1

https://www.aliexpress.com/w/wholesale-raspberry-pi.html?page=3&g=y&SearchText=raspberry+pi&streamId=416d21ff-950c-47f3-87d7-dbdef3c21685

Top loader:
https://www.shutterstock.com/search/cats?kw=shutterstock&page=2

https://rozetka.com.ua/ua/consoles/c80020/page=6/

Skeleton:
https://github.com/pnpm/pnpm/issues?page=8

https://gitlab.com/inkscape/inkscape/-/work_items?sort=created_date&state=opened&first_page_size=20&page_after=eyJjcmVhdGVkX2F0IjoiMjAyNS0wNi0wOCAxOTo1NDowMS4xNzA4MzkwMDAgKzAwMDAiLCJpZCI6IjE2ODYyNTAyNiJ9

https://www.airbnb.com/s/Kyiv--Ukraine/homes?refinement_paths%5B%5D=%2Fhomes&place_id=ChIJBUVa4U7P1EAR_kYBF9IxSXY&date_picker_type=calendar&query=Kyiv%2C%20Ukraine&flexible_trip_lengths%5B%5D=one_week&monthly_start_date=2026-04-01&monthly_length=3&monthly_end_date=2026-07-01&price_filter_input_type=2&channel=EXPLORE&pagination_search=true&price_filter_num_nights=5&federated_search_session_id=6caeb189-3336-45b9-a5fe-b0febaf36051&cursor=eyJzZWN0aW9uX29mZnNldCI6MCwiaXRlbXNfb2Zmc2V0IjozNiwidmVyc2lvbiI6MX0%3D

https://www.linkedin.com/search/results/people/?keywords=Andrii&origin=SWITCH_SEARCH_VERTICAL&page=1&spellCorrectionEnabled=true&prioritizeMessage=false



