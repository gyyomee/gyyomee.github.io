---
layout: post
title: 프로그래머스 - 소수찾기
tags:
- Algorithm
- C++
- Programmers
---

프로그래머스에서 <a href="https://programmers.co.kr/learn/courses/30/lessons/42839">소수찾기</a> 문제를 해결했다.

* `numbers` 에있는 모든 경우의 수를 만든 후 `set<int> s` 에 저장한다. 만드는 동안은 `vector<int> v`에 저장한 다음 마지막으로 `s`에 저장.
* 숫자의 개수들을 `int a[10]`에 저장해서 숫자수를 비교해서 숫자가 중복되어 사용될 경우는 경우의 수에 추가하지 않는다. 
* 소수인지 판정할때 맨 앞자리가 `0`이면 안되므로 이를 제외한다. 

C++에서의 `next_permutation`을 사용해서 순열을 구해서 깔끔한 코드로 계산한 사람들의 코드를 봤다. 나중에 시간이 나면 사용방법을 알고 나중에 코드를 고쳐야겠다.

너무 경우의 수도 많고 그냥 이것저것 하다 보니까 멘탈이 나가서 다시 코드 못보겠다... 이걸 왜 풀어야하는지 모르겠다.

소수 좀 그만 찾고 싶다.

<pre><code class="cpp">
#include &lt;string&gt;
#include &lt;vector&gt;
#include &lt;set&gt;

using namespace std;

bool prime(int number){
    if(number==1) return false;
    if(number%2==0){
        if(number==2) return true;
        return false;
    }
    for(int i=3;i&lt;number/2;i++){
        if(number%i==0) return false;
    }
    return true;
}

int solution(string numbers) {
    int answer = 0;
    int a[10] ={ 0 };
    for(int i=0;i&lt;numbers.length();i++){
        a[numbers.at(i)-'0']++;
    }
    //중복방지 위해 set사용
    set &lt;string&gt; s;
    vector &lt;string&gt; v;
    for(int k=0;k&lt;numbers.length();k++){   
        for(int i=0;i&lt;numbers.length();i++){
        if(s.empty()){
            string temp = "";
            temp+=numbers.at(i);
            v.push_back(temp);
        }
        for(auto itr= s.begin();itr!=s.end();++itr){
            string temp = *itr;
            int a2[10] = {0};
            int flag =0;
            a2[numbers.at(i)-'0']++;
            for(int z=0;z<(*itr).length();z++){
                if((*itr).at(z)==numbers.at(i)){
                    a2[numbers.at(i)-'0']++;
                    if(a2[numbers.at(i)-'0']>a[numbers.at(i)-'0']){
                        flag =1;
                        break;
                    }
                }
            }
            if(flag ==1){
                continue;
            }
            v.push_back(numbers.at(i)+temp);
            v.push_back(temp+numbers.at(i));
        }
        } 
        s.clear();
        for(int j=0;j&lt;v.size();j++)
            s.insert(v[j]);
        v.clear();
        
        //find prime
        for(auto itr= s.begin();itr!=s.end();++itr){
            if((*itr).at(0)=='0')
                continue;
            if(prime(stoi(*itr))){
                answer++;
            }
        }
    }
    
    return answer;
}
 </code></pre>
