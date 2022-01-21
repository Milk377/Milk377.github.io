---
title: Visual Studio, Vector []
categories: [Error,VisualStudio]
tags: [error] #lowercase    
---


<img src="https://user-images.githubusercontent.com/37606666/150254410-c290dc81-5e9e-46b3-834e-b9670bd23901.png">

# 원인 
- 벡터1이 할당되지 않은 벡터2와 스왑하여 범위 초과 오류가 발생함.
- 1566 line 일 경우 벡터의 범위 오류가 난것임.

# 코드

```C++
#include <iostream>
#include <vector>

using namespace std;

int main() {
	
	vector<int> v1;
	v1.push_back(1000);
	v1.push_back(2000);
	v1.push_back(3000);

    // 여기서 실수로 v1을 v2로 고치지않음. 그로 인해 에러 발생. 
    // v2로 수정후 해결
	vector<int> v2;
	v1.push_back(1);
	v1.push_back(2);
	v1.push_back(3);

	for (vector<int>::size_type i = 0; i < v1.size(); ++i)
	{
		cout << "V1 is : " << v1[i] << " , V2 is" << v2[i] << endl;
	}
	cout << endl;

	v1.swap(v2);

	cout << " SWAP " << endl;
	cout << endl;

	for (vector<int>::size_type i = 0; i < v1.size(); ++i)
	{
		cout << "V1 is : " << v1[i] << " , V2 is" << v2[i] << endl;
	}
	cout << endl;

	return 0;
}
```
