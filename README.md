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
```
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
