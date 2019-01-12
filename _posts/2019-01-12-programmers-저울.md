---
layout: post
title: 프로그래머스 - 저울
tags:
- Algorithm
- C++
- Programmers
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42886">저울</a> 문제를 해결했다.

기본적으로 생각한 탐욕법으로 해결한 아래 코드는 시간초과가 발생한다.

정렬한 후 큰수부터 차례대로 뺼수있는 큰 수를 계속 해서 빼나간다. 만약 0을 만들지 못하면 만들지 못하는 수이므로 그 수를 반환하였다.

<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;
#include &lt;algorithm&gt;

using namespace std;

int solution(vector&lt;int&gt; weight) {
    int answer = 1;
    sort(weight.begin(), weight.end());
    while (true) {
        int temp = answer;
        for (int i = weight.size()-1; i >=0; i--) {
            if (weight[i] <= temp)
                temp -= weight[i];
            if (temp == 0)
                break;
        }
        if (temp != 0)
            break;
        answer++;
    }
    return answer;
}
</code></pre>

시간초과가 발생해서 어떻게 하면 해결할지 찾아보았다.

<a href="http://oneshottenkill.tistory.com/377">여기</a>에서 해답을 찾아서 시간초과 문제를 해결할 수 있었다.

<pre><code class="cpp">
#include &lt;string&gt; 
#include &lt;vector&gt;
#include &lt;algorithm&gt;

using namespace std;

int solution(vector&lt;int&gt; weight) {
    int answer = 1;
    sort(weight.begin(), weight.end());
    for(int i=0;i&lt;weight.size();i++){
        if(answer&lt;weight[i])
            break;
        answer += weight[i];
    }
    return answer;
}
</code></pre>