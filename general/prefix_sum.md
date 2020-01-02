# Prefix Sum
Prefix sum (also called cumulative sum) is an array that helps to get the sum of elements to answer several queries with less complexity than answering each query by brute force.
A cumulative sum is a sequence of partial sums of a given sequence. For example, the cumulative sums of the sequence `(a, b, c, …)` are `(a, a+b, a+b+c, …)`

## Complexity:
* Building the array:
* One-dimensional array: O(n)
* Two-dimensional array: O(n*m)
* Answering each query: O(1)

## Lecture
In this video, you will learn about cumulative sum and its code.

[![](https://img.youtube.com/vi/PAUSwV4zj48/0.jpg)](https://www.youtube.com/watch?v=PAUSwV4zj48)

In this video, you will learn how to use prefix sum in one-dimensional arrays and two-dimensional arrays.
 
The prefix sum part starts at 25:25

[![](https://img.youtube.com/vi/_Xrh_Uuxf8g/0.jpg)](https://www.youtube.com/watch?v=_Xrh_Uuxf8g)

Building one-dimensional prefix sum array and printing the prefix sum between to indices for each query.
 
```cpp
#include <iostream>
using namespace std;
int n, q;
int v[111];
int PrefixSum[111];
int main() {
	cin >>n;
	for (int i=1;i<=n;i++){
		cin >>v[i];
	}
	//PrefixSum[0]=0 from the declartion 
	for (int i=1;i<=n;i++){
		PrefixSum[i]=PrefixSum[i-1]+v[i];
	}
	cin >>q;
	for (int i=0;i<q;i++){
		int l, r;
		cin >>l>>r;
		cout <<PrefixSum[r]-PrefixSum[l-1]<<endl;
	}
	return 0;
}
```

Building two-dimensional prefix sum array and printing the prefix sum between two indices for each query. 

```cpp
#include <iostream>
using namespace std;
int n , m , q;
int A[111][111] ={}; 
int PrefixSum[111][111] ={}; 
 
int main() {
	cin>>n>>m ;
	// the first row is filled with zeroes
	// the first column is filled with zeroes
	for(int i=1 ; i <= n  ; i++){
		for(int  j=1 ; j  <= m ; j++){
			cin>>A[i][j] ; 
			PrefixSum[i][j] = A[i][j] +  PrefixSum[i][j-1] + PrefixSum[i-1][j] - PrefixSum[i-1][j-1] ; 
		}
	}
	cin >>q;
	for(int i=0 ; i < q ; i++){
		int row1,column1,row2,column2;
		cin >>row1>>column1;
		cin >>row2>>column2;
		cout <<PrefixSum[row2][column2]-PrefixSum[row1-1][column2]-PrefixSum[row2][column1-1] +PrefixSum[row1-1][column1-1]<<endl;
	}
	return 0;
}
```

### Useful Technique: 
Plus-Minus Technique is a technique that helps us find the frequency for each number in a range `[left, right]` in `O(n)` which is better than O(n^2).

The technique is an application of Cumulative Sum.

So we have `n` ranges and each range is from `[L,R]` to we add 1 to the `PrefixSum[L]` and subtract 1 from `PrefixSum[R+1]`, and then do a cumulative sum to the array.
 
Why is that true? 

Adding one to the starting point means that we added 1 to the whole array from index L to the last one because we will do a cumulative sum then,

so we need to subtract that one in the last index in the range which is R+1 (since R is in the range),

so when we do the cumulative sum later the one we added to the index L will be added to the whole range from L to R and the in index R+1 the added one will be subtracted. 

### Example problem: 
University of Jordan is willing to open a new section for anatomy lab for n first-year medical students.

Due to their complex schedules and their precious time the university has offered each student the chance to suggest the best period of time ( l-r ) that suits him/her (from l to r). 
Knowing that the duration of the lab is only one hour.

After gathering their suggestions, the university will pick up the most preferred hour that suits the maximum number of students.

**Input:**

The first line contains n `(1 <= n <= 10^7)` — the number of first-year medical students.
Each of the next n lines contains li and ri `(1 <=l[i] <= r[i] <= 24)` the range of time that suits the ith Student. 

**Output:**

Print the hour that suits the maximum number of students.

**Solution:**

Since the constraints of n reach `10^7`, creating an array for the hours and going through a loop from each li until ri (inclusive) and adding one to the hours’ array for each hour between (li and ri). The complexity will be `O(n*24)`,

which is nearly `O(10^8)` in the worst case.

And `10^8` doesn’t always pass so we use Plus-Minus Technique with `O(n)` complexity.

```cpp
#include <iostream>
using namespace std;

int NumOfStudents;
int hours[26];
int maxVotes;
int ans;

int main() {
    cin >>NumOfStudents;
    for (int i=0;i<NumOfStudents;i++){
        int l,r;
        cin >>l>>r;
        hours[l]++;
        hours[r+1]--;
    }
    for(int i=2;i<=24;i++){
        hours[i]+=hours[i-1];
    }
    for (int i=1;i<=24;i++){
        if (hours[i]>maxVotes){
            maxVotes=hours[i];
            ans=i;
        }
    }
    cout <<ans;
	return 0;
}
```
		 

## Practice Problems:

Cumulative Sum Query [https://www.spoj.com/problems/CSUMQ/]

Kuriyama Mirai's Stones [https://codeforces.com/problemset/problem/433/B]

Land Lot [https://codeforces.com/contest/48/problem/B]

Ilya and Queries [https://codeforces.com/problemset/problem/313/B]

Stripe [https://codeforces.com/contest/18/problem/C]

Kefa and Company [https://codeforces.com/problemset/problem/580/B]

Alyona and flowers [https://codeforces.com/contest/740/problem/B]

Little Girl and Maximum Sum [https://codeforces.com/contest/276/problem/C]

Far Relative’s Problem [https://codeforces.com/contest/629/problem/B]

Nikita and string [https://codeforces.com/problemset/problem/877/B]

Karen and Coffee [https://codeforces.com/problemset/problem/816/B]

Chat Online [https://codeforces.com/contest/469/problem/B] 

#### Authors:
* Rand Abu Al-Ragheb
* Nour Bzour

#### Video Credits:
* Nada Al-Shamayleh
* Mohammad Zuhair

