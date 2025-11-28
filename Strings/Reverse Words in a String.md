https://leetcode.com/problems/reverse-words-in-a-string/

```
class Solution {
public:
    string reverseWords(string s) {
        vector<string> words;
        string word = "";
  
        int i=0, n = s.size();
  
        while(i<n){
            while(i<n && s[i] != ' '){
                word += s[i];
                i++;
            }

            if(!word.empty()){
                words.push_back(word);
                word = "";
            }              
            i++;
        }
  
        string ans = "";
        for(int i = words.size()-1; i >= 0; i--){
            ans += words[i];
            if(i==0) break;
            ans += ' ';
        }
  
        return ans;
    }
};
```

Return -> [[Strings]]

