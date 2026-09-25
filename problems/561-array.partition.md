### 561. Array Partition (Easy)

**Pattern:** Sort + Greedy

**Trigger:** "Maximize sum of minimums" + pairing/distribution of array elements

**Key insight:** Sort ascending, pair adjacent elements. The larger element in each pair is "wasted" either way — sorting minimizes that waste by keeping pairs as close as possible.

**Complexity:** O(n log n) time, O(1) space (in-place sort)

**Trap:** Mistaking this for sliding window. There is no dynamic window — just fixed pairs over a sorted array. Also: thinking O(n) is possible in the general case — it isn't; Ω(n log n) is the comparison-sort lower bound.