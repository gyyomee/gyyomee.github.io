---
layout: post
title: 프로그래머스 - 쇠막대기
tags:
- Algorithm
- C++
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42585">쇠막대기</a> 문제를 해결했다.

초반에 문제를 이해하기 어려웠지만 스텍안에 있는 것만 레이저가 자른다는것을 생각해서 스텍사용해서 어렵지않게 문제를 해결할 수 있었다.

한번에 코딩 성공해서 당황스러웠던...ㅎ

<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;

using namespace std;

int solution(string arrangement) {
	int answer = 0;
	vector&lt;int&gt; stack;
	for (int i = 0; i &lt; arrangement.length(); i++) {
		if (arrangement[i] == &#39;(&#39;) {
			stack.push_back(1); //막대 추가
		}
		else if (arrangement[i] == &#39;)&#39;) {
			if (arrangement[i - 1] == &#39;(&#39;) { //레이저일 경우
				stack.pop_back();
				for (int j = 0; j &lt; stack.size(); j++) {
					stack[j]  ;
				}
			}
			else { //아닐 경우
				int temp = stack.back();
				stack.pop_back();
				answer  = temp;
			}
		}
	}
	return answer;
}
 </code></pre>

