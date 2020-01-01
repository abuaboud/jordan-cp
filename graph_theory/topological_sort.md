# Topological Sort

> You can't stay in your corner of the forest waiting for others to come to you. You have to go to them sometimes. <br>- A.A. Milne

Topological sorting for Directed Acyclic Graph (DAG) is a linear ordering of vertices such that for every directed edge uv, vertex u comes before v in the ordering. Topological Sorting for a graph is not possible if the graph is not a DAG.


## Lecture 

What you will learn:
- Graph Representation
- Topological Sort


[![](https://img.youtube.com/vi/hl39eE9KdhM/0.jpg)](https://www.youtube.com/watch?v=hl39eE9KdhM)

```cpp
#include <bits/stdc++.h>
using namespace std;
vector< vector<int> > g;
int n,e;
// This code find a topological sort for a given graph
// n : number of nodes
// e : number of edges
int main(){
	cin >> n >> e;
	g.resize(n);
	vector<int> in(n);
	for(int i = 0 ; i < e ; ++i){
		int a,b;
		cin >> a >> b;
		g[a].push_back(b);
		in[b]++;
	}
	vector<int> ready,sol;
	for(int i = 0 ; i < n;++i)
		if(in[i] == 0)
			ready.push_back(i);
	while(!ready.empty()){
		int u = ready[ready.size()-1];
		ready.pop_back();
		sol.push_back(u);
		for(int i = 0 ; i < g[u].size();++i){
			int v = g[u][i];
			in[v]--;
			if(in[v] == 0)
				ready.push_back(v);
		}
	}
	if(sol.size() != n){
		cout << -1 << endl;
	}else{
		for (int i = 0; i < n; ++i){
			cout << sol[i] << " ";
		}
	}
	return 0;
}
```

## Practice Problems:

Fox And Names: [https://codeforces.com/contest/510/problem/C]

Coins: (Only on 3 Nodes)[https://codeforces.com/contest/47/problem/B]

Online Courses In BSU [https://codeforces.com/contest/770/problem/C]

**Authors:**
* Mohammad AbuAboud.

**Video Credits**:
* Hasan Al Hamsh