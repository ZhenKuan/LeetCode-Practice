# LeetCode-Practice
## 二元搜尋法(Binary Search)
###  35. Search Insert Position
Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

**Example 1:**                                                 
>**Input:** nums = [1,3,5,6], target = 5  
>                                                                               
>**Output:** 2                                                 

**Example 2:**
>**Input:** nums = [1,3,5,6], target = 2
>
>**Output:** 1

**Example 3:**
>**Input:** nums = [1,3,5,6], target = 7
>
>**Output:** 4|

**Example 4:**
>**Input:** nums = [1,3,5,6], target = 0
>
>**Output:** 0

**Example 5:**
>**Input:** nums = [1], target = 0
>
>**Output:** 0

#### Code
```python3
class Solution:
def searchInsert(self, nums: List[int], target: int) -> int:
    lo, hi = 0, len(nums) - 1
    while lo <= hi:
        mi = ( lo + hi ) // 2
        if nums[mi] == target:
            return mi
        elif nums[mi] > target:
            hi = mi - 1
        elif nums[mi] < target:  #else:
            lo = mi +1
   return lo
```

___

### 278. First Bad Version
You are a product manager and currently leading a team to develop a new product. Unfortunately, the latest version of your product fails the quality check. Since each version is developed based on the previous version, all the versions after a bad version are also bad.

Suppose you have n versions [1, 2, ..., n] and you want to find out the first bad one, which causes all the following ones to be bad.

You are given an API bool isBadVersion(version) which returns whether version is bad. Implement a function to find the first bad version. You should minimize the number of calls to the API.

**Example 1:**

>**Input:** n = 5, bad = 4
>
>**Output:** 4
>
>>**Explanation:**
>>
>>call isBadVersion(3) -> false
>>
>>call isBadVersion(5) -> true
>>
>>call isBadVersion(4) -> true
>>
>>**Then 4 is the first bad version.**

#### Code
```Python3
class Solution:
    def firstBadVersion(self, n):
        """
        :type n: int
        :rtype: int
        """
        lo, hi = 1, n
        while lo <= hi:
            mi = (lo + hi) // 2
            if isBadVersion(mi):
                if mi == 1 or not isBadVersion(mi - 1):
                    return mi
                else:
                    hi = mi - 1
            else:
                lo = mi + 1
            
        return None
```
