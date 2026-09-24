### 500. Keyboard Row (Easy)

**Pattern:** HashSet Lookup

**Trigger:** "Belongs to a group/row" — every character must come from the same fixed set

**Key insight:** Classify the word by its FIRST char into one row's Set, then verify all other chars are in that same Set

**Complexity:** O(n × L) time, O(n) space

**Trap:** filter(...)[0] instead of find(); missing break after failure; toLowerCase() inside the loop