https://leetcode.com/problems/is-subsequence/description/?envType=study-plan-v2&envId=top-interview-150
###### 2 Pointer Approach
```
class Solution {
public:
    bool isSubsequence(string s, string t) {
        int i=0;
        int j=0;
        while(i<s.size() && j<t.size()){
            if(s[i] == t[j])
                i++;
            j++;
        }
  
        return i == s.size();
    }
};
```

Return -> [[Arrays, Prefix-Suffix, Hashing, Maps]]

