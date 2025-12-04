https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/

```
class Solution {
public:
    Node* connect(Node* root) {
        if(!root) return root;

        queue<Node*> q;
        q.push(root);
  
        while(!q.empty()){
            int sz = q.size();
            Node* nextR = NULL;
  
            for(int i=0;i<sz;i++){
                Node* temp = q.front();
                q.pop();
  
                if(temp->right) q.push(temp->right);
                if(temp->left) q.push(temp->left);
  
                temp->next = nextR;
                nextR = temp;
            }
        }
        return root;
    }
};
```

Return -> [[Binary tree]]

