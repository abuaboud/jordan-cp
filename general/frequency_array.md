# Frequency Array
Frequency Array is an array used to find the frequency of some elements in a range of elements
(how often values occur within a range of values). 

## Prerequisites
* None

## Lecture
In this video, you will learn about the frequency array.

[![](https://img.youtube.com/vi/wKM6bQdtBbo/0.jpg)](https://www.youtube.com/watch?v=wKM6bQdtBbo)

Frequency array code for numbers:
```cpp
#include <iostream>
using namespace std;
int n;
int freq[100001];//all the values are zeroes because of the global declaration

int main() {
	cin >> n;
	for (int i = 0 ; i < n ; i++){
	    int x;
	    cin >> x;
	    freq[x]++;//freq[x]=freq[x]+1
	}
	for (int i=1;i<100001;i++){
	    if (freq[i]!=0){// if there is an occurrence for the value i in the given numbers print the the value i and it's frequency
	        cout <<"The frequency of "<< i << " in the given numbers = " <<freq[i]<<endl;
	    }
	}
	return 0;
}
```

In these two videos, you will know how frequency array is used in problems.

[![](https://img.youtube.com/vi/PJXnPgCryK4/0.jpg)](https://www.youtube.com/watch?v=PJXnPgCryK4)

First Problem Code (Doggo Recoloring): 

```cpp
#include <bits/stdc++.h>
using namespace std;
string s;
int n,freq[200];
int main() {
    cin >>n>>s;
    if (n==1){
        cout <<"YES";
        return 0;
    }
    for (int i=0;i<n;i++){
	    freq[s[i]]++;
	    if (freq[s[i]]==2) {
	    	cout <<"YES";
	    	return 0;
    	}
    }
    cout <<"NO";
	return 0;
}
```

Second Problem Code (Amusing Joke): 

```cpp
#include <bits/stdc++.h>
using namespace std;
string s1,s2,s3;
int freq1[200],freq2[200];
 
int main() {
    cin >>s1>>s2>>s3;
    for (int i=0;i<s1.size();i++) 
        freq1[s1[i]]++;
    for (int i=0;i<s2.size();i++) 
        freq1[s2[i]]++;
    for (int i=0;i<s3.size();i++) 
        freq2[s3[i]]++;
 
    for (char i='A';i<='Z';++i){
	    if (freq1[i] != freq2[i]){
		    cout <<"NO";
		    return 0;
	    }
    }
    cout <<"YES";
	return 0;
}

```


## Practice Problems:

Doggo Recoloring [https://codeforces.com/problemset/problem/1025/A]

Amusing Joke [https://codeforces.com/problemset/problem/141/A]

Different is Good [https://codeforces.com/problemset/problem/672/B]

Pangram [https://codeforces.com/problemset/problem/520/A]

Remove the Duplicates [https://codeforces.com/contest/978/problem/A]

I Wanna Be the Guy [https://codeforces.com/problemset/problem/469/A] 

Taxi [https://codeforces.com/problemset/problem/158/B]

Towers [https://codeforces.com/problemset/problem/37/A]

Cards [https://codeforces.com/contest/1220/problem/A]

LLPS [https://codeforces.com/problemset/problem/202/A]

Opposite Attract [https://codeforces.com/problemset/problem/131/B]

Inventory [https://codeforces.com/problemset/problem/569/B]

Boxes Packing [https://codeforces.com/problemset/problem/903/C]

Silent Classroom [https://codeforces.com/problemset/problem/1166/A]

Important Exam [https://codeforces.com/problemset/problem/1201/A]

ZgukistringZ [https://codeforces.com/contest/551/problem/B]

**Author:**
* Rand Abu Al-Ragheb

**Video Credits:**
* Nada Al-Shamayleh
* Mohammad Zuhair
    