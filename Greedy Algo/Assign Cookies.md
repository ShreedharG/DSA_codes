https://leetcode.com/problems/assign-cookies/

```
class Solution {
public:
    int findContentChildren(vector<int>& g, vector<int>& s) {
        sort(g.begin(),g.end());
        sort(s.begin(),s.end());

        int l=0;
        int r=0;

        int greedy = g.size();
        int size_cook = s.size();  

        while(r < size_cook && l < greedy){
            if(g[l] <= s[r])
                l++;
            r++;
        }
        return l;        
    }
};
```

Return to [[Greedy Algorithms]]


