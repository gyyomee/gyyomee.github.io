---
layout: post
title: 프로그래머스 - 베스트 앨범
tags:
- Algorithm
- C++
- Programmers
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42579">베스트앨범</a> 문제를 해결했다.

`plays` 값의 범위가 나와있지 않고 값이 정확하지 않아서 가중치를 설정하는게 힘들었다. 
처음에는 마지막 테케만 틀려서 가중치를 고치다보니 결국 정답을 맞출 수 있었다.

* `mGenres` 을 `map`을 이용하여 만들어 장르의 재생수를 저장했다. 
* `temp` 에 가중치를 계산한 `장르 + play수 + idx` 값을 넣었다. `idx` 값은 작을수록 가중치가 커야하므로 `genres.size() - i` 로 계산하였다. 
* 정렬을 한 후 장르마다 최대 두개의 곡만 `answer`에 넣었다.

<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;
#include &lt;map&gt;
#include &lt;algorithm&gt;
using namespace std;

vector&lt;int&gt; solution(vector&lt;string&gt; genres, vector&lt;int&gt; plays) {
	vector&lt;int&gt; answer;
	map&lt;string, int&gt; mGenres;	
	for (int i = 0; i < genres.size(); i++) {
		auto itr = mGenres.find(genres[i]);
		if (itr != mGenres.end()) {
			itr->second += plays[i];
		}
		else {
			mGenres.insert(make_pair(genres[i], plays[i]));
		}
	}

	vector&lt;pair&lt;int, int&gt;&gt; temp;
	for (int i = 0; i < genres.size(); i++) {
		int temp2 = 0;
		auto itr = mGenres.find(genres[i]);
		temp2 += itr->second * 1000;
		temp2 += plays[i] * 2;
		temp2 += genres.size() - i;
		temp.push_back(make_pair(temp2, i));
	}

	sort(temp.begin(), temp.end());

	int num = 1;
	string genre = genres[temp[temp.size() - 1].second];
	answer.push_back(temp[temp.size() - 1].second);

	for (int i = temp.size() - 2; i >= 0; i--) {
		if (genre != genres[temp[i].second]) {
			genre = genres[temp[i].second];
			num = 1;
			answer.push_back(temp[i].second);
		}
		else if (num < 2) {
			answer.push_back(temp[i].second);
			num++;
		}
	}

	return answer;
}
 </code></pre>
