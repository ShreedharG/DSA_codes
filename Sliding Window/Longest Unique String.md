https://leetcode.com/problems/longest-substring-without-repeating-characters/submissions/1775380777/

```
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int n = s.size();
        int left = 0;
        int maxLen = 0;
        set<char> mySet;
  
        for(int right = 0;right < n;right++){
            // Not unique character
            while(mySet.find(s[right]) != mySet.end()){
                mySet.erase(s[left]);
                left++;
            }
            
            mySet.insert(s[right]);
            maxLen = max(maxLen,right-left+1);
        }
        return maxLen;
    }
};
```

Return -> [[Sliding Window, 2 Pointer Approach]]

