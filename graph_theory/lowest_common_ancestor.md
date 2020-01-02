# Lowest Common Ancestor
Lowest common ancestor between two nodes (`u`,`v`) in tree is the first node that is
parent of `u` and also parent of `v`

## Lecture

Prerequisite:
- Introduction to Graph & Representation

What you will learn:
- Find Lowest Common Ancestor in Tree

Videos:

[![](https://img.youtube.com/vi/tHkaoi/0.jpg)](https://www.youtube.com/watch?v=tHkaoi)

Given a tree `n` number of nodes and `n-1` edges 

```cpp
#include <bits/stdc++.h>
using namespace std;
typedef long long ll;

int n,a,b,dp[100010][18],depth[100010];
vector<int> g[100100];

void dfs(int u , int parent){
	dp[u][0] = parent;
	for (int i = 0; i < g[u].size(); ++i){
		int v = g[u][i];
		if(v == parent)continue;
		depth[v] = depth[u] + 1;
		dfs(v,u);
	}
}
int lca(int u , int v){
	if(depth[u] < depth[v])
		swap(u,v);
	for(int k = 17 ; k >= 0 ; --k){
		if(depth[u]-(1<<k) >= depth[v]){
			u = dp[u][k];
		}
	}	
	if(u == v)return u;
	for(int k = 17 ; k >= 0 ; --k){
		if(dp[u][k] != dp[v][k]){
			u = dp[u][k];
			v = dp[v][k];
		}
	}
	return dp[u][0];
}
int main(){
	scanf("%d",&n);
	for (int i = 0; i < n-1; ++i){
		scanf("%d%d",&a,&b);
		g[a].push_back(b);
		g[b].push_back(a);
	}
	memset(dp,-1,sizeof dp);
	dfs(1,-1);
	for(int k = 1 ; k <= 17;++k){
		for(int u = 1 ; u <= n ; ++u){
			if(dp[u][k-1] == -1)continue;
			dp[u][k] = dp[dp[u][k-1]][k-1];
		}
	}
	// You can use LCA function now
	return 0;	
}
```
## Practice Problems

- https://codeforces.com/problemset/problem/20/C
- https://codeforces.com/contest/450/problem/D (solution: https://www.youtube.com/watch?v=CjihDdimgF8&list=PLPSFnlxEu99Ewm9LK4mBLkXeE-p_Bskha&index=11)
- https://codeforces.com/contest/208/problem/E
- https://codeforces.com/contest/191/problem/C
- https://codeforces.com/contest/587/problem/C
- https://codeforces.com/contest/609/problem/E
- https://codeforces.com/contest/176/problem/E
- https://codeforces.com/contest/466/problem/E

**Authors:**
* Zaina Al Mashni
