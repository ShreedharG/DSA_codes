https://www.geeksforgeeks.org/problems/sort-a-stack/1

```
void insert_into_stack(stack<int>& ans,int x){
    if(ans.empty() || ans.top() < x){
        ans.push(x);
        return;
    }
    int temp = ans.top(); 
    ans.pop();
    
    insert_into_stack(ans,x);
    ans.push(temp);
}

void SortedStack ::sort(){
    stack<int> ans;
    while(!s.empty()){
        int x = s.top(); 
        s.pop();
        
        insert_into_stack(ans,x);
    }    
    s = ans;
}
```

Return -> [[Recursion + Backtracking]]

