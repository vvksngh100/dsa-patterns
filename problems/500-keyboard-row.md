
### `problems/500-keyboard-row.md`

```markdown
# 500. Keyboard Row

**Pattern:** [HashSet Lookup](../patterns/hashset-lookup.md)
**Difficulty:** Easy
**Link:** https://leetcode.com/problems/keyboard-row/

## Problem (short)
Return all words that can be typed using letters from only one row of an
American keyboard.

## Approach
Pre-build a Set per row. Classify the word by its first character, then
verify every other character belongs to the same Set.

## Solution
```js
var findWords = function(words) {
    const keyboardRows = [
        new Set('qwertyuiop'),
        new Set('asdfghjkl'),
        new Set('zxcvbnm')
    ];

    const res = [];
    for (const word of words) {
        const lower = word.toLowerCase();
        const keyRow = keyboardRows.find(row => row.has(lower[0]));

        let flag = true;
        for (let i = 1; i < lower.length; i++) {
            if (!keyRow.has(lower[i])) { flag = false; break; }
        }
        if (flag) res.push(word);
    }
    return res;
};