# Segment Tree (Basics)

A segment tree is an advanced data structure that allows us to do fast update / queries on ranges of array elements.

We will focus mainly on element update / range queries problems here.

## Prerequisites

* Recursion

## Range Sum / Element Update Queries

[![](https://img.youtube.com/vi/KR7icII-RWI/0.jpg)](https://youtu.be/KR7icII-RWI)

```cpp
#include <bits/stdc++.h>
using namespace std;
typedef long long ll;
const int N = 100000 + 5;
int n, a[N], seg[4 * N];

void build(int p, int l, int r) {
	if(l == r) {
		seg[p] = a[l];
		return;
	}
	int mid = (l + r) / 2;
	build(p*2, l, mid);
	build(p*2+1, mid+1, r);
	seg[p] = seg[p*2] + seg[p*2+1];
}


int get(int p, int l, int r, int a, int b) {
	if(a <= l && r <= b)
		return seg[p];
	if(r < a || l > b)
		return 0;
	int mid = (l + r) / 2;
	return get(p*2, l, mid, a, b)
		  +get(p*2+1, mid+1, r, a, b);
}

void update(int p, int l, int r, int idx, int v){
	if(l == r) {
		seg[p] = a[idx] = v;
		return;
	}
	int mid = (l+r)/2;
	if(idx <= mid)
		update(p*2, l, mid, idx, v);
	else
		update(p*2+1, mid+1, r, idx, v);
	seg[p] = seg[p*2] + seg[p*2+1];
}

int main() {
	freopen("a.in", "r", stdin);
	scanf("%d", &n);
	for(int i=0; i<n; ++i)
		scanf("%d", a+i);
	build(1, 0, n-1);
	int q;
	scanf("%d", &q);
	for(int i=0, a, b, t; i<q; ++i) {
		scanf("%d%d%d", &t, &a, &b);
		if(t == 0) {
			--a, --b;
			printf("%d\n", get(1, 0, n-1, a, b));
		} else {
			--a;
			update(1, 0, n-1, a, b);
		}
	}
	return 0;
}

```

## Range Minimum / Element Update Queries

[![](https://img.youtube.com/vi/8QKIAcPyagA/0.jpg)](https://youtu.be/8QKIAcPyagA)

```cpp
#include <bits/stdc++.h>
using namespace std;
typedef long long ll;
const int N = 100000 + 5;
int n, a[N], seg[4 * N];

void build(int p, int l, int r) {
	if(l == r) {
		seg[p] = l;
		return;
	}
	int mid = (l + r) / 2;
	build(p*2, l, mid);
	build(p*2+1, mid+1, r);

	int il = seg[p*2];
	int ir = seg[p*2+1];
	if(a[il] < a[ir])
		seg[p] = il;
	else
		seg[p] = ir;
}


int get(int p, int l, int r, int a, int b) {
	if(a <= l && r <= b)
		return seg[p];
	if(r < a || l > b)
		return -1;
	int mid = (l + r) / 2;

	int il = get(p*2, l, mid, a, b);
	int ir = get(p*2+1, mid+1, r, a, b);
	if(ir == -1)
		return il;
	if(il == -1)
		return ir;

	if(::a[il] < ::a[ir])
		return il;
	else
		return ir;

}

void update(int p, int l, int r, int idx, int v){
	if(l == r) {
		a[idx] = v;
		seg[p] = idx;
		return;
	}
	int mid = (l+r)/2;
	if(idx <= mid)
		update(p*2, l, mid, idx, v);
	else
		update(p*2+1, mid+1, r, idx, v);

	int il = seg[p*2];
	int ir = seg[p*2+1];
	if(a[il] < a[ir])
		seg[p] = il;
	else
		seg[p] = ir;
}

int main() {
	freopen("a.in", "r", stdin);
	scanf("%d", &n);
	for(int i=0; i<n; ++i)
		scanf("%d", a+i);
	build(1, 0, n-1);
	int q;
	scanf("%d", &q);
	for(int i=0, a, b, t; i<q; ++i) {
		scanf("%d%d%d", &t, &a, &b);
		if(t == 0) {
			--a, --b;
			printf("%d\n", get(1, 0, n-1, a, b));
		} else {
			--a;
			update(1, 0, n-1, a, b);
		}
	}
	return 0;
}

```

## Problem CF597C

Link : [https://codeforces.com/contest/597/problem/C]

[![](https://img.youtube.com/vi/WRvpG8DTgzk/0.jpg)](https://youtu.be/WRvpG8DTgzk)

Solution :

```cpp
#include <bits/stdc++.h>
using namespace std;
typedef long long ll;
const int N = 100005;
int n, k, x[N], si, idx, a, b;
ll dp[12][N], st[12][4 * N], val;
    
void update(int p = 1, int l = 0, int r = n - 1) {
    st[si][p] += val;
    if (l == r)
        return;
    int mid = (l + r) >> 1;
    if (idx <= mid)
        update(p << 1, l, mid);
    else
        update((p << 1) + 1, mid + 1, r);
}
    
ll get(int p = 1, int l = 0, int r = n - 1) {
    if (r < a || l > b)
        return 0;
    if (a <= l && r <= b)
        return st[si][p];
    int mid = (l + r) >> 1;
    return get(p << 1, l, mid) + get((p << 1) + 1, mid + 1, r);
}
    
int main() {
    scanf("%d%d", &n, &k);
    ++k;
    for (int i = 0; i < n; ++i) {
        scanf("%d", x + i);
        --x[i];
        ++dp[1][i];
    }
    b = n - 1;
    for (int i = 2; i <= k; ++i) {
        for (int j = n - 1; j >= 0; --j) {
            idx = a = x[j];
            si = i - 1;
            dp[i][j] = get();
            val = dp[i - 1][j];
            update();
        }
    }
    ll ans = 0;
    for (int i = 0; i < n; ++i)
        ans += dp[k][i];
    cout << ans;
    
    return 0;
}
```

## Practice Problems:

Xenia and Bit Operations : [https://codeforces.com/contest/339/problem/D]

Pashmak and Parmida's problem : [https://codeforces.com/contest/459/problem/D]

Not Equal on a Segment (can be solved without segment tree) : [https://codeforces.com/contest/622/problem/C]

**Improvements Needed**

- More problems.
- Written material.

**Authors**:
- Obada Abadi

**Video Credits**:
* Ibraheem Tuffaha