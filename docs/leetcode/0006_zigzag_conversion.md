# 6. Zigzag Conversion

- [Leetcode: Zigzag Conversion](https://leetcode.com/problems/zigzag-conversion/)

## Problem Statement
The string `"PAYPALISHIRING"` is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)

```
P   A   H   N
A P L S I I G
Y   I   R
```

And then read line by line: `"PAHNAPLSIIGYIR"`

Write the code that will take a string and make this conversion given a number of rows:

```
string convert(string s, int numRows);
```

## Solutions

=== "Direction Flag"

    Push the characters into a vector of strings, one for each row. Use a direction flag to determine whether to move down or up the rows. When reaching the top or bottom row, reverse the direction.

    - Time Complexity: O(n)
    - Space Complexity: O(n)

    ```cpp linenums="1"
    string convert(string s, int numRows) {
        if (numRows == 1)
            return s;

        vector<string> rowStrs(numRows);
        int dir = 1, row = 0;
        for (auto &c: s) {
            rowStrs[row] += c;
            row += dir;
            if (row == 0 || row == numRows - 1)
                dir *= -1;
        }

        string ans = "";
        for (auto &str: rowStrs)
            ans += str;
        return ans;
    }
    ```

=== "Find Pattern"

    Calculate the length of each zigzag segment and use it to determine the characters' positions in the output string. This method avoids using extra space for row strings.

    - Time Complexity: O(n)
    - Space Complexity: O(1)

    ```cpp linenums="1"
    string convert(string s, int numRows) {
        if (numRows == 1)
            return s;

        string ans = "";
        int step = 2 * numRows - 2;
        for (int row = 0; row < numRows; row++) {
            for (int i = row; i < s.size(); i += step) {
                ans += s[i];
                int complement = i + step - 2 * row;
                if (!(row == 0 || row == numRows - 1) && complement < s.size())
                    ans += s[complement];
            }
        }
        return ans;
    }
    ```

??? Note "Tags"
    - [[leetcode_medium|Leetcode Medium]]
