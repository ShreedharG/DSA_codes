https://leetcode.com/problems/valid-anagram/

```
class Solution {
public:
    bool isAnagram(string s, string t) {
        if(s.size() != t.size()) return false;
  
        vector<int> freq(26,0);
        for(int i=0;i<s.size();i++){
            int c1 = s[i] - 'a', c2 = t[i] - 'a';
            freq[c1]++;
            freq[c2]--;
        }      
  
        for(int i=0;i<26;i++)
            if(freq[i] != 0) return false;
        
        return true;        
    }
};
```

Return -> [[Strings]]

