https://leetcode.com/problems/plus-one/?envType=problem-list-v2&envId=array

```
class Solution {
public:
    vector<int> plusOne(vector<int>& digits) {
        reverse(digits.begin(), digits.end());
        int c = 1;
        vector<int> res;
  
        for(int i = 0;i < digits.size(); i++){
            int sum = c + digits[i];
            res.push_back(sum%10);
            c = sum/10;
        }

        if(c == 1) res.push_back(c);
        reverse(res.begin(), res.end());

        return res;        
    }
};
```

Return -> [[Arrays, Prefix-Suffix, Hashing, Maps]]

