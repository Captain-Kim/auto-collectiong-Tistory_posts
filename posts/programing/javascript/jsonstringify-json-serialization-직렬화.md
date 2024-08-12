<p data-ke-size="size16">자바스크립트로 프로그래밍을 하다 보면 JSON이라는 데이터 형식에 익숙할 것이다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">풀 네임은 JavaScript Object Notation인데, 이름 그대로 자바스크립트 객체를 말한다.</p>
<p data-ke-size="size16">&nbsp;</p>
<pre id="code_1723144157858" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>const jsObject = {
    name: "John",
    age: 30,
    city: "New York"
};</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">위와 같은 형태가 JavaScript 객체인데, 이것은 프로그래밍을 위해 사용되는 데이터 구조이다.</p>
<p data-ke-size="size16">자바스크립트 코드 내에서 사용되는 데이터 구조라는 의미이다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">그런데 우리가 데이터를 서버와 주고 받을 때 사용하는 JSON은 이와 약간 차이가 있다.</p>
<p data-ke-size="size16">&nbsp;</p>
<pre id="code_1723144223452" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>{
    "name": "John",
    "age": 30,
    "city": "New York"
}</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">위의 데이터 형태가 JSON 문자열인데, key에도 string 처리가 되어 있는 것을 볼 수 있다.</p>
<p data-ke-size="size16">JSON 문자열은 서버와 데이터를 주고 받을 때 사용된다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">반대로 자바스크립트 객체로는 데이터를 주고 받을 수 없다. 프로그래밍을 위해 메모리에 할당되는 데이터 구조이기 때문이다.</p>
<p data-ke-size="size16">만약 자바스크립트 코드로 작성된 자바스크립트 객체가 있고, 이를 서버와 데이터를 주고 받으려면 JSON 문자열로 만드는 직렬화(serialization) 과정이 필요하다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">json.stringify라는 메서드를 사용해서 자바스크립트 객체를 직렬화하여 JSON 문자열로 변경할 수 있다.</p>
<pre id="code_1723144459276" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>const jsObject = { name: "John", age: 30, city: "New York" };
const jsonString = JSON.stringify(jsObject);
console.log(jsonString); // '{"name":"John","age":30,"city":"New York"}'</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">반대로 서버에서 전송받은 데이터를 자바스크립트 코드로 무언가 가공할 필요가 있다면 JSON 문자열을 자바스크립트 객체로 변환하는 역직렬화(deserialization)를 하면 된다.</p>
<p data-ke-size="size16">이는 json.parse 메서드로 가능하다.</p>
<p data-ke-size="size16">&nbsp;</p>
<pre id="code_1723144541155" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>const jsonString = '{"name":"John","age":30,"city":"New York"}';
const jsObject = JSON.parse(jsonString);
console.log(jsObject); // { name: 'John', age: 30, city: 'New York' }</code></pre>