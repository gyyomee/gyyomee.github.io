---
layout: post
title: 프로그래머스 - 라면공장
tags:
- Algorithm
- C++
- Programmers
- priority queue
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42629">라면공장</a> 문제를 해결했다.

최소한의 밀가루 공급으로 `k` 일까지 버티는 것이 문제 내용이다. 0일인 오늘을 포함해서 계산해야 한다.(오늘을 1일로 계산했다가 계속 틀렸다...)

최소한의 밀가루 공급이 필요하므로 거능한 `supplies`의 값이 큰 순서대로 사용을 하는것이 유리하므로 우선순위 큐를 사용하였다. 큐에 `pair`로 `supplies`와 `dates`값을 넣었다. 
만약 이 밀가루 공급일까지 현재양으로 사용이 가능하다면 공급을 받고 아닐경우는 `temp`에 넣어둔다. `temp`에 넣은 값은 밀가루를 공급받게 되면 다시 꺼내 `q`에 넣는다.

* 밀가루의 양 `supplies`와 공급일 `dates`를 `pair`로 우선순위큐 `q`에 저장한다.
* 최대값이지만 당장 사용하지 못할 경우 `temp` 에 임시저장해두어 밀가루를 공급받을때 다시 `q`에 저장한다.
* 공급받을때 `answer++` 


<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;
#include &lt;queue&gt;

using namespace std;

int solution(int stock, vector&lt;int&gt; dates, vector&lt;int&gt; supplies, int k) {
	int answer = 0;
	priority_queue&lt;pair&lt;int, int&gt;&gt; q;
	priority_queue&lt;pair&lt;int, int&gt;&gt; temp;
	for (int i = 0; i < supplies.size(); i++) {
		q.push(make_pair(supplies[i], dates[i]));
	}

	while (stock < k) {
		if (stock >= q.top().second) {
			stock += q.top().first;
			q.pop();
			answer++;

			while (!temp.empty()) {
				q.push(temp.top());
				temp.pop();
			}
		}
		else {
			temp.push(q.top());
			q.pop();
		}
	}
	return answer;
}
 </code></pre>
