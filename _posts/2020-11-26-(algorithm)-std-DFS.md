---
title: "(algorithm) std DFS"
tag: algorithm
---

백준의 '유기농 배추' 문제. 기본적인 DFS

```
import sys
sys.setrecursionlimit(10000)

def makezero():
    while stk:
        pp = stk.pop()
        if mp[pp[0]][pp[1]]==0:
            return None
        else:
            mp[pp[0]][pp[1]]=0
            if pp[0]<n-1:
                stk.append((pp[0]+1,pp[1]))
                makezero()
            if pp[1]<m-1:
                stk.append((pp[0],pp[1]+1))
                makezero()
            if pp[0]>0:
                stk.append((pp[0] - 1,pp[1]))
                makezero()
            if pp[1]>0:
                stk.append((pp[0],pp[1] - 1))
                makezero()
def checker():
    for i in mp:
        if True in i:
            return True
    return False

for i in range(int(input())):
    m,n,k=map(int,input().split())
    stk=list()
    cnt=0
    mp=[[0]*m for w in range(n)]
    for j in range(k):
        a,b=map(int,input().split())
        mp[b][a]=1
    while checker():
        for q in range(n):
            for p in range(m):
                if mp[q][p]==1:
                    stk.append((q, p))
                    makezero()
                    cnt+=1
                    break
    print(cnt)
```
