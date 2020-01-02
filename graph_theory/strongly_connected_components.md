# Strongly Connected Components 
Strongly Connected Components(SCC) is another application of DFS in a directed graphs.

An SCC is defined as follows:
if we pick any pair of vertices u, and v in the SCC we can find a path from u to v and vice versa. 

So if we have the following graph: 

![](https://github.com/Hiasat/JordanCP/blob/master/resources/graph.png?raw=true)

There are 3 SCCs.
There are two known algorithms to find SCCs ,Kosaraju’s and Tarjan’s algorithm.

## Prerequisites
* Graph Representation
* Depth first search
 
## Lecture
What you will learn:
* Strongly Connected Components
* Directed Graph Implementation
* Tarjan’s algorithm

## Video : 

 
[![](https://img.youtube.com/vi/lergyFWMSSY/0.jpg)](https://www.youtube.com/watch?v=lergyFWMSSY)

[![](https://img.youtube.com/vi/mDGqvjA31w0/0.jpg)](https://www.youtube.com/watch?v=mDGqvjA31w0)

Code to find the number SCCs of a directed graph:
```cpp
#include <bits/stdc++.h>

using namespace std;
 
typedef long long ll;
typedef unsigned long long ull;
const int N = 100000;
int n, e, idx[N], low[N], T;
vector<vector<int> > g;
vector<int> S;
bool vis[N];
int compID[N], cmp;
void DFS(int u) {
	idx[u] = low[u] = ++T;
	S.push_back(u);
	vis[u] = true;
	for (int i = 0; i < g[u].size(); ++i) {
		int v = g[u][i];
		if (idx[v] == 0)
			DFS(v);
		if (vis[v])
			low[u] = min(low[u], low[v]);
	}
	if (idx[u] == low[u]) {
		while (true) {
			int v = S.back();
			S.pop_back();
			vis[v] = false;
			compID[v] = cmp;
			if (v == u)
				break;
		}
		++cmp;
	}
}
int main() {
	cin >> n >> e;
	g.resize(n);
	for (int i = 0; i < e; ++i) {
		int from, to;
		cin >> from >> to;
		--from; --to;
		g[from].push_back(to);
	}
	for (int i = 0; i < n; ++i)
		if (idx[i] == 0)
			DFS(i);
 
	cout<<cmp<<endl;
	return 0;
}
 ```

#### Complexity:
the code given above explores the directed graph and reports the number of SCC, the recursive part is similar to standard 
DFS and the SCC part will run in amortized `O(V)` times, as each vertex will only belong to one SCC and thus reported only once.
In overall, this algorithm runs in `O(V + E)`.

## Practice Problems
C - Checkposts [https://codeforces.com/problemset/problem/427/C]

D - Ring Road 2 [https://codeforces.com/problemset/problem/27/D]

E - The Road to Berland is Paved With Good Intentions [https://codeforces.com/problemset/problem/228/E]

E - Ralph and Mushrooms [https://codeforces.com/problemset/problem/894/E]

E - Scheme [https://codeforces.com/problemset/problem/22/E]
 
http://www.spoj.com/problems/TFRIENDS/
 
http://www.spoj.com/problems/CAPCITY/ 

https://onlinejudge.org/index.php?option=onlinejudge&page=show_problem&problem=2938

https://onlinejudge.org/index.php?option=onlinejudge&page=show_problem&problem=2499

https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&page=show_problem&problem=2756

https://onlinejudge.org/index.php?option=onlinejudge&page=show_problem&problem=183


**Authors:**
* Nour Bzour

**Video Credits**:
* Hasan Al Hamsh