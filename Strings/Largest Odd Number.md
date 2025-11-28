https://leetcode.com/problems/largest-odd-number-in-string/

```
class Solution {
public:
    string largestOddNumber(string num) {
        int index = -1;
        for(int i=num.size()-1;i>=0;i--){
            if((num[i]-'0')%2==1){
                index = i;
                break;
            }
        }

        if(index==-1) return "";

        string ans;
        for(int i=0;i<=index;i++)
            ans += num[i];
        return ans;
    }
};
```

Return -> [[Strings]]



