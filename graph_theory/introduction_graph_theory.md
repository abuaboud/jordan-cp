# Introduction to Graph Theory
In mathematics, graph theory is the study of graphs, which are mathematical structures used to model pairwise relations between objects. 

A graph in this context is made up of vertices, nodes, or points which are connected by edges, arcs, or lines.
## Objectives

* Graph terminology (Node , Edge , Component ,Weighted Graph , Unweighted Graph)
* How to represent graph in code.

## Videos 


[![](https://img.youtube.com/vi/8oY9TjyIYdo/0.jpg)](https://www.youtube.com/watch?v=8oY9TjyIYdo)

```cpp

//-------------------------------------------------------------------------------------------
//----------------------------------- unweighted graph --------------------------------------
//-------------------------------------------------------------------------------------------

int n, m;
vector<vector<int> > g;

int main() {
	scanf("%d%d", &n, &m);

	g.clear();
	g.resize(n);

	for (int i = 0; i < m; i++) {
		int a, b;
		scanf("%d%d", &a, &b);

		g[a].push_back(b); // a -> b
		g[b].push_back(a); // b -> a (for un-directed graph)
	}

	return 0; 
}



//-------------------------------------------------------------------------------------------
//------------------------------------- weighted graph --------------------------------------
//-------------------------------------------------------------------------------------------

int n, m;
vector<vector<pair<int,int> > > g;

int main() {

	scanf("%d%d", &n, &m);

	g.clear();
	g.resize(n);

	for (int i = 0; i < m; i++) {
		int a, b, c;
		scanf("%d%d%d", &a, &b, &c);

		g[a].push_back(make_pair(b,c)); // a -> b with cost c
		g[b].push_back(make_pair(a,c)); // b -> a with cost c (for un-directed graph)
	}

	return 0; 
}
```

**Authors:**
* Mohammad AbuAboud