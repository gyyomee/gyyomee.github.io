---
layout: post
title: SW Expert Academy - 6692.다솔이의 월급상자
tags:
- Algorithm
- C++
- SW Expert Academy
---

SW Expert Academy에서 <a href="https://www.swexpertacademy.com/main/code/problem/problemDetail.do?contestProbId=AWdXofhKFkADFAWn&categoryId=AWdXofhKFkADFAWn&categoryType=CODE">6692. 다솔이의 월급 상자</a> 문제를 해결했다.

구하는건 단순 계산이었는데 소수점을 6자리까지 표시해야 하였다. <a href="http://pmoncode.tistory.com/20">C++의 소숫점 자리표시</a>방법을 알아보았다.

<pre><code class="cpp">
#include&lt;iostream&gt;

using namespace std;

int main(int argc, char** argv){
    int T, N, x;
    double p;
    cin >> T;
    for (int test_case = 1; test_case <= T; ++test_case){
        cin >> N;
        double answer = 0;
        for (int i = 0; i < N; i++) {
            cin >> p >> x;
            answer += p * x;
        }
        //소수점 6자리까지 표현
        cout << fixed;
        cout.precision(6);
        cout << "#" << test_case << " " << answer << endl;
    }
    return 0;
}
 </code></pre>
