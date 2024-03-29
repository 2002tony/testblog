---
title: '[Algorithm] Bronze 1-1. 시간복잡도(Time Complexity)'
date: 2021-11-22 22:30
category: 'Algorithm'
draft: false
---

[공부 자료](https://usaco.guide/bronze/time-comp?lang=cpp)

## 1. 시간 복잡도의 필요성

대부분의 프로그래밍 문제에서는 문제의 채점 제한 시간이 주어집니다. 컴퓨터의 연산 속도는 한정적이기 때문에, 주어진 시간 내에 문제를 해결하기 위해서는 컴퓨터가 몇 번의 연산까지 수행할 수 있는지를 생각하며 문제를 풀어야 합니다. 대부분의 채점 서버에서는 초당 10^8 번까지의 연산을 수행할 수 있습니다.이를 토대로, 주어진 입력값에 대한 최대 연산 회수가 제한 시간 내에 시행될 수 있는지를 염두에 두고 알고리즘을 선택하고 구성하여야 합니다.

## 2. 시간 복잡도

시간 복잡도를 나타내기 위해서는 Big-O Notation 을 사용합니다. Big-O Notation은 주어진 변수 n 에 대하여 n에 대한 함수의 형태로 최악의 경우 몇 번의 연산이 필요한지를 나타냅니다. 아래의 여러 예시를 살펴보며 이해해봅시다.

다음과 같은 코드는 한 번의 연산으로, O(1) 으로 표현되는 연산들입니다.

```cpp
int a=3;
int b=7;
int c=a+b;
```

다음과 같은 반복문은 n번 반복되기 때문에 O(n) 으로 표현되는 연산들입니다.

```cpp
for (int i = 0; i < n; i++) {
	//단순 연산 (O(1))
}
```

```cpp
int i=0;
while(i<n){
	//단순 연산 (O(1))
    i++;
}
```

Big O notation을 통해 차수가 더 낮은 항들과 계수는 무시하기 때문에, 다음과 같은 예시들도 모두 O(n) 으로 표현되는 연산들입니다.

```cpp
for (int i = 0; i < 5 * n + 23; i++) {
	//단순 연산 (O(1))
}
```

```cpp
for (int i = 0; i < n + 1557; i++) {
	//단순 연산 (O(1))
}
```

다음과 같은 중첩 반복문은 두 반복문의 실행 회수를 곱하여 O(nm) 으로 표현되는 연산입니다.

```cpp
for(int i=0; i<n; i++){
	for(int j=0; j<m; j++){
		//단순 연산 (O(1))
    }
}
```

따라서, 다음과 같이 안쪽 반복문과 바깥쪽 반복문의 실행 회수가 같으면 O(n^2) 으로 표현됩니다.

```cpp
for(int i=0; i<n; i++){
	for(int j=0; j<n; j++){
		//단순 연산 (O(1))
    }
}
```

여러 개의 반복문이 나타날 경우, 시간 복잡도는 그중 가장 많은 연산을 필요로 하는 반복문을 기준으로 합니다. 따라서, 다음과 같은 코드도 O(n^2) 으로 표현됩니다.

```cpp
for(int i=0; i<n; i++){
	for(int j=0; j<n; j++){
		//단순 연산 (O(1))
    }
}

for (int i = 0; i < n + 1557; i++) {
	//단순 연산 (O(1))
}
```

다음과 같이 여러 반복문이 나타나지만 두 반복문이 서로 다른 변수에 비례할 경우, 두 반복문의 연산 회수를 더해 시간복잡도를 나타냅니다. 예를 들어, 다음과 같은 코드는 O(n^2+m) 으로 표현됩니다.

```cpp
for(int i=0; i<n; i++){
	for(int j=0; j<n; j++){
		//단순 연산 (O(1))
    }
}

for (int i = 0; i < m; i++) {
	//단순 연산 (O(1))
}
```
