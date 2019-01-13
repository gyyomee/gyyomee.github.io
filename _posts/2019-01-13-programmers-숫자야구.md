---
layout: post
title: 프로그래머스 - 숫자야구
tags:
- Algorithm
- C++
- Programmers
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42841">숫자야구</a> 문제를 해결했다.

어떻게 하면 해결할 수 있을지 고민을 해보다가 어떻게 해야할지 감이 안잡혀서 풀이를 검색해보았다.

<a href="https://lkhlkh23.tistory.com/71">블로그</a>에서 모든 세자리수를 검사하는 방법을 알아서, 정말 완전탐색으로 해야되겠구나 싶어서 했다.

* 수에는 0이 포함되지 않는다. 수에는 중복되는 숫자가 존재하지 않는다. -> 이 조건에 제외되는 숫자는 제외한다.
* 숫자를 `baseball`에 있는 숫자 모두와 비교해서 `strike`와 `ball`숫자가 일치하면 이 수는 가능한 답이다.
* `flag`를 사용해서 조건에 부합하는지 아닌지 검사한다.

<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;
#include &lt;iostream&gt;

using namespace std;

int solution(vector&lt;vector&lt;int&gt;&gt; baseball) {
    int answer = 0;

    for (int i = 123; i <= 999; i++) {
        string s1 = to_string(i);
        int flag = 0;

        int flag2 = 0;
        for (int j = 0; j < 3; j++) {
            //수에 0이 존재하면안됨
            if (s1.at(j) == '0') {
                flag2 = 1;
                break;
            }
            //수에 중복되는수가 들어가면안됨
            for (int k = 0; k < 3; k++) {
                if (j == k)
                    continue;
                if (s1.at(j) == s1.at(k)) {
                    flag2 = 1;
                    break;
                }
            }
        }

        //수에 중복된 수가 있거나 0이 포함되었을 경우 제외
        if (flag2 == 1)
            continue;

        for (int j = 0; j < baseball.size(); j++) {
            int ball = 0;
            int strike = 0;
            string s2 = to_string(baseball[j][0]);

            for (int k = 0; k < 3; k++) {
                    for (int z = 0; z < 3; z++) {
                        //겹치는 수가 있을때
                        if (s1.at(k) == s2.at(z)) {
                            //같은 자리면 스트라이크
                            if (k == z)
                                strike++;
                            //다른 자리면 볼
                            else
                                ball++;
                        }
                    }
                
            }

            //스트라이크나 볼의 개수가 다르면 종료
            if (ball != baseball[j][2] || strike != baseball[j][1]) {
                flag = 1;
                break;
            }
        }

        if (flag == 0) {
            answer++;
        }
    }
    return answer;
}
</code></pre>