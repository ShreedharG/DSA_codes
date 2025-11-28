https://leetcode.com/problems/isomorphic-strings/

```
class Solution {
public:
    bool isIsomorphic(string s, string t) {
        map<char,char> st,ts;
        int n = s.size();

        for(int i=0;i<n;i++){
            char a = s[i];
            char b = t[i];

            if(st.find(a)==st.end()) st[a] = b;
            else if(st.find(a)!=st.end() && st[a]!=b) return false;
  

            if(ts.find(b)==ts.end()) ts[b] = a;
            else if(ts.find(b)!=ts.end() && ts[b]!=a) return false;
        }
        return true;
    }
};
```

Return -> [[Strings]]