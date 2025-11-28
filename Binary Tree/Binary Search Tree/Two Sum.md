[https://leetcode.com/problems/two-sum-iv-input-is-a-bst/]()

%% 
Here we use the [[BST Iterator]] class to always reach out to the next inorder successor from left and right with the use of two pointers. #two-pointer #bstiterator.
left_iterator : return left inorder successor
right_iterator : returns right inorder successor

The loop continues till the left value is less than right value and returns false if no pair is found.
%%

```
class Solution {
    public:
        bool findTarget(TreeNode* root, int k) {
            BST_iterator left_iterator(root,false);
            BST_iterator right_iterator(root,true);

            int left_val = left_iterator.next();
            int right_val = right_iterator.next();

            while(left_val < right_val){
                int sum = left_val + right_val;
                if(sum < k)
                    left_val = left_iterator.next();
                else if(sum > k)
                    right_val = right_iterator.next();
                else
                    return true;
            }
            
            return false;
        }
};
```
