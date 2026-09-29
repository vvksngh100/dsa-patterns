# 674. Longest Continuous Increasing Subsequence (Easy)

**Pattern:** Sliding Window (variable-size, run tracking)

**Trigger:** "Longest continuous increasing" → track a run; reset when the run breaks.

**Key insight:** Single pass: increment `count` when `nums[i] < nums[i+1]`, otherwise update `max` and reset `count = 1`. The final `Math.max` catches the case where the longest run extends to the end.

**Complexity:** O(n) time, O(1) space

**Trap:** Using `else if (nums[i] > nums[i+1])` — equal elements fall through and don't reset the run, giving wrong answers on inputs like `[1,2,3,3,4]`. Use `else` (any non-increasing pair breaks the run).