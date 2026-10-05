# 747. Largest Number At Least Twice of Others (Easy)

**Pattern:** Track Extremes (find max, verify constraint)

**Trigger:** "Largest number at least twice of others" → find the max, then verify every other element satisfies the constraint.

**Key insight:** Two passes: find max and its index, then check `max >= 2 * nums[i]` for every `i !== maxIndex`. **Skip by index, not by value** — duplicate maxes must both be checked.

**Complexity:** O(n) time, O(1) space

**Trap:** Skipping via `if (nums[i] === max) continue` — if the max appears twice, both are skipped, returning the wrong index. Use `if (i === maxIndex) continue` instead. Also: not bailing early when the condition fails.

**Solution:**
```js
var dominantIndex = function(nums) {
    let max = -Infinity, maxIndex = 0;
    for (let i = 0; i < nums.length; i++) {
        if (nums[i] > max) {
            max = nums[i];
            maxIndex = i;
        }
    }

    for (let i = 0; i < nums.length; i++) {
        if (i !== maxIndex && max < 2 * nums[i]) return -1;
    }
    return maxIndex;
};