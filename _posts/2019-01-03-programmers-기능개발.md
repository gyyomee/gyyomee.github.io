---
layout: post
title: 프로그래머스 - 기능개발
tags:
- Algorithm
- C++
- Programmers
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42586">기능개발</a> 문제를 해결했다.

`progresses` 에 작업의 진도가 `speed`에 개발속도가 저장되어있다. 
유의해아 할 점은 완료가 되더라도 앞에 작업이 완료되지 않았을 경우 배포가 되지 않는다는 점이었다. 

* 완료된 작업 수를 `total`에 저장하였다. while문을 사용해 `total`과 작업 개수가 일치하지 않을 동안 까지만 반복하게 설정하였다. 
* `subTotal`에 배포가 가능한 날에 몇개의 작업이 배포되는지 저장하였다. 
* `progresses`의 값이 100을 처음으로 넘었을 때만 배포를 검사하게 하여 이미 배포된 작업이 또 배포되지 않도록 하였다. 
* 100을 넘었을 경우 이전 작업이 완료되었는지 확인하고, 뒤의 완료가 되어 대기하는 작업이 있는지 검사하였다. 


<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;

using namespace std;

vector&lt;int&gt; solution(vector&lt;int&gt; progresses, vector&lt;int&gt; speeds) {
    vector&lt;int&gt; answer;
    int total =0 ;
    while(total != progresses.size()){
        int subTotal = 0;
        for(int i=0;i<progresses.size();i++){
            //완료되지 않은 작업일 경우
            if(progresses[i]<100) {
                progresses[i] += speeds[i];
                if(progresses[i]>=100){
                    int flag = 0;
                    for(int j=0;j<i;j++){
                        if(progresses[j] < 100){
                            flag = 1;
                        }
                    }
                    if(flag == 0){ //기존작업이 전부 완료되었을 경우
                        subTotal++;
                        for(int j=i+1;j<progresses.size();j++){
                            if(progresses[j]>=100) //대기하는 작업이 존재할 경우
                                subTotal++;
                            else //완료되지 않은 작업이 존재할 경우
                                break;
                        }
                    }
                }
            }
        }
        if(subTotal != 0){
            answer.push_back(subTotal);
            total += subTotal;
        }
    }
    return answer;
}
</code></pre>

