https://leetcode.com/problems/binary-tree-maximum-path-sum/submissions/1731720845/

```
class Solution {
public:
    int find_max(TreeNode* root,int& maxi){
        if(root==nullptr) return 0;

        int left_sum = max(0,find_max(root->left,maxi));
        int right_sum = max(0,find_max(root->right,maxi));
  
        maxi = max(maxi,root->val+left_sum+right_sum);
        return (root->val + max(left_sum,right_sum));
    }

    int maxPathSum(TreeNode* root) {
        int maxi = INT_MIN;
        find_max(root,maxi);
  
        return maxi;
    }
};
```

Return -> [[Binary tree]]