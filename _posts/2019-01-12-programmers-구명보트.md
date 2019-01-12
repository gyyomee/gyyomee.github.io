---
layout: post
title: 프로그래머스 - 구명보트
tags:
- Algorithm
- C++
- Programmers
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42885?language=cpp">구명보트</a> 문제를 해결했다.

효율성을 개선하는게 어려웠다.. 처음엔 `vector` 에 `erase`를 사용해서 하였는데 시간초과가 나서 조건문과 0을 넣어서 처리를 하였는데 이것도 시간초과가 났다.

최소 몸무게가 40이므로 `limit`에서 40을 뺀 것보다 큰수들은 무조건 혼자만 타야하므로 sort하거나 탐색하는 배열에서 제외시켰다. 제외시킨 나머지는 `people`에 저장하였다.

또, 무조건 전체를 탐색하지 않고 인덱스를 이용해서 처리를 하는 방법이 있어서 이를 이용하였다. 그랬더니 통과할 수 있었다.

뒤에서 부터 탐색하는 `i`와 맨앞의 인덱스인 `j`와 비교해서 클 경우는 혼자 태우고 태울수 있을경우는 둘다 태운다음에 `j`를 더해준다. 이 과정을 `i`와 `j`가 만날때까지 반복한다.

<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;
#include &lt;algorithm&gt;

using namespace std;

int solution(vector&lt;int&gt; peoples, int limit) {
    int answer = 0;
    vector&lt;int&gt; people;
    
    for(int i=0;i<peoples.size();i++){
        if(peoples[i]<=limit-40){
            people.push_back(peoples[i]);
        }
    }
    answer+= peoples.size() - people.size();
    sort(people.begin(),people.end());
    int j=0;
    for(int i=people.size()-1;i>=0;i--){
        if(i == j){
            answer++;
            break;
        }
        else if(j>i)
            break;
        if(people[i]+people[j]<=limit){
            j++;
            answer++;
        } 
        else{
            answer++;
        }
    }
    return answer;
}
 </code></pre>
