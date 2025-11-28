https://leetcode.com/problems/valid-parentheses/

```
class Solution {
public:
    bool isValid(string s) {
        stack<char> myStack;
        int n = s.size();
        for(int i=0;i<n;i++){
            if(s[i]=='(' || s[i]=='{' || s[i]=='[')
                myStack.push(s[i]);
            else{
                if(myStack.empty())
                    return false;
                char top = myStack.top();
                if((top=='(' && s[i]==')') ||
                   (top=='[' && s[i]==']') ||
                   (top=='{' && s[i]=='}'))
                    myStack.pop();
                else
                    return false;
            }
        }
        return myStack.empty();
    }
};
```

Return -> [[Stack and Queue]]