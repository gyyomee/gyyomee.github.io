---
layout: post
title: SW Expert Academy - 건초더미
tags:
- Algorithm
- C++
- SW Expert Academy
---

SW Expert Academy에서 <a href="https://www.swexpertacademy.com/main/code/problem/problemDetail.do?contestProbId=AWXGEbd6cjMDFAUo&categoryId=AWXGEbd6cjMDFAUo&categoryType=CODE">5603. [Professional] 건초더미</a> 문제를 해결했다.

* `s`는 건초더미의 수들을 저장한다.
* `sum`은 건초더미의 수의 총합을 저장한다. 나중에 건초더미의 평군 값을 구하기 위해서 사용한다.
* 탐색해서 평균값보다 작은 경우는 `answer`에 차이를 더한다. 이 차이만 더하게 되면 건초더미 이동의 최소값을 구할 수 있다.

<pre><code class="cpp">
#include&lt;iostream&gt;
#include&lt;vector&gt;
using namespace std;

int main(int argc, char** argv){
    int T;
    cin >> T;

    for (int test_case = 1; test_case <= T; ++test_case){
        int N;
        vector&lt;int&gt; s;
        int sum = 0;
        int answer = 0;
        cin >> N;
        for (int i = 0; i < N; i++) {
            int temp;
            cin >> temp;
            s.push_back(temp);
            sum += temp;
        }
        sum /= s.size();
        for (int i = 0; i < s.size(); i++) {
            if (sum > s[i])
                answer += sum - s[i];
        }
        cout << "#" << test_case << " " << answer << "\n";
    }
    return 0;
}
 </code></pre>
