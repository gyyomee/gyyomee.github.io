---
layout: post
title: 프로그래머스 - 주식가격
tags:
- Algorithm
- C++
- Programmers
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42584">주식가격</a> 문제를 해결했다.

가격을 유지하는 시간 기간이 살짝 이해하기 어려워서 초반에 계산을 잘못하였다. 
간단하게 생각하면 떨어지거나 마지막 시점이 3이고 시작시점이 1이면 3-1해서 유지된 기간은 2이다. 
반복문 시작할때 유지된 기간을 저장한 변수인 `time`을 증가시키고 떨어진 값일 경우 해당 `time`의 값을 `answer`에 넣어주면 되는식으로 코드를 짰다.



<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;

using namespace std;

vector&lt;int&gt; solution(vector&lt;int&gt; prices) {
    vector&lt;int&gt; answer;
    for(int i=0; i< prices.size();i++){
        int time = 0;
        for(int j=i+1;j<prices.size();j++){
            time++;
            if(prices[i] > prices[j]){
                break;
            }
        }
        answer.push_back(time);
    }
    return answer;
}
</code></pre>

