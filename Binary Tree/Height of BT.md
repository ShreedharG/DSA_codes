https://leetcode.com/problems/maximum-depth-of-binary-tree/

```
class Solution {
public:
    int maxDepth(TreeNode* root) {
        if(root==nullptr)
            return 0;
        
        return 1+max(maxDepth(root->left),maxDepth(root->right));        
    }
};
```


Return to [[Binary tree]]

