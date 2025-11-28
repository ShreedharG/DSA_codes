https://leetcode.com/problems/min-stack/

```
class MinStack {
public:
    stack<pair<int,int>> myStack;
    MinStack() { }

    void push(int val) {
        if(myStack.empty())
            myStack.push({val,val});
        else
            myStack.push({val,min(val,myStack.top().second)});
    }

    void pop() {
        myStack.pop();
    }

    int top() {
        return myStack.top().first;
    }

    int getMin() {
        return myStack.top().second;
    }
};
```

Return -> [[Stack and Queue]]