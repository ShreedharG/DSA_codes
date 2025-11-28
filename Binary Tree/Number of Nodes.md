https://leetcode.com/problems/count-complete-tree-nodes/submissions/1806556440/

```
class Solution {
public:
    int countNodes(TreeNode* root) {
        if(root == nullptr)
            return 0;
  
        return 1 + countNodes(root->right) + countNodes(root->left);
    }
};
```

Return -> [[Binary tree]]

