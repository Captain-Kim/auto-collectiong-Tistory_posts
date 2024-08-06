<h2 data-ke-size="size26">상황</h2>
<p data-ke-size="size16">API에서 데이터를 받아 오고 그 반환값으로 어떤 리스트를 렌더링 하는 경우, 그 렌더링 된 아이템 하나를 클릭하면 더 자세한 상세 페이지로 연결되는 것이 일반적인 user flow이다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">만약 쇼핑몰로 가정한다면 수천, 수만 개의 상품 정보가 있을 것이고, 상품명, 가격, 이미지... 등등의 정보가 반환값에 담겨 있다고 가정하자.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">이럴 때 각각의 아이템에는 그 아이템을 식별할 수 있는, 겹치지 않는 고유값의 id가 일반 number든 uuid든 어떤 식으로도 겹치지 않게 설정되어 있을 것이다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">보통은 이러한 고유값을 하나의 세그먼트로 받아서 해당 아이템의 상세 페이지를 라우팅하게 된다.</p>
<p data-ke-size="size16">제품에 대한 상세페이지 뿐만 아니라 유저에 대한 프로필도 마찬가지다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">https://ive.com/goods/1</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">이런 식으로 url을 갖도록 하는 것이 이 문서의 목적이다.</p>
<p data-ke-size="size16">바뀌는 건 맨 뒤의 숫자뿐이고, 해당 아이템의 고유 식별 값이다. 이렇게 동적인 라우팅을 하는 기본 패턴에 대해서 알아보자.</p>
<h2 data-ke-size="size26">디렉토리 구성</h2>
<pre id="code_1722185199686" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// 앱 라우터 방식
<p>/app
/goods
/[id]
page.tsx</p>
<p>// 페이지 라우터 방식</p>
<p>/pages
/goods
[id].tsx</code></pre></p>
<p data-ke-size="size16">앱 라우터와 페이지 라우터를 둘 다 적어 놨다. 사용하는 방식에 따라서 사용하시면 된다.</p>
<p data-ke-size="size16">그런데 본인은 최신 버전을 따를 것이기 때문에 앱 라우터를 기준으로 설명하겠다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">먼저 둘 다 공통적으로 [id]와 같은 대괄호의 네이밍이 존재한다는 공통점이 있고, 차이점이 있다면 페이지 자체가 그 대괄호 네이밍인가 폴더명이 대괄호 네이밍인가만 차이가 있다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">디렉토리만 봤을 땐 페이지 라우팅 방식이 url path의 순서 상 더 직관적인 것 같고, 동적 세그먼트가 폴더 이름으로 오니까 디렉토리만 보면 앱 라우터 방식은 좀 헷갈려 보일 수도 있겠다. (내가 그렇다)</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">대괄호로 감싸게 되면 동적으로 계속 바뀌는 라우트를 갖게 된다는 의미를 갖는다. 이를 dynamic routing이라 한다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">대괄호로 안 하면 아래처럼 모든 id에 1대1로 대응하는 끔찍한 하드코딩을 해야 한다.</p>
<pre id="code_1722189156889" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// 앱 라우터 방식
<p>/app
/goods
/1
page.tsx
/2
page.tsx
/3
page.tsx
/...</p>
<p>// 페이지 라우터 방식</p>
<p>/pages
/goods
1.tsx
2.tsx
3.tsx
...</code></pre></p>
<h2 data-ke-size="size26">동적으로 바뀌는 세그먼트 받아 오는 두 가지 패턴</h2>
<h3 data-ke-size="size23">컴포넌트의 props로 전달된 params를 사용하는 패턴</h3>
<pre id="code_1722185969312" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>type Props = {
  params: {
    id: number;
  }
}
<p>export default function GoodsPage({params}: Props) {
return (
&lt;&gt;
&lt;div&gt;상품번호 {params.id}의 굿즈 상세페이지 입니다.&lt;/div&gt;
&lt;/&gt;
)
}</code></pre></p>
<h3 data-ke-size="size23">useParams 훅을 사용하는 패턴</h3>
<pre id="code_1722186646392" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>import { useParams } from 'next/navigation';
<p>export default function GoodsPage() {
const params = useParams();
const { id } = params;</p>
<p>return (
&lt;&gt;
&lt;div&gt;상품번호 {id}의 굿즈 상세페이지 입니다.&lt;/div&gt;
&lt;/&gt;
)
}</code></pre></p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">뭘 선택해야 하는지 어려울 수 있는데,</p>
<p data-ke-size="size16">실제 예시를 보여드리겠다. 뭐가 더 편한지 판가름 해보시길.</p>
<h2 data-ke-size="size26">두 패턴의 실제 예시</h2>
<p data-ke-size="size16">기본적으로 실제 페이지 컴포넌트에서는 다른 코드가 없고 컴포넌트를 호출하여 렌더링 하는 방식이다.</p>
<p data-ke-size="size16">문제는 이 페이지 컴포넌트에서 저 params가 필요하다기 보다 각 컴포넌트에서도 그 값을 받아야 하는 상황이다.</p>
<h3 data-ke-size="size23">useParams 훅 사용</h3>
<pre id="code_1722186974863" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// useParams 훅 사용
<p>'use client';</p>
<p>import BuddyTemperature from '@/components/atoms/profile/BuddyTemperature';
import MyTrips from '@/components/atoms/profile/MyTrips';
import BuddyFollow from '@/components/molecules/profile/BuddyFollow';
import BuddyProfile from '@/components/molecules/profile/BuddyProfile';
import { useParams } from 'next/navigation';</p>
<p>function ProfilePage() {
const params = useParams();
const { id } = params;</p>
<pre><code>return (
    &amp;lt;&amp;gt;
        &amp;lt;section&amp;gt;유저 아이디 {id}&amp;lt;/section&amp;gt;

        &amp;lt;section className=&quot;flex flex-col items-center justify-center w-full h-full&quot;&amp;gt;
            &amp;lt;BuddyProfile /&amp;gt;
        &amp;lt;/section&amp;gt;

        &amp;lt;section className=&quot;w-full h-full&quot;&amp;gt;
            &amp;lt;BuddyFollow /&amp;gt;
        &amp;lt;/section&amp;gt;

        &amp;lt;section&amp;gt;
            &amp;lt;BuddyTemperature /&amp;gt;
        &amp;lt;/section&amp;gt;

        &amp;lt;section className=&quot;mt-16 mx-8&quot;&amp;gt;
            &amp;lt;MyTrips /&amp;gt;
        &amp;lt;/section&amp;gt;
    &amp;lt;/&amp;gt;
);
</code></pre>
<p>}</p>
<p>export default ProfilePage;</code></pre></p>
<pre id="code_1722187059875" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// 하위 컴포넌트에서 한 번 더 호출

