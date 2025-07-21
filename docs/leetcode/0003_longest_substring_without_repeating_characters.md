# 3. Longest Substring Without Repeating Characters

- [Leetcode: 3. Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

## Problem Statement
Given a string `s`, find the length of the longest substring without duplicate characters.

## Solutions

=== "Hash"
    ```cpp linenums="1"
    int lengthOfLongestSubstring(string s) {
        vector<int> table(256, -1);

        int l = 0, ans = 0;
        for (int i = 0; i < s.size(); i++) {
            char c = s[i];
            l = max(table[c] + 1, l);
            ans = max(i - l + 1, ans);
            table[c] = i;
        }
        return ans;
    }
    ```

??? Note "Tags"
    - [[leetcode_medium|Leetcode Medium]]
    - [[hash|Hash]]
