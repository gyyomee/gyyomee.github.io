---
layout: post
title: 프로그래머스 - 큰수만들기
tags:
- Algorithm
- C++
- Programmers
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42886">큰수만들기</a> 문제를 해결했다.

처음에 자꾸 테스트케이스 10번이 자꾸 시간초과가 나고 다른사람들도 시간 초과가 나는경우가 많았다...

스트링에서 비교하고 삭제하는 것이 아니라 `vector`에 저장해서 비교하고 삭제하였더니 시간이 줄어들어서 10번을 시간초과 나지 않고 통과할 수 있었다.

* 앞에서부터 비교하여 만약 뒤의 수보다 앞의 수가 작으면 삭제한다.
* 만약 위의 경우가 없을 경우는 가장 작은수를 찾아서 삭제한다.

<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;

using namespace std;

string solution(string number, int k) {
    string answer = "";
    vector&lt;char&gt; num;
    for (int i = 0; i < number.length(); i++)
        num.push_back(number.at(i));

    for (int erase = 0; erase < k; erase++) {
        int flag = 0;
        for (int i = 0; i < num.size() - 1; i++) {
            //앞의수가 작으면 삭제
            if (num[i] < num[i + 1]) {
                num.erase(num.begin() + i);
                flag = 1;
                break;
            }
        }
        //앞의수가 작은경우가 존재하지 않는경우
        if (flag == 0) {
            char min = '9';
            int idx;
            for (int i = 0; i < num.size(); i++) {
                if (num[i] <= min) {
                    min = number.at(i);
                    idx = i;
                }
            }
            //최소값 삭제
            num.erase(num.begin() + idx);
        }
    }
    for (int i = 0; i < num.size(); i++)
        answer += num[i];
    return answer;
}
</code></pre>