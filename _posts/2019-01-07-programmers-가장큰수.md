---
layout: post
title: 프로그래머스 - 가장큰수
tags:
- Algorithm
- C++
- Programmers
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42746#">가장큰수</a> 문제를 해결했다.

저번에 코딩테스트에서 못 해결했던 문제였다. 처음엔 string 배열을 일반정렬로 정리하였더니 30을 3보다 더 크게 취급하여서 엉뚱한 값이 나오는 뭐 그런 일이 생겨서 멘붕이 와서 못해결했었다.

이번에도 스스로 해결은 못했다. 해설은 <a href="https://blog.naver.com/teagu_news/221384817840">이 곳</a>을 참고하였다. `sort`에 직접 함수를 만들어 적용시켜서 해결하였다. 알고리즘 정렬함수의 다양한 사용법에 대해서 알게 되는 계기가 되었다.

마지막 테스트케이스가 오류가나서 뭔지봤더니 `[0,0,0]` 이 주어졌을때 `0`을 반환해야한다는 것이였다. 이를 마지막에 예외처리 해주었다.


<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;
#include &lt;algorithm&gt;

using namespace std;

bool compare(const string &a, const string &b){
    if(a+b>b+a) return true;
    else return false;
}

string solution(vector&lt;int&gt; numbers) {
    string answer = &quot;&quot;;
    vector&lt;string&gt; s;
    for(int i=0;i&lt;numbers.size();i++){
        s.push_back(to_string(numbers[i]));
    }
    sort(s.begin(), s.end(), compare);
   	for(int i=0;i&lt;s.size();i++)
        answer+=s[i];
    //answer가 "0000" 같을 경우
    if(answer.at(0) == '0' && answer.at(answer.length()-1)=='0')
        answer = "0";
    return answer;
}
 </code></pre>
