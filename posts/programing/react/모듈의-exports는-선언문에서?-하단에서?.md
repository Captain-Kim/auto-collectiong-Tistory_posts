<pre id="code_1722181389407" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// 선언문에서 바로 export 하는 use case

export function Login() {
  ...
}

export fuction Logout() {
  ...
}

// 하단에서 모아서 export 하는 use case

export function Login() {
  ...
}

export fuction Logout() {
  ...
}

export { Login, Logout }</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">위 예제는 컴포넌트로 예를 들었지만, 물론 보통 한 파일에서 컴포넌트를 여러 개 export 하는 경우는 잘 없었던 것 같다.</p>
<p data-ke-size="size16">함수를 여러 개 export 하는 경우를 생각해보면 더 적절하겠다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">둘의 기능은 완전히 같다. 단순히 취향 차이이다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">각각 장단점이 있는데,</p>
<p data-ke-size="size16">선언문에서 바로 export 하는 경우 함수나 컴포넌트가 export 됨을 알 수 있어서 가독성이 좋다.</p>
<p data-ke-size="size16">그리고 컴포넌트나 함수를 제거할 때 export도 같이 제거되니 손 쉽다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">물론 한 번에 모아서 하단에서 export 하는 경우도 어떤 컴포넌트나 함수들이 export되는지 알 수 있어서 이게 가독성이 더 좋다고 느낄 수 있다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">팀의 컨벤션에 맞추는 것이 먼저겠으나 잘 모르겠다면 하단에서 모아서 하는 방식을 추천한다. 실무 현장에서는 하단에서 모아서 export하는 방식이 더 널리 쓰인다. 유지보수에 더 용이하다고 보는 것이다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">그러나 취향 차이라고는 했지만 컴포넌트를 모듈화 하는 과정에서 프로젝트의 규모가 커지면 한 가지 문제가 발생할 순 있다. </p>
<p data-ke-size="size16">바로 순환 의존성 문제인데, 예를 들어 Login 컴포넌트에서 Logout 컴포넌트를 import하고 또 반대로 Logout 컴포넌트에서 Login 컴포넌트를 import 하는 경우가 생기기도 한다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">자바스크립트 코드의 해석 순서는 모듈을 먼저 export 하고 함수나 컴포넌트를 정의하게 되는데, 이렇게 서로 함수나 컴포넌트끼리 서로 export, import 하는 순환 의존성이 형성되면 <span style="color: #333333; text-align: start;">이런 경우 선언문에서 바로 export 하게 되면<span> 런타임 에러가 발생할 수 있다. 그런데 하단에서 모아서 export 하게 되면 함수나 컴포넌트를 먼저 정의하고 후에 export 하기 때문에 이런 문제가 발생하지 않을 수 있다.</span></span></p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16"><span style="color: #333333; text-align: start;"><span>참고로 위 코드에서는 export dafault를 사용하지 않았는데, 해주는 게 좋다.</span></span></p>
<p data-ke-size="size16"><span style="color: #333333; text-align: start;"><span>export dafault는 모듈이 여러 개 일 때 특히 어떤 내보내기가 기본인지 명시적으로 사용되기도 하고,</span></span></p>
<p data-ke-size="size16"><span style="color: #333333; text-align: start;"><span>또 단일 export는 함수나 컴포넌트의 이름을 그대로 import 해야 하지만 export default는 어차피 하나만 지정 가능하기 때문에 그거 아니고서는 하나만 기본 내보내기이기 때문에 import 할 때 내 마음대로 이름을 바꿔도 된다.</span></span></p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">여러 개의 모듈을 export 할 때 기본 내보내기와 혼용하는 경우 아래처럼 작성하면 된다.</p>
<p data-ke-size="size16">이러면 어떤 게 기본 내보내기인지, 코드가 길어질 수록 더 가독성이 좋아진다.</p>
<pre id="code_1722182234176" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>functionA () {
  ...
}
<p>functionB () {
...
}</p>
<p>export { functionA };
export default { functionB };</code></pre></p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">위의 코드에서 기본 내보내기는 functionB이다. 극단적인 예시르 예를 들어보겠다.</p>
<p data-ke-size="size16">&nbsp;</p>
<pre id="code_1722182431829" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// 다른 파일에서
<p>import lalala, { functionA } from './myFunction';</p>
<p>functionA();
lalala();</code></pre></p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">이런 식으로 export는 이름을 그대로 써주어야 하지만 export default는 lalala 처럼 내 마음대로 import 해도 된다는 뜻이다.</p>
<p data-ke-size="size16">기본 내보내기를 사용하면 유연해진다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">참고로 단일 export(named export)는 중괄호를 사용해서 정확한 이름을 가져와야 하고,</p>
<p data-ke-size="size16">export default는 중괄호를 사용하지 않고 가져와도 된다. 그리고 위에서 말했던 것처럼 자유롭게 이름을 바꿔서 import 해도 된다.</p>