# Bridges and Articulation Points
A bridges is an edge of a graph whose deletion increases its number of connected components. This means if we delete an edge and the number of components in the graph increases this edge is a bridge.
An articulation point is a node whose deletion increases its number of connected components same as a bridge.

![](https://github.com/Hiasat/JordanCP/blob/master/resources/bridges_graph.png?raw=true)

In the example above the edges 2-4, and 3-8 are bridges and the nodes 2, 3, and 8 are articulation points.

## Prerequisites

* Graph Representation
* Depth first search

## Objectives

* How to find bridges
* How to find articulation points

## Videos 

[![](https://img.youtube.com/vi/VpjykHVul2s/0.jpg)](https://www.youtube.com/watch?v=VpjykHVul2s)

```cpp

//Bridges and Articulation Points

#include <iostream>	
#include <vector>
using namespace std;

int n;
vector<vector<int> > g;
vector<int> idx, low;
int DFSTime;
vector<pair<int, int> > bridges;
vector<bool> art;
int child = 0;
void DFS(int u, int p) {
	idx[u] = low[u] = ++DFSTime;
	for(int i = 0; i < g[u].size(); ++i) {
		int v = g[u][i];
		if(idx[v] == 0) {
			if(p == -1)
				++child;
			DFS(v, u);
			low[u] = min(low[u], low[v]);
			if(low[v] > idx[u])
				bridges.push_back(make_pair(u, v));
			if(low[v] >= idx[u])
				art[u] = true;
		}
		else if(v != p)
			low[u] = min(low[u], idx[v]);
	}
}
int main() {
	int e;
	cin >> n >> e;
	art.resize(n);
	idx.resize(n);
	low.resize(n);
	g.resize(n);
	for(int i = 0; i < e; ++i) {
		int a, b;
		cin >> a >> b;
		--a; --b;
		g[a].push_back(b);
		g[b].push_back(a);
	}
	DFS(0, -1);
	art[0] = child > 1;
	return 0;
}
```

## Practice Problems:

Write here list of problem to practice on and their levels and some hints.

Problem 1: [https://codeforces.com/gym/100712] Problem H

Problem 2: [https://www.hackerrank.com/contests/2015-acm-acpc/challenges/uberfication]

Problem 3: [https://codeforces.com/problemset/problem/732/F]

**Authors:**
* Mohammad Aldehayat
