# 645. Set Mismatch (Easy)

**Pattern:** HashSet Lookup (frequency counting)

**Trigger:** "Find the duplicate and missing number" → need frequency of each value and a way to detect absent values.

**Key insight:** Build a frequency Map. Iterate `1..n` — if `count > 1` it's the duplicate; if the key is absent, it's the missing number. One Map gives both answers in O(n).

**Complexity:** O(n) time, O(n) space

**Trap:** Using `indexOf`/`includes` for the missing lookup → O(n²). Also: assuming a number can be both duplicate and missing (impossible — hence the `else if` is safe).