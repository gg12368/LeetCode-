LeetCode709.转换成小写字母
实现函数 ToLowerCase()，该函数接收一个字符串参数 str，并将该字符串中的大写字母转换成小写字母，之后返回新的字符串。
示例 1：
输入: “Hello”
输出: “hello”

示例 2：
输入: “here”
输出: “here”

示例 3：
输入: “LOVELY”
输出: “lovely”

class Solution {
    public String toLowerCase(String str) {
        /*
        if(str==null){
            return null;
        }
        return str.toLowerCase();
        */
        if(str==null){
            return null;
        }
        char[] array=str.toCharArray();
        int length=array.length;
        for(int i=0;i<length;i++){
            if(array[i]>='A'&&array[i]<='Z'){
                array[i]+=32;
            }
        }
        //return String.valueOf(array);
        String s=new String(array);
        return s;
    }
}
