# 605. Can Place Flowers (Easy)

**Pattern:** Greedy — Neighbor Constraint

**Trigger:** "Can place" + "no two adjacent" → local constraint, greedily plant earliest valid spot.

**Key insight:** At each index, if `left === 0 && center === 0 && right === 0`, plant there. Committing immediately (mutate `flowerbed[i] = 1`) makes neighbors see the choice. Greedy is provably optimal because earliest placement leaves the most room to the right.

**Complexity:** O(n) time, O(1) space

**Trap:** Setting `flowerbed[i] = 0` instead of `= 1` — the whole algorithm depends on committing the choice so neighbors are updated. Also: forgetting boundary handling for `i=0` and `i=length-1` (treat out-of-bounds as `0`).