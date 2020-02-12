LeetCode917.仅仅反转字母

给定一个字符串 S，返回 “反转后的” 字符串，其中不是字母的字符都保留在原地，而所有字母的位置发生反转。
示例 1：
输入：“ab-cd”
输出：“dc-ba”
示例 2：
输入：“a-bC-dEf-ghIj”
输出：“j-Ih-gfE-dCba”
示例 3：
输入：“Test1ng-Leet=code-Q!”
输出：“Qedo1ct-eeLg=ntse-T!”

class Solution {
    public String reverseOnlyLetters(String S) {
        char[] array=S.toCharArray();
        Stack<Character> letters = new Stack();
        for (char c: array)
            if (Character.isLetter(c))
                letters.push(c);

        StringBuilder ans = new StringBuilder();
        for (char c: array) {
            if (Character.isLetter(c))
                ans.append(letters.pop());
            else
                ans.append(c);
        }

        return ans.toString();
        //StringBuilder叫字符串缓存区对象,使用时可以不断添加字符、字符串等已有内容。
        //需要使用时调用toString()获得对象里的所有字符串

		//思路：将 s 中的所有字母单独存入栈中，所以出栈等价于对字母反序操作。（或者，可以用数组存储字母并反序数组。）
		//然后，遍历 s 的所有字符，如果是字母我们就选择栈顶元素输出。

    }
}
