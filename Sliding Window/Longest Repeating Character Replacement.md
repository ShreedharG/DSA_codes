https://leetcode.com/problems/longest-repeating-character-replacement/description/
###### Brute-force
```
class Solution {
public:
    int characterReplacement(string s, int k) {
        map<char,int> myMap;
        int n = s.size();
        int maxLen = 0;
  
        for(int i=0;i<n;i++){
            vector<int> hashArr(26,0);
            int max_freq = 0;
            for(int j=i;j<n;j++){
                hashArr[s[j]-'A']++;
                max_freq = max(max_freq, hashArr[s[j]-'A']);
  
                int changes = (j-i+1) - max_freq;
  
                if(changes <= k) maxLen = max(maxLen, j-i+1);
                else break;
            }
  
        }        
        return maxLen;
    }
};
```

###### Sliding Window Optimal
```
class Solution {
public:
    int characterReplacement(string s, int k) {
        map<char,int> myMap;
        int n = s.size();
        int maxLen = 0;
        int left = 0;
        int maxF = 0;

        vector<int> hashArr(26,0);
  
        for(int right=0; right < n; right++){
            hashArr[s[right]-'A']++;
            maxF = max(maxF, hashArr[s[right]-'A']);
  
            while(right-left+1 - maxF > k){
                hashArr[s[left] - 'A']--;
                int newMaxF = 0;
                for(int i=0;i<26;i++)
                    newMaxF = max(newMaxF, hashArr[i]);

                maxF = newMaxF;
                left++;
            }
  
            if(right-left+1 - maxF <= k)
                maxLen = max(maxLen, right-left+1);
        }      
        return maxLen;
    }
};
```

Return -> [[Sliding Window, 2 Pointer Approach]]

