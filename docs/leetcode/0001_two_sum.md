# 1. Two Sum

- [Leetcode: 1. Two Sum](https://leetcode.com/problems/two-sum/)

## Problem Statement
Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.


## Solutions

=== "Hash"
    We can use a hash map to store the indices of the elements as we iterate through the array. For each element, we check if the complement (i.e., `target - nums[i]`) exists in the hash map. If it does, we return the indices of the current element and its complement.

    - Time Complexity: O(n)
    - Space Complexity: O(n)

    ```cpp linenums="1"
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> umap;
        for (int i = 0; i < nums.size(); i++) {
            int n = nums[i];
            if (umap.count(target - n)) {
                return {umap[target - n], i};
            }
            umap[n] = i;
        }
        return {-1, -1};
    }
    ```

=== "Two Pointers"
    This approach is not applicable for this problem since the array is not sorted. However, if the array were sorted, we could use two pointers to find the two numbers that add up to the target.

    - Time Complexity: O(n log n) for sorting, O(n) for the two-pointer traversal, resulting in O(n log n) overall.
    - Space Complexity: O(n)

    ```cpp linenums="1"
    vector<int> twoSum(vector<int>& nums, int target) {
      vector<pair<int, int>> sortedNums;

      for (int i = 0; i < nums.size(); ++i) {
        sortedNums.push_back({nums[i], i});
      }

      sort(sortedNums.begin(), sortedNums.end());

      int L = 0, R = sortedNums.size() - 1;
      while (L < R) {
        int sum = sortedNums[L].first + sortedNums[R].first;
        if (sum == target)
          return {sortedNums[L].second, sortedNums[R].second};
        else if (sum < target)
          ++L;
        else
          --R;
      }
      return {-1, -1}; // Return -1, -1 if no solution is found
    }
    ```

=== "Brute Force"
    We can use a brute force approach by checking every pair of elements in the array to see if they add up to the target. This approach has a time complexity of `O(n^2)`.

    - Time Complexity: O(n^2)
    - Space Complexity: O(1)

    ```cpp linenums="1"
    vector<int> twoSum(vector<int>& nums, int target) {
        for (int i = 0; i < nums.size(); i++) {
            for (int j = i + 1; j < nums.size(); j++) {
                if (nums[i] + nums[j] == target) {
                    return {i, j};
                }
            }
        }
        return {-1, -1};
    }
    ```


??? Note "Tags"
    - [[leetcode_easy|Leetcode Easy]]
    - [[hash|Hash]]
    - [[unordered_map|Unordered Map]]
    - [[two_pointers|Two Pointers]]
