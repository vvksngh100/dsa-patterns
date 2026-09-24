# HashSet Lookup

## When to use (Trigger)
- Problem asks whether an element **belongs to a group / category / row**
- You need **membership testing** ("does X exist in set Y?")
- Repeated checks against a fixed collection of characters/values
- Keywords: "belongs to", "valid word", "contains only", "group", "category"

## Template
1. Pre-build one or more **Sets** (or a single Map) from the allowed values.
2. For each item to validate, pick the correct set (usually based on the first char/value).
3. Check every subsequent part of the item against that same set.
4. Bail out (`break`) as soon as a check fails.

## Key insight
`Set.has(x)` is **O(1)** average; `String.includes(x)` is **O(k)**.
For repeated membership checks, a Set is strictly better.
When items map to different sets, do **one** decision up front
(e.g. "which row does the first char belong to?") and validate the rest against it.

## Complexity
- **Time:** O(n × L) — you must inspect every character of every item (this is optimal)
- **Space:** O(n) for the result; the Sets themselves are O(1) (fixed alphabet/rows)

## Problems

| # | Problem | Key insight | Trap |
|---|---------|-------------|------|
| 500 | Keyboard Row | Decide the row from `word[0]`; check the rest against that row's Set | Missing `break` after failure; using `filter()[0]` instead of `find()` |
| 217 | Contains Duplicate | One pass with a Set; if `has()` → true | Sorting works too but is O(n log n) vs O(n) |
| 349 | Intersection of Two Arrays | Put one array in a Set, filter the other | Duplicates in the result — use a second Set to dedupe |

## The one thing to remember
If you're doing **repeated membership checks**, reach for a `Set`.
If the item first needs to be *classified* (which row/category), do that classification
**once** from a stable key (like the first character), then validate the rest.