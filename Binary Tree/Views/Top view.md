https://www.geeksforgeeks.org/problems/top-view-of-binary-tree/1

```
class Solution {
  public:
    vector<int> topView(Node *root){
        vector<int> ans;
        if(root==NULL) return ans;

		queue<pair<Node*,int>> q;
		map<int,int> top_view;
		
        q.push({root,0});
        while(!q.empty()){
            pair<Node*,int> temp = q.front(); q.pop();
            Node* f_node = temp.first;
            int hd = temp.second;
            
            if(top_view.find(hd) == top_view.end())
                top_view[hd] = f_node->data;
            
            if(f_node->left) q.push({f_node->left,hd-1});
            if(f_node->right) q.push({f_node->right,hd+1});
        }
        
        for(map<int,int>::iterator i=top_node.begin();i!=top_node.end();i++)
            ans.push_back(i->second);
        
        return ans;
    }
};
```

Return -> [[Views]]

