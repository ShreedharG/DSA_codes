https://chatgpt.com/c/689a4c48-29d4-8332-be7c-5b084d412358

```
class Solution {
public:
    int widthOfBinaryTree(TreeNode* root){
        unsigned long long ans = 0;
        if(root==nullptr)
            return ans;

        queue<pair<TreeNode*,unsigned long long>> q;
        q.push({root,0});
        
        while(!q.empty()){
            int n = q.size();
            unsigned long long first,last;

            for(int i=0;i<n;i++){
                pair<TreeNode*,unsigned long long> front = q.front(); q.pop();

                TreeNode* f_node = front.first;
                unsigned long long index = front.second;
  
                if(i==0) first = index;
                if(i==n-1) last = index;
  
                if(f_node->left) q.push({f_node->left,2*index});
                if(f_node->right) q.push({f_node->right,2*index+1});
            }
            ans = max(ans,last-first+1);
        }
        return (int)ans;
    }
};
```

Return -> [[Binary tree]]