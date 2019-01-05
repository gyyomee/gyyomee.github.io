---
layout: post
title: 프로그래머스 - 디스크 컨트롤러
tags:
- Algorithm
- C++
- Programmers
- set
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42627#">디스크 컨트롤러</a> 문제를 해결했다.

C++의 `set` 을 사용하여 문제를 해결하였다. `set`은 priority queue와 같은 역할을 한다. `set`의 우선순위는 작은 순서부터이다. 전에는 잘 몰라서 `priority_queue`에 음수를 넣어서 사용했는데 이렇게 사용해야겠다. `set` 에 관한 내용은 <a href="https://modoocode.com/224">블로그</a>를 통해 학습하고 참고하여 사용하였다. 

아무리 컨트롤러 잘 조합해도 답이 안나오고 틀려서 힘들었는데 조건에 하드디스크가 작업을 수행하고 있지 않을 때에는 먼저 요청이 들어온 작업부터 처리한다고 적혀있었다. 그걸 몰라서 이걸 어떻게 처리해야하나 고민했던 내가 멍청했다...

코드는 <a href = "https://blog.naver.com/gooldare/221396855619">여기</a>에서 참조했다. 깜박한 조건도 찾을 수 있었고 문제 해결할 수 있었다. 난 이 이문제가 정말 싫다...

* `jobs`를 정렬해서 먼저 실행되는 순서로 정렬하였다. 
* `q`에 현재 대기중인 job을 삼입한다. 
* 대기중인 작업이 존재할경우 가장 빠른시간 내에 끝낼수있는 작업을 실행하고. 실행한후 `jobs`에서 삭제한다. 
* 존재하지 않을경우 가장빠르게 시작되는 작업을 실행하고 실행한후 `jobs`에서 삭제한다. 

<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;
#include &lt;set&gt;
#include &lt;algorithm&gt;

using namespace std;

int solution(vector&lt;vector&lt;int&gt;&gt; jobs) {
	set&lt;pair&lt;int, int&gt;&gt; q;
	int answer = 0;
	sort(jobs.begin(), jobs.end());
	int time = 0;
	int size = jobs.size();

	while (!jobs.empty()) {
		for (int i = 0; i < jobs.size(); ++i) {
			if (jobs[i][0] <= time)
				q.insert(make_pair(jobs[i][1], i));
		}

		if (q.empty()) {
			time = jobs[0][0] + jobs[0][1];
			answer += jobs[0][1];
			jobs.erase(jobs.begin());
			continue;
		}

		auto var = q.begin();
		time += var->first;
		answer += time - jobs[var->second][0];
		jobs.erase(jobs.begin() + var->second);
		q.clear();
	}
	answer /= size;
	return answer;
}

 </code></pre>
