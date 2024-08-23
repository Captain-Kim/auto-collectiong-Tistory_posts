<p data-ke-size="size16">이것이 무슨 말이냐?</p>
<p data-ke-size="size16">상황을 보면 이해될 것이다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">코드를 작성하다 보니 이런 케이스가 발생했다.</p>
<p data-ke-size="size16">&nbsp;</p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>다른 커스텀 훅을 통해 유저의 아이디만 추출한다.</li>
<li>추출한 아이디로 API 라우트에 쿼리 매개 변수에 실어 GET 요청을 보낸다.</li>
</ul>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">이거 두 개를 하고 싶었을 뿐인데,</p>
<p data-ke-size="size16">문제는 유저의 아이디만 추출해올 때</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">undefined가 찍혔다가 데이터가 불러와져서 그 사이에 비동기 함수인 GET 요청이 쿼리 매개 변수에 아무 값이 없는 상태로 넘어가게 되는 것이다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">그러니 계속 400 상태 코드와 함께 에러를 뿜어 낸다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">TanStack Query로 상태 관리 중이라면 아주 간단하게 해결할 수 있다.</p>
<p data-ke-size="size16">&nbsp;</p>
<h2 data-ke-size="size26">문제의 코드</h2>
<pre id="code_1723809176878" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>const { data: clickedBuddy, isLoading, error } = useBuddyProfile(params.id);
const { data: followList } = useFollowCountQuery(
    clickedBuddy?.buddy_id || '',
);</code></pre>
<p data-ke-size="size16">useBuddyProfile이라는 커스텀 훅에서 clickedBuddy라는 객체를 꺼내 와 그 중에서도 buddy_id를 꺼내온 뒤</p>
<p data-ke-size="size16">그것을 useFollowCountQuery라는 TanStack Query 커스텀 훅으로 인자로 전달하고자 했던 것이다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">그러면 useFollowCountQuery 훅에서는 인자로 받은 uuid를 다시 페칭 함수로 넘긴다.</p>
<pre id="code_1723809329169" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>import { useQuery } from '@tanstack/react-query';
import { QUERY_KEY_FOLLOW_COUNT } from '@/constants/query.constants';
import { fetchFollowData } from '@/api-services/auth/client';
import { Follow } from '@/types/Follow.types';
<p>export function useFollowCountQuery(
clickedBuddyId: string,
) {
return useQuery&lt;Follow[] | null, Error&gt;({
queryKey: [QUERY_KEY_FOLLOW_COUNT],
queryFn: () =&gt; fetchFollowData(clickedBuddyId),
staleTime: 0,
});
}</code></pre></p>
<p data-ke-size="size16">그러면 이 string 값을 받아 fetch 함수로 넘기게 되고, fetch 함수에서는 이 아이디를 쿼리 매개 변수 자리에 쏙 넣어서 GET 요청을 수행한다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">그런데 혹시 staleTime이 0이면 캐싱을 하지 않는다는 의미인데 그러면 TanStack Query를 왜 쓰느냐?</p>
<p data-ke-size="size16">TanStack Query로 데이터를 관리하는 것에는 캐싱 말고도 여러가지 이점이 있다.</p>
<p data-ke-size="size16">&nbsp;</p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>나는 이 fetch 함수를 이곳에서만 사용하는 게 아니라 세 군데에서 사용한다. 따라서 재사용을 계속 해야 하는데, 어차피 fetch 함수를 유틸 함수로 작성해서 재사용 할 거라면, 조금 더 공수를 들여 TanStack Query로 관리하는 게 불러올 때 더 편하다.</li>
<li>위는 너무 단순한 이유고, TanStack Query는 Automatic Refetching 기능을 제공한다. 창이 다시 포커싱 되거나, 네트워크 상태가 변하면 자동으로 리페칭 해주기 때문에 데이터가 변질되지 않게 도와준다.</li>
<li>그리고 내가 이번에 TanStack Query 중 이 기능 때문에 반드시 써야만 하는 상황이 됐는데 바로 Dependency Management 기능이다. 즉 의존성 관리를 해주기 때문에 특정 조건이 충족할 때 페칭하는 로직을 구현할 수 있다. 물론 내장 fetch 함수와 바닐라 자바스크립트 만으로도 조건문으로 구현 가능할 지는 모르겠지만, TanStack Query에서는 매우 간단하게 구현이 가능하다. 이따가 방법을 자세하게 알아 보겠다.</li>
<li> Pending(Loading) and Error Handling. TanStack Query 훅을 호출할 때 { data, isPending, error } = use...() 이렇게 꺼내오는 것이 일반적인 패턴이라는 것을 알 것이다. isPending(isLoading으로 써도 되나 공식문서에서 pending으로 바꾸길 권장함) 즉 내가 별도로 loading state를 만들지 않아도 알아서 관리해준 다는 게 정말 편하다는 것이다. error도 마찬가지인데 Next.js로 넘어 오면서는 API Route Handler로 서버를 직접 구축하다 보니 큰 이점은 못 느끼긴 했다.</li>
</ul>
<pre id="code_1723809762959" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>export async function fetchFollowData(
    clickedBuddyId: string,
): Promise&lt;Follow[]&gt; {
    const url = `/api/buddyProfile/follow/followList?current_buddy_id=${clickedBuddyId}`;
    try {
        const res = await fetch(url);
        const data = await res.json();
<pre><code>    if (res.ok) {
        return data.originFollow as Follow[];
    } else {
        console.error(data.message);
        return [];
    }
} catch (error) {
    console.error(
        '팔로잉 데이터를 가져오는 중 오류가 발생했습니다:',
        error,
    );
    return [];
}
</code></pre>
<p>}</code></pre></p>
<p data-ke-size="size16">위와 같이 페칭을 전달하고</p>
<pre id="code_1723811828223" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>import { createClient } from '@/utils/supabase/server';
import { NextRequest, NextResponse } from 'next/server';
<p>export async function GET(req: NextRequest) {
const { searchParams } = new URL(req.url);
const currentBuddyId = searchParams.get('current_buddy_id');</p>
<pre><code>if (!currentBuddyId) {
    return NextResponse.json(
        { message: '조회하려는 버디 id가 조회되지 않았습니다.' },
        {
            status: 400,
        },
    );
}

const supabase = createClient();

try {
    const { data: originFollow, error } = await supabase
        .from('follow')
        .select('*')
        .or(
            `follow_following_id.eq.${currentBuddyId},follow_follower_id.eq.${currentBuddyId}`,
        );

    if (error) {
        return NextResponse.json(
            { message: '팔로잉 데이터를 불러올 수 없습니다.' },
            {
                status: 500,
            },
        );
    }

    // 명시적으로 빈 배열 반환
    if (!originFollow || originFollow.length === 0) {
        return NextResponse.json({ originFollow: [] }, { status: 200 });
    }

    return NextResponse.json({ originFollow }, { status: 200 });
} catch (error) {
    return NextResponse.json(
        { message: '팔로잉 데이터를 불러올 수 없습니다.' },
        {
            status: 500,
        },
    );
}
</code></pre>
<p>}</code></pre></p>
<p data-ke-size="size16">API Route에서는 위와 같이 서버 로직을 구성해서 supabase로 요청을 전달했다.</p>
<h2 data-ke-size="size26">해결방법</h2>
<p data-ke-size="size16">위에서 말했던 dependency management 측면에서 조건부로 쿼리가 실행되도록 설정할 수 있다.</p>
<p data-ke-size="size16">즉, 쿼리를 보내긴 보낼 건데 내가 하라고 할 때 하라는 명령을 내릴 수 있다는 것이다.</p>
<h3 data-ke-size="size23">query 수정</h3>
<pre id="code_1723812048773" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>export function useFollowCountQuery(
    clickedBuddyId: string,
    enabled: boolean = true,
) {
    return useQuery&lt;Follow[] | null, Error&gt;({
        queryKey: [QUERY_KEY_FOLLOW_COUNT],
        queryFn: () =&gt; fetchFollowData(clickedBuddyId),
        staleTime: 0,
        enabled,
    });
}</code></pre>
<p data-ke-size="size16">ena bled라는 옵션이 추가되었고, 값을 직접 입력하진 않았고 props로 받을 것인데 기본값은 true로 설정했다.</p>
<p data-ke-size="size16">즉 이 쿼리는 사용자가 enabled를 false로 토글해주지 않으면 호출했다고 해서 실행되지 않는다는 의미이다.</p>
<h3 data-ke-size="size23">클라이언트 코드 수정</h3>
<pre id="code_1723812177235" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>const [readyToFetch, setReadyToFetch] = useState&lt;boolean&gt;(false);
<p>useEffect(() =&gt; {
if (clickedBuddy?.buddy_id) {
setReadyToFetch(true);
}
}, [clickedBuddy?.buddy_id]);</p>
<pre><code>const { data: followList } = useFollowCountQuery(
    clickedBuddy?.buddy_id || '',
    readyToFetch,
);

