https://leetcode.com/problems/symmetric-tree/description/

```
class Solution {
public:
    bool check_Symmetric(TreeNode* root1,TreeNode* root2){
        if(root1==nullptr || root2==nullptr)
            return (root1==root2);

        return ((root1->val==root2->val) &&
                check_Symmetric(root1->left,root2->right) &&
                check_Symmetric(root1->right,root2->left)) ;
    }

    bool isSymmetric(TreeNode* root) {
        return check_Symmetric(root,root);
    }
};
```

Return -> [[Binary tree]]