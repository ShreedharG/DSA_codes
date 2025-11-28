https://leetcode.com/problems/word-ladder/

```
class Solution {
public:
    int ladderLength(string beginWord, string endWord, vector<string>& wordList) {
        if(beginWord == endWord) return 2;
  
        set<string> s(wordList.begin(),wordList.end());
        queue<pair<string,int>> q;

        q.push({beginWord,1});
        while(!q.empty()){
            auto [word,length] = q.front();
            q.pop();
  
            if(word==endWord) return length;
  
            for(int i=0;i<word.size();i++){
                char og_letter = word[i];
                for(char j='a'; j<='z'; j++){
                    word[i] = j;
                    if(s.find(word) != s.end()){
                        s.erase(word);
                        q.push({word,length+1});
                    }
                }
                word[i] = og_letter;
            }
        }
        return 0;
    }
};
```

Return -> [[Based on BFS-DFS Traversals]]

