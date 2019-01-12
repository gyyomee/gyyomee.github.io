---
layout: post
title: 프로그래머스 - 섬 연결하기
tags:
- Algorithm
- C++
- Programmers
- Kruskal 알고리즘
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42861">섬 연결하기</a> 문제를 해결했다.

<a href="https://m.blog.naver.com/PostView.nhn?blogId=ndb796&logNo=221230994142&proxyReferer=https%3A%2F%2Fwww.google.com%2F">Kruskal 알고리즘</a>을 이용해서 문제를 해결할 수 있었다. 

가중치가 작은 순서대로 정렬한 후 위의 알고리즘에 따라 싸이클을 이루지 않는 간선들을 추가하였다.


<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;
#include &lt;algorithm&gt;

using namespace std;

int getParent(vector&lt;int&gt; parent, int x) {
    if (parent[x] == x) return x;
    return parent[x] = getParent(parent, parent[x]);
}

void unionParent(vector&lt;int&gt; &parent, int a, int b) {
    a = getParent(parent, a);
    b = getParent(parent, b);
    if (a < b)parent[b] = a;
    else parent[a] = b;
}

//같은부모를 가리키는지
bool find(vector&lt;int&gt; parent, int a, int b) {
    a = getParent(parent, a);
    b = getParent(parent, b);
    if (a == b) return true;
    else return false;
}

//간선의 가중치를 기준으로 정렬
bool cmp(vector&lt;int&gt; a, vector&lt;int&gt; b) {
    if (a[2] < b[2])
        return true;
    else return false;
}

int solution(int n, vector&lt;vector&lt;int&gt;&gt; costs) {
    int answer = 0;

    sort(costs.begin(), costs.end(), cmp);

    vector&lt;int&gt; parent;
    for (int i = 0; i < n; i++)
        parent.push_back(i);
    
    for(int i=0;i&lt;costs.size();i++){
        if (!find(parent, costs[i][0], costs[i][1])){
            answer += costs[i][2];
            cout << costs[i][2] << endl;
            unionParent(parent, costs[i][0], costs[i][1]);
        }
    }
    return answer;
}
 </code></pre>
