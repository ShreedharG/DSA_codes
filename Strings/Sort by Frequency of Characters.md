https://leetcode.com/problems/sort-characters-by-frequency/

```
class Solution {
public:
    static bool comp_f(pair<char,int> a,pair<char,int> b){
        return a.second > b.second;
    }
  
    string frequencySort(string s) {
        map<char,int> freq;
        for(auto c : s)
            freq[c]++;

        vector<pair<char,int>> vec(freq.begin(), freq.end());
        sort(vec.begin(),vec.end(), comp_f);
  
        string ans = "";
        for(auto& v : vec)
            ans += string(v.second,v.first);
        return ans;
    }
};
```

Return -> [[Strings]]

