---
layout: post
title: 블로그에 코드올리기- highlight.js
tags:
- Blog
- highlight.js
---

블로그에 코드를 올릴 때 테그가 말을 안들어서 highlight.js를 직접 적용시켰다. html테그도 `< >`을 사용해서 C++코드를 올릴때 정말 말을 안들었다고 한다...

우선 <a href="https://highlightjs.org/">highlight.js</a> 에서 다운로드 버튼을 눌러서 원하는 언어를 선택한 후 다운로드를 해준다.

다운로드 된 파일에서 `highlight.pack.js`  파일과 `styles` 폴더에 있는 css파일 중 본인이 원하는 코드 하이라이트 스타일을 선택해서 이 두 파일을 깃헙 블로그에 업로드 해준다.

현재 블로그에는 `atom-one-light.css` 스타일이 적용되어있다. 어떻게 표시되는지는 아래를 참고하자!

<pre><code class="cpp">
#include&lt;iostream&gt;
using namespace std;
int main() {
	cout &lt;&lt; &quot;hello world&quot; &lt;&lt; endl;
}
</code></pre>

이제 적용시키기 위해서 `_includes\head.html` 파일을 수정하러 가야한다.

자신의 경로에 따라서 경로부분만 유의해서 다음과 같은 내용을 추가해주면된다.

<pre><code class="html">
  &lt;link rel=&quot;stylesheet&quot; href=&quot;{{ site.baseurl }}/public/css/atom-one-light.css&quot;&gt;

  &lt;!-- js --&gt;
  &lt;script src=&quot;{{ site.baseurl }}/public/highlight.pack.js&quot;&gt;&lt;/script&gt; 
  &lt;script&gt;hljs.initHighlightingOnLoad();&lt;/script&gt;
</code></pre>

이제 끝이다. 사용하는 방법은 게시글에서 `<pre><code class="클래스 이름">...</code></pre>` 을 넣어주면 된다.

C++일 경우는 저 클래스 이름 부분에 cpp를 넣어주면 된다.

C++의 저 `< >` 문제를 해결하는 방법은 꺽쇠를 `&lt`, `&gt` 로 친절하게 바꿔주는 <a href="http://www.elliotswan.com/postable/">postable</a> 사이트를 이용하면 편하다.

단점은 `+`가 삭제되기 때문에 유의해야 한다...

