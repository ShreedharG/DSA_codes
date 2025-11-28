https://leetcode.com/problems/roman-to-integer/

```
class Solution {
public:
    int romanToInt(string s) {
        int n = s.size();
        int ans = 0;
        int i=0;
  
        while(i<n){
            if(i+1<n && s[i]=='I' && (s[i+1]=='V' || s[i+1]=='X')){
                ans += (s[i+1]=='V' ? 4 : 9);
                i = i+2;
            }
            else if(i+1<n && s[i]=='X' && (s[i+1]=='L' || s[i+1]=='C')){
                ans += (s[i+1]=='L' ? 40 : 90);
                i = i+2;
            }

            else if(i+1<n && s[i]=='C' && (s[i+1]=='D' || s[i+1]=='M')){
                ans += (s[i+1]=='D' ? 400 : 900);
                i = i+2;
            }
            else{            
                if(s[i]=='I') ans += 1;
                else if(s[i]=='V') ans += 5;
                else if(s[i]=='X') ans += 10;
                else if(s[i]=='L') ans += 50;
                else if(s[i]=='C') ans += 100;
                else if(s[i]=='D') ans += 500;
                else if(s[i]=='M') ans += 1000;
                i++;
            }
        }
        return ans;
    }
};
```

Return -> [[Strings]]

