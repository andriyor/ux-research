# pagination


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

