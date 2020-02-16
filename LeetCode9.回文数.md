LeetCode9.回文数
判断一个整数是否是回文数。回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。
示例 1:
输入: 121
输出: true
示例 2:
输入: -121
输出: false
解释: 从左向右读, 为 -121 。 从右向左读, 为 121- 。因此它不是一个回文数。
示例 3:
输入: 10
输出: false
解释: 从右向左读, 为 01 。因此它不是一个回文数。

class Solution {
    public boolean isPalindrome(int x) {
        String s=String.valueOf(x);
        char[] array=s.toCharArray();
        if(array.length<2){
            return true;
        }
        int l=0;
        int r=array.length-1;
        while(l<r){		//优化半点：while(l<=(l+r)/2)
            if(array[l++]!=array[r--]){
                return false;
            }
        }
        return true;
    }
}
思路：利用前后指针，各自对比半段即可
