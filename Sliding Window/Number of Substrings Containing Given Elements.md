https://leetcode.com/problems/number-of-substrings-containing-all-three-characters/

```
class Solution {
public:
    int numberOfSubstrings(string s) {
        int n = s.size();
        int left = 0;
        int ans = 0;
        unordered_map<char,int> myMap;
  
        for(int right = 0; right < n; right++){
            myMap[s[right]]++;
  
            while(myMap['a']>0 && myMap['b']>0 && myMap['c']>0){
                ans += (n-right);
                myMap[s[left]]--;
                left++;
            }    
        }
        return ans;
    }
};
```

Return -> [[Sliding Window, 2 Pointer Approach]]

