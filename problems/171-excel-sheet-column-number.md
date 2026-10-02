# 171. Excel Sheet Column Number (Easy)

**Pattern:** Base Conversion (1-indexed, reverse of 168)

**Trigger:** "Convert to number" from Excel column letters → base-26 conversion.

**Key insight:** Horner's method: `res = res * 26 + digit`, iterating left-to-right. Each digit is `charCode - 64` (A=1, ..., Z=26). This is the reverse of problem 168.

**Complexity:** O(n) time, O(1) space

**Trap:** Using `charCode % 65 + 1` — only works for uppercase. Use `charCode - 64`. Also: computing `26 ** power` when Horner's method avoids powers entirely.