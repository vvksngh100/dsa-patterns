# Prefix Sum

## When to use (Trigger)
- You need **sums of subarrays** or **ranges** many times
- "Find the index where left sum equals right sum"
- "Count subarrays with sum k"
- "Range sum query"
- Keywords: "pivot", "running sum", "cumulative", "left sum equals right sum"

## Template
1. Compute the total sum (once).
2. Maintain a running `leftSum` as you iterate.
3. `rightSum = total - leftSum - currentElement`.
4. Compare / record based on the problem.

## Key insight
Instead of recomputing right sum each iteration (O(n²)), **compute the total once**
and derive `rightSum = total - leftSum - nums[i]` in O(1). This turns an O(n²)
solution into O(n).

## Complexity
- **Time:** O(n) — single pass
- **Space:** O(1) — just the running sum

## Problems

| # | Problem | Key insight | Trap |
|---|---------|-------------|------|
| 724 | Find Pivot Index | `rightSum = total - leftSum - nums[i]` | Recomputing right sum each iteration → O(n²) |
| 560 | Subarray Sum Equals K | Prefix sum + hashmap: `map[prefix]` counts | Forgetting to seed `map[0] = 1` |
| 303 | Range Sum Query | Precompute prefix array; `sum[i..j] = pre[j+1] - pre[i]` | Off-by-one on indices |
| 1480 | Running Sum of 1D Array | Simple prefix sum | Overcomplicating |

## The one thing to remember
**Compute the total once; derive the rest from it.**
`rightSum = total - leftSum - current`. Never recompute sums inside a loop
when you can derive them from a running value.