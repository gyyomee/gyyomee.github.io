---
layout: post
title: 프로그래머스 - 탑
tags:
- Algorithm
- C++
- Programmers
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42588">탑</a> 문제를 해결했다.

송신의 방향은 왼쪽으로 진행되며 동시에 신호를 보낸다. 자신보다 높은 송신탑만 자신의 신호를 수신할 수 있다. 왼쪽 중 자기보다 높은 탑 중 자기와 가장 가까운 탑을 찾으면 된다. 
`answer`에는 자신의 신호를 수신한 탑의 순번?을 저장하면 된다. `idx+1`

간단하게 해결할 수 있었다.

* 가장 왼쪽의 탑은 신호가 도달할 수 없으므로 0을 처음에 넣어준다.
* 반복문을 자신보다 가까운 탑부터 검사하도록 하였다.
* `flag`로 수신한 탑이 존재하는지 여부를 검사하였다. 0이면 존재하지 않을경우 1이면 존재한다.


<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;

using namespace std;

vector&lt;int&gt; solution(vector&lt;int&gt; heights) {
    vector&lt;int&gt; answer;
    answer.push_back(0);
    for(int i=1;i<heights.size();i++){
        int flag = 0;
        for(int j=i-1;j>=0;j--){
            if(heights[j]>heights[i]){
                answer.push_back(j+1);
                flag = 1;
                break;
            }
        }
        if(flag == 0)
            answer.push_back(0);
    }
    return answer;
}
</code></pre>

