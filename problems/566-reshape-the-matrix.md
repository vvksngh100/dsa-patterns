# 566. Reshape the Matrix (Easy)

**Pattern:** Flatten → Rebuild

**Trigger:** "Reshape" — same elements, different shape. No element added, removed, or transformed.

**Key insight:** Validate `r * c === rows * cols` first; return original on mismatch. Then `flat()` the matrix to 1D and chunk it with `.slice(i, i + c)` in a loop. Every element maps to a fixed target position — no decisions to make.

**Complexity:** O(m × n) time, O(m × n) space

**Trap:** Using `+` instead of `*` in the size check (`mat.length + mat[0].length`) — returns wrong fallback. Also: `flat(Infinity)` is overkill for a 2D matrix; and `[...arr.slice(...)]` double-copies.