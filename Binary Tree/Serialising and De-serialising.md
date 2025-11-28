https://leetcode.com/problems/serialize-and-deserialize-binary-tree/

```
class Codec {
public:
    string serialize(TreeNode* root) {
        if(root==nullptr)
            return "";
  
        string ser = "";
        queue<TreeNode*> q;
  
        q.push(root);
        while(!q.empty()){
            TreeNode* node = q.front();
            q.pop();
  
            if(node){
                ser += (to_string(node->val) + ',');
                q.push(node->left);
                q.push(node->right);
            }
            else{
                ser += '#,';
            }
        }
  
        return ser;
    }
  
    // Decodes your encoded data to tree.
    TreeNode* deserialize(string data) {
        if(data == "")
            return nullptr;

        stringstream ss(data);
        string token;
  
        getline(ss,token,',');
        TreeNode* root = new TreeNode(stoi(token));
        queue<TreeNode*> q;
  
        q.push(root);
        while(!q.empty()){
            TreeNode* node = q.front();
            q.pop();
  
            if(getline(ss,token,',')){
                if(token == "#" || token == "")
                    node->left = nullptr;
                else{
                    node->left = new TreeNode(stoi(token));
                    q.push(node->left);
                }
            }
  
            if(getline(ss,token,',')){
                if(token == "#" || token == "")
                    node->right = nullptr;
                else{
                    node->right = new TreeNode(stoi(token));
                    q.push(node->right);
                }
            }
        }
  
        return root;
    }
};
```

Return -> [[Binary tree]]

