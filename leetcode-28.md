```
28. 实现 strStr()
实现 strStr() 函数。

给你两个字符串 haystack 和 needle ，请你在 haystack 字符串中找出 needle 字符串出现的第一个位置（下标从 0 开始）。如果不存在，则返回  -1 。

 

说明：

当 needle 是空字符串时，我们应当返回什么值呢？这是一个在面试中很好的问题。

对于本题而言，当 needle 是空字符串时我们应当返回 0 。这与 C 语言的 strstr() 以及 Java 的 indexOf() 定义相符。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/implement-strstr
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
```

解题思路：

1. 直接遍历原字符串，再与模板字符串对比，若相等，则逐渐比较下一个字符
2. 如果不相等，从原字符串的下个字符开始，再重新比较与模板字符是否相等
3. 只需比较到 haystack.length() - needle.length() 即可，因为往后比的话，haystack的长度已经不够了，一定找不到了

```
class Solution {
    public int strStr(String haystack, String needle) {
        if(needle.length() == 0){
            return 0;
        }
        if(needle.length() > haystack.length()){
            return -1;
        }
        int right = 0;
        while(right < haystack.length() - needle.length() + 1){
            char c = haystack.charAt(right);
            int begin = right;
            right ++;

            int index = 0;
            while(index < needle.length() && begin < haystack.length()){
                if(needle.charAt(index) != haystack.charAt(begin)){
                    break;
                }
                if(index == needle.length() - 1){
                    return right - 1;
                }

                index ++;
                begin ++;
            }
        }

        return -1;
    }
}
```

