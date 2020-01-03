# Range Queries using DFS numbering

It’s a method for representing a rooted tree as sequence of nodes in array, 
useful for using segment tree data structure on trees

## Prerequisites

* Depth First Search
* Segment Tree
* Segment tree lazy propagation(Good to know)

## Objectives

* How to represent a rooted tree as sequence of nodes in array
* Solving subtree problems : update/get value(s) in a subtree

## Brief tutorial

When traversing the tree using Depth-first search(DFS), insert each node in a vector(or array), and set the entry time(the time DFS entered the node) and the exit time(the time DFS finished visiting the node and all it’s children) in separate arrays.

Consider a rooted tree with 6 vertices connected as given below

![](https://raw.githubusercontent.com/Hiasat/JordanCP/master/resources/tree1.png)

After applying DFS numbering on them

![](https://raw.githubusercontent.com/Hiasat/JordanCP/master/resources/tree2.png)


now as you can see, the entry time and exit time values represent a subarray in dfs_array, the values in the subarray are the nodes in that subtree

example using above graph:
node : 3
entry time : 1
exit time : 4
dfs_array[1: 4] represent the subtree of node 3

![](https://raw.githubusercontent.com/Hiasat/JordanCP/master/resources/tree3.png)

Code example:

```cpp
const int N = 1e5 + 100;
vector < int > dfs_array;
vector < int > graph[N];
int in [N]; // in[node_number] = time when DFS entered the node  
int out[N]; // out[node_number] = time when DFS finished visiting the node and it's children  
bool vis[N]; // check if visited  
int current_time = 0;
void dfs_array_build(int n) {
  vis[n] = true;

  dfs_array.push_back(n); // normal array could be used => dfs_array[current_time] = n  
  in [n] = current_time;
  current_time++;
  for (int next, i = 0; i < graph[n].size(); i++) {
    next = graph[n][i];
    if (vis[next])
      continue;
    dfs_array_build(next);
  }

  out[n] = current_time - 1;

}
```

Now Segment Tree array will be built using dfs_array, and when we want to do a query(update/get) to a subtree, we will use the entry and exit time(as ranges) for the required node

## Videos 

Segment Tree - Problem New Year Tree
video by Ibraheem Tuffaha
[![](https://img.youtube.com/vi/vD6DtgP1ix0/0.jpg)](https://youtu.be/vD6DtgP1ix0)


solution code: 
```cpp
#include <bits/stdc++.h>
using namespace std;
typedef long long ll;
const int N = 400000 + 10;

int n, m, c[N], in[N], out[N], id = 0, rev[N];
vector<int> g[N];
ll seg[4*N], lazy[4*N];

void dfs(int u, int p) {
	rev[id] = u;
	in[u] = id++;
	for(int i=0, v; i<g[u].size(); ++i) {
		v = g[u][i];
		if(v == p) continue;
		dfs(v, u);
	}
	out[u] = id - 1;
}

void build(int p, int l, int r) {
	if(l == r) {
		seg[p] = (1LL << c[rev[l]]);
		return;
	}
	int mid = (l+r)/2;
	build(p*2, l, mid);
	build(p*2+1, mid+1, r);
	seg[p] = seg[p*2] | seg[p*2+1];
}

void update(int p, int l, int r, int a, int b, int val) {
	if(lazy[p] != 0) {
		seg[p] = (1LL << lazy[p]);
		if(l != r) {
			lazy[p*2] = lazy[p];
			lazy[p*2+1] = lazy[p];
		}
		lazy[p] = 0;
	}
	if(r < a || l > b) return;
	if(a <= l && r <= b) {
		seg[p] = (1LL << val);
		if(l != r) {
			lazy[p*2] = val;
			lazy[p*2+1] = val;
		}
		return;
	}

	int mid = (l+r)/2;
	update(p*2, l, mid, a, b, val);
	update(p*2+1, mid+1, r, a, b, val);
	seg[p] = seg[p*2] | seg[p*2+1];
}

ll get(int p, int l, int r, int a, int b) {
	if(lazy[p] != 0) {
		seg[p] = (1LL << lazy[p]);
		if(l != r) {
			lazy[p*2] = lazy[p];
			lazy[p*2+1] = lazy[p];
		}
		lazy[p] = 0;
	}
	if(r < a || l > b) return 0;
	if(a <= l && r <= b) return seg[p];
	int mid = (l+r)/2;
	return get(p*2, l, mid, a, b) | get(p*2+1, mid+1, r, a, b);
}

int main() {
	scanf("%d%d", &n, &m);
	for(int i=0; i<n; ++i)
		scanf("%d", c+i);

	for(int i=1, u, v; i<n; ++i) {
		scanf("%d%d", &u, &v);
		--u, --v;
		g[u].push_back(v);
		swap(u, v);
		g[u].push_back(v);
	}

	dfs(0, -1);

	build(1, 0, n-1);
	int t, v, clr, res;
	ll x;
	while(m--) {
		scanf("%d", &t);
		if(t == 1) { // update
			scanf("%d%d", &v, &clr);
			--v;
			update(1, 0, n-1, in[v], out[v], clr);
		} else {
			scanf("%d", &v);
			--v;
			res = 0;
			x = get(1, 0, n-1, in[v], out[v]);
			while(x) {
				res += (x&1);
				x /= 2;
			}
			printf("%d\n", res);
		}
	}


	return 0;
}
```

## Practice Problems:

On Changing Tree: [[https://codeforces.com/problemset/problem/396/C](https://codeforces.com/problemset/problem/396/C)]

Water tree: [[https://codeforces.com/problemset/problem/343/D](https://codeforces.com/problemset/problem/343/D)]

Tree and Queries: [[https://codeforces.com/problemset/problem/375/D](https://codeforces.com/problemset/problem/375/D)]

Propagating tree: [[https://codeforces.com/problemset/problem/383/C](https://codeforces.com/problemset/problem/383/C)] 


**Authors:**
*   Samer Rawashdeh
