# 7. Reverse Integer

- [Leetcode: 7. Reverse Integer](https://leetcode.com/problems/reverse-integer/)

## Problem Statement
Given a signed 32-bit integer `x`, return `x` with its digits reversed. If reversing `x` causes the value to go outside the signed 32-bit integer range `[-2^31, 2^31 - 1]`, then return `0`.

Assume the environment does not allow you to store 64-bit integers (signed or unsigned).

## Solution
```cpp linenums="1"
int reverse(int x) {
    int ans = 0;

    while (x) {
        if (ans > INT_MAX / 10 || ans < INT_MIN / 10)
            return 0;
        ans = ans * 10 + x % 10;
        x /= 10;
    }

    return ans;
}
```

??? Note "Tags"
    - [[leetcode_medium|Leetcode Medium]]
