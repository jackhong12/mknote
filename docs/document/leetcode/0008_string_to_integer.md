# 8. String to Integer

```cpp linenums="1"
int myAtoi(string s) {
    int i = 0;
    long long value = 0;
    bool negative = false;

    // skip leading spaces
    for (; i < s.size() && s[i] == ' '; i++) ;

    // parse signed character
    if (i < s.size()) {
        if (s[i] == '+')
            i++;
        else if (s[i] == '-') {
            negative = true;
            i++;
        }
    }

    // parse digital characters
    for (; i < s.size(); i++) {
        if (s[i] < '0' || s[i] > '9')
            break;
        value *= 10;
        value += s[i] - '0';
        value = min(value, (long long) 1 << 31);
    }
    return negative ? -value : min(value, (long long)INT_MAX);
}
```
