[https://leetcode.com/problems/binary-tree-postorder-traversal/]()

```
class Solution {
public:
    void post_order(vector<int>& ans_array,TreeNode* root){
        if(root==nullptr)
                return;

        post_order(ans_array,root->left);
        post_order(ans_array,root->right);
        ans_array.push_back(root->val);
    }
    
    vector<int> postorderTraversal(TreeNode* root) {
        vector<int> ans_array;
        post_order(ans_array,root);  

        return ans_array;
    }
};
```