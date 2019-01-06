---
layout: post
title: 프로그래머스 - 이중우선순위큐
tags:
- Algorithm
- C++
- Programmers
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42628">이중우선순위큐</a> 문제를 해결했다.

* `vector`로 값 들을 저장해서 `D 1`이나 `D -1` 연산이 주어질 경우 정렬해서 최댓값을 삭제할 경우 `pop_back`을 최소값을 삭제할경우 `erase(q.begin())`을 수행하여 삭제하도록 하였다.
* 값이 `string` 형식으로 주어졌으므로 `stoi`와 `substr`을 사용하여 값을 `int`로 변환하였다.


<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;가
#include &lt;algorithm&gt;

using namespace std;

vector&lt;int&gt; solution(vector&lt;string&gt; operations) {
    vector&lt;int&gt; answer;
    vector&lt;int&gt; q;
    for(int i=0;i&lt;operations.size();i++){
        if(operations[i].at(0) =='I' ){
            q.push_back(stoi(operations[i].substr(2, operations[i].length()-2)));
        }
        else if(operations[i] =="D 1"){
            if(q.size()==0)
                continue;
            sort(q.begin(), q.end());
            q.pop_back();
        }
        else if(operations[i] =="D -1"){
            if(q.size()==0)
                continue;
            sort(q.begin(), q.end());
            q.erase(q.begin());
        }
    }

    //q가 비어있지 않다면
    if(q.size()!=0){
        sort(q.begin(), q.end());
        answer.push_back(q[q.size()-1]);
        answer.push_back(q[0]);
    }
    else{
        answer.push_back(0);
        answer.push_back(0);
    }
    return answer;
}
 </code></pre>
