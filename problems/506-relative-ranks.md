### 506. Relative Ranks (Easy)

**Pattern:** Sort + HashMap

**Trigger:** "Need rank/order" + "return in original positions"

**Key insight:** Sort a copy to get order; use a value→index Map to map back in O(1)

**Complexity:** O(n log n) time, O(n) space

**Trap:** Using indexOf() in the loop → O(n²)