https://leetcode.com/problems/odd-even-linked-list/
###### Optimal {O(1) Space and O(N) Time Complexity}
```
class Solution {
public:
    ListNode* oddEvenList(ListNode* head) {
        if(head==nullptr || head->next==nullptr)
            return head;

        ListNode* e_head = new ListNode(-1);
        ListNode* o_head = new ListNode(-1);
        ListNode* temp = head;

        ListNode* e_pointer = e_head;
        ListNode* o_pointer = o_head;

        int i=1;
        while(temp!=nullptr)
            if(i%2==1){
                o_pointer->next = temp;
                o_pointer = o_pointer->next;
            }
            else{
                e_pointer->next = temp;
                e_pointer = e_pointer->next;
            }
            temp = temp->next;
            i++;
        }
        
        ListNode* odd_head = o_head->next;
        delete(o_head);
        ListNode* eve_head = e_head->next;
        delete(e_head);

        o_pointer->next = eve_head;
        e_pointer->next = nullptr;
        
        return odd_head;
    }
};
```
###### Brute Force{O(N) Space and O(N) Time Complexity}
```
class Solution {
public:
    ListNode* oddEvenList(ListNode* head) {
        if(head==nullptr || head->next==nullptr)
            return head;

        vector<int> odd_list;
        vector<int> eve_list;
        int i=1;

        for(ListNode* temp=head;temp!=nullptr;temp=temp->next){
            if(i%2==1)
                odd_list.push_back(temp->val);
            else
                eve_list.push_back(temp->val);
            i++;
        }
        
        ListNode* temp = head;
        for(int i=0;i<odd_list.size();i++){
            temp->val = odd_list[i];
            temp = temp->next;
        }
        
        for(int i=0;i<eve_list.size();i++){
            temp->val = eve_list[i];
            temp = temp->next;
        }

        return head;
    }
};
```


Return -> [[Linked List]]

