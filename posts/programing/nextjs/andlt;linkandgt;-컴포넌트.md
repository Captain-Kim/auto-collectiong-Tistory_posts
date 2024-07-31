<p data-ke-size="size16">넥스트에서는 &lt;Link&gt; 컴포넌트와 useRouter() 훅으로 페이지 간 이동을 할 수 있다.</p>
<p data-ke-size="size16">&nbsp;</p>
<pre id="code_1722083193695" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>import Link from 'next/link'
<p>function Home() {
return (
&lt;div&gt;
&lt;Link href=&quot;/&quot;&gt;Main&lt;/Link&gt;
&lt;Link href=&quot;/login&quot;&gt;Login&lt;/Link&gt;
&lt;/div&gt;
)
}</code></pre></p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">앵커 태그와 비슷한 형태로 되어 있는 것을 알 수 있다.</p>
<p data-ke-size="size16">Link 컴포넌트로 만든다고 해서 별도의 태그로 만들어지는 것이 아니라 개발자 도구에서 확인해보면 HTML 문서에서는 앵커 태그로 변환되어 있는 것을 확인 할 수 있다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">앵커 태그로 만들어져야 검색 엔진 크롤러가 페이지를 읽을 수 있기 때문에 그런 부분은 넥스트에서 잘 변환해주니 걱정하지 않아도 된다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">다만 Link 컴포넌트로 페이지 이동할 수 있는 링크를 만들어 놓으면 a 태그와는 다르게, 사용자의 뷰포트에 들어오는 순간 prefeching 해주기 떄문에 사용자가 누를 것이라고 예상하고 페이지를 미리 로드해두기 때문에 페이지 간의 전환이 보다 매끄럽고 자연스러워진다.</p>