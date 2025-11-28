https://www.geeksforgeeks.org/problems/children-sum-parent/1

```
class Solution {
  public:
    bool check_property(Node *root){
        if(root==NULL) return true;
        if(!root->left && !root->right) return true;
        
        int left_val = root->left ? root->left->data : 0;
        int right_val = root->right ? root->right->data : 0;
        
        return ((root->data == left_val+right_val) && 
                 check_property(root->left) && 
                 check_property(root->right));
        
    }
    int isSumProperty(Node *root) {
        return check_property(root);
    }
};

```

Return -> [[Binary tree]]

