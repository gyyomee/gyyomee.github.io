---
layout: post
title: 프로그래머스 - 카펫
tags:
- Algorithm
- C++
- Programmers
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42842">카펫</a> 문제를 해결했다.

`red`의 개수인 직사각형을 찾아서 만약 그 주변을 `brown`으로 둘러쌀 수 있을 경우 값을 반환하였다.

`brown`으로 둘러쌀 수 있는지 없는지의 여부는 `가로 * 2 + 세로 * 2  + 4` 가 `brown`이랑 수가 동일해야 한다. 

정답은 `red`의 가로와 세로에 +2 한 값이 정답이 된다.

<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;

using namespace std;

vector&lt;int&gt; solution(int brown, int red) {
    vector&lt;int&gt; answer;
    int temp;

    for (int i = 1; i <= red; i++) {
        if (red % i == 0) {
            int v = red / i;
            if (v < i)
                break;
            if ((v * 2 + i * 2) + 4 == brown) {
                temp = i;
            }
        }
    }
    answer.push_back((red / temp)+2);
    answer.push_back(temp+2);
    return answer;
}
</code></pre>