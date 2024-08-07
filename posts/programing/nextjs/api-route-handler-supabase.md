<p data-ke-size="size16">8.7</p>
<h2 data-ke-size="size26">라우트 핸들러란?</h2>
<h2 data-ke-size="size26">라우트 핸들러가 왜 필요한가?</h2>
<h2 data-ke-size="size26">사용법</h2>
<h3 data-ke-size="size23">API 라우트 생성</h3>
<pre id="code_1722190703030" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>src
  app
    api
      route.ts</code></pre>
<p data-ke-size="size16">위와 같은 구조로 파일을 만들고 이름은 route.ts 또는 .js여야만 한다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">기본 사용법은 위와 같으나, 본인은 사용자 정보를 가져오는 동적 라우팅에서 사용할 동적인 라우트 핸들러를 만들어보겠다.</p>
<pre id="code_1722190825004" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>src
  app
    api
      users
        [id]
          route.ts</code></pre>
<pre id="code_1722190855168" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// app/api/users/[id]/route.ts
<p>import { NextResponse } from 'next/server';
import { supabase } from '@/lib/supabaseClient';</p>
<p>export async function GET(request, { params }) {
const { id } = params;</p>
<p>const { data, error } = await supabase
.from('users')
.select('*')
.eq('id', id)
.single();</p>
<p>if (error) {
return NextResponse.json({ error: error.message }, { status: 500 });
}</p>
<p>return NextResponse.json(data, { status: 200 });
}</code></pre></p>
<h3 data-ke-size="size23">클라이언트 컴포넌트에서 API 호출</h3>
<pre id="code_1722190894254" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>import BuddyTemperature from '@/components/atoms/profile/BuddyTemperature';
import MyTrips from '@/components/atoms/profile/MyTrips';
import BuddyFollow from '@/components/molecules/profile/BuddyFollow';
import BuddyProfile from '@/components/molecules/profile/BuddyProfile';
import { ProfilePageProps, BuddyProfileProps } from '@/types';
<p>async function fetchUser(id: string) {
const res = await fetch(<code>/api/users/${id}</code>);
if (!res.ok) {
throw new Error('Failed to fetch user');
}
return res.json();
}</p>
<p>export default async function ProfilePage({ params }: ProfilePageProps) {
const user = await fetchUser(params.id);</p>
<p>return (
&lt;&gt;
&lt;section&gt;유저 아이디 {params.id}&lt;/section&gt;
&lt;section className=&quot;flex flex-col items-center justify-center w-full h-full&quot;&gt;
&lt;BuddyProfile id={params.id} user={user} /&gt;
&lt;/section&gt;
&lt;section className=&quot;w-full h-full&quot;&gt;
&lt;BuddyFollow id={params.id} /&gt;
&lt;/section&gt;
&lt;section&gt;
&lt;BuddyTemperature id={params.id} /&gt;
&lt;/section&gt;
&lt;section className=&quot;mt-16 mx-8&quot;&gt;
&lt;MyTrips id={params.id} /&gt;
&lt;/section&gt;
&lt;/&gt;
);
}</code></pre></p>
<p data-ke-size="size16">페이지 컴포넌트(클라이언트 컴포넌트) 에서 페칭한 데이터를 하위 컴포넌트에서는 아래와 같이 사용하면 된다.</p>
<pre id="code_1722191125299" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// types.ts
<p>export type Params = {
id: string;
};</p>
<p>export type ProfilePageProps = {
params: Params;
};</p>
<p>export type BuddyProfileProps = {
id: string;
user: {
name: string;
email: string;
};
};</code></pre></p>
<pre id="code_1722191059116" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>import { BuddyProfileProps } from '@/types';

function BuddyProfile({ id, user }: BuddyProfileProps) {
  return (
    &lt;div&gt;
      &lt;h1&gt;Buddy Profile for user {id}&lt;/h1&gt;
      &lt;p&gt;Name: {user.name}&lt;/p&gt;
      &lt;p&gt;Email: {user.email}&lt;/p&gt;
    &lt;/div&gt;
  );
}

export default BuddyProfile;</code></pre>
<p data-ke-size="size16">&nbsp;</p>