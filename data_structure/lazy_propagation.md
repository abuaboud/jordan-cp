# Segment Tree - Lazy Propagation

Lazy propagation allows us to do fast updates on a range, so we will be able to solve range update / range queries problems here.

## Prerequisites

* Recursion
* Segement tree.

## Explanation

[![](https://img.youtube.com/vi/yLDdGkT4GkM/0.jpg)](https://youtu.be/yLDdGkT4GkM)

## Problem CF52C

This is a simple range increment / range sum problem with a slight modification

```cpp
#include <stdio.h>
#include <algorithm>
using namespace std;
int n,q,x,y,v[200001];
long long seg[2000000],lazy[2000000],val;
void build(int n,int s,int e){
    if(s>e){
        seg[n]=1ll<<62;
        return;
    }
    if(s==e){
        seg[n]=v[s];
        return;
    }
    build(n*2,s,(s+e)/2);
    build(n*2+1,(s+e)/2+1,e);
    seg[n]=min(seg[2*n],seg[2*n+1]);
}
void update(int n,int s,int e){
    if(lazy[n]){
        lazy[2*n]+=lazy[n];
        lazy[2*n+1]+=lazy[n];
        seg[n]+=lazy[n];
        lazy[n]=0;
    }
    if(s>y || e<x)
        return;
    if(s>=x && e<=y){
        lazy[2*n]+=val;
        lazy[2*n+1]+=val;
        seg[n]+=val;
        return;
    }
    update(n*2,s,(s+e)/2);
    update(n*2+1,(s+e)/2+1,e);
    seg[n]=min(seg[2*n],seg[2*n+1]);
}
long long get(int n,int s,int e){
    if(e<x || s>y)
        return 1ll<<62;
    if(lazy[n]){
        lazy[2*n]+=lazy[n];
        lazy[2*n+1]+=lazy[n];
        seg[n]+=lazy[n];
        lazy[n]=0;
    }
    if(s>=x && e<=y)
        return seg[n];
    return min(get(n*2,s,(s+e)/2),get(n*2+1,(s+e)/2+1,e));
}
int main()
{
    int a,b;
    long long r;
    scanf("%d",&n);
    for(int i=1;i<=n;++i)
        scanf("%d",v+i);
    build(1,1,n);
    scanf("%d\n",&q);
    char line[64];
    while(q--){
        if(sscanf(gets(line),"%d%d%lld",&x,&y,&val)==3){
            ++x;++y;
            if(y>=x)
                update(1,1,n);
            else{
                swap(x,y);
                a=x;
                b=y;
                x=1;
                y=a;
                update(1,1,n);
                x=b;
                y=n;
                update(1,1,n);
            }
        }else{
            ++x;++y;
            if(y>=x)
                printf("%lld\n",get(1,1,n));
            else{
                swap(x,y);
                a=x;
                b=y;
                x=1;
                y=a;
                r=get(1,1,n);
                x=b;
                y=n;
                r=min(r,get(1,1,n));
                printf("%lld\n",r);
            }
        }
    }
    return 0;
}

```

## Practice Problems:

HORRIBLE - Horrible Queries : [https://www.spoj.com/problems/HORRIBLE/]

Lucky Queries : [https://codeforces.com/contest/145/problem/E]

**Authors**
- Obada Alabbadi.

**Video Credit**
- Ibraheem Tuffaha.

**Improvements Needed**

- More simple problems.
- Written material.