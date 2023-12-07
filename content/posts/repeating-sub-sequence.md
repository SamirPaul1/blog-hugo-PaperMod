---
title: repeating sub sequence
tags: [interviewbit]
keywords: interviewbit, interviewbit solution in Python3 C++ Java, repeating sub sequence solution
description: repeating sub sequence Interviewbit Solution Explained
cover:
    image: https://scdn.netlify.app/img/interviewbit-cover.jpg
    alt: interviewbit-cover
    caption: interviewbit-cover
image: https://scdn.netlify.app/img/interviewbit-cover.jpg
date: 2021-10-04T15:58:26+08:00
lastmod: 2022-03-04T15:58:26+08:00
draft: false
author: Samir Paul
authorLink: https://twitter.com/intent/follow?screen_name=SamirPaulb
license: CC BY 4.0
---

# Repeating Sub-Sequence

https://www.interviewbit.com/problems/repeating-subsequence/


Given a string, find if there is any sub-sequence that repeats itself.
A sub-sequence of a string is defined as a sequence of characters
generated by deleting some characters in the string without changing
the order of the remaining characters.

```
Input:
string

Output: 0/1
0 -> No
1 -> Yes

Example:
abab ------> yes, ab is repeated. So, return 1. 
abba ------> No, a and b follow different order. So, return 0. 

NOTE : sub-sequence length should be greater than or equal to 2
```

## Hint1

Our task is to find a repeating subsequence. 
Or rather, lets say if we can find the longest repeating subsequence. If the length > 1, we return 0.

Now, to find longest repeating subsequence, lets try finding the longest common subsequence between the string A and itself ( LCS(A, A) ). 
The only restriction we want to impose is that you cannot match a character with its replica in the other string. 
In other words, if S1 and S2 are the replicas of the string for which we want to find LCS, S1[i] != S2[i] for all index i.

## Solution Approach


Ok here we will see what is the recurrance relation for our problem
```
Rec(i, j) =   |
              |   Rec(i + 1, j)
         max  |
              |   Rec(i, j + 1)
              |
              |   Rec(i + 1, j + 1) + 1 IF i != j and A[i] == A[j] 
              |
```
We will leave it upto you to take care of the base cases

Happy Coding


## Solution
### Editorial
```cpp
int N;
vector<vector<int>> dp;

int rec(int x, int y, string str) {

    if (x == N || y == N)
        return 0;

    if (dp[x][y] != -1)
        return dp[x][y];

    int ans = rec(x + 1, y, str);
    ans = max(ans, rec(x, y + 1, str));
    if (x != y && str[x] == str[y]) {
        ans = max(ans, rec(x + 1, y + 1, str) + 1);
    }

    return dp[x][y] = ans;
}

int Solution::anytwo(string str) {
    N = str.size();
    dp.clear();
    dp.resize(N, vector<int>(N, -1));

    int ans = rec(0, 0, str);
    return ans >= 2;
}

```

### Mine
```cpp
int Solution::anytwo(string A) {
    unordered_map<char, vector<int>> m;
    string s;
    for (int i = 0; i < A.length(); i++) {
        m[A[i]].push_back(i);
        if (m[A[i]].size() >= 3) {
            return 1;
        }
    }
    for (int i = 0; i < A.length(); i++) {
        if (m[A[i]].size() == 2) {
            s = s + A[i];
        }
    }
    int i = 0, j = s.length() - 1;
    while (i < j) {
        if (s[i] != s[j]) {
            return 1;
        } else {
            i++;
            j--;
        }
    }
    return 0;
}
```

## Asked in

* Google