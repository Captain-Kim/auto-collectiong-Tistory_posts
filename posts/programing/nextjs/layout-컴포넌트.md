<p data-ke-size="size16">React.js에서 App 컴포넌트에서 했던 일을 Next.js에서는 layout 컴포넌트가 해주고 있다고 생각하면 된다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">프로젝트를 처음 생성하고 나면 src/app 폴더 하위에서부터 layout.tsx 컴포넌트가 만들어져 있을 건데,</p>
<p data-ke-size="size16">이곳에서 해당 레이아웃 컴포넌트가 있는 폴더 내부의 모든 파일들 (자식 요소들, children)에 대해서 공통된 레이아웃을 설정할 수 있다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">예를 들어 아래처럼 모든 페이지에 둥둥 떠있는 내비게이션 헤더를 만들 수도 있다.</p>
<p data-ke-size="size16">&nbsp;</p>
<pre id="code_1722084294550" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>import Link from 'next/link';
<p>export default function Layout({ children }) {
return (
&lt;div&gt;
&lt;nav&gt;
&lt;Link href=&quot;/home&quot;&gt;홈&lt;/Link&gt; ㅣ &lt;Link href=&quot;/login&quot;&gt;로그인&lt;/Link&gt;
&lt;/nav&gt;
&lt;div&gt;{children}&lt;/div&gt;
&lt;/div&gt;
);
}</code></pre></p>
<p data-ke-size="size16">&nbsp;</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1600" data-origin-height="606"><span data-url="https://blog.kakaocdn.net/dn/bbCzWi/btsIPYSyNxs/R0v2aWuFqk3Y5dxguVkoe1/img.png" data-phocus="https://blog.kakaocdn.net/dn/bbCzWi/btsIPYSyNxs/R0v2aWuFqk3Y5dxguVkoe1/img.png"><img src="https://blog.kakaocdn.net/dn/bbCzWi/btsIPYSyNxs/R0v2aWuFqk3Y5dxguVkoe1/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbbCzWi%2FbtsIPYSyNxs%2FR0v2aWuFqk3Y5dxguVkoe1%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1600" data-origin-height="606"/></span></figure>
</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">위 사진을 보면 페이지는 두 개가 있음을 알 수 있다.</p>
<p data-ke-size="size16">1) /dashboard</p>
<p data-ke-size="size16">2) /dashboard/settings</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">그런데 layout 파일은 하나다.</p>
<p data-ke-size="size16">settings 폴더 안에도 레이아웃 파일을 만들 수 있는데, 이렇게 되면 /dashboard/layout.js 파일과 /dashboard/settings/layout.js 파일이 중첩되어 사용된다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">즉 위 사진 상황에서는 dashboard 라우트 내에 존재하는 layout 파일이 두 개의 페이지에 함께 공유된다는 것을 알 수 있다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">만약 중첩된 레이아웃(Nesting Layout)을 만든다면 아래와 같은 구성을 하고 있을 것이다.</p>
<pre id="code_1722086130260" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>export default function DashboardLayout({
  children,
}: {
  children: React.ReactNode
}) {
  return &lt;section&gt;{children}&lt;/section&gt;
}</code></pre>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1600" data-origin-height="1026"><span data-url="https://blog.kakaocdn.net/dn/sITGw/btsIOGSSDCk/XQzBkZ82SisaZQ5tNYxFi0/img.png" data-phocus="https://blog.kakaocdn.net/dn/sITGw/btsIOGSSDCk/XQzBkZ82SisaZQ5tNYxFi0/img.png"><img src="https://blog.kakaocdn.net/dn/sITGw/btsIOGSSDCk/XQzBkZ82SisaZQ5tNYxFi0/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FsITGw%2FbtsIOGSSDCk%2FXQzBkZ82SisaZQ5tNYxFi0%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1600" data-origin-height="1026"/></span></figure>
</p>
<p data-ke-size="size16">그림을 보면 좀 더 명확히 이해가 되는데, app 폴더에 바로 위치한 루트 레이아웃에서 헤더를 만들고, 대시보드 폴더에 있는 레이아웃에서 사이드바를 만들었다면, 앱 폴더 내에 있는 라우터에서 어디를 가도 헤더는 무조건 떠 있는데 /dashboard로 접근하면 헤더와 사이드바가 동시에 보이는 것이다.</p>
<p data-ke-size="size16">즉 대시보드에 있는 레이아웃은 /dashboard라는 라우트에 대한 독립적인 레이아웃이면서 상위 레이아웃과 중첩시킬 수 있는 레이아웃이 된다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">이걸 코드로 표현하면 아래와 같을 것이다.</p>
<pre id="code_1722086514598" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// app/layout.js
export default function RootLayout({ children }) {
  return (
    &lt;html&gt;
      &lt;head /&gt;
      &lt;body&gt;
        &lt;header&gt;Header&lt;/header&gt;
        &lt;main&gt;{children}&lt;/main&gt;
        &lt;footer&gt;Footer&lt;/footer&gt;
      &lt;/body&gt;
    &lt;/html&gt;
  )
}</code></pre>
<pre id="code_1722086530857" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// app/dashboard/layout.js
export default function DashboardLayout({ children }) {
  return (
    &lt;div&gt;
      &lt;aside&gt;Sidebar&lt;/aside&gt;
      &lt;section&gt;{children}&lt;/section&gt;
    &lt;/div&gt;
  )
}</code></pre>
<h2 data-ke-size="size26">Root Layout(필수)</h2>
<p data-ke-size="size16">이렇게 앱 라우트 마다 별도로 설정하는 레이아웃 말고, 루트 단에서도 레이아웃이 있다. app 폴더에 바로 위치한 layout.js를 말하는데, 이 파일은 필수 파일이고 리액트에서는 app.tsx가 하던 역할을 한다. (확장자를 계속 혼용해서 이야기 하고 있는데, 공식 문서에서 js라고 나와 있어서 그런 것이고 실제로 사용하시는 확장자로 보시면 된다.)</p>
<p data-ke-size="size16">&nbsp;</p>
<pre id="code_1722086023193" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>export default function RootLayout({
  children,
}: {
  children: React.ReactNode
}) {
  return (
    &lt;html lang="en"&gt;
      &lt;body&gt;
        {/* Layout UI */}
        &lt;main&gt;{children}&lt;/main&gt;
      &lt;/body&gt;
    &lt;/html&gt;
  )
}</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">루트 레이아웃은 위와 같이 구성되어 있다. children은 app 폴더 내에 존재하는 모든 페이지를 말한다.</p>
<p data-ke-size="size16">그리고 이 루트 레이아웃에서는 페이지의 전체적인 메타데이터를 설정할 수도 있다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">그렇다면 페이지 마다 고유한 메타데이터도 동적으로 설정할 수 있나? ===&gt;&gt;&gt; 있다.</p>
<h2 data-ke-size="size26">그 외 레이아웃 컴포넌트의 특징</h2>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>레이아웃 컴포넌트는 .js .jsx .tsx 파일 확장자 모두 지원한다.</li>
<li>루트 레이아웃에만 &lt;html&gt;과 &lt;body&gt;를 포함시킬 수 있다.
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>루트 레이아웃 파일은 앱 전체의 공통 레이아웃을 설정하기 때문에 가능하다.</li>
<li>그 외 하위 레이아웃 파일은 특정 라우트에 대한 라우트만 적용하기 때문에 &lt;HTML&gt; 태그와 &lt;BODY&gt; 태그는 사용할 수 없다. 오로지 상위 레이아웃 파일과 중첩된 레이아웃을 만들기 위해서만 사용된다. 여기에는 이 태그를 사용하지 않아도 루트 레이아웃의 &lt;main&gt; 태그 내에서 렌더링 된다.</li>
<li>이런 방식은 SEO 최적화에도 유리하다.</li>
</ul>
</li>
</ul>
<pre id="code_1722086671389" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// app/layout.js
export default function RootLayout({ children }) {
  return (
    &lt;html lang="en"&gt;
      &lt;head&gt;
        &lt;title&gt;My App&lt;/title&gt;
      &lt;/head&gt;
      &lt;body&gt;
        &lt;header&gt;Header&lt;/header&gt;
        &lt;main&gt;{children}&lt;/main&gt;
        &lt;footer&gt;Footer&lt;/footer&gt;
      &lt;/body&gt;
    &lt;/html&gt;
  );
}
<p>// app/dashboard/layout.js
export default function DashboardLayout({ children }) {
return (
&lt;div className=&quot;dashboard-layout&quot;&gt;
&lt;aside&gt;Sidebar&lt;/aside&gt;
&lt;section&gt;{children}&lt;/section&gt;
&lt;/div&gt;
);
}</code></pre></p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>레이아웃 컴포넌트는 별도 설정하지 않으면 기본으로 서버 컴포넌트로 설정된다. 하지만 클라이언트 컴포넌트로도 만들 수 있다. 'use client' 지시어를 명시하면 된다.</li>
<li>레이아웃 컴포넌트에서도 데이터 페칭이 가능하다. 레이아웃 컴포넌트의 영향을 받는 모든 페이지에서 필요한 데이터가 있다면 레이아웃 컴포넌트에서 데이터 페칭을 하면 모든 페이지에서 공통적으로 필요한 데이터를 미리 로드할 수 있다.</li>
</ul>
<pre id="code_1722087051074" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// app/layout.js
<p>import React from 'react';</p>
<p>// 가정: 데이터 페칭 함수
async function fetchGlobalData() {
const response = await fetch('https://api.example.com/global');
return response.json();
}</p>
<p>export default async function RootLayout({ children }) {
const globalData = await fetchGlobalData();</p>
<p>return (
&lt;html lang=&quot;en&quot;&gt;
&lt;head&gt;
&lt;title&gt;My App&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;header&gt;Header&lt;/header&gt;
&lt;main&gt;
&lt;GlobalDataContext.Provider value={globalData}&gt;
{children}
&lt;/GlobalDataContext.Provider&gt;
&lt;/main&gt;
&lt;footer&gt;Footer&lt;/footer&gt;
&lt;/body&gt;
&lt;/html&gt;
);
}</p>
<p>// 전역 데이터를 위한 Context 생성
const GlobalDataContext = React.createContext(null);</p>
<p>export function useGlobalData() {
return React.useContext(GlobalDataContext);
}</code></pre></p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>레이아웃 컴포넌트에서 데이터 페칭을 하는 경우, 페이지 컴포넌트에서 동일한 데이터 페칭을 하더라도 리액트가 이를 중복된 요청으로 생각하고 중복 요청을 제거하기 때문에 성능에 영향을 끼치지 않는다. 이를 Dedupe라고 한다.</li>
</ul>
<pre id="code_1722088690723" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// app/dashboard/layout.js
<p>import React from 'react';</p>
<p>// 가정: 데이터 페칭 함수
async function fetchDashboardData() {
const response = await fetch('https://api.example.com/dashboard');
return response.json();
}</p>
<p>export default async function DashboardLayout({ children }) {
const dashboardData = await fetchDashboardData();</p>
<p>return (
&lt;div className=&quot;dashboard-layout&quot;&gt;
&lt;aside&gt;Sidebar&lt;/aside&gt;
&lt;section&gt;
&lt;h1&gt;Dashboard Layout&lt;/h1&gt;
&lt;p&gt;Dashboard Data: {JSON.stringify(dashboardData)}&lt;/p&gt;
{children}
&lt;/section&gt;
&lt;/div&gt;
);
}</p>
<p>// app/dashboard/page.js</p>
<p>import React from 'react';</p>
<p>// 가정: 데이터 페칭 함수
async function fetchDashboardData() {
const response = await fetch('https://api.example.com/dashboard');
return response.json();
}</p>
<p>export default async function DashboardPage() {
const dashboardData = await fetchDashboardData();</p>
<p>return (
&lt;div&gt;
&lt;h1&gt;Dashboard Page&lt;/h1&gt;
&lt;p&gt;Dashboard Data: {JSON.stringify(dashboardData)}&lt;/p&gt;
&lt;/div&gt;
);
}</code></pre></p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>Route Groups를 사용하면 특정 경로 세그먼트를 공통 레이아웃에 포함하거나 제외 시킬 수 있다.
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>라우트 그룹은 (관심사) 형태로 폴더명을 지어주면 된다.</li>
<li>아래 폴더 구조를 보면 (marketing)과 (dashboard)라는 라우트 그룹이 존재하는데, 각각 라우트 그룹 안에 있는 최상위 레이아웃 파일이 해당 라우트 그룹 내에 있는 파일들에만 공통적으로 영향을 줄 수 있다. 예를 들어 /app/(marketing)/layout.ts 파일은 home과 about 라우트에만 레이아웃을 공유한다. dashboard는 그 layout만 공유한다.</li>
</ul>
</li>
</ul>
<pre id="code_1722088848372" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>app/
  (marketing)/
    layout.js
    home/
      page.js
    about/
      page.js
  (dashboard)/
    layout.js
    stats/
      page.js
    settings/
      page.js</code></pre>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>참고로 app 폴더 안에 있는 루트 레이아웃 파일이 페이지 라우터 방식에서의 _app.tsx, _document.tsx의 역할을 하는 것이다.</li>
</ul>