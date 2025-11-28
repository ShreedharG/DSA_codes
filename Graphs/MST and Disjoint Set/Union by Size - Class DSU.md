
```
class DSU{
private:
	vector<int> size;
	vector<int> parent;
public:
	DSU(int n){
		size.resize(n,1);
		parent.resize(n);
		for(int i=0;i<n;i++)
			parent[i] = i;
	}
	
	int find(int x){
		if(x == parent[x])
			return x;
		
		return (parent[x] = find(parent[x]));
	}
	
	void union_(int x,int y){
		int px = find(x);
		int py = find(y);
		
		if(px != py){
			if(size[px] >= size[py]){
				size[px] = size[px] + size[py];
				parent[py] = px;
			}
			else{
				size[py] = size[py] + size[px];
				parent[px] = py;
			}
		}
	}
	
	int getSize(int x){
		int root = find(x);
		return size[root];
	}
};
```

Return -> [[MST and Disjoint Set Problems]]

