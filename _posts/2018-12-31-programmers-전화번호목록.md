---
layout: post
title: 프로그래머스 - 전화번호 목록
tags:
- Algorithm
- C++
- Programmers
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42577">전화번호 목록</a> 문제를 해결했다.

이전 문제 <a href="">완주하지 못한 선수</a> 문제와 유사해서 비슷한 방식으로 해결할 수 있었다. 

정렬한 후 뒤의 string이 앞 string 보다 짧을 경우 `substr`을 이용하여 접두어를 찾았다.


<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;
#include &lt;algorithm&gt;

using namespace std;

bool solution(vector&lt;string&gt; phone_book) {
	bool answer = true;
	sort(phone_book.begin(), phone_book.end());
	for (int i = 0; i < phone_book.size()-1; i++) {
		if (phone_book[i].length() < phone_book[i + 1].length()) {
			if (phone_book[i] == phone_book[i + 1].substr(0, phone_book[i].length())) {
				answer = false;
				break;
			}
		}
	}
	return answer;
}
 </code></pre>
