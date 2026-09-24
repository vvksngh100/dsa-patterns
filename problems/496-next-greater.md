### 496. Next Greater Element I (Easy)

**Pattern:** Monotonic Stack + HashMap

**Trigger:** "Next greater element" — nearest element to the right that is greater

**Key insight:** Build a value→nextGreater map for nums2 with a decreasing stack; answer nums1 lookups in O(1)

**Complexity:** O(n + m) time, O(n) space

**Trap:** Using indexOf() + inner scan per query → O(n × m); thinking the nested while makes it O(n²) when it's amortized O(n)