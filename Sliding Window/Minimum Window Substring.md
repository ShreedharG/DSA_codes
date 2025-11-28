https://leetcode.com/problems/minimum-window-substring/

```
class Solution {
public:
    bool checkWind(unordered_map<char,int>& ms,unordered_map<char,int>& mt){
        for(auto& p : mt){
            if(ms[p.first] < p.second)
                return false;
        }
        return true;
    }

    string minWindow(string s, string t) {
        if(s.size() < t.size()) return "";
        if(s == t) return s;
  
        unordered_map<char,int> mt;
        for(auto c : t)
            mt[c]++;

        int ans = INT_MAX;
        int n = s.size();
        int left = 0;
        unordered_map<char,int> ms;
        int s_l = 0, s_r = 0;
  
        for(int right=0;right<n;right++){
            ms[s[right]]++;
  
            while(checkWind(ms,mt)){
                if(ans > right-left+1){
                    ans = right-left+1;
                    s_r = right;
                    s_l = left;
                }

                ms[s[left]]--;
                if(ms[s[left]] == 0)
                    ms.erase(s[left]);
                left++;
            }
        }
  
        return ans==INT_MAX ? "" : s.substr(s_l, s_r-s_l+1);
    }
};
```

Return -> [[Sliding Window, 2 Pointer Approach]]

