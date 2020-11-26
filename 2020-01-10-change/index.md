# [프로그래머스]거스름돈

[https://programmers.co.kr](https://programmers.co.kr)

# 문제:

Finn은 편의점에서 야간 아르바이트를 하고 있습니다. 야간에 손님이 너무 없어 심심한 Finn은 손님들께 거스름돈을 n 원을 줄 때 방법의 경우의 수를 구하기로 하였습니다.



예를 들어서 손님께 5원을 거슬러 줘야 하고 1원, 2원, 5원이 있다면 다음과 같이 4가지 방법으로 5원을 거슬러 줄 수 있습니다.



- 1원을 5개 사용해서 거슬러 준다.
- 1원을 3개 사용하고, 2원을 1개 사용해서 거슬러 준다.
- 1원을 1개 사용하고, 2원을 2개 사용해서 거슬러 준다.
- 5원을 1개 사용해서 거슬러 준다.



거슬러 줘야 하는 금액 n과 Finn이 현재 보유하고 있는 돈의 종류 money가 매개변수로 주어질 때, Finn이 n 원을 거슬러 줄 방법의 수를 return 하도록 solution 함수를 완성해 주세요.



# 풀이:

현재 가격 : num

거스름돈 : a

num 에서의 경우의 수 = 원래 num에서의 경우의 수  + num - a 에서의 경우의 수

단, 0원일 때, 경우의 수를 1로 만들어 주는 것을 잊지말자.

[[백준\]2293 동전1](https://jyukki97.github.io/blog/2017-11-23-2293/) 같은 문제이므로 참고하자.



# **코드:**

사용언어 : c++
```c++
#include <string>
#include <vector>

using namespace std;
vector<int> a(100001, 0);
int solution(int n, vector<int> money) {
	a[0] = 1;
	for (int i : money)
		for (int t = i; t <= n; t++)
			a[t] += a[t - i];
    return a[n];
}
```

