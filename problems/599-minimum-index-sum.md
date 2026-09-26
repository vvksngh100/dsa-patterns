# 599. Minimum Index Sum of Two Lists (Easy)

**Pattern:** HashSet Lookup

**Trigger:** "Common elements" + "minimize a sum" → lookup in one list while scanning the other.

**Key insight:** Build a Map from `list1` (value → index). Scan `list2`; when a common item is found, compute the index sum. Track the **minimum** sum: reset `res` when a smaller sum is found, push when tied.

**Complexity:** O(n + m) time, O(n) space

**Trap:** Using `res[count] = item` — creates a sparse array instead of a list. Forgetting to **reset** `res` when a new minimum is found. Calling it "greedy" — there's no choice, just min-tracking.
