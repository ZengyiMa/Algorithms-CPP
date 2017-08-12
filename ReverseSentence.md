# 翻转句子

描述:句子反转 “I am a student.” -> “student. a am I”


思路:
先反转一个句子，然后根据空格在反转回来，注意，在结尾处也要反转一次

```
class Solution {
public:
    string ReverseSentence(string str) {
        if(str.length() == 0) return str;
        
        reverseString(str, 0, str.length() - 1);
        
        int ps = 0;

        for (int i = 0; i < str.length(); ++i) {
            if (str[i] == ' ') {
                // 是空格；
                reverseString(str, ps, i - 1);
                ps = i + 1;
            } else if (i == str.length() - 1) {
                // 结尾
               reverseString(str, ps, i);
            }
        }
           
        return str;
        
    }
    void reverseString(string &str, int s, int e) {
        while (s <= e) {
            char temp = str[s];
            str[s++] = str[e];
            str[e--] = temp;
        }
    }
    
    
    
};
```