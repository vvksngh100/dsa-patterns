# Flatten → Rebuild

## When to use (Trigger)
- Input and output have the **same elements** but different shapes
- Reshape, transpose, or re-chunk an array/matrix
- No element is added, removed, or transformed — only repositioned
- Keywords: "reshape", "transpose", "chunk", "flatten", "reorder"

## Template
1. Validate dimensions if reshaping (`r * c === rows * cols`) — return original on mismatch.
2. Flatten the source into 1D (`.flat()` for 2D arrays).
3. Rebuild the target shape — usually chunk with `.slice(i, i + c)` in a loop.
4. Return the new structure.

## Key insight
Every element maps to exactly one target position by a **fixed rule**. No decisions,
no optimization — just a bijection. If your solution has a `if (should I pick this?)`,
it's the wrong pattern.

## Complexity
- **Time:** O(m × n) — every element touched once
- **Space:** O(m × n) — the flattened intermediate + result

## Problems

| # | Problem | Key insight | Trap |
|---|---------|-------------|------|
| 566 | Reshape the Matrix | Check `r*c === rows*cols`; `flat()` then chunk with `slice` | Using `+` instead of `*`; `flat(Infinity)` overkill |
| 867 | Transpose Matrix | `res[j][i] = mat[i][j]` — pure index mapping | Allocating wrong dimensions |
| 118 | Pascal's Triangle | Build each row from the previous | Off-by-one on the boundaries |

## The one thing to remember
**Same elements, different shape → Flatten → Rebuild.**
No choices to make. If you're choosing, it's a different pattern.