# Sort + HashMap

## When to use
- Need to determine rank, order, or relative position
- Must return results in the ORIGINAL order/positions
- Ordering requires comparison; lookup must be fast

## Template
1. Build a Map from value → original index (once, O(n))
2. Sort a COPY of the array to establish order
3. Iterate sorted; assign result to original position via the Map
4. Return

## Problems
| # | Problem | Key insight | Trap |
|---|---------|-------------|------|
| 506 | Relative Ranks | medals[0..2] + String(i+1) | indexOf in loop → O(n²) |
| 1331 | Rank Transform | Map distinct sorted values | O(n²) via indexOf |
| 451 | Sort by Frequency | freq map + sort by count | recomputing counts |

## The one thing to remember
Never use indexOf/includes/find inside a loop. Precompute into a Map.