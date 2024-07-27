<pre id="code_1722090298767" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>import { useEffect, useState } from "react";
import "./styles.css";
import axios from 'axios';

export default function App() {
  const [products, setProducts] = useState();

  useEffect(() =&gt; {
    axios.get('http://localhost:4000/products').then(response =&gt; {
      setProducts(response.data);
    })
  }, []);

  console.log(products);

  return (
    &lt;div className="App"&gt;
    &lt;/div&gt;
  );
}</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">db.json이라는 데이터 파일을 만들고 json-server로 로컬에서 node.js 환경에서 서버를 가동시킬 때의 예시이다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">base url/endpoint로 get 요청을 보내서 반환받은 response에서 data에 접근하여 이것을 products라는 상태에 담는 것까지 하고 있다. 그런데 useEffect 훅을 사용해서 의존성 배열을 비워두어 컴포넌트가 마운트 되었을 때에만 상태를 사용하는 모습이다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">콘솔에 상태를 찍어보고 있는데, 콘솔에 두 번씩 찍히게 될 것이다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">리액트의 strict mode가 켜져 있기 때문인데, 리액트 개발 과정에서 사이드 이펙트를 관리할 수 있도록 도와주는 모드이다. 특별히 의도하는 바가 없다면 켜두고 작업하는 것이 안전하다. 컴포넌트가 두 번 렌더링 되는 현상은 개발 모드에서만 실행되고 프로덕션 모드에서는 실행되지 않으니 안심해도 된다. 따라서 실제 배포 환경에서는 이로 인한 성능저하는 없다.</p>