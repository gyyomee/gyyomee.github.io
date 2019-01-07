---
layout: post
title: 프로그래머스 - K번째수
tags:
- Algorithm
- C++
- Programmers
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42748">K번쨰수</a> 문제를 해결했다.

* 주어진 값을 idx로 잘 활용해서 잘 이용하면 쉽게 구한다. 
* `temp`벡터에 범위값을 저장해서 정렬한 후 `answer`에 해당값을 넣어주었다.


<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;
#include &lt;algorithm&gt;

using namespace std;

vector&lt;int&gt; solution(vector&lt;int&gt; array, vector&lt;vector&lt;int&gt;&gt; commands) {
    vector&lt;int&gt; answer;
    for(int i=0;i&lt;commands.size();i++){
        vector&lt;int&gt; temp;
        for(int j=commands[i][0]-1;j&lt;commands[i][1];j++)
            temp.push_back(array[j]);
        sort(temp.begin(), temp.end());
        answer.push_back(temp[commands[i][2]-1]);
    }
    return answer;
}
 </code></pre>
