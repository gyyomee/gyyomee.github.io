---
layout: post
title: 프로그래머스 - 더 맵게
tags:
- Algorithm
- C++
- Programmers
- priority queue
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42626#">더 맵게</a> 문제를 해결했다.

우선순위 큐로 해결하기에 적합한 문제였기에 <a href="https://blog.naver.com/metalingus58/221388200725">우선순위 큐</a>를 사용해보았다. 우선순위 큐는 pop되는 순서에 최대값이나 최소값 부터 나오게된다. 
C++의 경우는 최대값 부터 나오게된다.  

* 이 문제의 경우 최소값 두개를 이용하여 계산한 다음 `K` 를 넘는것이 목적이므로 큐에 푸시할때 `-1`을 곱해서 최소값 부터 나오게 하였다.
* 최소값이 K보다 클경우는 더 이상 검사할 필요가 없으므로 `answer` 을 리턴한다. 효율성 테스트를 위해 이  <a href="https://blog.naver.com/gooldare/221377040504">블로그</a>를 참조하였다.
* 마지막으로 남은 값이`K`보다 작을 경우는 만들수 없는 경우이므로 `-1`을 리턴한다.


<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;
#include &lt;queue&gt;

using namespace std;

int solution(vector&lt;int&gt; scoville, int K) {
	int answer = 0;
	priority_queue&lt;int&gt; q;
	for (int i = 0; i < scoville.size(); i++) {
		q.push(scoville[i] * -1);
	}
	while (!q.empty()) {
		if (q.top() > (K * -1)) {
			if (q.size() == 1) {
				return -1;
			}
			answer++;
			int first = q.top();
			q.pop();
			int second = q.top();
			q.pop();
			q.push(first + (second* 2));
		}
		else if (q.top() <= (K * -1))
			return answer;
		else q.pop();
	}
	return answer;
}
 </code></pre>
