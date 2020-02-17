LeetCode35.搜索插入位置
给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。
你可以假设数组中无重复元素。

示例 1:
输入: [1,3,5,6], 5
输出: 2

示例 2:
输入: [1,3,5,6], 2
输出: 1

示例 3:
输入: [1,3,5,6], 7
输出: 4

示例 4:
输入: [1,3,5,6], 0
输出: 0

class Solution {
    public int searchInsert(int[] nums, int target) {
        int left=0;
        int right=nums.length-1;
        while(left<=right){
            int mid=(left+right)/2;
            if(nums[mid]==target){
                return mid;
            }else if(nums[mid]>target){
                right=mid-1;
            }else{
                left=mid+1;
            }
        }
        return left;
    }
}

思路：利用二分查找

时间复杂度：O(logn)
空间复杂度：O(1)

需要注意：
int mid = (left + right) / 2;
这种写法在绝大多数情况下没问题，但是在 left 和 right 特别大的场景中，left + right 会发生整形溢出，得到一个负数，mid 的值随之也是负数。
改进的写法是：
int mid = left + (right - left) / 2;
这两种写法事实上没有本质的区别，在 left 和 right 都表示数组索引的时候，几乎不会越界，因为绝大多数情况下不会开那么长的数组。
