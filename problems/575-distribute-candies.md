# 575. Distribute Candies (Easy)

**Pattern:** HashSet Lookup

**Trigger:** "Maximum distinct" + "distribute n/2" — need the count of unique elements, then apply a constraint.

**Key insight:** Alice can eat at most `n/2` candies, and the number of distinct types available is `set.size`. The answer is `min(n/2, set.size)` — no loop, no greedy decision, just a Set for counting plus a constraint.

**Complexity:** O(n) time, O(n) space

**Trap:** Calling it greedy — there's no loop decision, just `min` of two counts. Also: overcomplicating with a frequency Map when a Set already gives distinct count.
