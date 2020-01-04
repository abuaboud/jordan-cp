# Minimum/Maximum spanning tree

A spanning tree of undirected graph is a subgraph that is a tree and connects all the vertices together. A single graph can have many different spanning trees.

A minimum spanning tree (MST) is the spanning tree with the minimum weight over other spanning trees of a graph, where the weight of a spanning tree is the sum of weights given to each edge of the spanning tree.

## Prerequisite:

- Introduction to Graph & Representation

- Disjoint sets

## Lecture

#### What you will learn:

· Minimum/Maximum Spanning Tree Algorithm

[![](https://img.youtube.com/vi/HQ5ANfzSDn0/0.jpg)](https://www.youtube.com/watch?v=HQ5ANfzSDn0)

Code:

C++ code
```cpp
#include <bits/stdc++.h>
using namespace std;

const int MAX_INTEGER = 9;

int n , m;

struct edge{
	int a ,b , c;

	// To find minimum spanning tree, edges with smaller weight should come first.
	bool operator<(const edge &rhs) const{
		return c < rhs.c;
	}
};

edge E[N];

int find(int u){
	return dsu[u] == u ? u : dsu[u] = u;
}

int main() {
	cin >> n >> m;
	for(int i = 1; i <= n ; ++i)dsu[i] = i;
	for (int i = 0; i < m; ++i){
		scanf("%d%d%d",&E[i].a,&E[i].b,&E[i].c);
	}
	sort(E,E+m);
	for(int i = 0 ; i < m ; ++i){
		if(find(E[i].a) != find(E[i].b)){
			// Edge E[i] is in the spanning tree, since it connect two disconnected component
			dsu[find(E[i].a)] = find(E[i].b);
		}
	}
	return 0;
}
```

Practice Problems
- MST - Minimum Spanning Tree: [http://www.spoj.com/problems/MST/]
    Sol: https://paste2.org/IcsFGM90
    
**Author**:
- Hanan Al-Najar
- Mohammad AbuAboud

**Video Credits**:
- Mohammad Amjad