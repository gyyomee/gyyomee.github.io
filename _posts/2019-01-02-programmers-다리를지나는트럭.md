---
layout: post
title: 프로그래머스 - 다리를 지나는 트럭
tags:
- Algorithm
- C++
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42583">다리를 지나는 트럭</a> 문제를 해결했다.

어떻게 해결했는지 모르겠다... 계속 오류가 생기다가 변수 증가를 좀 수정하고 이것 저것 손대고 마지막에 다리길이를 더하니 정답이 나왔다. 
마지막 트럭이 나온 후 다리를 지나야 하니까 다리길이를 더하는게 맞지만 맞았다는 출력문에 어벙벙했다. 

* 답인 `answer` 을 시간으로 취급해서 계산했다. 
* `bridge_truck`에 현재 다리에 있는 트럭을 추가했다. 
탐색을 하는 중 제거를 하게 되면 포인터 참조오류가 나서 그냥 다리를 빠져 나올 트럭이 있을경우 `pop`의 값을 증가시켜서 나중에 한꺼번에 제거했다. 
* `total`은 현재 다리위에 있는 총 트럭들의 무게합이다. 

<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;
#include &lt;list&gt;
using namespace std;

int solution(int bridge_length, int weight, vector&lt;int&gt; truck_weights) {
	int answer = 0;
	list&lt;pair&lt;int, int&gt;&gt; bridge_truck;
	int total = 0;

	for (int i = 0; i &lt; truck_weights.size(); i++) {
    //트럭을 못 올릴 경우
		while (total + truck_weights[i] &gt; weight) { 
			answer++;
			list&lt;pair&lt;int, int&gt;&gt;::iterator iter;
			int pop = 0;
			for (iter = bridge_truck.begin(); iter != bridge_truck.end(); iter++) {
				(*iter).first++;
				if ((*iter).first == bridge_length) {
					total -= (*iter).second;
					pop++;
				}
			}
			//따로 전부 삭제
			for (int i = 0; i &lt; pop; i++) {
				bridge_truck.pop_front();
			}
		}
    
		answer++;
		
    list&lt;pair&lt;int, int&gt;&gt;::iterator iter;
		int pop = 0;
		for (iter = bridge_truck.begin(); iter != bridge_truck.end(); iter++) {
			(*iter).first++;
			if ((*iter).first == bridge_length) {
				total -= (*iter).second;
				pop++;
			}
		}
		for (int i = 0; i &lt; pop; i++) {
			bridge_truck.pop_front();
		}

		bridge_truck.push_back(make_pair(1, truck_weights[i]));
		total += truck_weights[i];
	}
	answer += bridge_length;
	return answer;
}
 </code></pre>
