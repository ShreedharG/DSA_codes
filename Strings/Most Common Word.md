https://leetcode.com/problems/most-common-word/?envType=problem-list-v2&envId=array

```
class Solution {
public:
    string mostCommonWord(string paragraph, vector<string>& banned) {
        map<string,int> words;
        unordered_set<string> s(banned.begin(),banned.end());
  
        int i = 0, n = paragraph.size();
        string word = "";
  
        while(i < n){
            while(i<n && isalpha(paragraph[i])){
                word += tolower(paragraph[i]);
                i++;
            }
  
            if(!word.empty()){
                if(s.find(word)==s.end())
                    words[word]++;
                word = "";
            }
            i++;
        }
  
        int maxFreq = 0;
        string maxWord = "";
        for (auto &p : words) {
            if (p.second > maxFreq) {
                maxFreq = p.second;
                maxWord = p.first;
            }
        }
  
        return maxWord;        
    }
};
```

Return -> [[Strings]]

