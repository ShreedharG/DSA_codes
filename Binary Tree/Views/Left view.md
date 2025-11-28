https://www.naukri.com/code360/problems/left-view-of-a-binary-tree_920519

```
vector<int> getLeftView(TreeNode<int> *root){
    vector<int> ans;
    queue<TreeNode<int>*> q;

    if(root==nullptr)
        return ans;
        
    q.push(root);  

    while(!q.empty()){
        int size_q = q.size();
  
        for(int i=0;i<size_q;i++){
            TreeNode<int> *temp = q.front();
            if(temp->left) q.push(temp->left);
            if(temp->right) q.push(temp->right);
            
            if(i==0) ans.push_back(temp->data);
            q.pop();                
        }
    }
    return ans;
}
```

Return -> [[Views]]

