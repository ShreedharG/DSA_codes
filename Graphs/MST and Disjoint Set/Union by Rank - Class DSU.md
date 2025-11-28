
```
class DSU{
private:
    vector<int> parent;
    vector<int> rank;
public:
    DSU(int total) {
        rank.resize(total,0);
        parent.resize(total);
        for(int i=0; i < total; i++)
            parent[i] = i;
    }
    
    int find(int x){
        if(x == parent[x])
            return x;
        return (parent[x] = find(parent[x]));
    }
    
    void union_(int x,int y){
        int px = find(x), py = find(y);
        if(px != py){
            if(rank[px] > rank[py]) parent[py] = px;
            else if(rank[px] < rank[py]) parent[px] = py;
            else{
                rank[px]++;
                parent[py] = px;
            }
        }
    }
    ~DSU(){
        parent.clear();
        rank.clear();
        parent.shrink_to_fit();
        rank.shrink_to_fit();
    }
};
```

Return -> [[MST and Disjoint Set Problems]]

