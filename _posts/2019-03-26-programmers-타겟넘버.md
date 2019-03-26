---
layout: post
title: 프로그래머스 - 타켓넘버
tags:

- Algorithm
- C++
- Programmers
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/43165">타겟넘버</a> 문제를 해결했다.

`q` 에 나올 수 있는 경우의 수를 저장하였다. `queue` 에 저장된 작업들을 탐색하고 수를 더하거나 빼서 값을 저장하였다. `BFS` 탐색으로 문제를 해결하였다.

```c++
#include <string>
#include <vector>
#include <queue>

using namespace std;

int solution(vector<int> numbers, int target) {
    int answer = 0;
    queue<int> q;
    q.push(numbers[0]);
    q.push(numbers[0]*-1);
    for(int i=1;i<numbers.size();i++){
        int num = q.size();
        for(int j=0;j<num;j++){
            int a = q.front();
            q.push(a-numbers[i]);
            q.push(a+numbers[i]);
            q.pop();
        }
    }

    while(!q.empty()){
        if(q.front()==target)
            answer++;
        q.pop();
    }
    return answer;
}
```