import { useParams } from 'next/navigation';

function BuddyProfile() {
    const params = useParams();
    const { id } = params;

    return &lt;div&gt;Buddy Profile for user {id}&lt;/div&gt;;
}

export default BuddyProfile;</code></pre>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li data-ke-style="style1">useParams 훅을 사용했다고 해서 하위 컴포넌트에서는 호출하지 않아도 되는 것이 아니다. 각 컴포넌트에서도 개별적으로 호출해주어야 한다.</li>
</ul>
<h3 data-ke-size="size23">Params Props 전달</h3>
<pre id="code_1722187113928" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// 파라미터 Props 전달 방식
<p>'use client';</p>
<p>import BuddyTemperature from '@/components/atoms/profile/BuddyTemperature';
import MyTrips from '@/components/atoms/profile/MyTrips';
import BuddyFollow from '@/components/molecules/profile/BuddyFollow';
import BuddyProfile from '@/components/molecules/profile/BuddyProfile';</p>
<p>type Props = {
params: {
id: number;
};
};</p>
<p>function ProfilePage({ params }: Props) {
return (
&lt;&gt;
&lt;section&gt;유저 아이디 {params.id}&lt;/section&gt;</p>
<pre><code>        &amp;lt;section className=&quot;flex flex-col items-center justify-center w-full h-full&quot;&amp;gt;
            &amp;lt;BuddyProfile id={params.id} /&amp;gt;
        &amp;lt;/section&amp;gt;

        &amp;lt;section className=&quot;w-full h-full&quot;&amp;gt;
            &amp;lt;BuddyFollow id={params.id} /&amp;gt;
        &amp;lt;/section&amp;gt;

        &amp;lt;section&amp;gt;
            &amp;lt;BuddyTemperature id={params.id} /&amp;gt;
        &amp;lt;/section&amp;gt;

        &amp;lt;section className=&quot;mt-16 mx-8&quot;&amp;gt;
            &amp;lt;MyTrips id={params.id} /&amp;gt;
        &amp;lt;/section&amp;gt;
    &amp;lt;/&amp;gt;
);
</code></pre>
<p>}</p>
<p>export default ProfilePage;</code></pre></p>
<p data-ke-size="size16">&nbsp;</p>
<pre id="code_1722187170916" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// 하위 컴포넌트에서는 Props를 받아야 함
<p>type BuddyProfileProps = {
id: number;
};</p>
<p>function BuddyProfile({ id }: BuddyProfileProps) {
return &lt;div&gt;Buddy Profile for user {id}&lt;/div&gt;;
}</p>
<p>export default BuddyProfile;</code></pre></p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>Props를 전달하는 경우에는 Props를 일일이 받아 주어야 한다.</li>
<li>위 예제에서는 하위 컴포넌트에서 Props의 type을 한 번 더 지정해주었지만, 더 좋은 예시는 types.ts 등의 파일에서 한 번에 타입을 정의하고, import 해서 사용하는 게 유지보수 측면에서도 유리하다.</li>
</ul>
<pre id="code_1722187540160" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// types.ts(자유작명, 팀 컨벤션)
<p>export type Params = {
id: number;
};</p>
<p>export type ProfilePageProps = {
params: Params;
};</p>
<p>export type BuddyProfileProps = {
id: number;
};</code></pre></p>
<pre id="code_1722187551601" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// ProfilePage.tsx
'use client';

