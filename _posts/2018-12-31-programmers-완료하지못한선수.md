---
layout: post
title: 프로그래머스 - 완료하지 못한 선수
tags:
- Algorithm
- C++
- Programmers
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42576">완료하지 못한 선수</a> 문제를 해결했다.

해시 항목에 포함되어 있어서 해시를 이용해서 짜는 중 코드가 개판이 되어가고 있었다... 그러면서 C++에 <a href="https://blog.naver.com/didwnsah26/220934296072">해시 맵</a>이 있다는 것도 알게되었는데, 아무도 이 해시 맵을 사용해서 해결하지 않았다. 

검색으로 알게된 방법이 효율성이 좋은 것같아 그냥 이를 이용해서 문제를 해결했다. `Java`로는 해시를 써서 해결한 분이 있었다. 코드들을 잘 정리해 놓은 <a href="https://dreamhollic.tistory.com/entry/%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EB%AC%B8%EC%A0%9C-%ED%92%80%EC%9D%B45-%EC%99%84%EC%A3%BC%ED%95%98%EC%A7%80-%EB%AA%BB%ED%95%9C-%EC%84%A0%EC%88%98-JAVA">포스팅</a>이 도움이 되었다. 

`participant`가 `completion` 에 있는 내용보다 한 한목이 더 많고 나머지는 동일 하므로 정렬 한 후 일치하지 않을경우 완주하지 못한 사람이다.


<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;
#include &lt;algorithm&gt;

using namespace std;

string solution(vector&lt;string&gt; participant, vector&lt;string&gt; completion) {
	string answer = "";

	sort(participant.begin(), participant.end());
	sort(completion.begin(), completion.end());

	for (int i = 0; i < participant.size(); i++) {
		if (participant[i] != completion[i]) {
			answer += participant[i];
			break;
		}
	}
	return answer;
}
 </code></pre>
