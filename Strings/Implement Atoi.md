https://leetcode.com/problems/string-to-integer-atoi/description/

```
class Solution {
public:
    int myAtoi(string s) {
        int n = s.size();
        int i=0;
        int sign = 1;
        long long num = 0;
        string s_num;
  
        while(i<n && s[i]==' ')
            i++;
            
        if(i < n && (s[i]=='-' || s[i]=='+')){
            sign = (s[i]=='-' ? -1 : 1);
            i++;
        }
  
        while(i<n && s[i]=='0')
            i++;
            
        while(i<n && isdigit(s[i])){
            num = num*10 + s[i] - '0';
  
            if(sign == 1 && num > INT_MAX) return INT_MAX;
            if(sign == -1 && -num < INT_MIN) return INT_MIN;
  
            i++;
        }
        
        return (int)(sign * num);
    }
};
```

Return -> [[Strings]]

