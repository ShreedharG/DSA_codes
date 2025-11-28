https://leetcode.com/problems/course-schedule/

```
class Solution {
public:
    vector<vector<int>> make_graph(vector<vector<int>>& edges,int numCourses,vector<int>& inDegree){
        vector<vector<int>> graph(numCourses);
        for(int i=0; i < edges.size(); i++){
            graph[edges[i][1]].push_back(edges[i][0]);
            inDegree[edges[i][0]]++;
        }
        return graph;
    }

    bool canFinish(int numCourses, vector<vector<int>>& prerequisites) {
        vector<int> inDegree(numCourses,0);
        vector<vector<int>> graph = make_graph(prerequisites,numCourses,inDegree);
        
        queue<int> q;
        vector<int> topo_sort;
  
        for(int i=0;i<numCourses;i++){
            if(inDegree[i] == 0)
                q.push(i);
        }
  
        while(!q.empty()){
            int node = q.front();
            q.pop();

            topo_sort.push_back(node);
            
            for(auto neigh : graph[node]){
                inDegree[neigh]--;
                if(inDegree[neigh] == 0)
                    q.push(neigh);
            }
        }

        return (topo_sort.size() == numCourses);
    }
};
```


Return -> [[Topological Sort Problems]]

