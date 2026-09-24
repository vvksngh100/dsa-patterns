# 496. Next Greater Element I

**Pattern:** [Monotonic Stack](../patterns/monotonic-stack.md)
**Difficulty:** Easy
**Link:** https://leetcode.com/problems/next-greater-element-i/

## Problem (short)
Given nums1 (subset of nums2), find the next greater element for each nums1[i]
within nums2. Return -1 if none.

## Approach
Build a `value → nextGreater` map for nums2 using a decreasing monotonic stack.
Answer each nums1 query with an O(1) map lookup.

## Solution
```js
var nextGreaterElement = function(nums1, nums2) {
    const map = new Map();
    const stack = [];

    for (const num of nums2) {
        while (stack.length && stack[stack.length - 1] < num) {
            map.set(stack.pop(), num);
        }
        stack.push(num);
    }

    return nums1.map(n => map.get(n) ?? -1);
};