import BuddyTemperature from '@/components/atoms/profile/BuddyTemperature';
import MyTrips from '@/components/atoms/profile/MyTrips';
import BuddyFollow from '@/components/molecules/profile/BuddyFollow';
import BuddyProfile from '@/components/molecules/profile/BuddyProfile';
import { ProfilePageProps } from '@/types'; // 타입을 import

function ProfilePage({ params }: ProfilePageProps) {
    return (
        &lt;&gt;
            &lt;section&gt;유저 아이디 {params.id}&lt;/section&gt;

            &lt;section className="flex flex-col items-center justify-center w-full h-full"&gt;
                &lt;BuddyProfile id={params.id} /&gt;
            &lt;/section&gt;

            &lt;section className="w-full h-full"&gt;
                &lt;BuddyFollow id={params.id} /&gt;
            &lt;/section&gt;

            &lt;section&gt;
                &lt;BuddyTemperature id={params.id} /&gt;
            &lt;/section&gt;

            &lt;section className="mt-16 mx-8"&gt;
                &lt;MyTrips id={params.id} /&gt;
            &lt;/section&gt;
        &lt;/&gt;
    );
}

export default ProfilePage;</code></pre>
<pre id="code_1722187558997" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// BuddyProfile.tsx
import { BuddyProfileProps } from '@/types'; // 타입을 import

function BuddyProfile({ id }: BuddyProfileProps) {
    return &lt;div&gt;Buddy Profile for user {id}&lt;/div&gt;;
}

export default BuddyProfile;</code></pre>
<h2 data-ke-size="size26">무엇을 써야 하나?</h2>
<p data-ke-size="size16">장단점이 있다.</p>
<p data-ke-size="size16">어차피 컴포넌트들에 접근해서 useParams 훅을 호출하든 props로 내리든 여러 번 작업해주어야 하는 건 같은데</p>
<p data-ke-size="size16">필자 생각에는 Props로 내리는 방식이 더 직관적이다.</p>
<p data-ke-size="size16">모든 컴포넌트가 해당 prams를 필요로 하면 상관 없겠지만, 어느 컴포넌트는 params가 필요하고 어느 컴포넌트는 단순 렌더링용으로 필요하지 않다고 하면 useRouter훅을 사용하면 페이지를 일일이 들어가 봐야만 어느 컴포넌트에서 params를 필요로 하는지 알 수 있는데, Props를 내리는 경우에는 페이지 컴포넌트 단에서 명확히 알 수 있다.</p>
<p data-ke-size="size16">다만 동적 라우팅이 한 개가 아니라 중첩된 동적 라우팅으로 여러 개의 Props를 내리는 경우 코드가 지저분해질 순 있겠다.</p>