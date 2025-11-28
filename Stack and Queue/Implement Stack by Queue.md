https://leetcode.com/problems/implement-stack-using-queues/

```
class MyStack {
    public:
        queue<int> q1;
        queue<int> q2;
        MyStack() {}

        void push(int x) {
            if(q1.empty())
                q1.push(x);
            else{
                while(!q1.empty()){
                    q2.push(q1.front());
                    q1.pop();
                }

                q1.push(x);

                while(!q2.empty()){
                    q1.push(q2.front());
                    q2.pop();
                }
            }
            return;
        }

        int pop() {
            if(q1.empty())
                return -1;
            else{
                int temp = q1.front();
                q1.pop();
                return temp;
            }
        }

        int top() {
            return q1.front();
        }

        bool empty() {
            return q1.empty();
        }
};
```

Return -> [[Stack and Queue]]