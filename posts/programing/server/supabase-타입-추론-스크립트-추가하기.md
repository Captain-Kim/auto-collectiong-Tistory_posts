<h2 data-ke-size="size26">상황</h2>
<p data-ke-size="size16">무엇이 되었든 타입스크립트로 데이터를 받아 오려면 응답값의 타입을 지정해주어야 한다.</p>
<p data-ke-size="size16">그런데, 관계형 데이터베이스를 사용하는 수파베이스의 특성 상 아무리 작은 프로젝트여도 데이터베이스와 컬럼의 개수가 상당히 많아질 테고 중간 중간 데이터베이스나 컬럼이 수정되는 소요가 있을 텐데 그 때마다 타입을 지정해주어야 한다는 것은 정말 끔찍한 일이다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1242" data-origin-height="1348"><span data-url="https://blog.kakaocdn.net/dn/bOM3E2/btsIqDPQGeB/ohbAtJjfLyUD6R1DAWncAk/img.png" data-phocus="https://blog.kakaocdn.net/dn/bOM3E2/btsIqDPQGeB/ohbAtJjfLyUD6R1DAWncAk/img.png"><img src="https://blog.kakaocdn.net/dn/bOM3E2/btsIqDPQGeB/ohbAtJjfLyUD6R1DAWncAk/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbOM3E2%2FbtsIqDPQGeB%2FohbAtJjfLyUD6R1DAWncAk%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1242" data-origin-height="1348"/></span></figure>
</p>
<p data-ke-size="size16">정말 간단한 토이 프로젝트에서도 이런 타입이 400 라인 가깝게 필요하다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">그러나 다행인 것은 supabase에서는 타입을 자동으로 추론해주는 메서드를 제공한다.</p>
<h2 data-ke-size="size26">공식문서 원문</h2>
<p data-ke-size="size16"><a href="https://supabase.com/docs/guides/api/rest/generating-types" target="_blank" rel="noopener&nbsp;noreferrer">https://supabase.com/docs/guides/api/rest/generating-types</a></p>
<figure id="og_1720450075750" contenteditable="false" data-ke-type="opengraph" data-ke-align="alignCenter" data-og-type="article" data-og-title="Generating TypeScript Types | Supabase Docs" data-og-description="How to generate types for your API and Supabase libraries." data-og-host="supabase.com" data-og-source-url="https://supabase.com/docs/guides/api/rest/generating-types" data-og-url="https://supabase.com/docs/guides/api/rest/generating-types" data-og-image="https://scrap.kakaocdn.net/dn/cZOYrv/hyWvTwUX6L/ry4tkMZVIJKTo8p7wM760K/img.png?width=1200&amp;height=600&amp;face=0_0_1200_600"><a href="https://supabase.com/docs/guides/api/rest/generating-types" target="_blank" rel="noopener" data-source-url="https://supabase.com/docs/guides/api/rest/generating-types">
<div class="og-image" style="background-image: url('https://scrap.kakaocdn.net/dn/cZOYrv/hyWvTwUX6L/ry4tkMZVIJKTo8p7wM760K/img.png?width=1200&amp;height=600&amp;face=0_0_1200_600');">&nbsp;</div>
<div class="og-text">
<p class="og-title" data-ke-size="size16">Generating TypeScript Types | Supabase Docs</p>
<p class="og-desc" data-ke-size="size16">How to generate types for your API and Supabase libraries.</p>
<p class="og-host" data-ke-size="size16">supabase.com</p>
</div>
</a></figure>
<p data-ke-size="size16">이 글 작성 시점과 게시글을 확인하는 시점에서 코드의 버전이 달라지면 에러가 발생할 수 있으니 공식 문서를 참고바람.</p>
<h2 data-ke-size="size26">방법</h2>
<h3 data-ke-size="size23">supabase CLI 패키지 설치</h3>
<pre id="code_1720450192789" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>yarn i supabase@"&gt;=1.8.1" --save-dev</code></pre>
<h3 data-ke-size="size23">토큰 발급받고 로그인하기</h3>
<pre id="code_1720450228101" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>npx supabase login</code></pre>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>패키지 매니저를 npm, yarn 어떤 것으로 했든 앞으로의 코드에서 npx라고 명시되어 있는 것은 npx 그대로 입력해야 함.</li>
<li>터미널에 위 명령어를 입력하면 웹 브라우저에서 supabase 토큰 발급 페이지가 열리며 에디터에서 로그인이 완료됨.</li>
<li>발급한 토큰은 supabase AccessToken 메뉴를 찾아서 확인하면 됨.</li>
</ul>
<h3 data-ke-size="size23">supabase 폴더 초기화</h3>
<pre id="code_1720450375358" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>npx supabase init</code></pre>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>위 명령어를 입력하면 root 폴더에 supabase 폴더가 생기고, config.toml, seed.sql 등 파일이 생성됨.</li>
</ul>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="694" data-origin-height="480"><span data-url="https://blog.kakaocdn.net/dn/dg8FLu/btsIrsz0Hy1/GvJIAxPuyeKwsFO7881fL1/img.png" data-phocus="https://blog.kakaocdn.net/dn/dg8FLu/btsIrsz0Hy1/GvJIAxPuyeKwsFO7881fL1/img.png"><img src="https://blog.kakaocdn.net/dn/dg8FLu/btsIrsz0Hy1/GvJIAxPuyeKwsFO7881fL1/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fdg8FLu%2FbtsIrsz0Hy1%2FGvJIAxPuyeKwsFO7881fL1%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" width="416" height="288" data-origin-width="694" data-origin-height="480"/></span></figure>
</p>
<h3 data-ke-size="size23">types 폴더 생성</h3>
<p data-ke-size="size16">루트 폴더에 types 폴더만 만든다.</p>
<h3 data-ke-size="size23">타입 추론하기 (생략하고 다음으로 넘어가도 됨)</h3>
<pre id="code_1720450567300" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>npx supabase gen types typescript --project-id "$PROJECT_REF" --schema public &gt; types/supabase.ts</code></pre>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>$PROJECT_REF 부분에는 쌍 따옴표는 두고 안의 내용만 프로젝트URL의 뒤의 랜덤한 알파벳의 나열을 복사-붙여넣기.</li>
</ul>
<h3 data-ke-size="size23">타입 추론 스크립트 설정</h3>
<pre id="code_1720451194682" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// package.json
 "genTypes": "npx supabase gen types typescript --project-id \"$PROJECT_ID\" --schema public &gt; types/supabase.ts"</code></pre>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>역시 달러사인부터 $PROJECT_ID 이 부분만 프로젝트 URL 맨 뒷 부분으로 교체.</li>
<li>바로 위 과정을 생략했으면 이제부터는 yarn genTypes 또는 npm run genTypes만 입력해도 컬럼이나 테이블에 수정사항이 있을 경우 자동으로 바뀜. 명령어는 알아서 취향껏 수정 가능.</li>
</ul>
<h3 data-ke-size="size23">supabaseClient.ts 타입 지정</h3>
<pre id="code_1720451437832" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// lib/supabaseClient.ts (Next.js 기준 폴더 디렉토리임)
<p>import { Database } from '../types/supabase';
import { createClient } from '@supabase/supabase-js';</p>
<p>const supabaseUrl = process.env.NEXT_PUBLIC_SUPABASE_URL! as string;
const supabaseAnonKey = process.env.NEXT_PUBLIC_SUPABASE_ANON_KEY! as string;</p>
<p>export const supabase = createClient&lt;Database&gt;(supabaseUrl, supabaseAnonKey);</code></pre></p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>기존 supabaseClient 셋업과 달라진 점은 as string, &lt;Database&gt;가 추가되었다는 것.</li>
<li>여기까지 하면 끝이다.</li>
</ul>