# Monotonic Stack

## When to use (Trigger)
- Problem asks for the **"next greater"** or **"next smaller"** element
- You need the **nearest** element to the left/right that satisfies a comparison
- Brute force would be "scan right/left until you find one" → O(n²)
- Keywords: "next greater", "next smaller", "warmer day", "span", "histogram"

## Template
1. Initialize an empty stack (holds **indices** or **values** waiting for their answer).
2. Iterate through the array once.
3. While the stack is non-empty AND `stack.top` satisfies the comparison with the current element:
   - Pop it — the current element is its answer.
   - Record the answer (in a map or result array).
4. Push the current element onto the stack.
5. After the loop, any leftover elements have **no** greater/smaller element (use default like -1).

## Key insight
Each element is **pushed once and popped at most once**. So the inner `while` loop runs
O(n) times **total** across the whole run — not O(n) per iteration.
This is why the nested loop is still **O(n) amortized**.

## Complexity
- **Time:** O(n) — single pass, each element pushed/popped at most once
- **Space:** O(n) — the stack (and a map if you're answering queries)

## Problems

| # | Problem | Key insight | Trap |
|---|---------|-------------|------|
| 496 | Next Greater Element I | Build a `value → nextGreater` map from nums2 using the stack; then answer nums1 lookups | Thinking the nested `while` makes it O(n²) — it's amortized O(n) |
| 739 | Daily Temperatures | Stack holds **indices**; answer = `currentIndex - poppedIndex` | Storing values instead of indices when you need distances |
| 503 | Next Greater Element II | Circular array → iterate `2 * n` times with `% n` | Forgetting to stop after one full loop |

## The one thing to remember
"Next greater/smaller" → **monotonic stack**. Each element enters and leaves the stack once,
so the nested loop is **O(n) total**, not O(n²).