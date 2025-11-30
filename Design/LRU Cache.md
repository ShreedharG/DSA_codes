```
class Node{
public:
    int key;
    int value;
    Node* prev;
    Node* next;
  
    Node(int k, int v){
        key = k;
        value = v;
        prev = nullptr;
        next = nullptr;
    }
};
  
class LinkedList{
private:
    Node* head;
    Node* tail;
public:
    LinkedList(){
        head = new Node(-1,-1);
        tail = new Node(-1,-1);
  
        head->next = tail;
        tail->prev = head;
    }
  
    void add_to_tail(Node* node){
        Node* prevNode = tail->prev;
        prevNode->next = node;
        node->prev = prevNode;
        node->next = tail;
        tail->prev = node;
    }
  
    void removeNode(Node* node){
        Node* pNode = node->prev;
        Node* nNode = node->next;
  
        pNode->next = nNode;
        nNode->prev = pNode;
    }
  
    Node* removeHead(){
        Node* lru = head->next;
        if(lru == tail) return nullptr;
  
        removeNode(lru);
        return lru;
    }
  
    void move_to_tail(Node* node){
        removeNode(node);
        add_to_tail(node);
    }
};  

class LRUCache {
public:
    int capacity;
    LinkedList l1;
    unordered_map<int, Node*> mp;

  
    LRUCache(int capacity) {
        this->capacity = capacity;
    }

    int get(int key) {
        auto it = mp.find(key);
        if(it == mp.end())
            return -1;

        l1.move_to_tail(it->second);
        return it->second->value;
    }

    void put(int key, int value) {
        auto it = mp.find(key);
  
        if(it != mp.end()){
            Node* exist = it->second;
            exist->value = value;
            l1.move_to_tail(exist);
  
            return;
        }

        if((int)mp.size() == capacity){
            Node* lru = l1.removeHead();
            if(lru)
                mp.erase(lru->key);
        }
  
        Node* newN = new Node(key,value);
        mp[key] = newN;
        l1.add_to_tail(newN);
  
        return;
    }
};
```

Return -> [[Design Problems]]

