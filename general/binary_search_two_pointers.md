# Binary Search

> Learn to enjoy it and build passion for problem solving, because unless you see the beauty in it don’t expect to keep going for long.

Binary Search is a searching algorithm in which you can find an element in a sorted big range of possible solutions but in each but in each iteration we erase half of the range. 
Such solution takes no more than O(logN) which is really small even for really big numbers.


# Two Pointers

Two Pointers is a technique that is used to find a segment in an array that satisfies some conditions.
The approach relies on the sequence following one specific property on which our pointers can move, we start with an interval and  keep expanding this interval as long as it satisfies the properties, otherwise we move the pointers. 

## Lecture 

What you will learn:
- Binary search Algorithm
- lower_bound
- upper_bound
- Built-in Binary search function
- Two Pointers technique


[![](https://img.youtube.com/vi/C--fpya1vBw/0.jpg)](https://www.youtube.com/watch?v=C--fpya1vBw)

This code finds a number in a given range using Binary Search algorithm
```cpp
#include <bits/stdc++.h>
using namespace std;
#define ll long long
#define all(x) x.begin(),x.end()
 
int const N = 200001;
int n, v[N], number;
 
int main(){
	scanf("%d", &n);
	for(int i = 0; i<n; ++i)scanf("%d",v+i);
	scanf("%d", &number);
	int l = 0, r = n-1, md, an = -1;
	while(l <= r){
		 md = (l+r)/2;
		 if(v[md] < number)l = md+1;
		 if(v[md] > number)r = md-1;
		 if(v[md] == number){
		 	 printf("YES\n%d\n", md+1);
		 	 return 0;
		 }
	}
	printf("NO\n");
}
```
This code finds the maximum range that such that their sum is less than or equal to some number using two pointers 
```cpp
#include <bits/stdc++.h>
using namespace std;
#define ll long long
#define all(x) x.begin(),x.end()
 
 
int const N = 200001;
int n, v[N], number;
 
int main(){
   scanf("%d", &n);
   for(int i = 0; i<n; ++i)scanf("%d", v+i);
   scanf("%d", &number);
   int l = 0, sum = 0, an = 0, from = 0, to = 0;
   for(int i = 0; i<n; ++i){
   	sum += v[i];
   	while(sum > number){sum -= v[l], ++l;}
   	if(i - l + 1 > an){
   		an = i - l + 1;
   		from = l, to = i;
   	}
   }
   printf("%d %d %d\n", an, from , to);
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