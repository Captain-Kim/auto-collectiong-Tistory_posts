<h2 data-ke-size="size26">파일 기반 라우팅</h2>
<p data-ke-size="size16">넥스트는 파일 시스템 기반 라우터 방식을 채택한다. 이 말은 폴더를 만들면 그 폴더 이름으로 URL 세그먼트가 만들어지고, 폴더 안에 폴더 안에 폴더를 만들면 /폴더/폴더/폴더/page.tsx 처럼 중첩 라우팅도 가능하다는 이야기다.</p>
<p data-ke-size="size16">리액트에서 라우트 파일을 별도로 만들어서 일일이 설정해줬던 것에 비하면 굉장히 직관적이고 간편하다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1600" data-origin-height="594"><span data-url="https://blog.kakaocdn.net/dn/wNzZ7/btsIpyG5u1q/bMg7opwPl49azf2ZQxdH8k/img.png" data-phocus="https://blog.kakaocdn.net/dn/wNzZ7/btsIpyG5u1q/bMg7opwPl49azf2ZQxdH8k/img.png"><img src="https://blog.kakaocdn.net/dn/wNzZ7/btsIpyG5u1q/bMg7opwPl49azf2ZQxdH8k/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FwNzZ7%2FbtsIpyG5u1q%2FbMg7opwPl49azf2ZQxdH8k%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1600" data-origin-height="594"/></span></figure>
</p>
<p data-ke-size="size16">마지막 경로(leaf)에 있는 폴더 안에 page.tsx를 만들면 그 경로의 최종적인 페이지를 렌더링 할 수 있음.</p>
<p data-ke-size="size16">물론 nated route(중첩 경로)이더라도 중간에서도 페이지를 만들 수도 있음.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">예를 들어 app/detail/[id] 라는 라우트가 있을 때 detail 폴더에도 page.tsx 하나, [id] 폴더에도 page.tsx 하나 만들면 디테일 페이지의 전체적인 페이지도 만들 수 있고, 거기서 id를 파라미터로 받는 페이지도 [id] 폴더 안에 만들 수 있음.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">아래 그림이 그 예시임.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1600" data-origin-height="687"><span data-url="https://blog.kakaocdn.net/dn/0I5Ff/btsIpstnCcw/vuVb57QlkWDqJLWSdTz9l0/img.png" data-phocus="https://blog.kakaocdn.net/dn/0I5Ff/btsIpstnCcw/vuVb57QlkWDqJLWSdTz9l0/img.png"><img src="https://blog.kakaocdn.net/dn/0I5Ff/btsIpstnCcw/vuVb57QlkWDqJLWSdTz9l0/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F0I5Ff%2FbtsIpstnCcw%2FvuVb57QlkWDqJLWSdTz9l0%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1600" data-origin-height="687"/></span></figure>
</p>
<h2 data-ke-size="size26">page.tsx 만들기</h2>
<p data-ke-size="size16">리액트 함수형 컴포넌트 만들듯이 똑같이 만들면 됨.</p>
<pre id="code_1720181252504" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// `app/page.tsx` is the UI for the `/` URL
export default function Page() {
  return &lt;h1&gt;Hello, Home page!&lt;/h1&gt;
}</code></pre>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1600" data-origin-height="444"><span data-url="https://blog.kakaocdn.net/dn/cFX74E/btsIo65ftZU/k3oiRZd0kUHNgPUNJPEkF1/img.png" data-phocus="https://blog.kakaocdn.net/dn/cFX74E/btsIo65ftZU/k3oiRZd0kUHNgPUNJPEkF1/img.png"><img src="https://blog.kakaocdn.net/dn/cFX74E/btsIo65ftZU/k3oiRZd0kUHNgPUNJPEkF1/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcFX74E%2FbtsIo65ftZU%2Fk3oiRZd0kUHNgPUNJPEkF1%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1600" data-origin-height="444"/></span></figure>
</p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>.js .jsx. tsx 파일을 사용할 수 있음.</li>
<li>페이지는 leaf 파일에 작성함.</li>
<li>페이지를 만들 때 코드로 아무런 설정을 하지 않으면 서버 컴포넌트로 동작함.</li>
<li>하지만 "use client" 라는 키워드를 최상단에 작성하면 클라이언트 컴포넌트로 작성할 수 있음.</li>
</ul>