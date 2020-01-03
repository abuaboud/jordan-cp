# DFS ( Depth-First-Search )

After we store our data in graph data-structure , in some cases we need to search or traversing in this data , so in 19th century French mathematician “Charles Pierre Trémaux” investigate a DFS algorithm .

The idea behind DFS is 
- Travel as far as you can down a path .
- Back up as little as possible when you reach a "dead end" (i.e., next vertex has been "visited" or there is no next vertex) .

DFS can works with : 

1 – Directed Graphs 

2 - Undirected Graphs

3 - Weighted Graphs

4 – Unweighted Graphs

for applying DFS we usually use < Stack > 

## Prerequisites

* Introduction into graphs
* Graphs representation

## Objectives

* How to search and traversing in graph

## Videos 

[![](https://i.ytimg.com/vi/Qu6wQEAqyx0/hqdefault.jpg)](https://www.youtube.com/watch?v=Qu6wQEAqyx0)
[![](https://i.ytimg.com/vi/HvUCH2Swf2I/hqdefault.jpg)](https://www.youtube.com/watch?v=HvUCH2Swf2I)


## pseudo code of DFS :
```
Procedure DFS (L: adjacencyList, v : vertex)
initialize stack.
visit, mark and push(v).
while stack is nonempty do 
	while there is an unmarked vertex w adjacent to top(stack) do 
		visit, mark and push(w).
	end
	pop(stack) //the top(stack) was completely explored
end.
```

## Code Of DFS :

C++ :


```cpp
#include <iostream>
#include <stdio.h>
#include <memory.h>
#include <algorithm>
#include <vector>
#include <stack>


using namespace std;

int n, m;
vector<vector<int> > g;
bool vis[10001];

void dfs(int u) {
	vis[u] = 1;

	for (int i = 0; i < g[u].size(); i++)
		if (!vis[g[u][i]])
			dfs(g[u][i]);
}

void dfs_stack(int u) {
	stack<int> s;
	vis[u] = 1;
	s.push(u);

	while (!s.empty()) {
		int v = s.top();
		s.pop();

		for (int i = 0; i < g[v].size(); i++)
			if (!vis[g[v][i]]) {
				vis[g[v][i]] = 1;
				s.push(g[v][i]);
			}
	}
}

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

	memset(vis, 0, sizeof(vis));

	dfs(0); // or    dfs_stack(0);

	return 0; 
}
```

Java : 


```java
import java.util.*;

public class Main {

    static int n,m;
    static List<Integer> [] g;
    static boolean [] vis;
    
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        n = in.nextInt();
        m = in.nextInt();
        
        g = new List[n];
        for(int i=0; i<n; i++)
            g[i] = new ArrayList();
        
        for(int i=0; i<m; i++) {
            int a = in.nextInt();
            int b = in.nextInt();
            
            g[a].add(b); // a -> b
            g[b].add(a); // b -> a  (for un-directed graph)
        }
        
        vis = new boolean[n];
        dfs(0); // or    dfs_stack(0);
        
    }
    
    static void dfs(int u) {
        vis[u] = true;
        
        for(int w : g[u]) 
            if(!vis[w]) 
                dfs(w);
    }
    
    static void dfs_stack(int u) {
        Stack<Integer> s = new Stack();
        
        vis[u] = true;
        s.add(u);
        
        while(!s.isEmpty()) {
            int v = s.pop();
            
            for(int w : g[v]) {
                if(!vis[w]) {
                    vis[w] = true;
                    s.add(w);
                }
            }
        }
    }
}
```

## Time Complexity :
	O(V+E).

## Practice Problems:


Problem 1: [https://codeforces.com/group/qAGblhphAA/contest/227610/problem/B]
Code 1 : https://ideone.com/0IIKDo

Problem 2: [https://codeforces.com/contest/277/problem/A]
Code 2 : https://ideone.com/Ogu9Jp

Problem 3: [https://codeforces.com/contest/60/problem/B]
Code 3 : https://ideone.com/vEGUzG

Problem 4: [https://codeforces.com/contest/500/problem/B]
Code 4 : https://ideone.com/W0o0GV


**Authors:**
* Abdalah AbuSalah
