https://www.geeksforgeeks.org/problems/minimum-window-subsequence/1

```
class Solution {
  public:
    string minWindow(string& s1, string& s2){
        if(s1.size() < s2.size()) return "";
        if(s1 == s2) return s1;
        
        int n = s1.size();
        int m = s2.size();
        int i = 0, j = 0;
        int start = -1;
        int minLen = INT_MAX;
        
        while(i < n){
            if(s1[i] == s2[j]){
                j++;
                if(j == m){
                    int end = i;
                    j--;
                    int k = i;
                    while(j >= 0){
                        if(s1[k] == s2[j])
                            j--;
                        k--;
                    }
                    k++;
                    
                    if(minLen > end-k+1){
                        minLen = end-k+1;
                        start = k;
                    }
                    j = 0;
                    i = k;
                }
            }
            i++;
        }
        
        return (start == -1) ? "" : s1.substr(start, minLen);
    }
};
```

Return -> [[Sliding Window, 2 Pointer Approach]]

