https://leetcode.com/problems/implement-queue-using-stacks/description/

```
class MyQueue {
public:
    stack<int> s1;
    stack<int> s2;
    MyQueue() {}

    void push(int x) {
        if(s1.empty())
            s1.push(x);
        else{
            while(!s1.empty()){
                s2.push(s1.top());
                s1.pop();
            }

            s1.push(x);

            while(!s2.empty()){
                s1.push(s2.top());
                s2.pop();                
            }
        }
        return;
    }

    int pop() {
        if(s1.empty())
            return -1;
        else{
            int temp = s1.top();
            s1.pop();
            return temp;
        }
    }

    int peek() {
        return s1.top();
    }

    bool empty() {
        return s1.empty();
    }
};
```

Return -> [[Stack and Queue]]