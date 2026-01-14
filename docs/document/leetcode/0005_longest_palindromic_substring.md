# 5. Longest Palindromic Substring

- [Leetcode: 5. Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/)

## Problem Statement

Given a string `s`, return the longest palindromic substring in `s`.


## Solutions

=== "Brute Force"

    Check all possible substrings and determine if they are palindromes.

    - Time Complexity: `O(n^3)`
    - Space Complexity: `O(1)`

    ```cpp linenums="1"
    string longestPalindrome(string s) {
        int L = 0, R = 0, Max = 0;
        for (int i = 0; i < s.size(); i++) {
            for (int j = i; j < s.size(); j++) {
                int isPalindrome = true;

                for (int k = 0; k < (j - i + 1) / 2; k++) {
                    if (s[i + k] != s[j - k]) {
                        isPalindrome = false;
                        break;
                    }
                }

                if (isPalindrome && j - i + 1 > Max) {
                    L = i;
                    R = j;
                    Max = j - i + 1;
                }
            }
        }

        return string(s.begin() + L, s.begin() + R + 1);
    }
    ```

=== "Expand Around Center"
 
    Expand around each character and each pair of characters to find the longest palindromic substring.

    - Time Complexity: `O(n^2)`
    - Space Complexity: `O(1)`

    ```cpp linenums="1"
    string longestPalindrome(string s) {

        auto expandFromCenter = [&] (int l, int r) {
            while (l >= 0 && r < s.size() && s[l] == s[r]) {
                l--;
                r++;
            }
            l++; r--;
            if (r < l)
                return string("");
            return s.substr(l, r - l + 1);
        };

        string ans = s.substr(0, 1);
        for (int i = 0; i < s.size(); i++) {
            string odd = expandFromCenter(i, i);
            string even = expandFromCenter(i, i + 1);
            if (odd.size() > ans.size())
                ans = odd;
            if (even.size() > ans.size())
                ans = even;
        }

        return ans;
    }
    ```

=== "Dynamic Programming"

    Use a 2D DP table to quickly check if substrings are palindromes. `dp[i][j]` is true if the substring `s[i...j]` is a palindrome.

    If `s[i] == s[j]` and the substring `s[i+1..j-1]` is a palindrome, then `s[i..j]` is also a palindrome, otherwise it is not.

    - Time Complexity: `O(n^2)`
    - Space Complexity: `O(n^2)`

    ```cpp linenums="1"
    string longestPalindrome(string s) {
        vector<vector<bool>> dp(s.size(), vector<bool>(s.size(), false));

        int len = 1, start = 0;
        for (int i = 0; i < s.size(); i++) {
            dp[i][i] = true;
            for (int j = 0; j < i; j++) {
                if (s[j] == s[i] && (i - j < 2 || dp[j + 1][i - 1])) {
                    dp[j][i] = true;
                    if (len < i - j + 1) {
                        len = i - j + 1;
                        start = j;
                    }
                }
            }
        }

        return s.substr(start, len);
    }
    ```

??? Note "Tags"
    - [[leetcode_medium|Leetcode Medium]]
    - [[dynamic_programming|Dynamic Programming]]
    - [[two_pointers|Two Pointers]]
    - [[manacher_algorithm|Manacher's Algorithm]]
