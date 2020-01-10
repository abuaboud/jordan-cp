# KMP
KMP Algorithm is one of the most popular patterns matching algorithms and it stands for Knuth Morris Pratt.

KMP algorithm was the first linear time complexity algorithm for string matching.

KMP algorithm is one of the string matching algorithms used to find a Pattern in a Text.

This algorithm compares character by character from left to right, But whenever a mismatch occurs, it uses a preprocessed
table called "Prefix Table" to skip characters comparison while matching.

Sometimes prefix table is also known as LPS Table. Here LPS stands for "Longest proper Prefix which is also Suffix".

## Prerequisites
* None

## Lecture

[![](https://img.youtube.com/vi/V_cS906OMWc/0.jpg)](https://youtu.be/V_cS906OMWc)

This code represents that if you have the failure array you could do the search as the following
```cpp
//KMP Part 1
#include <bits/stdc++.h>
using namespace std;
string s, t;
int f[100] = {0,0,0,1,2,3,0};
void search() {
	int len = 0;
	for (int i = 0; i < s.size(); ++i) {
		while (len>0 && s[i] != t[len])
			len = f[len - 1];
		if (s[i] == t[len])
			++len;
		if (len == t.size()) {
			cout << i - len + 1 << endl;
			len = f[len - 1];
		}
	}
}
int main() {
	//   01234567890123456789012345
	s = "carcarcarcarcardcarcardcar";
	t = "carcard";
	search();
	return 0;
}
```

[![](https://img.youtube.com/vi/d7FnvZUtRQQ/0.jpg)](https://youtu.be/d7FnvZUtRQQ)

This code represents how to build the failure array and use it for searching

```cpp
#include <bits/stdc++.h>
using namespace std;
string s, t;
int f[100];
void search() {
	int len = 0;
	for (int i = 0; i < s.size(); ++i) {
		while (len>0 && s[i] != t[len])
			len = f[len - 1];
		if (s[i] == t[len])
			++len;
		if (len == t.size()) {
			cout << i - len + 1 << endl;
			len = f[len - 1];
		}
	}
}
void build() {
	int len = 0;
	f[0] = 0;
	for (int i = 1; i < t.size(); ++i) {
		while (len>0 && t[i] != t[len])
			len = f[len - 1];
		if (t[i] == t[len])
			++len;
		f[i] = len;
	}
}
int main() {
	//   01234567890123456789012345
	s = "carcarcarcarcardcarcardcar";
	t = "carcard";
	build();
	search();
	return 0;
}
```


##Practice Problems


* https://www.spoj.com/problems/EPALIN/

* https://www.spoj.com/problems/NHAY/

* https://www.spoj.com/problems/PERIOD/

* https://www.spoj.com/problems/NAJPF/

* https://www.spoj.com/problems/FINDSR/

* https://www.spoj.com/problems/ARDA1/

* https://www.spoj.com/problems/FILRTEST/

* https://www.spoj.com/problems/PSTRING/

* https://www.spoj.com/problems/VPALIN/

* https://www.spoj.com/problems/JZPGYZ/

* https://codeforces.com/problemset/problem/126/B

* https://codeforces.com/problemset/problem/432/D

* https://codeforces.com/problemset/problem/535/D

* https://codeforces.com/contest/625/problem/B


**Authors:**
- Ahed Al-Rashaida

**Video Credits:**
- Hasan Al Hamsh
