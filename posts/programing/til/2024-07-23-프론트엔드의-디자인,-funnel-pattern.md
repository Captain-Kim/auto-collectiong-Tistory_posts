<h2 data-ke-size="size26">사용법</h2>
<h3 data-ke-size="size23">커스텀 훅 살펴보기</h3>
<pre class="javascript"><code>// useState, useCallback과 같은 리액트 훅을 사용하기 때문에 클라이언트 컴포넌트로 설정합니다.
'use client';
<p>import { useCallback, useState } from 'react';</p>
<p>// useNextButton 커스텀 훅을 정의합니다. 이 커스텀 훅은 Funnel 패턴을 구현하기 위해 단계를 넘기는 기능을 합니다.
// 인자를 3개 받습니다.
const useNextButton = (
// initialStep은 초기 시퀀스의 숫자입니다. 보통은 0부터 설정하시고 실제 사용하는 페이지에서도 그렇게 작성하시면 됩니다.
initialStep: number,
// 버튼에 렌더링 되는 텍스트입니다. 쓰는 곳이 전부 다르니 prop으로 받았습니다.
buttonText: string = '다음',
// 단계를 어디까지 넘길 수 있는지 리미트를 주는 값입니다. 렉이 걸리거나 사용자가 연타를 해서 개발자가 작성하지도 않은
// 시퀀스 번호까지 넘어가는 일을 예방하고자 설정했습니다.
limit: number,
) =&gt; {
// step이라는 상태를 만들어서 숫자를 증가시키면서 단계를 올립니다.
// 초기값으로는 이 커스텀훅을 사용하는 페이지에서 props로 내린 값 중 첫번째 initialStep의 값으로 설정합니다.
const [step, setStep] = useState(initialStep);</p>
<p>// handleNext라는 함수를 만들어서 사용자가 클릭할 버튼에 이벤트 핸들러로 연결합니다.
// 그런데 이 함수는 useCallback 훅을 사용했는데, 함수 재생성을 막기 위해서 최적화 한 것입니다.
// 하지만 정확한 메커니즘은 현재 학습 중으로 보시는 분이 따로 보셔야 할 것 같습니다.
const handleNext = useCallback(() =&gt; {
if (step &lt; limit) {
setStep(prevStep =&gt; prevStep + 1);
}
}, [setStep, step, limit]);</p>
<pre><code>const NextButton = ({ className }: { className: string }) =&amp;gt; (
</code></pre>
<p>// className을 이 컴포넌트에서 선언했을 때 tailiwindCSS와 충돌이 나는 점을 확인했습니다.
// 따라서 사용할 곳에서 직접 className을 지정하고 prop으로 전달해줍니다.
&lt;button onClick={handleNext} className={className}&gt;
{buttonText}
&lt;/button&gt;
);</p>
<pre><code>return { NextButton, step };
</code></pre>
<p>};</p>
<p>export default useNextButton;</code></pre></p>
<h3 data-ke-size="size23">써야 할 페이지에서</h3>
<h4 data-ke-size="size20">커스텀 훅 import</h4>
<pre class="clean"><code>import useNextButton from '@/hooks/useFunnelNextStep';</code></pre>
<h4 data-ke-size="size20">커스텀 훅 호출</h4>
<pre class="angelscript"><code> const { NextButton, step } = useNextButton(0, '다음', 4);</code></pre>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>인자로 3개를 받습니다.</li>
<li>첫번째 인자는 몇번째 시퀀스에서 시작할 것인지 정합니다. 보통은 0번으로 두고, 코드도 그렇게 작성하면 됩니다.</li>
<li>두번째 인자는 버튼에 렌더링 할 텍스트 내용입니다.</li>
<li>세번째 인자는 버튼의 최대 클릭 횟수를 몇 번으로 제한할 것인지 정합니다.</li>
</ul>
<h4 data-ke-size="size20">시퀀스 변경에 따른 조건부 렌더링</h4>
<pre class="1c"><code>{step === 0 &amp;&amp; &lt;WelcomePage /&gt;}
{step === 1 &amp;&amp; &lt;NextPage /&gt;}</code></pre>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>step 증가에 따라서 조건부로 렌더링 할 컴포넌트를 호출합니다.</li>
</ul>
<h4 data-ke-size="size20">NextButton 호출</h4>
<pre class="subunit"><code>&lt;NextButton className="text-2xl bg-main-color font-bold py-2 px-4 rounded" /&gt;</code></pre>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>버튼의 렌더링 텍스트 등은 커스텀 훅을 호출하면서 설정했기 때문에 여기서는 className만 사용합니다.</li>
<li>버튼의 스타일링을 NextButton 컴포넌트를 호출하면서 직접 동적 스타일링을 해주시면 됩니다.</li>
<li>원래는 동적 스타일링을 할 생각은 없었고, 커스텀 훅에서 스타일링을 하고자 했으나</li>
<li>TailwindCSS는 정적 클래스 이름을 기반으로 작동하기 때문에 훅 내부에서 클래스를 정의하면 충돌이 발생하여 이렇게 작성했습니다.</li>
<li>그러나 럭키비키의 관점에서 생각해보았을 때 이렇게 동적으로 스타일링을 하는 것의 장점은 아래와 같습니다.</li>
<li>사용하는 곳마다 버튼의 함수는 같아도 스타일링은 달라질 수 있는데, 이런 경우 유연하게 적용이 가능합니다.</li>
<li>컴포넌트를 사용하는 곳에서 직접 스타일링 하기 때문에 코드 가독성이 더 좋습니다.</li>
</ul>