https://leetcode.com/problems/remove-outermost-parentheses/

```
class Solution {
public:
    string removeOuterParentheses(string s) {
        int start = 0;
        string ans = "";
  
        for(int i=0;i < s.size(); i++){
            if(s[i] == '('){
                if(start!=0)
                    ans += s[i];
                start++;
            }
            else{
                if(start!=1)
                    ans += s[i];
                start--;
            }
        }
        return ans;
    }
};
```

Return -> [[Strings]]

