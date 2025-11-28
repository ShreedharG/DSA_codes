https://www.geeksforgeeks.org/problems/connected-components-in-an-undirected-graph/1

```
class Solution {
  public:
    vector<vector<int>> make_graph(int V,vector<vector<int>>& edges){
        vector<vector<int>> graph(V);
        
        for(int i=0;i<edges.size();i++){
            graph[edges[i][0]].push_back(edges[i][1]);
            graph[edges[i][1]].push_back(edges[i][0]);
        }
        return graph;
    }
    
    vector<vector<int>> getComponents(int V, vector<vector<int>>& edges){
        vector<vector<int>> graph = make_graph(V,edges);
        vector<bool> vis(V,false);
        vector<vector<int>> ans;
        
        for(int i=0;i<V;i++){
           queue<int> q;
           vector<int> component = {};
           
           if(vis[i]==false){
               vis[i] = true;
               q.push(i);
               while(!q.empty()){
                   int node = q.front();
                   q.pop();
                   
                   component.push_back(node);
                   for(int k=0; k < graph[node].size(); k++){
                       if(vis[(graph[node][k])] == false){
                           vis[(graph[node][k])] = true;
                           q.push(graph[node][k]);
                       }
                   }
               }
            }
            if(!component.empty())
                ans.push_back(component);
        }
        return ans;
    }
};

```

Return -> [[Learning]]

