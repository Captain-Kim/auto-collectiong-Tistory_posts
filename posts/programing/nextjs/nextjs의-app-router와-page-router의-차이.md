<h2 data-ke-size="size26">App Router? Page Router?</h2>
<p data-ke-size="size16">Next.js는 Page Router 방식을 사용하다 13.4 버전 이후부터 App Router라는 개념이 도입되었다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">App Router 방식은 비교적 정말 최신 기술이기 때문에 아직까지는 Next.js에서 Page Router 방식으로 제작되어 있는 프로젝트가 훨씬 많다.</p>
<p data-ke-size="size16">따라서 지금 막 입문한 프론트 엔드 엔지니어는 Page Router의 개선 버전인 App Router를 배우되, Page Router와의 차이점을 짚고 넘어가는 것도 중요할 것이다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">Next.js를 배우기 위해서 인터넷에 검색을 하거나 강의를 찾아볼 때 이것이 App Router 방식의 자료인지 Page Router 방식의 자료인지 구분할 수 없다면 큰 혼동이 올 수 있다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">기본적으로 둘 다 공통점은 파일 시스템 기반 라우팅이라는 점이다. 무슨 말이냐면 리액트에서 라우트를 설정하기 위해선 React-Router-Dom이라는 라이브러리를 설치해서 개발자가 별도로 라우팅 설정을 일일이 해주었던 것에 비해 Next.js는 프레임워크의 성격을 갖고 있기 때문에 프로젝트를 셋업하는 순간 파일을 만드는 것만으로도 하나의 라우트를 갖게 해준다는 의미이다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">다만 app 폴더 내부에 파일을 만드느냐, pages 폴더에 파일을 만드느냐에 따라 달라질 것이다.</p>
<h2 data-ke-size="size26">App Router</h2>
<pre id="code_1722076540461" class="bash" data-ke-language="bash" data-ke-type="codeblock"><code>app/
  layout.js
  page.js
  about/
    page.js
  blog/
    layout.js
    page.js
    [slug]/
      page.js</code></pre>
<h3 data-ke-size="size23">주요 특징</h3>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>Server Components : 개발자가 별도로 'use client' 등을 명시하지 않으면, 파일은 서버 컴포넌트로 작성된다.</li>
<li>app 폴더 내의 디렉토링 기반 라우팅 : app 폴더 내에 폴더를 만들면 그것이 하나의 세그먼트를 갖는 라우트가 되고, 그 안에 page.tsx 파일을 만들어서 페이지를 만들 수 있다.</li>
<li>중첩된 레이아웃 기능 제공 : 각 디렉토리에서 layout.js 파일을 만들어 상위 폴더의 layout.js 파일과 중첩된 레이아웃을 정의할 수 있다.</li>
<li>Loading UI : loading.js 파일을 사용하여 로딩 상태를 쉽게 관리할 수 있다.</li>
<li>Error Handling : error.js 파일을 사용하여 에러 상태를 쉽게 처리할 수 있다.</li>
</ul>
<h2 data-ke-size="size26">Page Router</h2>
<pre id="code_1722076806814" class="bash" data-ke-language="bash" data-ke-type="codeblock"><code>pages/
  index.js
  about.js
  blog/
    [slug].js
  _app.js
  _document.js</code></pre>
