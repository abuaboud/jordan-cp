# Two Pointers
Not to be confused with the programming term _pointer_ ```int* ptr = new int;```.
A two pointer is the use of regular variables to point at index locations for the sake of reducing the time complexity,
it's not a special algorithm rather just a simple technique, sometimes referred to as _sliding window_.

Two Pointers is a technique that is used to find a segment in an array that satisfies some conditions. The approach relies on the sequence following one specific property on which our pointers can move, we start with an interval and keep expanding this interval as long as it satisfies the properties, otherwise we move the pointers.

## Prerequisites

* Basic understanding of time complexity analysis.
* Knowlege of STL data structures (vector, set and map)

## Objectives

What you will learn:
* The use-cases of Two Pointers' Technique (when and how to use it).
* Be capable of reducing the time complexity for a nested-loop solution to _O(n)_ using Two Pointers.
* Identifying the criteria that should be met to accept or reject the current/local state as a solution.

## Videos 

[![](https://img.youtube.com/vi/wKM6bQdtBbo/0.jpg)](https://www.youtube.com/watch?v=n-Xwrr8RFQ0)

```cpp
#include<iostream>
#include<vector> // A
#include<map> // cnt
#include<set> // s
using namespace std;

const int INF = 1e9 + 5;
map<int, int> cnt;
set<int> s;

int n, K;
vector<int> A;

int main() {

/* SAMPLE INPUT */
	A = { 1, 5, 5, 4, 2, 4, 3, 5, 6, 6, 7, 9, 7 };
	n = 13, K = 5;

/*
	// Add Your Own Custom Input:
	cin >> n >> K;
	for (int i = 0, P; i < n; ++i) {
		cin >> P;
		A.push_back(P);
	}
*/
	int l = 0, r = 0, ans = INF;

	while (l < n) {
		while (r < n && s.size() < K) {
			s.insert(A[r]);
			cnt[A[r]]++;
			r++;
		}

		if (s.size() >= K) {
			ans = min(ans, r - l);
		}

		if (cnt[A[l]] == 1)
			s.erase(A[l]);

		cnt[A[l]]--;
		l++;
	}

	cout << ans << '\n';

	return 0;
}

```

[![](https://img.youtube.com/vi/wKM6bQdtBbo/0.jpg)](https://www.youtube.com/watch?v=5As8FW_FldQ)

```cpp
#include <bits/stdc++.h>
using namespace std;
typedef long long ll;
#define mp make_pair
#define pb push_back 
const int M=100001;
int n,m,x,y,t,a[M];
int main() {
	ios_base::sync_with_stdio(0); cin.tie(NULL);	
	cin>>n>>t;
	for(int i=0;i<n;i++){
		cin>>a[i];
	}
	int l=0,r=0,ans=0,sum=a[0];
	while(l<n && r<n){
		if(l>r){
			r++;
			sum+=a[r];
			continue;
		}
		if(sum>t){
			sum-=a[l];
			l++;
		}
		else{
			ans=max(ans,r-l+1);
			r++;
			if(r!=n)
				sum+=a[r];
		}
	}
	cout<<ans;
	return 0;
}
```

## Practice Problems:

Books: [https://codeforces.com/problemset/problem/279/B]
(The solution is discussed with the previous SolverToBe video)

Sereja and Dima: [https://codeforces.com/problemset/problem/381/A]

!hasan : [https://codeforces.com/problemset/gymProblem/101257/D]

Points on Line:  [https://codeforces.com/contest/251/problem/A]

Cartons of Milk: [https://codeforces.com/contest/767/problem/D]

* Time Limit Exceeded? :[https://codeforces.com/gym/100676/attachments]

* Mission in Amman(B) : [https://codeforces.com/gym/100989/problem/G] 

Longest K-Good Segment : [https://codeforces.com/problemset/problem/616/D]

Exposition : [https://codeforces.com/contest/6/problem/E]

Foe Pairs : [https://codeforces.com/problemset/problem/652/C]

Hard Process :[https://codeforces.com/problemset/problem/660/C]

Beaver: [https://codeforces.com/problemset/problem/79/C]


## Needs Improvement:
* Add the correct photo thumbnail for the YouTube videos.
* Sort the problems by difficulty.
* Check if 'Time Limit Exceeded?' and 'Mission in Amman(B)' can be solved using Two Pointers.


**Authors:**
* Nour Bzour
* Najm Nabhani

**Credits:**
* Mostafa Sadd Ibrahim
* Essa Hindi
