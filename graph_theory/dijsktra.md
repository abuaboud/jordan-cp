# Dijkstra
Dijkstra is an algorithm for finding the shortest path between nodes in a weighted graph (no negative weights). It fixes a single node as the 'source' and finds the shortest paths from the source to all other nodes in the graph.

## Lecture

Prerequisite:
- Data Structure (Priority Queue)
- Introduction to Graph & Representaion
- Breadth-First Search (bfs)

What you will learn:
- Dijkstra's Algorithm

Videos:

[![](https://img.youtube.com/vi/2zjv48EqNWU/0.jpg)](https://www.youtube.com/watch?v=2zjv48EqNWU)

[![](https://img.youtube.com/vi/rT9q0-xwUcE/0.jpg)](https://www.youtube.com/watch?v=rT9q0-xwUcE)

Code:

Code to find the shortest path from specified node 'source' to all nodes (1 to n) in an undirected graph, result will be stored in 'cost' array. Complexity of dijkstra's algorithm is noOfEdges*log(noOfEdges).

Code takes input in the form of:
The first line contains two integers `n` and `m`, where `n` is the number of nodes and `m` is the number of edges.
Following `m` lines contain one edge each in form `ai`, `bi` and `wi` ,
where `ai`,`bi` are edge endpoints and `wi` is the length of the edge. Last line contains one integer `s`, source node.

```cpp
#include <bits/stdc++.h>
using namespace std;
typedef long long ll;
 
const int N = 1e5 + 2;
vector<vector<pair<int, int>>>graph;
ll cost[N];
bool visited[N];
 
void dijkstra(int source) {
  priority_queue<pair<ll, int>>shortestpath; //use priority queue to sort distances in increasing order (smallest distance at top)
  for (int i = 0; i < N; ++i) {
    cost[i] = 1e18; //initialize cost to the maximum positive number
    visited[i] = 0;
  }
  shortestpath.push(make_pair(0, source)); //add source node with distance 0
  cost[source] = 0;
  while (!shortestpath.empty()) {
    int node = shortestpath.top().second;
    ll dist = -shortestpath.top().first; //make distance positive again
    shortestpath.pop();
    if (visited[node]) //continue if we have already found shortest path to this node
      continue;
    visited[node] = 1; 
    for (int i = 0; i < graph[node].size(); ++i) { //find shortest path to other nodes
      int newnode = graph[node][i].first;
      ll newdist = graph[node][i].second + dist;
      if (newdist < cost[newnode]) {
        cost[newnode] = newdist;
        shortestpath.push(make_pair(-newdist, newnode)); //distances are stored as negative numbers so that priority queue can sort them properly
      }
    }
  }
}
 
int main() {
  int noOfNodes, noOfEdges;
  cin >> noOfNodes >> noOfEdges;
  graph.resize(noOfNodes + 1);  //graph is represented as an adjacency list
  int node1, node2, dist;
  for (int i = 0; i < noOfEdges; ++i) {
    cin >> node1 >> node2 >> dist;
    graph[node1].push_back(make_pair(node2, dist));
    graph[node2].push_back(make_pair(node1, dist));
  }
  int source;
  cin >> source;
  dijkstra(source);
  for (int i = 1; i <= noOfNodes; ++i) {
    cout << "Shortest path between " << source << " and " << i << " is: " << cost[i] << endl;
  }
  return 0;
}
```
## Practice Problems

- https://codeforces.com/problemset/problem/20/C
- https://codeforces.com/contest/450/problem/D (solution: https://www.youtube.com/watch?v=CjihDdimgF8&list=PLPSFnlxEu99Ewm9LK4mBLkXeE-p_Bskha&index=11)

**Authors:**
* Zaina Al Mashni

**Video Credits**:
* Essa Hindi