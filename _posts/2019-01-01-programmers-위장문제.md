---
layout: post
title: 프로그래머스 - 위장문제
tags:
- Algorithm
- C++
- Programmers
- map
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42578">위장문제</a> 문제를 해결했다.

C++의 `map` 을 사용하여 문제를 해결하였다. `map` 에 관한 내용은 <a href="https://modoocode.com/224">블로그</a>를 통해 학습하고 참고하여 사용하였다.

처음에 조합의 개수를 이상하게 생각해서 계산을 잘못하였는데 <a href="https://tallman.tistory.com/7">블로그</a>에서 설명된 내용을 보며 조합의 개수를 맞게 구하여 문제를 해결 할 수 있었다.

* `clothes_list` 에 `map`을 이용하여 옷의 종류와 개수를 넣었다. 
* `종류+1` 한 값을 전부 곱한 다음 1을 빼어 결과를 계산하였다. 이에 대한 자세한 내용은 위에 조합 개수에 참고하였다고 한 <a href="https://tallman.tistory.com/7">블로그</a>에 자세히 설명되어 있다.

<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;
#include &lt;map&gt;

using namespace std;

int solution(vector&lt;vector&lt;string&gt;&gt; clothes) {
	int answer = 0;
	map&lt;string, int&gt; clothes_list;
	for (int i = 0; i < clothes.size(); i++) {
		auto itr = clothes_list.find(clothes[i][1]);
		if (itr != clothes_list.end()) {
			//존재할 경우 개수 증가
			itr->second++;
		}
		//존재하지 않을 경우 새로 추가
		else {
			clothes_list.insert(make_pair(clothes[i][1], 1));
		}
	}

	auto itr = clothes_list.begin();
	answer = itr->second + 1;
	itr++;
	for (; itr != clothes_list.end(); itr++) {
		int r = itr->second + 1;
		answer *= r;
	}

	answer--;
	return answer;
}
 </code></pre>
