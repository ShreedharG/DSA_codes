https://leetcode.com/problems/reverse-linked-list/
###### Iterative
```
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        if(head==nullptr)
            return head;

        ListNode* prev = nullptr;
        ListNode* temp = head; 

        while(temp!=nullptr){
            ListNode* front = temp->next;
            temp->next = prev;
            prev = temp;
            temp = front;
        }        
        return prev;
    }
};
```

###### Recursive
```
class Solution {
public:
    ListNode* reverseLL(ListNode* prev,ListNode* temp){
        if(temp == nullptr)
            return prev;

        ListNode* front = temp->next;
        temp->next = prev;

        return reverseLL(temp,front);
    }

    ListNode* reverseList(ListNode* head) {
        if(head == nullptr || head->next == nullptr) return head;
  
        head = reverseLL(nullptr,head);
        return head;
    }
};
```
###### Memory-utilisation
```
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        if(!head || !head->next) return head;
        stack<int> s;
  
        for(ListNode* temp = head; temp != nullptr; temp = temp->next)
            s.push(temp->val);  

        for(ListNode* temp = head; temp != nullptr; temp = temp->next){
            int value = s.top(); s.pop();
            temp->val = value;
        }  
        return head;
    }
};
```


Return -> [[Linked List]]

