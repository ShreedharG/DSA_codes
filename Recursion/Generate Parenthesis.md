https://leetcode.com/problems/generate-parentheses/

```
class Solution {
public:
    void generate(int open,int close,vector<string>& ans,string& s){
        if(open==0 && close==0){
            ans.push_back(s);
            return;
        }
  
        if(open > close || open<0 || close<0) return;

        s += '(';
        generate(open-1,close,ans,s);
        s.pop_back();

        s += ')';
        generate(open,close-1,ans,s);
        s.pop_back();
    }
  
    vector<string> generateParenthesis(int n) {
        vector<string> ans;
        string s;
  
        generate(n,n,ans,s);
        return ans;
    }
};
```

Return  -> [[Recursion + Backtracking]]