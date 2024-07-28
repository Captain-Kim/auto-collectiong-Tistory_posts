<pre id="code_1722180770809" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>import { useEffect, useState } from "react";
// axios import

export default function App() {
  const [products, setProducts] = useState();

  useEffect(() =&gt; {
    axios.get('http://localhost:4000/products').then(response =&gt; {
      setProducts(response.date);
    });
  }, []);

  return (
    &lt;div className="App"&gt;
      &lt;h1&gt;상품 목록 페이지&lt;/h1&gt;
      &lt;ul&gt;
        {products &amp;&amp; products.map(products =&gt; {
          return &lt;li&gt;{products.name}&lt;/li&gt;
        })}
      &lt;/ul&gt;
    &lt;/div&gt;
  );
}</code></pre>
<p data-ke-size="size16">코드 로직을 보면</p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>반환 값을 저장할 state를 만든 후</li>
<li>useEffect 훅을 사용해서 의존성 배열을 비워 컴포넌트가 마운트 되었을 때에만 API 호출을 한 뒤 (안 그러면 무한 fetch 날아감)</li>
<li>map 메서드를 통해 반환값에서 특정 key에 해당하는 정보를 추출한다.</li>
</ul>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">매우 간단한 로직이지만 이 기본 패턴을 적어두는 이유는,</p>
<p data-ke-size="size16">products &amp;&amp; 으로 시작하는 부분 때문인데, 보통은 리액트를 자바스크립트로 배우는 것이 가장 먼저 선행될 것이고 나 역시 그랬는데 타입스크립트로 넘어오는 순간</p>
<p data-ke-size="size16">반환 값이 undefined일 때의 처리도 명시해주어야 한다. 그런데 이 개념에 익숙하지 않아서 저 구문을 항상 빼 먹고 코드를 작성하는데 리액트에 처음 입문하는 분들은 습관적으로 위 패턴을 기억하면 좋을 것 같다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">products &amp;&amp; 은 if문을 표현식으로 축약한 버전으로, 좌항이 truthy한 값이면 우항을 렌더링하라는 의미이다. 즉 products라는 반환값이 api 통신이 제대로 안 되었든 코드가 잘못 되었든 서버에 문제가 생겼든 어떠한 문제로 반환값이 없을 경우가 있으니, 없을 때는 렌더링 하지 말고 있을 때만 하라는 의미이다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">어차피 반환값이 없으면 렌더링이 안 되겠지만, 더 안전하게 코드를 작성하는 패턴이라고 생각하면 된다.</p>