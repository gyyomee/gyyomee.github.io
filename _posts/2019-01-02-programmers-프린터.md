---
layout: post
title: 프로그래머스 - 프린터
tags:
- Algorithm
- C++
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42587?language=cpp">프린터</a> 문제를 해결했다.

프린터에 있는 모든 우선순위 목록을 탐색해서 우선순위가 높은것이 존재할 경우 목록의 뒤로 보내고, 존재하지 않을 경우는 출력하는 방식으로 진행된다.

앞에선 삭제를 뒤에선 삼입이 필요했기 때문에 `list`를 사용해서 구현하였다. `list<pair<int,int>>` 로 앞에는 priorities를 뒤에는 location을 저장한다.

코딩 중 pop을 제대로 안시켜줘서 런타임에러가 처음에 몇 번 발생했다...


<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;
#include &lt;list&gt;
#include &lt;algorithm&gt;

using namespace std;

int solution(vector&lt;int&gt; priorities, int location) {
	int answer = 0;
	list&lt;pair&lt;int, int&gt;&gt; print;
	for (int i = 0; i &lt; priorities.size(); i  ) {
		print.push_back(make_pair(priorities[i], i));
	}

	while (!print.empty()) {
		int flag = 0;

		list&lt;pair&lt;int, int&gt;&gt;::iterator iter;
		for (iter = print.begin(); iter != print.end();   iter) {
			if ((*iter).first &gt; print.front().first) { //큰값이 존재할 경우
				print.push_back(make_pair(print.front().first, print.front().second));
				print.pop_front();
				flag = 1;
				break;
			}
		}

		//높은문서가 없으면
		if (flag == 0) {
			answer  ;
			if (print.front().second == location)	
				return answer;
			print.pop_front();
		}		
	}

	return answer;
}
</code></pre>

