# 205. Isomorphic Strings (Easy)

**Pattern:** HashSet Lookup (bidirectional mapping)

**Trigger:** "Isomorphic" — check if characters in `s` can be consistently replaced to get `t`, and vice versa.

**Key insight:** Isomorphism is a **bijection**. Track BOTH `s → t` and `t → s`. Checking only one direction misses cases where two different characters in `s` both map to the same character in `t`.

**Complexity:** O(n) time, O(k) space (k = distinct characters)

**Trap:** Using only one map — fails on `s = "badc"`, `t = "baba"` (both `b` and `d` would map to `b`). Must verify `t → s` too.

**Solution:**
```js
var isIsomorphic = function(s, t) {
    if (s.length !== t.length) return false;

    const sMap = new Map();
    const tMap = new Map();
    for (let i = 0; i < s.length; i++) {
        const a = s[i];
        const b = t[i];

        if (sMap.has(a)) {
            if (sMap.get(a) !== b) return false;
        } else {
            sMap.set(a, b);
        }

        if (tMap.has(b)) {
            if (tMap.get(b) !== a) return false;
        } else {
            tMap.set(b, a);
        }
    }
    return true;
};