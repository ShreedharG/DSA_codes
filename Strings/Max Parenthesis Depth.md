https://leetcode.com/problems/maximum-nesting-depth-of-the-parentheses/

```
class Solution {
public:
    int maxDepth(string s) {
        int curr_depth = 0;
        int max_depth = 0;
  
        for(int i=0;i<s.size();i++){
            if(s[i]=='('){
                curr_depth++;
                max_depth = max(max_depth,curr_depth);
            }
            else if(s[i]==')')
                curr_depth--;
        }
        return max_depth;
    }
};
```

Return -> [[Strings]]
