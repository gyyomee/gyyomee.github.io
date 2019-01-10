---
layout: post
title: 프로그래머스 - 조이스틱
tags:
- Algorithm
- C++
- Programmers
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42860">조이스틱</a> 문제를 해결했다.

* 현재 커서위치는 `now`
* `now`에서 왼쪽 이동 최소값, 오른쪽 이동 최소값을 구한다음 적게 이동하는 방향으로 커서이동
* 이동한 위치에서 상 하로 움직이는 횟수를 더한다.

다른사람의 풀이에서 확인한건데 이동횟수는 `길이 - A가아닌 수 - 1` 을 한것과 동일하였다... 대박


<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;

using namespace std;

int solution(string name) {
    int answer = 0;

    //비교할 string 생성
    string make = "";
    for (int i = 0; i < name.length(); i++) {
        make += "A";
    }

    int now = 0;
    while (make != name) {
        int i = 0;
        int temp1 = 0;
        int temp2 = 0;
        int j, k;
        //오른쪽으로 찾는다
        for (k = 0; k < name.length(); k++) {
            int idx = (now + k) % name.length();
            if (make.at(idx) != name.at(idx)) {
                if ((idx - now )< 0) {
                    temp1 = name.length() - now + idx;
                    break;
                }
                else {
                    temp1= idx - now;
                    break;
                }
            }
        }

        //왼쪽으로 찾는다
        for (j = 0; j < name.length(); j++) {
            int idx = (now - j + name.length()) % name.length();
            if (make.at(idx) != name.at(idx)) {
                if ((now - idx) < 0) {
                    temp2 += name.length() - idx + now;
                    break;
                }
                else {
                    temp2 += now - idx;
                    break;
                }
            }
        }

        //비교해서 최소값을 찾는다
        if (temp1 <= temp2) {
            i = (now + k) % name.length();
            answer += temp1;
        }
        else {
            i = (now - j + name.length()) % name.length();
            answer += temp2;
        }

        //상하로 움직이는거 더함
        now = i;
        if (name.at(i) - 'A' < 13) {
            answer += name.at(i) - 'A';
            make.at(i) = name.at(i);
        }
        else {
            answer += 'Z' - name.at(i) + 1;
            make.at(i) = name.at(i);
        }
    }
    return answer;
}
 </code></pre>
