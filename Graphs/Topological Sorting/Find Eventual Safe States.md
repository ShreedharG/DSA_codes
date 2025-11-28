https://leetcode.com/problems/find-eventual-safe-states/

```
class Solution {
public:
    vector<int> eventualSafeNodes(vector<vector<int>>& graph) {
        int n = graph.size();
        vector<vector<int>> revGraph(n);
        vector<int> inDegree(n);
  
        for(int i=0;i<n;i++){
            for(auto child : graph[i])
                revGraph[child].push_back(i);
            inDegree[i] = graph[i].size();
        }

        vector<int> ans;
        queue<int> q;
        for(int i=0;i<n;i++){
            if(inDegree[i] == 0)
                q.push(i);
        }
  
        while(!q.empty()){
            int node = q.front();
            q.pop();

            ans.push_back(node);
  
            for(auto neigh : revGraph[node]){
                inDegree[neigh]--;
                if(inDegree[neigh] == 0)
                    q.push(neigh);
            }
        }
        
        sort(ans.begin(),ans.end());
        return ans;
    }
};
```

Return -> [[Topological Sort Problems]]

