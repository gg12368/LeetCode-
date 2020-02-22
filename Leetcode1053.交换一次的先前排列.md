Leetcode1053. 交换一次的先前排列

给你一个正整数的数组 A（其中的元素不一定完全不同），请你返回可在 一次交换（交换两数字 A[i] 和 A[j] 的位置）后得到的、按字典序排列小于 A 的最大可能排列。
如果无法这么操作，就请返回原数组。

示例1：
输入：[3,2,1]
输出：[3,1,2]
解释：交换2和1

示例2：
输入：[1,1,5]
输出：[1,1,5]
解释：这已经是最小排列


class Solution {
     public int[] prevPermOpt1(int[] A) {
        for(int i = A.length - 2; i >=0; i--){
            //说明找到了第一个非递减的数
            if(A[i] > A[i+1]){
                //找到从i+1下标后中最大的数
                int index = i+1;
                for(int j = i+2;j < A.length;j++){
                    //第一个非递减的数还得小于后面数组中最大的数，否则交换完后的数字可能大于原数字
                   if(A[i] > A[j] && A[index] < A[j]){
                       index = j;
                   }
                }
                //这里出来后说明已经找到最大的数,其下标也被记住，直接交换即可
                int t = A[i];
                A[i] = A[index];
                A[index] = t;
                return A;                    
            }
        }
        return A;
    }
}
