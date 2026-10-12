# Leetcode_Day72
# Day 72: Generate Parentheses

**LeetCode Problem:** 22. Generate Parentheses  
**Difficulty:** Medium  
**Topic:** Backtracking, Recursion, Strings  
**Language:** Java

## Problem Statement

Given `n` pairs of parentheses, generate all possible combinations of well-formed parentheses.

A combination is valid when every opening parenthesis has a matching closing parenthesis and the parentheses are correctly ordered.

## Approach: Backtracking

I solved this problem using recursion and backtracking.

The idea is to build valid combinations one character at a time while following two rules:

1. Add an opening parenthesis `(` only when the number of opening parentheses used is less than `n`.
2. Add a closing parenthesis `)` only when the number of closing parentheses used is less than the number of opening parentheses used.

When both counts reach `n`, the current string is complete and is added to the result list.

This approach avoids generating invalid combinations.

## Java Solution

```java
class Solution {
    public void balance(String str, int open, int close,
                        int n, List<String> ans) {

        if (open == n && close == n) {
            ans.add(str);
            return;
        }

        if (open < n) {
            balance(str + "(", open + 1, close, n, ans);
        }

        if (close < open) {
            balance(str + ")", open, close + 1, n, ans);
        }
    }

    public List<String> generateParenthesis(int n) {
        List<String> ans = new ArrayList<>();
        balance("", 0, 0, n, ans);
        return ans;
    }
}
```

## Example 1

**Input:**
```text
n = 3
```

**Output:**
```text
["((()))", "(()())", "(())()", "()(())", "()()()"]
```

**Explanation:** There are five valid combinations of three pairs of parentheses.

## Example 2

**Input:**
```text
n = 1
```

**Output:**
```text
["()"]
```

## Complexity Analysis

- **Time Complexity:** O( n × Cₙ ), where \(C_n\) is the nth Catalan number. There are \(C_n\) valid combinations, each containing `2n` characters.
- **Space Complexity:** O( n × Cₙ ) to store the generated strings, excluding auxiliary recursion space.

## What I Learned

- How backtracking builds solutions step by step.
- How recursion explores different possible combinations.
- Why restricting choices helps avoid invalid results.
- How to use opening and closing counts to maintain balanced parentheses.

## Takeaway

Today's problem reminded me that exploring every possibility doesn't mean accepting every possibility. Setting the right conditions helps us reach valid solutions without wasting effort.

**Day 72 complete — another problem solved, another step forward in my DSA journey.**