// ... 이하 생략&lt;/code&gt;&lt;/pre&gt;
</code></pre>
<p data-ke-size="size16">readyToFecth나 뭐 마음대로 작명을 해서 불린 값을 담아준다.</p>
<p data-ke-size="size16">initialState는 false이다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">그리고 내가 페칭을 허락하는 순간은,</p>
<p data-ke-size="size16">clickedBuddy.buddy_id의 값이  truthy할 때, 즉 값이 undefined가 아니라, 제대로 생겼을 때 true로 토글해준다.</p>
<p data-ke-size="size16">이 값은 다른 state가 변경될 때마다 리렌더링 될 필요 없고, 유저의 UUID에 변화가 있을 때만 재실행하면 되니, useEffect 훅으로 생애 주기에 맞춰 관리하고 의존성 배열도 구성해준다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">이러면 끝이다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">유저의 uuid가 준비되어야만 페칭이 이루어지기 때문에 내가 의도한 대로, undefined 일 때 페칭이 안 가게 할 수 있다.</p>
<h2 data-ke-size="size26">추가 개선</h2>
<p data-ke-size="size16">글을 다 쓰고 나서 의도치 않은 상황이 발생하여 약간 개선을 했다.</p>
<p data-ke-size="size16">역시나 여기서만 이렇게 사용되면 문제가 없건만, 다른 곳에서 재사용을 하려니 또 다른 케이스가 발견되었다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">위 상황에서는 enabled를 클라이언트가 직접 통제해줄 수 있는 상황인데,</p>
<p data-ke-size="size16">다른 컴포넌트에서 useFollowCountQuery라는 쿼리가 품고 있는 쿼리 키를 invalidate만 시켜야 할 때,</p>
<p data-ke-size="size16">저렇게 true, false를 토글하기가 여간 번거로운 일이 아니다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">그냥 커스텀 훅 내부에서 전달받은 인자의 값이 존재할 때만 쿼리를 실행하게 하면 되지 않을까? 라는 생각으로 리팩토링 해보았고 아주 흡족하게 작동한다.</p>
<pre id="code_1723815323307" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// before
<p>import { useQuery } from '@tanstack/react-query';
import { QUERY_KEY_FOLLOW_COUNT } from '@/constants/query.constants';
import { fetchFollowData } from '@/api-services/auth/client';
import { Follow } from '@/types/Follow.types';</p>
<p>export function useFollowCountQuery(
clickedBuddyId: string,
enabled: boolean = true,
) {
return useQuery&lt;Follow[] | null, Error&gt;({
queryKey: [QUERY_KEY_FOLLOW_COUNT],
queryFn: () =&gt; fetchFollowData(clickedBuddyId),
staleTime: 0,
enabled,
});
}</p>
<p>// after</p>
<p>import { useState, useEffect } from 'react';
import { useQuery } from '@tanstack/react-query';
import { QUERY_KEY_FOLLOW_COUNT } from '@/constants/query.constants';
import { fetchFollowData } from '@/api-services/auth/client';
import { Follow } from '@/types/Follow.types';</p>
<p>export function useFollowCountQuery(clickedBuddyId: string) {
const [enabled, setEnabled] = useState&lt;boolean&gt;(false);</p>
<pre><code>useEffect(() =&amp;gt; {
    if (clickedBuddyId) {
        setEnabled(true);
    }
}, [clickedBuddyId]);

return useQuery&amp;lt;Follow[] | null, Error&amp;gt;({
    queryKey: [QUERY_KEY_FOLLOW_COUNT, clickedBuddyId],
    queryFn: () =&amp;gt; fetchFollowData(clickedBuddyId),
    staleTime: 0,
    enabled,
});
</code></pre>
<p>}</code></pre></p>
<p data-ke-size="size16">이렇게 개선하면 굳이 props로 상태를 전달받지 않아도 알아서 조건문에 의해 값이 truthy한지 판단한 후 불린 값을 토글하기 때문에 편한다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">뭐하려고 하다가 그런 거냐면,</p>
<pre id="code_1723815513173" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>showAlert('success', '팔로우가 취소되었습니다.');
            setIsFollowing(false);
            queryClient.invalidateQueries({
                queryKey: [QUERY_KEY_FOLLOW_COUNT, currentBuddyId],
            });</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">follow, unfollow 함수 종료 후 쿼리 키를 invalidate시켜 데이터를 최신화 하려고 보니, 훅에서 enabled 옵션의 기본값이 true여서 작동을 안 하길래 리팩토링을 하게 되었다.</p>