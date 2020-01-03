# BFS ( Breadth-First-Search )

After we store our data in graph data-structure , in some cases we need to search or traversing in this data, so in 1945 “Konrad Zuse” invented a BFS algorithm .

The idea behind BFS is 
- Look at all possible paths at the same depth before you go at a deeper level .
- Back up as far as possible when you reach a "dead end" (i.e., next vertex has been "visited" or there is no next vertex) . 

BFS can works with : 

  1 - Directed Graphs 

  2 - Undirected Graphs

  3 - Weighted Graphs

  4 - Unweighted Graphs


for applying BFS we usually use < Queue > 

## Prerequisites

* Introduction into graphs
* Graphs representation

## Objectives

* How to search and traversing in graph

## Videos 

[![](https://i.ytimg.com/vi/PdHP2mbCgIw/hqdefault.jpg)](https://www.youtube.com/watch?v=PdHP2mbCgIw)
[![](https://i.ytimg.com/vi/9sUZE9kydXM/hqdefault.jpg)](https://www.youtube.com/watch?v=9sUZE9kydXM)


## pseudo code of BFS :
```
Procedure BFS (L: adjacencyList, v : vertex) 
	initialize the queue Q.
	visit and mark v.
	enqueue (v, Q ).
	while Q is nonempty do
		x = the next vertex in the queue Q
		for each unmarked vertex w adjacent to x do
			visit and mark w 
			enqueue(w, Q)
		end
		remove x from the queue Q
	end.
```
## Code Of BFS :

```cpp
#include <iostream>
#include <stdio.h>
#include <memory.h>
#include <algorithm>
#include <vector>
#include <stack>
#include <queue>

using namespace std;

int n, m;
vector<vector<int> > g;
bool vis[10001];

void bfs(int u) {
	queue<int> s;
	vis[u] = 1;
	s.push(u);

	while (!s.empty()) {
		int v = s.front();
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

	bfs(0);

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
        bfs(0);
        
    }
    
    
    static void bfs(int u) {
       	Queue<Integer> q = new LinkedList();
        
        vis[u] = true;
        q.add(u);
        
        while(!q.isEmpty()) {
            int v = q.remove();
            
            for(int w : g[v]) {
                if(!vis[w]) {
                    vis[w] = true;
                    q.add(w);
                }
            }
        }
    }
}
```

## Time Complexity :
	O(V+E).

## Practice Problems:


Problem 1: [https://codeforces.com/problemset/problem/25/D]
Code 1 : https://ideone.com/MJa976

Problem 2: [https://codeforces.com/problemset/problem/377/A]
Code 2 : https://ideone.com/Ivwigz


Problem 3: [https://codeforces.com/contest/199/problem/D]
Code 3 : https://ideone.com/tyWXrN


Problem 4: [https://codeforces.com/contest/242/problem/C]
Code 4 : https://ideone.com/gLIKKS




**Authors:**
* Abdalah AbuSalah
