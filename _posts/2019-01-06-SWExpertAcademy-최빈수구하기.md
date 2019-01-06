---
layout: post
title: SW Expert Academy - 최빈수 구하기
tags:
- Algorithm
- C++
- SW Expert Academy
---

SW Expert Academy에서 <a href="https://www.swexpertacademy.com/main/code/problem/problemDetail.do?contestProbId=AV13zo1KAAACFAYh&categoryId=AV13zo1KAAACFAYh&categoryType=CODE">1204. 최빈수 구하기</a> 문제를 해결했다.

* `vector`에 `pair`을 이용하여 수가 등장한 횟수와 수를 저장한다. 점수는 총 1000개이므로 반복문을 사용하여 입력 받았다.
* `flag`로 기존에 등장했던 수인지 아닌지를 검사하여, 등장하지 않았던 수이면 `v`에 추가한다.
* 마지막에 `sort`로 정렬하여 최대값인 마지막 값을 출력하였다.


<pre><code class="cpp">
#include&lt;iostream&gt;
#include&lt;vector&gt;
#include&lt;algorithm&gt;
using namespace std;

int main() {
    int T;
    cin >> T;
    for (int test_case = 0; test_case < T; test_case++) {
        vector&lt;pair&lt;int,int&gt;&gt; v;
        cin >> test_case;
        test_case--;

        for (int i = 0; i < 1000; i++) {
            int temp;
            cin >> temp;
            
            int flag = 0;
            for (int j = 0; j < v.size(); j++) {
                if (v[j].second == temp) {
                    v[j].first++;
                    flag = 1;
                    break;
                }
            }
            if (flag == 0) {
                v.push_back(make_pair(1, temp));
            }
        }
        sort(v.begin(), v.end());
        cout << "#" << test_case + 1 << " " << v.back().second << "\n";
    }
}
 </code></pre>
