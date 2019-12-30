# Binary Search

> Learn to enjoy it and build passion for problem solving, because unless you see the beauty in it don’t expect to keep going for long.

Binary Search is a searching algorithm in which you can find an element in a sorted big range of possible solutions but in each iteration we erase half of the range. 
Such solution takes no more than O(logN) which is really small even for really big numbers.

## Lecture 

What you will learn:
- Binary search Algorithm
- lower_bound
- upper_bound
- Built-in Binary search function

The Binary Search part ends at 1:28:00.

[![](**https://img.youtube.com/vi/C--fpya1vBw/0.jpg**)](https://www.youtube.com/watch?v=C--fpya1vBw)

This code finds a number in a given range using Binary Search algorithm
```cpp
#include <bits/stdc++.h>
using namespace std;

int const N = 200001;
int n, v[N], number;
 
int main(){
	scanf("%d", &n);
	for(int i = 0; i<n; ++i)scanf("%d",v+i);
	scanf("%d", &number);
	int l = 0, r = n-1, md;
	while(l <= r){
		 mid = (l+r)/2;
		 if(v[mid] < number)l = mid+1;
		 if(v[mid] > number)r = mid-1;
		 if(v[mid] == number){
		 	 printf("YES\n%d\n", mid+1);
		 	 return 0;
		 }
	}
	printf("NO\n");
}
```

## Practice Problems:

!hasan : [https://codeforces.com/problemset/gymProblem/101257/D]

Points on Line:  [https://codeforces.com/contest/251/problem/A]

Cartons of Milk: [https://codeforces.com/contest/767/problem/D]

String Game [https://codeforces.com/problemset/problem/778/A]

Burning Midnight Oil : [https://codeforces.com/contest/165/problem/B]

Save The Nature : [https://codeforces.com/contest/1241/problem/C]

Time Limit Exceeded? :[https://codeforces.com/gym/100676/attachments]

Mission in Amman(B) : [https://codeforces.com/gym/100989/problem/G]

Candies : [https://codeforces.com/contest/991/problem/C]

Maximum Median: [https://codeforces.com/contest/1201/problem/C]

Computer Game : [https://codeforces.com/contest/1183/problem/C]

Longest K-Good Segment : [https://codeforces.com/problemset/problem/616/D]

Exposition : [https://codeforces.com/contest/6/problem/E]

Distances to Zero : [https://codeforces.com/problemset/problem/803/B]

Foe Pairs : [https://codeforces.com/problemset/problem/652/C]

Hard Process :[https://codeforces.com/problemset/problem/660/C]

Beaver: [https://codeforces.com/problemset/problem/79/C]

Two Tvs: [https://codeforces.com/contest/845/problem/C]

**Authors:**
* Nour Bzour