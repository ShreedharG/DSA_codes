https://leetcode.com/problems/convert-bst-to-greater-tree/description/

```
class Solution {
public:
    void change_BST(TreeNode* root,int& sum){
        if(root==nullptr)
            return;

        change_BST(root->right,sum);
        
        sum += root->val;
        root->val = sum;

        change_BST(root->left,sum);

    }

    TreeNode* convertBST(TreeNode* root) {
        int sum = 0;
        change_BST(root,sum);
        
        return root;        
    }
};
```

Return -> [[Binary search tree]]

