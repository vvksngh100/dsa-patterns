# Sort + HashMap

## When to use (Trigger)
- Problem asks for **rank**, **order**, or **relative position**
- Results must be returned in the **original order / original positions**
- Ordering requires comparison (so you must sort), but lookup must be fast
- Keywords: "rank", "relative order", "return in original order", "sort by X, output by Y"

## Template
1. Build a `value → original index` Map in **one pass** (O(n)).
2. Sort a **copy** of the array to establish order (O(n log n)).
3. Iterate the sorted array; for each element, use the Map to find where it
   originally lived, and write the result there.
4. Return the result array (or the mutated original).

## Key insight
Sorting tells you the *order*, but destroys the *original positions*.
The Map restores the link between a value and where it came from — in O(1) per lookup.
This turns an O(n²) "search for the element" step into O(n).

## Complexity
- **Time:** O(n log n) — sort dominates; all map operations are O(1)
- **Space:** O(n) — the map + the sorted copy

## Problems

| # | Problem | Key insight | Trap |
|---|---------|-------------|------|
| 506 | Relative Ranks | `medals[i] ?? String(i+1)` for ranks 4+ | Using `indexOf()` inside the loop → O(n²) |
| 1331 | Rank Transform of an Array | Map **distinct sorted values** to their rank | Same `indexOf` trap; also handle duplicates |
| 451 | Sort Characters by Frequency | Frequency map, then sort entries by count | Recomputing counts inside the sort comparator |
| 1122 | Relative Sort Array | Map arr1 values to their order index; sort arr2 by it | Forgetting to append leftover arr1 values in sorted order |

## The one thing to remember
**Never use `indexOf` / `includes` / `find` inside a loop.**
Precompute a `Map` once, then every lookup is O(1). This single habit
converts countless O(n²) solutions into O(n log n) or O(n).