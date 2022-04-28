---
title: 백준_9375_패션왕 신해빈
categories: [Algorithm,Daily]
tags: [bakejoon] #lowercase    
---

```C++

#include <bits/stdc++.h>
using namespace std;
int t, n;
string a, b;

int main(){
    cin >> t;

    while(t--){
        map<string, int> _map;
        cin >> n;

        for(int i = 0; i < n; i++){
            cin >> a >> b;
            _map[b]++; // 왜 그냥 넣어주면 되는건지

        }

        cin.clear();
        
        // 이 밑으로 다 이해 안됨
        long long ret = 1; 
        for(auto c : _map){
            ret *= ((long long)c.second + 1);
        }
        ret--;
        cout << ret << "\n";
    }
    return 0;
}


```


