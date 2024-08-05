<h2 data-ke-size="size26">Image 컴포넌트란?</h2>
<p data-ke-size="size16">Next.js 에서 제공하는 이미지 최적화 컴포넌트이다.</p>
<p data-ke-size="size16">Next.js 프로젝트에서는 &lt;img&gt; 태그를 사용하면 컴파일 에러가 발생한다. 런타임 환경에서 사용하는 데는 아무런 문제가 없지만, 이왕이면 Next.js에서 제공하는 &lt;Image&gt; 컴포넌트를 써서 대역폭을 줄이고 최적화를 하라는 의미의 에러가 뜬다.</p>
<h2 data-ke-size="size26">Image 컴포넌트의 장점</h2>
<p data-ke-size="size16">Image 컴포넌트를 사용하면 아래와 같은 장점이 있다.</p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>사이즈 최적화 : 브라우저에 적합한 크기의 이미지를 자동으로 제공하여 불필요한 대역폭 사용을 줄여 줌.</li>
<li>포멧 최적화 : WebP와 같은 최신 이미지 포맷을 사용해서 파일 크기를 줄이고 로딩 속도를 향상시킴.</li>
<li>반응형 이미지 : 다양한 해상도에 맞게 이미지를 자동으로 조절해 줌.</li>
<li>레이아웃 보정 : 이미지가 로드되기 전에 공간을 예약해서 레이아웃 시프트(이미지가 뒤늦게 로드되면서 화면에 먼저 렌더링 되었던 것들이 밀려나는 현상)를 막아주어 사용자 경험이 향상됨.</li>
<li>지연 로딩(Lazy Loading) : 사용자의 뷰포트에 보이지 않는 이미지는 일단 불러오지 않고 사용자가 스크롤을 내렸을 때만 로드해서 초기 로딩 속도가 빨라짐.</li>
<li>우선 로딩(Priority Loading) : 중요한 이미지는 우선 로드하게 할 수 있어 사용자가 더 빠르게 이미지를 볼 수 있게 할 수 있음.</li>
<li>Vercel 이미지 최적화 : Next.js는 보통 vercel로 배포할 텐데, 이런 경우 자동으로 이미지가 CDN에 캐싱이 되어서 전 세계 어디서 접속하더라도 빠른 속도를 보장 받음.</li>
<li>SEO 최적화 : img 태그에서는 alt 속성을 생략해도 되지만 Image 컴포넌트는 강제하고 있어 SEO 최적화에 유리함.</li>
</ul>
<h2 data-ke-size="size26">Image 컴포넌트 사용법</h2>
<pre id="code_1722184228431" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>import Image from 'next/image';
<p>function HomePage() {
return (
&lt;div&gt;
&lt;h1&gt;Welcome to My Site&lt;/h1&gt;
&lt;Image
src=&quot;https://storage.ive.com/member/wonyoung.jpg&quot;
alt=&quot;Picture of the JangWonYoung&quot;
width={500}
height={500}
priority
/&gt;
&lt;/div&gt;
);
}</p>
<p>export default HomePage;</code></pre></p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>priority 속성 말고 나머지는 기본값이다. 무조건 명시해주어야 한다.</li>
<li>Image 컴포넌트는 기본적으로 Lazy Loading을 활성화 시킨다.</li>
<li>priority 속성을 명시하면 해당 이미지는 Lazy Loading을 비활성화 시켜 즉시 로드된다.</li>
</ul>
<h3 data-ke-size="size23">호스트 서버 등록</h3>
<pre id="code_1722184471700" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// next.config.mjs 또는 next.config.js
<p>module.exports = {
images : {
{
protocol: 'https',
hostname: 'storage.ive.com',
port:'', // 없어도 됨
pathname: '/member/**', // 없어도 됨
},
},
}</code></pre></p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>위 json은 Next.js에서 권장하는 속성을 전부 적은 것인데, 없어도 되는 항목도 있으니 확인해보시길.</li>
</ul>