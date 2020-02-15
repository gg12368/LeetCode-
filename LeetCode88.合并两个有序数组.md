LeetCode88.合并两个有序数组

给定两个有序整数数组 nums1 和 nums2，将 nums2 合并到 nums1 中，使得 num1 成为一个有序数组。
说明:初始化 nums1 和 nums2 的元素数量分别为 m 和 n。你可以假设 nums1 有足够的空间（空间大小大于或等于 m + n）来保存 nums2 中的元素。
示例:
输入:
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6], n = 3

输出:
[1,2,2,3,5,6]

class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int p1 = m - 1;
        int p2 = n - 1;
        int p = m + n - 1;
        while ((p1 >= 0) && (p2 >= 0))
            nums1[p--] = (nums1[p1] < nums2[p2]) ? nums2[p2--] : nums1[p1--];
        System.arraycopy(nums2, 0, nums1, 0, p2 + 1);
    }
}

思路：
需要两个指针p1，p2分别指向两个数组的待比较末尾元素。
另外加上一个指针p用来存储p1和p2指针相比较得出的最大元素。
通过指针的移动解决这个问题。

最后需要考虑nums2数组的前几个元素比nums1数组的索引为0的元素值要小，即p2未指向尽头。
这时需要考虑将已排好序的这几个元素通过System.arraycopy()函数拷贝至nums1数组。
