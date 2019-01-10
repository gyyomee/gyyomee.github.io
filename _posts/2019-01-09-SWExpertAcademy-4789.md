---
layout: post
title: [SW Expert Academy] 4789.성공적인 공연 기획
tags:
- Algorithm
- C++
- SW Expert Academy
---

SW Expert Academy에서 <a href="https://www.swexpertacademy.com/main/code/problem/problemDetail.do?contestProbId=AWS2dSgKA8MDFAVT&categoryId=AWS2dSgKA8MDFAVT&categoryType=CODE">4789. 성공적인 공연 기획</a> 문제를 해결했다.

* `num`은 현재 박수를 치고 있는 사람의 수이다.
* `answer`은 고용해야할 사람의 수이다.
* `i`번째 수 에있는 사람들은 `i`이상의 사람들이 박수를 칠때 박수를 친다. `i`가 `num`이상일 경우는 `num`에 `i`번째 사람의 수를 더한다. 
* `i`가 `num`이상이 아닐경우는 `answer`에 부족한 사람의 수를 더한 뒤 `i`번째 사람의 수를 더하여 반복.

<pre><code class="cpp">
#include&lt;iostream&gt;
using namespace std;

int main(int argc, char** argv){
    int T;
    cin >> T;
    for (int test_case = 1; test_case <= T; ++test_case){
        string s;
        int num = 0;
        int answer = 0;
        for (int i = 0; i < s.length(); i++) {
            if (num <= i) {
                num += s.at(i) - '0';
            }
            else {
                answer += i - num;
                num = i + s.at(i) - '0';
            }
        }
        cout << "#" << test_case << " " << answer << endl;
    }
    return 0;
}
 </code></pre>
