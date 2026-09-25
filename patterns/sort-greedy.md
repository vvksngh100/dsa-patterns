# Sort + Greedy

## When to use (Trigger)
- "Maximize / minimize sum" combined with "pairing" or "distribution"
- Elements need to be assigned, matched, or grouped
- The optimal choice depends on relative order, not absolute values
- Keywords: "pair", "maximize sum", "assign", "match", "intervals", "distribute"

## Template
1. Sort the array (ascending or by a specific key).
2. Iterate through the sorted array.
3. At each step, make the locally optimal greedy choice.
4. Accumulate the result.

## Key insight
Sorting converts "which element should I pick?" into a trivial local decision.
Once sorted, the greedy choice is usually obvious — pair adjacent elements,
match smallest to smallest, or process in a fixed order.

## Complexity
- **Time:** O(n log n) — sort dominates
- **Space:** O(1) or O(n) depending on whether you sort in place

## Problems

| # | Problem | Key insight | Trap |
|---|---------|-------------|------|
| 561 | Array Partition | Sort ascending, pair adjacent; take the left element of each pair | Calling it sliding window — no dynamic window, just fixed pairs |
| 455 | Assign Cookies | Sort both arrays; two pointers; give smallest cookie that satisfies | Matching largest to greediest first — smaller-that-satisfies is simpler |
| 435 | Non-overlapping Intervals | Sort by END time; greedily pick earliest-ending non-overlapping | Sorting by START time breaks the greedy proof |
| 452 | Min Arrows to Burst Balloons | Sort by END; shoot at end of first; skip balloons it pops | Shooting at start instead of end — end maximizes overlap |

## The one thing to remember
When "maximize/minimize sum" meets "pairing/matching", **sort first**.
The greedy choice after sorting is almost always "process in order and take the
locally optimal step" — sort by start, end, or value depending on the problem.