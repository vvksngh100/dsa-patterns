# 594. Longest Harmonious Subsequence (Easy)

**Pattern:** HashSet Lookup (frequency counting)

**Trigger:** "Longest subsequence" where the max and min differ by exactly 1 → need frequency of adjacent values.

**Key insight:** A harmonious subsequence consists of only two distinct values `x` and `x+1`. Build a frequency Map once, then for each `num` check if `num + 1` exists — the candidate length is `freq[num] + freq[num + 1]`.

**Complexity:** O(n) time, O(n) space

**Trap:** Using a sort + sliding window when a Map gives O(n). Also: `freqMap.get(num+1)` as a truthy check is unsafe — use `.has()`.