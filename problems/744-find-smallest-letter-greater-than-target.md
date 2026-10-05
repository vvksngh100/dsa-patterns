# 744. Find Smallest Letter Greater Than Target (Easy)

**Pattern:** Binary Search (boundary variant)

**Trigger:** Sorted array + "find smallest element greater than X" → boundary binary search.

**Key insight:** Use the **boundary** form of binary search: `left < right`, `right = mid` (not `mid - 1`). After the loop, `left` points to the first index where `letters[left] > target`. Wrap with `% letters.length` for the "no such letter" case.

**Complexity:** O(log n) time, O(1) space

**Trap:** Using the exact-match form (`left <= right`, `mid ± 1`) — that's for finding a value, not a boundary. Also: forgetting the wrap-around when target is ≥ the largest letter.

**Solution:**
```js
var nextGreatestLetter = function(letters, target) {
    let left = 0, right = letters.length;
    while (left < right) {
        const mid = left + Math.floor((right - left) / 2);
        if (letters[mid] <= target) left = mid + 1;
        else right = mid;
    }
    return letters[left % letters.length];
};