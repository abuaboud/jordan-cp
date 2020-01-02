# Permutation and Combination

Permutation is the mathematics of counting and arranging items where is
the order important

Combination is the mathematics of counting and arranging items where is
the order is not important

## Prerequisites

* Modular Arithmetic

## Objectives
* Permutation
* Combination

## Videos 

[![](https://img.youtube.com/vi/TDHiHSfRxCM/0.jpg)](https://www.youtube.com/watch?v=TDHiHSfRxCM)

```cpp
#include <bits/stdc++.h>
using namespace std;
typedef long long ll;
const int mod = 1000000007;

ll factorial[200001],inverseFactorial[200001];

ll fastPower(ll a , ll b){
  if(b==0)
    return 1;
  ll res = fastPower(a,b/2);
  if(b%2 == 1)
    return ((res * res)%mod * a)%mod;
  return (res*res)%mod;
}
ll nChooseK(ll n , ll k){
  return ((factorial[n]*inverseFactorial[k])%mod*inverseFactorial[n-k])%mod;
}

int main(){
  factorial[0]=inverseFactorial[0] = 1;
  for(int i = 1 ; i<= 200000; ++i){
    factorial[i] = (i * factorial[i-1])%mod;
    // If mod is prime, we can use little fermat to find the modular inverse
    inverseFactorial[i] = fastPower(factorial[i],mod-2);
  }
  cout << nChooseK(3,2) << endl;
  return 0; 
}
```
Problem PSUT Qualification Round 2017 G Bad Subsequences

[![](https://img.youtube.com/vi/FUnF34CPDiM/0.jpg)](https://www.youtube.com/watch?v=FUnF34CPDiM)

Solution:
```cpp
#include <bits/stdc++.h>
using namespace std;
typedef long long ll;
const int mod = 1000000007;

ll f[200001],inv[200001];

ll fastPower(ll a , ll b){
	if(b==0)
		return 1;
	ll res = fastPower(a,b/2);
	if(b%2 == 1)
		return ((res * res)%mod * a)%mod;
	return (res*res)%mod;
}
ll nCk(ll n , ll k){
	return ((f[n]*inv[k])%mod*inv[n-k])%mod;
}
char tmp[200011];
int main(){
	f[0]=1;
	inv[0] = fastPower(1,mod-2);
	for(int i = 1 ; i<= 200000; ++i){
		f[i] = (i * f[i-1])%mod;
		inv[i] = fastPower(f[i],mod-2);
	}
	int t;
	scanf("%d",&t);
	while(t--){
		string s;
		scanf("%s",tmp);
		s = tmp;
		int zeros = 0 , ones = 0;
		for (int i = 0; i < s.size(); ++i){
			if(s[i] == '1')ones++;
			else zeros++;
		}
		ll numberOfWayToChooseOddNumberOfOnes = 0;
		for(int i = 1 ; i <= ones;i+= 2){
			numberOfWayToChooseOddNumberOfOnes = (numberOfWayToChooseOddNumberOfOnes + nCk(ones,i))%mod;
		}
		ll numberofWaysToChooseOddNumberOfZeros = 0;
		for(int i = 1 ; i <= zeros; i += 2)
			numberofWaysToChooseOddNumberOfZeros = (numberofWaysToChooseOddNumberOfZeros + nCk(zeros,i))%mod;
		ll ans = (fastPower(2,s.size())-(numberofWaysToChooseOddNumberOfZeros*numberOfWayToChooseOddNumberOfOnes)%mod+mod)%mod;
		printf("%lld\n", (ans-1+mod)%mod);		
	}
	return 0;	
}
```
## Practice Problems:

Rectangles [https://codeforces.com/contest/844/problem/B]

Bad Subsequences [https://codeforces.com/group/BDIXyZZHhT/contest/215961/problem/G]


**Authors:**
* Mohammad AbuAboud