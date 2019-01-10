---
layout: post
title: 프로그래머스 - 체육복
tags:
- Algorithm
- C++
- Programmers
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42862">체육복</a> 문제를 해결했다.

체육복 문제에서 주의해야 할 점
* 학생은 모두 체육복을 한개를 가지고 있다.
* `reserve`배열에 있는 여벌 옷을 가지고 있는 학생은 한개를 더 가지고있다.
* `lost`배열에 있는 체육복을 잃어버린 학생은 한개를 잃어버린다.
* 따라서 `reserve`와 `lost` 배열모두에 들어있게 되면 자신이 입을 수 있는 한개의 체육복만 가지게 된다.

* `vector<int> v`에 각 학생에 체육복을 몇개 가지고 있는지 저장하여 이를 이용하여 `answer`을 계산하였다.


<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;
#include &lt;iostream&gt;

using namespace std;

//v안에 n이 있는지 찾아주는 함수
bool find(vector&lt;int&gt; v, int n) {
    for (int i = 0; i < v.size(); i++) {
        if (v[i] == n)
            return true;
    }
    return false;
}

int solution(int n, vector&lt;int&gt; lost, vector&lt;int&gt; reserve) {
    int answer = 0;
    vector&lt;int&gt; v;

    for (int i = 0; i < n; i++) {
        int temp = 1;
        if (find(lost, i + 1))
            temp--;
        if (find(reserve, i + 1))
            temp++;
        v.push_back(temp);
    }

    for (int i = 0; i < n; i++) {
        //체육복이 없는경우
        if (v[i] == 0) {
            //이전학생이 여벌옷이 있는경우
            if (i != 0 && v[i - 1] == 2) {
                answer++;
                v[i - 1]--;
            }
            //다음학생이 여벌옷이 있는경우
            else if (i != 4 && v[i + 1] == 2) {
                answer++;
                v[i + 1]--;
            }
        }
        else answer++;
    }
    return answer;
}
 </code></pre>
