https://leetcode.com/problems/remove-nth-node-from-end-of-list/
###### Reverse List Method
```
class Solution {
public:
    ListNode* reverseLL(ListNode* head){
        if(head==nullptr)
            return head;

        ListNode* prev = nullptr, temp = head;
        
        while(temp!=nullptr){
            ListNode* front = temp->next;
            temp->next = prev;
            prev = temp;
            temp = front;
        }
        return prev;
    }

    ListNode* removeNthFromEnd(ListNode* head, int n) {
        if(head==nullptr)
            return head;

        head = reverseLL(head);

        if(n==1){
            ListNode* next = head->next;
            delete head;
            head = next;
            head = reverseLL(head);
            return head;
        }

        int i = 0;
        ListNode* temp = head;

        while(temp!=nullptr && i<(n-2)){
            temp = temp->next;
            i++;
        }

        if(temp==nullptr || temp->next==nullptr)
            return head;

        ListNode* deleteNode = temp->next;
        temp->next = deleteNode->next;
        delete deleteNode;

        head = reverseLL(head);
        return head;
    }
};
```
###### Optimal
```
class Solution {
public:
    int get_length(ListNode* head){
        if(head==nullptr)
            return 0;        
        return (1+get_length(head->next));
    }

    ListNode* removeNthFromEnd(ListNode* head, int n) {
        if(head==nullptr || n > get_length(head))
            return head;

        ListNode* temp = head;
        for(int i=0;i<n;i++)
            temp = temp->next;

        if(temp==nullptr)
            return head->next;

        ListNode* prev = head;
        while(temp->next!=nullptr){
            temp = temp->next;
            prev = prev->next;
        }

        ListNode* delNode = prev->next;
        prev->next = delNode->next;
        delete delNode;

        return head;
    }
};
```

Return -> [[Linked List]]