# 70. Climbing Stairs

**Difficulty:** Easy  
**Topics:** Math, Dynamic Programming, Memoization  
**LeetCode Link:** [Climbing Stairs](https://leetcode.com)

---

## 📝 Problem Statement

You are climbing a staircase. It takes `n` steps to reach the top.

Each time you can either climb `1` or `2` steps. In how many distinct ways can you climb to the top?

### Examples

**Example 1:**
```text
Input: n = 2
Output: 2
Explanation: There are two ways to climb to the top:
1. 1 step + 1 step
2. 2 steps
```

**Example 2:**
```text
Input: n = 3
Output: 3
Explanation: There are three ways to climb to the top:
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
```

### Constraints
* `1 <= n <= 45`

---

## 💡 Approach & Intuition

To reach step `n`, you could have only arrived from:
1. Step `n - 1` (by taking a **1-step** jump)
2. Step `n - 2` (by taking a **2-step** jump)

Therefore, the total number of distinct ways to reach step `n` is the sum of the ways to reach `n - 1` and `n - 2`:

\[\text{ways}(n) = \text{ways}(n - 1) + \text{ways}(n - 2)\]

This follows the **Fibonacci sequence**. Instead of using an array of size `n` (which takes O(n) space), we can optimize space by only keeping track of the last two computed values.

---

## ⚙️ Complexity Analysis

* **Time Complexity:** \(\mathcal{O}(n)\) — We loop from `3` up to `n` once.
* **Space Complexity:** \(\mathcal{O}(1)\) — Only two variables are used to store previous states.

---

## 💻 Solution

*(Replace this section with your code file or snippet)*

```python
class Solution:
    def climbStairs(self, n: int) -> int:
        if n <= 2:
            return n
        
        first, second = 1, 2
        for _ in range(3, n + 1):
            first, second = second, first + second
            
        return second
```
