https://leetcode.com/problems/longest-palindromic-substring/

```
class Solution {
public:
    pair<int,int> expand_center(int j,int i,const string &s){
        while(j>=0 && i<s.size() && s[j]==s[i]){
            j--;
            i++;
        }
        return {j+1,i-1};
    }
  
    string longestPalindrome(string s) {
        int n = s.size();
        if(n <= 1) return s;
  
        int start = 0, end = 0;
  
        for(int i=0;i<n;i++){
            auto [l1,r1] = expand_center(i,i,s);
            auto [l2,r2] = expand_center(i,i+1,s);
  
            if(r1-l1 > end - start){
                start = l1;
                end = r1;
            }
            if(r2-l2 > end - start){
                start = l2;
                end = r2;
            }
        }
  
        return s.substr(start,end-start+1);        
    }
};
```

Return -> [[Strings]]

