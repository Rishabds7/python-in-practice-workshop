# Python in Practice: Workshop Exercises

Here is the starter code for the exercises we'll work on during the workshop. You can copy each code block into your own Jupyter notebook or a Python file.

Try solving the exercises before looking at the walkthrough on screen. The solutions are not included here.

## 1. Refactor a login function

The login function works, but it's doing several things at once. Can you make it easier to read and maintain?

Try using clear function names, `snake_case`, and smaller functions that each have one job. Keep the same login behavior.

```python
def LoginUser(UserName, Password, Users):
    UserName = UserName.strip().lower()

    if UserName not in Users:
        print("User not found")
        return False

    if Users[UserName] != Password:
        print("Incorrect password")
        return False

    print("Login successful")
    return True


users = {
    "alex_21": "Python2026",
    "maya_dev": "SecurePass9",
}
```

## 2. Work with Python built-in tools

We've recorded how many times each user entered an incorrect password. Use `enumerate()`, `zip()`, `sorted()`, and `any()` to answer the questions below.

1. Number the users starting from 1.
2. Show each username with its number of failed attempts.
3. List the users from most failed attempts to least.
4. Check whether anyone has 3 or more failed attempts.

```python
usernames = ["alex_21", "sam99", "maya_dev", "dev_01"]
failed_attempts = [1, 3, 0, 2]

# Write your code here.
```

## 3. Practice list comprehensions

We have a few user accounts with their activity status and scores. Create a new list containing only the usernames of **active users with scores of 80 or higher**.

Try doing it with a list comprehension rather than a regular `for` loop.

```python
users = [
    {"username": "alex_21", "active": True, "score": 82},
    {"username": "sam99", "active": False, "score": 91},
    {"username": "maya_dev", "active": True, "score": 88},
    {"username": "dev_01", "active": True, "score": 74},
]

selected_users = []

print(selected_users)
```

Expected result: `['alex_21', 'maya_dev']`

## 4. Debugging: Average login attempts

This function should calculate the average number of login attempts, but there are a couple of mistakes in the code.

Uncomment the last two lines, run the program, and look at the error message. Fix one issue at a time. If you're using VS Code, try adding a breakpoint and checking the variables.

```python
def average_attempts(attempts):
    return sum(attempts) / len(attempt)

attempts = ["1", "2", "3", "2"]

# Uncomment these lines to test the function:
# average = average_attempts(attempts)
# print(average)
```

Expected result after fixing the code: `2.0`

## 5. Debugging: Merge Sorted Array (LeetCode 88)

[View the original problem on LeetCode](https://leetcode.com/problems/merge-sorted-array/)

You are given two sorted lists of numbers. The first list has enough extra space to hold the values from the second list. Merge them so that `nums1` contains all the numbers in sorted order.

The code below runs, but it doesn't work correctly for this test case. Use the debugger to follow `i`, `j`, and `k`, and find out why.

```python
def merge(nums1, m, nums2, n):
    i = m - 1
    j = n - 1
    k = m + n - 1

    while i >= 0 and j >= 0:
        if nums1[i] > nums2[j]:
            nums1[k] = nums1[i]
            i -= 1
        else:
            nums1[k] = nums2[j]
            j -= 1
        k -= 1


nums1 = [4, 5, 6, 0, 0, 0]
merge(nums1, 3, [1, 2, 3], 3)
print(nums1)
```

Expected result: `[1, 2, 3, 4, 5, 6]`

## 6. Debugging: Top K Frequent Elements (LeetCode 347)

[View the original problem on LeetCode](https://leetcode.com/problems/top-k-frequent-elements/)

Given a list of numbers, return the `k` numbers that appear most often. The order of the returned numbers doesn't matter.

This solution uses `Counter`, `sorted()`, and a `lambda` function, but it produces the wrong result. Run it first, then use a breakpoint to inspect `frequency`, `ranked`, and `result`.

```python
from collections import Counter


def top_k_frequent(nums, k):
    frequency = Counter(nums)
    ranked = sorted(frequency, key=lambda num: frequency[num])
    result = ranked[:k]
    return result


nums = [1, 1, 1, 2, 2, 3]
k = 2

print(top_k_frequent(nums, k))
```

Expected result: `[1, 2]` (in either order)

---

