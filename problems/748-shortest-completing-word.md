# 748. Shortest Completing Word (Easy)

**Pattern:** HashSet Lookup (frequency counting)

**Trigger:** "Shortest word that contains all letters of the plate" → frequency map + verification.

**Key insight:** Build a frequency map for letters in `licensePlate` (ignoring digits and case). For each word, build its own frequency map, then verify each required letter's count is satisfied. Track the shortest valid word.

**Complexity:** O(L + Σ|word|) time, O(26) space

**Trap:** Using `licenseMap.get(licenseMap)` instead of `get(char)` — count never increments. Forgetting `.toLowerCase()`. Using `\w` regex (includes digits and `_`). Inverted minimization: `min < word.length` gives the longest word; want `<`.

**Solution:**
```js
var shortestCompletingWord = function(licensePlate, words) {
    const required = new Map();
    for (const char of licensePlate) {
        const lower = char.toLowerCase();
        if (lower >= 'a' && lower <= 'z') {
            required.set(lower, (required.get(lower) ?? 0) + 1);
        }
    }

    let res = '';
    let min = Infinity;
    for (const word of words) {
        const count = new Map();
        for (const c of word.toLowerCase()) {
            count.set(c, (count.get(c) ?? 0) + 1);
        }
        let flag = true;
        for (const [char, need] of required) {
            if ((count.get(char) ?? 0) < need) { flag = false; break; }
        }
        if (flag && word.length < min) {
            min = word.length;
            res = word;
        }
    }
    return res;
};