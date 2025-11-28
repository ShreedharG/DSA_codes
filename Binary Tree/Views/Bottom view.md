https://www.geeksforgeeks.org/problems/bottom-view-of-binary-tree/1

```
class Solution {
  public:
    vector<int> bottomView(Node *root){
        map<int,int> bottom_node;
        queue<pair<Node*, int>> q;
        vector<int> ans;
        
        if(root==NULL)
            return ans;
        
        q.push({root,0});
        
        while(!q.empty()){
            pair<Node*,int> temp = q.front();  q.pop();
            Node* front_node = temp.first;
            int hd = temp.second;
            
            bottom_node[hd] = front_node->data;
            
            if(front_node->left) q.push({front_node->left,hd-1});
            if(front_node->right) q.push({front_node->right,hd+1});
        }
        
        for(auto& it:bottom_node)
            ans.push_back(it.second);
            
        return ans;
    }
};
```

Return -> [[Views]]

