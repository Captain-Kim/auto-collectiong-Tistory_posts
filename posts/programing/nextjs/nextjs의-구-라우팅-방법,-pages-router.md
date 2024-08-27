<h2 data-ke-size="size26">Pages Router란?</h2>
<p data-ke-size="size16">지금 Next.js에 입문하는 사람은 App Router 방식으로 라우팅을 처리하도록 배웠을 것이다. 그게 가장 최신버전의 방식이다.</p>
<p data-ke-size="size16">그러나 넥스트 13 버전 이전까지는 페이지 라우터 방식이 라우트를 만드는 방식이었다. 페이지 라우터 방식은 파일을 기반으로 라우트를 만드는 가장 직관적인 방식이다. 넥스트 13 버전부터 도입된 앱 라우터 방식은 디렉토리 기반으로 라우트를 만든다는 것과 큰 차이가 있다고 보면 된다.</p>
<p data-ke-size="size16">지금은 넥스트 15버전까지 나왔기 때문에 13버전 이전까지 메인으로 사용된 라우팅 방식이라고 설명하면 굉장히 레거시하고 오래된 방식이고 쓰면 안 될 것 같이 보이지만, 그렇진 않다. 넥스트의 버전업이 너무 빨라서 13, 14, 15까지 너무 많이 버전이 올라간 것처럼 보이지만 메이저 업그레이드는 라우팅 방식이 페이지 라우터에서 앱 라우터로 바뀐 것 뿐이고 나머지는 마이너한 업데이트인데 버전 숫자 자체를 바꾸어 버려서 그렇게 느껴질 순 있다.</p>
<p data-ke-size="size16">그러면 실제로 어떤 라우팅 방식이 프로덕션 레벨에서 더 많이 사용될까? 이제 막 만드는 프로젝트는 앱 라우터 방식으로 만들겠지만, 이미 만들어져있는 프로젝트는 페이지 라우터 방식이 훨씬 많을 것이다. 넥스트에서 페이지 라우터 방식을 지원 중단한 것도 아니고 여전히 잘 지원하고 있기도 하다. 물론 넥스트에서 마이그레이션을 권장하곤 있지만 여전히 페이지 라우터 방식으로 되어 있는 프로젝트들이 많기 때문에 분명 알고는 있는 게 좋다.</p>
<p data-ke-size="size16">아니, 이제 막 Next.js 학습에 입문한 개발자라면 페이지 라우터 방식부터 배우고 앱 라우터로 넘어가는 게 좋을 것 같다. 왜냐면 페이지 라우터 방식이나 앱 라우터 방식이나 라우팅을 파일 기반으로 하느냐, 폴더 기반으로 하느냐의 차이고 다른 매커니즘은 같기 때문에 오히려 Next.js라는 프레임워크를 이해하는 데 있어서 페이지 라우터를 먼저 배우는 게 더 도움이 될 것이다.</p>
<h2 data-ke-size="size26">파일명 기반 라우팅 방식</h2>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="930" data-origin-height="602"><span data-url="https://blog.kakaocdn.net/dn/qbhcL/btsJidgBZyF/skbxifgjWjk5pjwXj3ffQK/img.png" data-phocus="https://blog.kakaocdn.net/dn/qbhcL/btsJidgBZyF/skbxifgjWjk5pjwXj3ffQK/img.png"><img src="https://blog.kakaocdn.net/dn/qbhcL/btsJidgBZyF/skbxifgjWjk5pjwXj3ffQK/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FqbhcL%2FbtsJidgBZyF%2FskbxifgjWjk5pjwXj3ffQK%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="930" data-origin-height="602"/></span></figure>
</p>
<p data-ke-size="size16">pages라는 폴더 안에 index.js를 만들면 그게 메인 페이지가 되고 접속 세그먼트는 /가 된다. 그리고 만드는 파일명에 따라서 각각의 접속 세그먼트를 갖게 되는 파일명 기반 라우팅 방식이다.</p>
<h2 data-ke-size="size26">폴더명에 따른 라우팅</h2>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="930" data-origin-height="816"><span data-url="https://blog.kakaocdn.net/dn/wbDl1/btsJg9zvuUx/NbYvyJCVn2lPY2pNLCkk2k/img.png" data-phocus="https://blog.kakaocdn.net/dn/wbDl1/btsJg9zvuUx/NbYvyJCVn2lPY2pNLCkk2k/img.png"><img src="https://blog.kakaocdn.net/dn/wbDl1/btsJg9zvuUx/NbYvyJCVn2lPY2pNLCkk2k/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FwbDl1%2FbtsJg9zvuUx%2FNbYvyJCVn2lPY2pNLCkk2k%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="930" data-origin-height="816"/></span></figure>
</p>
<p data-ke-size="size16">파일명 뿐만 아니라 폴더 이름으로도 라우팅을 할 수 있다. 관심사 별로 페이지를 묶거나 컴포넌트와 같은 것들을 한 폴더 안에 넣을 때 폴더로 묶기도 한다.</p>
<h2 data-ke-size="size26">동적 경로 라우팅</h2>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="930" data-origin-height="816"><span data-url="https://blog.kakaocdn.net/dn/byJBDf/btsJg459CCe/v8fLk6HyPtv6BAI0XwxuA0/img.png" data-phocus="https://blog.kakaocdn.net/dn/byJBDf/btsJg459CCe/v8fLk6HyPtv6BAI0XwxuA0/img.png"><img src="https://blog.kakaocdn.net/dn/byJBDf/btsJg459CCe/v8fLk6HyPtv6BAI0XwxuA0/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbyJBDf%2FbtsJg459CCe%2Fv8fLk6HyPtv6BAI0XwxuA0%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="930" data-origin-height="816"/></span></figure>
</p>
<p data-ke-size="size16">그런데 웹 사이트에서 단순하게 딱 떨어지는 세그먼트 말고 상세페이지나 유저별 마이페이지 같은 곳들은 뒤의 주소가 동적으로 바뀌는데 이러한 Dynamic Routing도 [id]처럼 대괄호로 파일명을 생성하게 되면 간단하게 만들 수 있다.</p>
<h2 data-ke-size="size26">Pages Router 방식으로 프로젝트 생성하기</h2>
<pre id="code_1724747162789" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>npx create-next-app@14 [폴더명]</code></pre>
<p data-ke-size="size16">위와 같이 터미널에 명령어를 입력해준다.</p>
<p data-ke-size="size16">그런데 이미 Next.js로 프로젝트를 만들어 봤다면 조금 이상하다는 걸 알 수 있을 것이다. Next.js 15 버전까지 나와 있고, 버전이 몇 까지 나와 있든지 보통은 아래처럼 latest 버전을 설치하는데 14버전으로 강제하는 이유가 궁금할 수 있다.</p>
<pre id="code_1724747342949" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>npx create-next-app@latest</code></pre>
<p data-ke-size="size16">위의 프로젝트 생성 명령어는 next.js 공식문서에서 권장하는 방식이다. 그런데 Next.js 최신 버전은 App Router 방식이 주가 되는 방식이고, Pages Router를 지원하지 않는 것은 아니지만 안정적이지 않기 때문에 개발을 하다 보면 잔버그들이 계속 생긴다. 그래서 페이지 라우터 방식으로 프로젝트를 만들 거면 14 버전으로 만드는 게 낫다. 어차피 15 버전에서 제공하는 기능은 앱 라우터 방식에 대한 방식이기 때문에 페이지 라우터 방식의 프로젝트에서는 사용하지 않아서 괜찮다.</p>
<pre id="code_1724747454584" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>What is your project named? my-app
Would you like to use TypeScript? No / Yes
Would you like to use ESLint? No / Yes
Would you like to use Tailwind CSS? No / Yes
Would you like your code inside a `src/` directory? No / Yes
Would you like to use App Router? (recommended) No / Yes
Would you like to use Turbopack for `next dev`?  No / Yes
Would you like to customize the import alias (`@/*` by default)? No / Yes
What import alias would you like configured? @/*</code></pre>
<p data-ke-size="size16">그러면 터미널에 위와 같이 프레임워크에서 제공하는 기능들 중에서 어떤 것들을 사용할 지 이것저것 물어본다 본인 취향껏 하거나 팀 프로젝트의 경우 팀원들과 협의하며 팀 컨벤션에 맞게 설정하면 된다.</p>
<p data-ke-size="size16">하나씩 살펴보겠다. 저 위의 질문이 다 나오진 않는다.</p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>프로젝트 이름은 무엇으로 할 것인가?
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>처음에 [폴더명]까지 터미널에 같이 입력했으면 안 물어본다. 근데 버전까지만 작성하면 여기서 작성하면 된다. 폴더명이자 프로젝트 이름이 된다. 나중에 얼마든지 수정 가능하다.</li>
</ul>
</li>
<li>타입스크립트를 사용할 것인가?
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>본인이 타입스크립트를 사용할 줄 안다면 사용하는 것이 좋다. Next.js에서는 웬만하면 다 사용한다. 타입스크립트의 장점은 여기서 굳이 설명하지 않겠다.</li>
</ul>
</li>
<li>ESLint를 사용할 것인가?<br />
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>ESLint는 코드를 작성할 때 의존성 배열에 리액트에서 권장하는 방식으로 담겼는지 아닌지 등 개발 안정성을 돕기 위해 경고를 띄워주는 역할을 한다. 이게 거슬리면 꺼도 되지만 초보자는 켜는 게 좋을 것 같고 나도 도움을 많이 받는다.</li>
</ul>
</li>
<li>src 디렉토리를 사용할 것인가?
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>특별한 이유가 없으면 사용하는 게 좋을 것 같다. 여러 예제들이나 소스코드들이 src 디렉토리 기반으로 많이 나와있다.</li>
</ul>
</li>
<li>앱 라우터 방식을 사용할 것인가?
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>사용할 거면 Yes지만, 지금은 Pages Router 방식을 사용할 것이므로 No를 선택하겠다.</li>
</ul>
</li>
<li>import alias 방식을 별도로 커스터마이징 할 것인가?
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>import alias가 무엇이냐면 리액트 라이브러리 단독으로 프로젝트를 개발해보았다면 모듈을 import 할 때 상대경로에 따라서 ../../../../components 이렇게 복잡해지는 것을 본 적이 있을 것이다. 이것을 @/components 이렇게 절대경로로 간결하게 바꾸어주는 것이 import alias인데, 이것을 사용하지 않고 다른 방식으로 커스터마이징 할 것인가? 라는 질문이다.</li>
<li>너무 편리하므로 No를 선택해서 커스터마이징 하지 않고 기본적으로 제공하는 import alias를 사용하도록 하겠다.</li>
</ul>
</li>
</ul>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1132" data-origin-height="306"><span data-url="https://blog.kakaocdn.net/dn/DQiTt/btsJicvlJtn/ukUh0TJFWEdFgJj04C2Kfk/img.png" data-phocus="https://blog.kakaocdn.net/dn/DQiTt/btsJicvlJtn/ukUh0TJFWEdFgJj04C2Kfk/img.png"><img src="https://blog.kakaocdn.net/dn/DQiTt/btsJicvlJtn/ukUh0TJFWEdFgJj04C2Kfk/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FDQiTt%2FbtsJicvlJtn%2FukUh0TJFWEdFgJj04C2Kfk%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1132" data-origin-height="306"/></span></figure>
</p>
<p data-ke-size="size16">여기까지 완료되면 이렇게 프로젝트가 생성된다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="670" data-origin-height="886"><span data-url="https://blog.kakaocdn.net/dn/b1e8Lp/btsJiiCdYJl/GKVJRsMT2s6gim0pk1USm0/img.png" data-phocus="https://blog.kakaocdn.net/dn/b1e8Lp/btsJiiCdYJl/GKVJRsMT2s6gim0pk1USm0/img.png"><img src="https://blog.kakaocdn.net/dn/b1e8Lp/btsJiiCdYJl/GKVJRsMT2s6gim0pk1USm0/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fb1e8Lp%2FbtsJiiCdYJl%2FGKVJRsMT2s6gim0pk1USm0%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="670" data-origin-height="886"/></span></figure>
</p>
<p data-ke-size="size16">파일 구조를 보면 package-lock.json 파일이 확인되는 것을 보니 프로젝트가 기본적으로 npm 패키지 매니저를 사용하도록 설정되어 있는 것을 확인할 수 있다.</p>
<p data-ke-size="size16">만약 npm이 싫거나 팀에서 yarn 패키지 매니저를 사용하기로 했다면 node_modules와 package-lock.json를 삭제하시고 yarn 또는 yarn install을 입력해서 의존성을 yarn 패키지로 설치함과 동시에 삭제했던 node_modules가 다시 생성되고 yarn.lock 파일이 다시 생겨난다. 만약 안 생겨난다면 ctrl + shift + p 후 개발창 다시 로드! (reload)</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="682" data-origin-height="1142"><span data-url="https://blog.kakaocdn.net/dn/2IGZS/btsJg5jR1C6/ab7rSjIkb7CXfLcT89Btb1/img.png" data-phocus="https://blog.kakaocdn.net/dn/2IGZS/btsJg5jR1C6/ab7rSjIkb7CXfLcT89Btb1/img.png"><img src="https://blog.kakaocdn.net/dn/2IGZS/btsJg5jR1C6/ab7rSjIkb7CXfLcT89Btb1/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F2IGZS%2FbtsJg5jR1C6%2Fab7rSjIkb7CXfLcT89Btb1%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="682" data-origin-height="1142"/></span></figure>
</p>
<h2 data-ke-size="size26">특수파일 : _app.jsx</h2>
<pre id="code_1724753741867" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>import "@/styles/globals.css";
import type { AppProps } from "next/app";
<p>export default function App({ Component, pageProps }: AppProps) {
return &lt;Component {...pageProps} /&gt;;
}</code></pre></p>
<p data-ke-size="size16">리액트 프로젝트에서 App 컴포넌트가 했던 역할을 같이 하는 파일이다. 모든 컴포넌트의 부모 컴포넌트가 된다.</p>
<p data-ke-size="size16">props를 보면 하위의 모든 Component를 받고 있고 pageProps를 내려주고 있는 것을 볼 수 있다.</p>
<p data-ke-size="size16">모든 페이지에 동일하게 떠야 하는 헤더나 푸터를 만들고 싶다면 이곳에 넣어주면 된다.</p>
<pre id="code_1724754167093" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>import "@/styles/globals.css";
import type { AppProps } from "next/app";
<p>export default function App({ Component, pageProps }: AppProps) {
return
&lt;&gt;
&lt;Header&gt;&lt;글로벌헤더컴포넌트/&gt;&lt;/Header&gt;
&lt;Component {...pageProps} /&gt;;
&lt;/&gt;
}</code></pre></p>
<h2 data-ke-size="size26">특수파일 : _document.jsx</h2>
<pre id="code_1724754056344" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>import { Html, Head, Main, NextScript } from "next/document";
<p>export default function Document() {
return (
&lt;Html lang=&quot;en&quot;&gt;
&lt;Head /&gt;
&lt;body&gt;
&lt;Main /&gt;
&lt;NextScript /&gt;
&lt;/body&gt;
&lt;/Html&gt;
);
}</code></pre></p>
<p data-ke-size="size16">프로젝트의 모든 페이지에 공통적으로 적용되어야 할 HTML 태그를 작성하는 곳이다. 리액트 프로젝트에서 index.html이 하는 역할을 하고 있다고 보면 된다.</p>
<p data-ke-size="size16">보통 메타데이터 설정, 폰트 설정, 캐릭터셋 설정 등을 이곳에서 하고 있다.</p>
<h2 data-ke-size="size26">넥스트 설정 파일 : next.config.mjs</h2>
<pre id="code_1724754406056" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>/** @type {import('next').NextConfig} */
const nextConfig = {
  reactStrictMode: true,
};
<p>export default nextConfig;</code></pre></p>
<p data-ke-size="size16">넥스트 프로젝트의 설정 파일인데, 기본 세팅으로는 리액트 스트릭트 모드 설정 하나만 있다. 기본 옵션으로 true가 할당되어 켜져 있는데, 기호에 따라 false로 꺼주어도 된다. 리액트 컴포넌트의 잠재적인 문제점을 발견하기 위해서 작동하는데 콘솔에 두 번 씩 함수가 실행되게 해서 문제를 발견하는 방식이다. 그런데 사실 나는 이것의 장점을 크게 못 느끼고 있고, 또 잘 활용하는 것 같지 않아서 끄는 게 좋은 편이다. 잘 쓸 수 있으면 쓰고 아니면 꺼도 된다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">끝.</p>
<p data-ke-size="size16">&nbsp;</p>