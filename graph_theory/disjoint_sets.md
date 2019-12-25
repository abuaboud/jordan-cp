# Disjoint sets

A disjoint-sets is a data structure that keeps track of a set of elements partitioned into number of non-overlapping subsets.

It has two powerful operation 

- connect two subsets together.

- determine the subset that each element belong to.

## Lecture 

What you will learn:
- Disjoint sets

Make you sure you solve all practice problems as they contains extra ideas and tricks.


[![](https://img.youtube.com/vi/14yCWubaXMk/0.jpg)](https://www.youtube.com/watch?v=14yCWubaXMk)

```cpp
#include <iostream>
using namespace std;

const int N = 1000;
int p[N];

int find(int u) {
	if (p[u] == u)
		return u;

	return p[u] = find(p[u]);
}

int main() {
	int n, m;
	cin >> n >> m;

	for (int i = 0; i < n; i++)
		p[i] = i;

	while (m--) {
		int a, b;
		cin >> a >> b;

		a = find(a);
		b = find(b);

		if (a != b) {
			p[a] = b;
		}
	}
	return 0;
}
```

## Practice Problems:

Roads not only in Berland: [https://codeforces.com/problemset/problem/25/D]

Learning Languages[https://codeforces.com/contest/277/problem/A]

Find Lexicographically Smallest Permutation [https://www.spoj.com/problems/IITKWPCI/]

Civilization [https://codeforces.com/problemset/problem/455/C]

**Authors:**
* Mohammad AbuAboud.