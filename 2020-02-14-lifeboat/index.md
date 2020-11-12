# [프로그래머스]구명보트

[https://programmers.co.kr](https://programmers.co.kr)

# 문제:

무인도에 갇힌 사람들을 구명보트를 이용하여 구출하려고 합니다. 구명보트는 작아서 한 번에 최대 **2명**씩 밖에 탈 수 없고, 무게 제한도 있습니다.



예를 들어, 사람들의 몸무게가 [70kg, 50kg, 80kg, 50kg]이고 구명보트의 무게 제한이 100kg이라면 2번째 사람과 4번째 사람은 같이 탈 수 있지만 1번째 사람과 3번째 사람의 무게의 합은 150kg이므로 구명보트의 무게 제한을 초과하여 같이 탈 수 없습니다.



구명보트를 최대한 적게 사용하여 모든 사람을 구출하려고 합니다.



사람들의 몸무게를 담은 배열 people과 구명보트의 무게 제한 limit가 매개변수로 주어질 때, 모든 사람을 구출하기 위해 필요한 구명보트 개수의 최솟값을 return 하도록 solution 함수를 작성해주세요.



# 풀이:

배열 people을 정렬한다.

people에 들어있는 값 중 최댓값 + 최솟값 이 limit 보다 작거나 같다면 최대 최소값을 없애고 보트 갯수를 +1 해준다.

최댓값 + 최솟값 이 limit 보다 크다면 최대값만 없애고 보트 갯수를 +1 해준다.

people에 들어있는 값이 모두 사라질 때까지 반복한다.



# **코드:**

사용언어 : c++
```c++
#include <string>
#include <vector>
#include <algorithm>
using namespace std;

int solution(vector<int> people, int limit) {
	int answer = 0, f = 0, l = people.size() - 1;
	sort(people.begin(), people.end());
	while (f <= l) {
		if (people[f] + people[l] <= limit) {
			f++;
			l--;
		}
		else	l--;
		answer++;
	}
    return answer;
}
```

