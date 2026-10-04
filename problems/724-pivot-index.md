# 724. Find Pivot Index (Easy)

**Pattern:** Prefix Sum

**Trigger:** "Find the pivot index where left sum equals right sum" → running sum + total.

**Key insight:** Compute total sum once. Then iterate: `rightSum = total - leftSum - nums[i]`. If `leftSum === rightSum`, return `i`. After comparing, add `nums[i]` to `leftSum` for the next iteration.

**Complexity:** O(n) time, O(1) space

**Trap:** Recomputing right sum by slicing/looping each iteration → O(n²). Mutating `rightSum` inside the loop with confusing conditions.