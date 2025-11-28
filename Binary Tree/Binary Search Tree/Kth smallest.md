[https://leetcode.com/problems/kth-smallest-element-in-a-bst/]()

The question simply asks to find out the k_th smallest element in the bst. We can traverse the entire the bst using #inOrder traversal while maintaining the node count and when the node count becomes equal to k, we set its value to the current node value.

```
class Solution {
    public:
        void fetch_kth(TreeNode* root, int k, int* i, int* kth){
            if(root==nullptr || *i>k)
                return; 

            fetch_kth(root->left,k,i,kth);

            (*i)++;
            if((*i)==k){
                *kth = root->val;
                return;
            }

            fetch_kth(root->right,k,i,kth);
        }

        int kthSmallest(TreeNode* root,int k){
            int i = 0;
            int kth_smallest = -1;
            fetch_kth(root,k,&i,&kth_smallest);
            
            return kth_smallest;        
        }
};
```
