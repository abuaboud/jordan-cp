## Dynamic Programming
> Those who cannot remember the past are condemned to repeat it. <br> - George Santayana

is an algorithmic technique which is usually based on a recurrent formula and one (or some) starting states. A sub-solution of the problem is constructed from previously found ones.
 
DP solutions have a polynomial complexity which assures a much faster running time than other techniques like backtracking, brute-force etc.

One of the best way to learn something, to learn it from its applications

### Problem 1 (Cut Ribbon)

What you will learn: Basic understanding of dynamic programming

[Problem Link](https://codeforces.com/problemset/problem/189/A)

[![](https://img.youtube.com/vi/4VBt8sKocyw/0.jpg)](https://www.youtube.com/watch?v=4VBt8sKocyw)

Recursive solution:
```cpp
#include <bits/stdc++.h>
using namespace std;
int n , a , b , c,dp[4001];
int calc(int len){
	if(len < 0)return -1e9;
	if(len == 0)return 0;
	int &ret = dp[len];
	if(ret != -1)return ret;
	return ret = max(1+calc(len-c),max(1+calc(len-a),1+calc(len-b)));
}
int main(){
	memset(dp,-1,sizeof dp);
	cin >> n >> a >> b >> c;
	cout << calc(n) << endl;
	return 0;
}
```
Iterative solution:
```cpp
#include <bits/stdc++.h>
using namespace std;
int n , a , b , c,dp[4001];
int main(){
	cin >> n >> a >> b >> c;
	dp[0] = 0;
	for(int i = 1; i <= n ; ++i){
		dp[i] = -1e9;
		if(i >= a)dp[i] = max(dp[i],1+dp[i-a]);	
		if(i >= b)dp[i] = max(dp[i],1+dp[i-b]);
		if(i >= c){dp[i] = max(dp[i],1+dp[i-c]);
	}
	cout << dp[n] << endl;
	return 0;
}
```

### Problem 2 (Plus or Minus)

What you will learn: transfer complete search into dynamic programming with memoization technique , 2D dynamic programming

Easy version (Complete Search): [Problem Link](https://codeforces.com/gym/100989/problem/L)

Hard version (Dynamic Programming): [Problem Link](https://codeforces.com/gym/100989/problem/M)

[![](https://img.youtube.com/vi/mULWTmbICUQ/0.jpg)](https://www.youtube.com/watch?v=mULWTmbICUQ)

```cpp
#include <bits/stdc++.h>
using namespace std;
const int oo= 1e9;
int n,a[301];
string sign;
int dp[301][180010];
int calc(int idx , int sum){
	if(idx == n)return (sum == 0 ? 0 : oo);
	int &ret = dp[idx][sum+300*300];
	if(ret != -1)return ret;
	ret = calc(idx+1,sum+a[idx]);
	if(idx > 0)ret = min(ret,1 + calc(idx+1,sum-1*a[idx]));
	return ret;
}
int main(){
	cin >> n;
	for (int i = 0; i < n; ++i){
		int s = 1;
		if(i>0){
			cin >> sign;
			if(sign == "-")s *= -1;
		}
		cin >> a[i];
		a[i] *= s;
	}
	cout << calc(0,0) << endl;
	return 0;
}
```
### Problem 3 (Divide by Three)

What you learn: construct the answer after calculating the dynamic programming , Harder question 

[Problem Link](https://codeforces.com/problemset/problem/792/C)

[![](https://img.youtube.com/vi/8JFv2K6zuT8/0.jpg)](https://www.youtube.com/watch?v=8JFv2K6zuT8)

```cpp
#include <bits/stdc++.h>

using namespace std;
string s,ans="";
const int oo = 1e9;
int dp[100001][3][2];

int calc(int idx ,int mod,bool take){
	if(idx == s.size())
		return (mod == 0&&take)?0:oo;
	int &ret = dp[idx][mod][take];
	if(ret != -1)return ret;
	ret = 1+calc(idx+1,mod,take);
	if(s[idx] == '0'){
		if(take)
			ret = min(ret,calc(idx+1,(mod*10+(s[idx]-'0'))%3,1));
	}else{
		ret = min(ret,calc(idx+1,(mod*10+(s[idx]-'0'))%3,1));
	}
	return ret;
}

void build(int idx , int mod , bool take){
	if(idx == s.size())return;
	if(1+calc(idx+1,mod,take)==calc(idx,mod,take)){
		build(idx+1,mod,take);
		return;
	}
	if(s[idx] == '0'){
		if(take && calc(idx+1,(mod*10+(s[idx]-'0'))%3,1)==calc(idx,mod,take)){
			ans += '0';
			build(idx+1,(mod*10+(s[idx]-'0'))%3,1);
			return;
		}
	}else{
		if(calc(idx+1,(mod*10+(s[idx]-'0'))%3,1) == calc(idx,mod,take)){
			ans += s[idx];
			build(idx+1,(mod*10+(s[idx]-'0'))%3,1);
			return ;
		}
	}
}


int main(){
	memset(dp,-1,sizeof dp);
	cin >> s;
	int res = calc(0,0,0);
	if(res == oo){
		for (int i = 0; i < s.size(); ++i){
			if(s[i] == '0'){
				puts("0");
				return 0;
			}
		}
		puts("-1");
		return 0;
	}
	build(0,0,0);
	cout << ans << endl;
	return 0;
}
```

#### Practice Problems:

Frog 1: [ https://atcoder.jp/contests/dp/tasks/dp_a ] 

Frog 2: [ https://atcoder.jp/contests/dp/tasks/dp_b ]

Vacation: [ https://atcoder.jp/contests/dp/tasks/dp_c ]

Knapsack 1: [ https://atcoder.jp/contests/dp/tasks/dp_d ]

Knapsack 2: [ https://atcoder.jp/contests/dp/tasks/dp_e ]

LCS: [ https://atcoder.jp/contests/dp/tasks/dp_f ]

Longest Path: [ https://atcoder.jp/contests/dp/tasks/dp_g ]

Atcoder DP educational problems: [ https://atcoder.jp/contests/dp/tasks ]