<h3 data-ke-size="size23">주요 특징</h3>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>pages 폴더 내의 디렉토링 기반 라우팅 : pages 폴더를 만들고 그 안에 라우팅명.js와 같이 파일을 만들면 그것이 페이지가 된다.</li>
<li>app 라우팅처럼 폴더를 만들어 동적 라우팅이 가능하다. 그런데 앱 라우터에서는 폴더명을 [id] 와 같이 만드는 데, 페이지 라우터에서는 폴더는 그대로 만들고 파일명을 [id].js와 같이 만든다.</li>
<li>단순한 구조 : 앱 라우터는 라우트 하나를 만들 때마다 폴더를 만들어야 하기 때문에 디렉토리가 깊어질 수 있다. 그런데 페이지 라우터는 파일 하나 당 하나의 라우트를 갖기 때문에 구조가 단순할 수 있다.</li>
<li>getStaticProps, getServerSideProps 함수 제공 : 정적 생성(static generation)과 서버사이드 렌더링(server-side rendering)을 지원하는 함수를 사용한다. 앱 라우터 방식은 기본 방식이 서버사이드 렌더링이기 때문에 이 함수가 필요 없다.</li>
<li>커스텀앱 : pages/_app.js 또는 pages/_document.js와 같이 언더스코어가 붙는 파일을 만들어 전역적인 설정과 초기 HTML 문서를 구성할 수 있다. 앱라우터 방식에는 없는 개념이다.</li>
</ul>
<table style="border-collapse: collapse; width: 100%;" border="1" data-ke-align="alignLeft">
<tbody>
<tr>
<td style="width: 33.3333%;"><b>특징</b></td>
<td style="width: 33.3333%;"><b>App Router</b></td>
<td style="width: 33.3333%;"><b>Page Router</b></td>
</tr>
<tr>
<td style="width: 33.3333%;"><b>라우팅 방식</b></td>
<td style="width: 33.3333%;">디렉토리 및 파일 이름 기반</td>
<td style="width: 33.3333%;">파일 이름 기반</td>
</tr>
<tr>
<td style="width: 33.3333%;"><b>기본 렌더링 방식</b></td>
<td style="width: 33.3333%;">서버 컴포넌트</td>
<td style="width: 33.3333%;">클라이언트 컴포넌트</td>
</tr>
<tr>
<td style="width: 33.3333%;"><b>레이아웃 관리</b></td>
<td style="width: 33.3333%;">layout.js 파일 사용</td>
<td style="width: 33.3333%;">_app.js 파일 사용</td>
</tr>
<tr>
<td style="width: 33.3333%;"><b>로딩 상태 관리</b></td>
<td style="width: 33.3333%;">loading.js 파일 사용</td>
<td style="width: 33.3333%;">별도의 사용자 정의 로딩 상태 관리 필요&nbsp;</td>
</tr>
<tr>
<td style="width: 33.3333%;"><b>오류 처리</b></td>
<td style="width: 33.3333%;">error.js 파일 사용</td>
<td style="width: 33.3333%;">별도의 사용자 정의 오류 처리 필요</td>
</tr>
<tr>
<td style="width: 33.3333%;"><b>정적 및 서버사이드 렌더링</b></td>
<td style="width: 33.3333%;">지원되지 않음 (기본이 서버 컴포넌트임)</td>
<td style="width: 33.3333%;">getStaticProps, getServerSideProps 함수 지원</td>
</tr>
<tr>
<td style="width: 33.3333%;"><b>초기 HTML 문서 구성</b></td>
<td style="width: 33.3333%;">지원되지 않음</td>
<td style="width: 33.3333%;">_document.js 파일 사용</td>
</tr>
</tbody>
</table>
<h2 data-ke-size="size26">App Router 파일 컨벤션과 역할</h2>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>layout : 공통 UI(레이아웃)를 배치하는 컴포넌트&nbsp;</li>
<li>page : 특정 URL에 해당하는 페이지 컴포넌트. page라는 이름을 붙이면 해당 URL로 접근 가능</li>
<li>loading : 해당 영역에 대한 로딩 컴포넌트</li>
<li>not-found : 404 에러에 해당하는 에러 바운더리 컴포넌트</li>
<li>error : 에러가 발생했을 때 에러 UI를 표시하는 에러 바운더리 컴포넌트</li>
<li>global-error : 전역 에러 UI를 표시하는 에러 처리 컴포넌트</li>
<li>route : API 엔드포인트로 취급되는 파일</li>
<li>template : 레이아웃 컴포넌트가 다시 그려질 때 표시될 UI</li>
<li>default : 병렬 라우팅 처리 시 표시할 기본 UI</li>
</ul>
<h2 data-ke-size="size26">뭘 써야 하나?</h2>
<p data-ke-size="size16">초심자의 경우 최신의 방식인 App Router를 먼저 배우는 게 좋다. 기존 페이지 라우터 방식에 불편한 점이 있어 개선된 버전을 내놓은 것이기 때문이다.</p>
<h2 data-ke-size="size26">App Router의 장점</h2>
<p data-ke-size="size16">아래 일부는 페이지 라우터에서도 가능한 방식이지만, 앱 라우터에서 더 개선되었다.</p>
<h3 data-ke-size="size23">관심사 별 파일 분류</h3>
<p data-ke-size="size16">기존 페이지 라우터 방식은 pages, layouts, components, libs 등의 폴더가 항상 별도로 만들어져 있어 코드 간 서로 참조하는 코드를 보느라 계속 왔다 갔다 하는 비용이 컸다. 그러나 App Router 방식은 하나의 폴더에 관심사 별로 정리할 수 있기 때문에 App 폴더 안에 특정 라우팅과 관계된 페이지 컴포넌트인 page.js의 바로 옆에 레이아웃 컴포넌트, 라이브러리 파일을 배치할 수 있어 파일 배치가 더 쉬워졌다는 장점이 있기 때문이다.</p>
<h3 data-ke-size="size23">Prefectching</h3>
<p data-ke-size="size16">&lt;Link&gt; 컴포넌트나 router.prefetch() 등의 메서드를 통해 Next.js가 알아서 사용자가 다음으로 이동할 라우터의 정보를 미리 로딩해둔다는 장점이 있다.</p>
<p data-ke-size="size16">서버 레벨에서는 URL별로 페이지 컴포넌트가 연결되어 있는데, 이 URL 별로 자동으로 코드 스플리팅이 된다.</p>
<p data-ke-size="size16">코드 스플리팅(Code Splitting)이란 웹 애플리케이션의 성능을 최적화 할 수 있는 기법 중 하나다. 웹 페이지를 구성하는 코드를 여러 청크(chuck)로 나누어 필요한 부분만 로드하는 방법을 말한다. 코드 스플리팅 기법을 사용하면 초기 로딩 속도가 빨라지고, 사용자가 필요한 순간에만 코드를 로드하여 사용자 경험이 증가할 수 있다. 그리고 웹 앱을 구성하는 모든 코드를 로드하는 것이 아니라 사용자가 필요한 코드만 로드하기 때문에 네트워크 자원과 메모리 절약 측면에서도 좋다.</p>
<p data-ke-size="size16">Next.js에서는 기본적으로 페이지 단위로 코드 스플리팅을 자동으로 수행한다는 의미이다.</p>
<p data-ke-size="size16">위에서 말했던 &lt;Link&gt; 컴포넌트의 작동 원리는 다음과 같다. 사용자의 뷰포트에 단순 &lt;a&gt; 태그가 아닌 &lt;Link&gt; 로 연결된 링크가 들어온다면 Next.js는 사용자가 그 링크를 누를 수도 있을 것이라고 예측하고 페이지를 미리 로드 해 놓는다. 그러면 사용자가 실제로 그 링크를 눌렀을 때 더 빨리 페이지가 열리게 된다.</p>
<p data-ke-size="size16">router.prefetch() 메서드 또한 마찬가지의 원리인데, 특정 페이지의 코드를 미리 로드하도록 명시할 수 있는 메서드이다.</p>
<h3 data-ke-size="size23">Soft Navigation</h3>
<p data-ke-size="size16">Hard Navigation과 대비되는 개념이다. 하드 내비게이션은 브라우저가 전체 페이지를 새로고침 하는 방식을 이야기 한다. 즉 HTML로만 이루어진 문서를 이동할 때의 모습을 생각하면 된다. 페이지 전체가 다시 로드되면서 깜빡거리기도 하면서 사용자 경험과 로딩 속도가 느리다는 상대적인 단점이 있는 방식이다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">반면에 소프트 내비게이션은 페이지의 일부만 다시 렌더링하는 방식을 말한다. 전체 페이지가 아니라 필요한 부분만 업데이트 하기 떄문에 전체 페이지를 로드하는 하드 내비게이션 방식보다 로딩 속도가 빠르다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">리렌더링 되지 않은 영역의 상태는 유지되기 때문에 사용자 경험도 상대적으로 좋다. 예를 들어 입력 필드에 입력되어 있는 데이터가 초기화되지 않는다거나, 사용자의 스크롤 위치가 보존되는 것을 말한다.</p>