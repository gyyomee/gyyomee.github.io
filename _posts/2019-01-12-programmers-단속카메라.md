---
layout: post
title: 프로그래머스 - 단속카메라
tags:
- Algorithm
- C++
- Programmers
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42884#">단속카메라</a> 문제를 해결했다.

* `routes`를 정렬한 후 차례대로 읽는다. 
* `end`에 차량 전출값의 최소값을 저장한다. 
* 만약 `end`보다 큰 위치에서 진입하는 차량이 생길경우 `answer`을 더한 후 `end`를 최대값으로 초기화 해준 후 반복한다. 

<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;
#include &lt;algorithm&gt;

using namespace std;

int solution(vector&lt;vector&lt;int&gt;&gt; routes) {
    int answer = 1;
    sort(routes.begin(), routes.end());
    int end = 30000;
    for (int i = 0; i < routes.size(); i++) {
        if (end < routes[i][0]) {
            answer++;
            cout << end << endl;
            end = 30000;
        }
        if (end >= routes[i][1])
            end = routes[i][1];
    }
    return answer;
}
</code></pre>
