# [프로그래머스]최솟값 만들기

[https://programmers.co.kr](https://programmers.co.kr)

# 문제:

길이가 같은 배열 A, B 두개가 있습니다. 각 배열은 자연수로 이루어져 있습니다. 
 배열 A, B에서 각각 한 개의 숫자를 뽑아 두 수를 곱합니다. 이러한 과정을 배열의 길이만큼 반복하며, 두 수를 곱한 값을 누적하여 더합니다. 이때 최종적으로 누적된 값이 최소가 되도록 만드는 것이 목표입니다. (단, 각 배열에서 k번째 숫자를 뽑았다면 다음에 k번째 숫자는 다시 뽑을 수 없습니다.)



예를 들어 A = `[1, 4, 2]` , B = `[5, 4, 4]` 라면



- A에서 첫번째 숫자인 1, B에서 두번째 숫자인 5를 뽑아 곱하여 더합니다. (누적된 값 : 0 + 5(1x5) = 5)
- A에서 두번째 숫자인 4, B에서 세번째 숫자인 4를 뽑아 곱하여 더합니다. (누적된 값 : 5 + 16(4x4) = 21)
- A에서 세번째 숫자인 2, B에서 첫번째 숫자인 4를 뽑아 곱하여 더합니다. (누적된 값 : 21 + 8(2x4) = 29)



즉, 이 경우가 최소가 되므로 **29**를 return 합니다.



배열 A, B가 주어질 때 최종적으로 누적된 최솟값을 return 하는 solution 함수를 완성해 주세요.



# 풀이:

배열 A와 배열B를 정렬한다.

정렬된 배열 A와 B의 처음값 * 마지막 값을 반복한다.

(합이 최소가 되기 위해서는 A의 최솟값 * B의 최댓값을 해야하기 때문) 

  

# **코드:**
사용언어 : c++
```c++
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int solution(vector<int> A, vector<int> B)
{
	sort(A.begin(), A.end());
	sort(B.begin(), B.end());
	int answer = 0;
	for (int i = 0;i < A.size();i++) {
		answer += A[i] * B[B.size() - i - 1];
	}
    return answer;
}
```

