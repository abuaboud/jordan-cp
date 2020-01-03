# Frequency Array
Frequency Array is an array used to find the frequency of some elements in a range of elements
(how often values occur within a range of values). 

## Prerequisites
* None

## Lecture
In this video, you will learn about the frequency array.

[![](https://img.youtube.com/vi/kQGTjql8WjI/0.jpg)](https://www.youtube.com/watch?v=kQGTjql8WjI)


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

In case we want to make a frequency array code for lowercase and uppercase characters and numbers in strings:

Each character has an ASCII code (ex: ‘a’=97,’A’=65,’0’=48).

So for the frequency array, we create an array with the size of Alphabets or numbers (from 0 to 9) 

How can we get the index zero for the letter ‘a’, index one for ‘b’ …. Index 25 for ‘z’?

The answer is just subtracting ‘a’(the ASCII value) from each character we want to get its frequency.

‘a’-‘a’=0 --> 97-97=0

‘b’-‘a’=1 --> 98-97=1

‘z’-‘a’=25 --> 122-97=25

And for uppercase characters, we subtract ‘A’.
And for numbers (as characters), we subtract ‘0’.

```cpp
#include <iostream>
using namespace std;
string s;
int freq[25];//all the values are zeroes because of the global declaration

int main() {
	cin >> s;
	for (int i = 0 ; i < s.size() ; i++){
	    freq[s[i]-'a']++;//freq[x]=freq[x]+1
	}
	for (int i=0;i<25;i++){
	    if (freq[i]){// if there is an occurrence for the character (i+'a') in the given numbers print the character and it's frequency
	        cout <<"The frequency of "<< char(i+'a') << " in the given string = " <<freq[i]<<endl;
	    }
	}
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
    