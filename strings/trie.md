# Trie
* A simple but powerful data structure.
* It adds/searches for string in O (L).
* It is a tree with branches as letters.

## Prerequisites
* None

## Lecture

[![](https://img.youtube.com/vi/0GuTn_g7B2o/0.jpg)](https://youtu.be/0GuTn_g7B2o)

```cpp
#include <bits/stdc++.h>

using namespace std;
vector<vector<int> > v;
vector<bool> e;
void insert(string &s) {
	int cur = 0;
	for (int i = 0; i < s.size(); ++i) {
		char c = s[i] - 'a';
		if (v[cur][c] == -1) {
			v[cur][c] = v.size();
			v.push_back(vector<int>(26, -1));
			e.push_back(false);
		}
		cur = v[cur][c];
	}
	e[cur] = true;
}
bool find(string &s) {
	int cur = 0;
	for (int i = 0; i < s.size(); ++i) {
		char c = s[i] - 'a';
		if (v[cur][c] == -1) {
			return false;
		}
		cur = v[cur][c];
	}
	return e[cur];
}
int main() {
	int n;
	cin >> n;
	v.resize(1);
	v[0].resize(26, -1);
	e.push_back(false);
	for (int i = 0; i < n; ++i) {
		string s;
		cin >> s;
		insert(s);
	}
	int q;
	cin >> q;
	for (int i = 0; i < q; ++i) {
		string s;
		cin >> s;
		if (find(s))
			cout << "Yes" << endl;
		else
			cout << "No" << endl;
	}
	return 0;
}
```
## Practice Problems

* https://www.spoj.com/problems/SUBXOR/

* https://www.spoj.com/problems/MORSE/

* https://www.spoj.com/problems/PRHYME/

* https://www.spoj.com/problems/TAP2012D/

* https://codeforces.com/problemset/problem/271/D

* https://codeforces.com/problemset/problem/923/C

* https://codeforces.com/problemset/problem/858/D

* https://codeforces.com/problemset/problem/455/B

* https://codeforces.com/problemset/problem/282/E

* https://codeforces.com/problemset/problem/842/D

* https://codeforces.com/problemset/problem/514/C

* https://codeforces.com/problemset/problem/706/D

* https://www.codechef.com/problems/PPTREE

* https://www.codechef.com/problems/XRQRS

* https://www.codechef.com/problems/MINXOR

* https://www.codechef.com/problems/KGP13G

* https://www.codechef.com/problems/SUBBXOR

**Authors:**
- Ahed Al-Rashaida

**Video Credits:**
- Hasan Al Hamsh
