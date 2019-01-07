---
layout: post
title: 프로그래머스 - H-Index
tags:
- Algorithm
- C++
- Programmers
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42747#">H-Index</a> 문제를 해결했다.

프로그래머스는 문제 설명을 참 그지같이 한다. <a href="https://en.wikipedia.org/wiki/H-index">H-Index</a>의 관한 내용과 테스트케이스에 관한 설명은 <a href="https://blog.naver.com/promarketyj/221434899288">블로그</a>를 참조해서 해결했다. H-Index의 관한 설명에 나와있는 그래프와 함께보면 쉽게 이해할수있다. 

<pre><code class="cpp">
#include &lt;vector&gt;
#include &lt;algorithm&gt;
using namespace std;

int solution(vector&lt;int&gt; citations) {
    int answer = 0;
    int temp = 0;
    sort(citations.begin(), citations.end());
    for (int i = citations.size() - 1; i >= 0; i--) {
        if (citations[i] <= temp) 
            break;
        temp++;
    }
    answer = temp;
    return answer;
}
 </code></pre>
