LeetCode383.赎金信

给定一个赎金信 (ransom) 字符串和一个杂志(magazine)字符串，判断第一个字符串ransom能不能由第二个字符串magazines里面的字符构成。如果可以构成，返回 true ；否则返回 false。
(题目说明：为了不暴露赎金信字迹，要从杂志上搜索各个需要的字母，组成单词来表达意思。)

注意：
你可以假设两个字符串均只含有小写字母。
canConstruct(“a”, “b”) -> false
canConstruct(“aa”, “ab”) -> false
canConstruct(“aa”, “aab”) -> true

class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
        int[ ] buckets=new int[26];
        for(int i=0;i<magazine.length();i++){
            buckets[magazine.charAt(i)-'a']++;
        }
        for(int j=0;j<ransomNote.length();j++){
            if(--buckets[ransomNote.charAt(j)-'a']<0){
                return false;
            }
        }
        return true;
    }
}

思路：
本题重在理解题意，采用巧妙构思。
题意：有两个字符串a和b，要求使用b中包含的字符组成a，b中的每个字符只能用一次。
构思：使用了桶来进行计数，首先遍历字符串b，将b中的字母及其频次存入桶中，例如a就会存在桶的0这个索引位置。然后再遍历字符串a，每次遍历将a的的这个字符对应的桶中的数-1，如果这个桶为负数，则会返回false，说明这个桶中的元素不够用了。
