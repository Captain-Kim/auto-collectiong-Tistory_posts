<h2 data-ke-size="size26">문제 상황</h2>
<p data-ke-size="size16">사용자의 프로필 카드를 만들었다.</p>
<p data-ke-size="size16">그리고 그 프로필 카드 우측 상단에 하트를 만들었고, 하트를 클릭하면 팔로우가 되도록 하였다.</p>
<p data-ke-size="size16">follow API route가 다른 곳에서도 재사용되고 있는데 optimistic하게 보여줄 수 없는 페이지도 있어서</p>
<p data-ke-size="size16">optimistic update는 아니고,&nbsp;</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">기대하는 상황은 하트를 누르면 사용자의 프로필로 넘어가는 것이 아니라 (프로필은 카드 자체를 누르면 넘어가게 링크되어 있다.)</p>
<p data-ke-size="size16">팔로우 기능만 작동하기를 바란다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">그런데 팔로우 기능만 작동하는 것이 아니라 팔로우 버튼이 눌림과 동시에 카드 자체도 눌려진다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">버튼 위에 버튼이 있는 형상이다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">즉 자식 요소의 클릭 이벤트가 부모 요소의 클릭 이벤트까지 전파가 되었다는 것을 의미하고,</p>
<p data-ke-size="size16">이를 이벤트 버블링이라 한다. 마치 거품이 아래에서부터 보글보글 위로 솟아나는 모습을 생각하면 이해가 쉬울 것이다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">아래 첨부한 영상은 개발 서버라 끔찍하게 느리다. 잘못 만든 것 아니니 참고바람.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="410" data-origin-height="564"><span data-url="https://blog.kakaocdn.net/dn/52NX1/btsI5iws0PN/1pRkOVKYeugwZgMGLUL2R0/img.gif" data-phocus="https://blog.kakaocdn.net/dn/52NX1/btsI5iws0PN/1pRkOVKYeugwZgMGLUL2R0/img.gif"><img src="https://blog.kakaocdn.net/dn/52NX1/btsI5iws0PN/1pRkOVKYeugwZgMGLUL2R0/img.gif" srcset="https://blog.kakaocdn.net/dn/52NX1/btsI5iws0PN/1pRkOVKYeugwZgMGLUL2R0/img.gif" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="410" data-origin-height="564"/></span></figure>
</p>
<p data-ke-size="size16">&nbsp;</p>
<h2 data-ke-size="size26">문제의 코드</h2>
<p data-ke-size="size16">보기 편하도록 일부러 컴포넌트 분리를 하지 않은 상태임을 감안하고 보시기 바람.</p>
<pre id="code_1723737066003" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>import BuddyTemperature from '@/components/atoms/profile/BuddyTemperature';
import Image from 'next/image';
import Link from 'next/link';
import { Buddy } from '@/types/Auth.types';
import MascotImage from '@/components/atoms/common/MascotImage';
import { getAgeFromBirthDate } from '@/utils/common/getAgeFromBirthDate';
import React, { useState, useEffect } from 'react';
import { useAuth } from '@/hooks';
<p>function HomePageRecommendBuddiesList({
buddies,
className,
}: {
buddies: Buddy[];
className?: string;
}) {
const { buddy: currentBuddy } = useAuth();
return (
&lt;&gt;
{buddies
? buddies.map((buddy: Buddy, index: number) =&gt; (
&lt;Link
key={index}
href={<code>/profile/${buddy.buddy_id}</code>}
passHref
&gt;
&lt;div
className={<code>relative min-w-[200px] h-[75px] mx-1 rounded border border-gray-200 cursor-pointer flex items-center ${className}</code>}
&gt;
&lt;div className=&quot;flex items-center justify-center w-full h-full relative&quot;&gt;
&lt;div className=&quot;flex-shrink-0 w-[75px] h-[75px] flex items-center justify-center&quot;&gt;
{buddy.buddy_profile_pic ? (
&lt;Image
src={buddy.buddy_profile_pic}
alt=&quot;profile&quot;
width={60}
height={60}
className=&quot;rounded-lg w-[60px] h-[60px]&quot;
/&gt;
) : (
&lt;MascotImage intent=&quot;happy&quot; /&gt;
)}
&lt;/div&gt;
&lt;div className=&quot;mx-1 flex flex-col w-full relative&quot;&gt;
&lt;span className=&quot;text-xs font-bold text-gray-500 whitespace-nowrap overflow-hidden text-ellipsis&quot;&gt;
{buddy.buddy_preferred_buddy1 &amp;&amp;
buddy.buddy_preferred_buddy2
? <code>#${buddy.buddy_preferred_buddy1} #${buddy.buddy_preferred_buddy2}</code>
: '#태그없음'}
&lt;/span&gt;
&lt;div className=&quot;text-m font-bold whitespace-nowrap overflow-hidden text-ellipsis w-full&quot;&gt;
&lt;span className=&quot;block truncate&quot;&gt;
{buddy.buddy_nickname}
{typeof buddy.buddy_birth ===
'string'
? <code> / ${getAgeFromBirthDate(                                                         buddy.buddy_birth,                                                     )} 세</code>
: null}
&lt;/span&gt;
&lt;/div&gt;</p>
<pre><code>                                  &amp;lt;div className=&quot;w-full flex justify-between items-center&quot;&amp;gt;
                                      &amp;lt;BuddyTemperature
                                          isLabel={false}
                                          isTempText={false}
                                          temperature={
                                              buddy.buddy_temperature
                                          }
                                      /&amp;gt;
                                  &amp;lt;/div&amp;gt;
                              &amp;lt;/div&amp;gt;
                          &amp;lt;/div&amp;gt;

                          &amp;lt;FollowButton
                              followingId={buddy.buddy_id}
                              followerId={currentBuddy?.buddy_id || ''}
                          /&amp;gt;
                      &amp;lt;/div&amp;gt;
                  &amp;lt;/Link&amp;gt;
              ))
            : null}
    &amp;lt;/&amp;gt;
);
</code></pre>
<p>}</p>
<p>function FollowButton({
followingId,
followerId,
}: {
followingId: string;
followerId: string;
}) {
const [isFollowing, setIsFollowing] = useState(false);</p>
<pre><code>useEffect(() =&amp;gt; {
    // 기존 팔로우 여부 검사
    const checkFollowStatus: () =&amp;gt; Promise&amp;lt;void&amp;gt; = async () =&amp;gt; {
        const res = await fetch(
            `/api/buddyProfile/follow?followingId=${followingId}&amp;amp;followerId=${followerId}`,
        );
        const data = await res.json();
        setIsFollowing(data.originFollow.length &amp;gt; 0);
    };

    checkFollowStatus();
}, [followingId, followerId]);

const handleFollowToggle = async () =&amp;gt; {
    if (isFollowing) {
        await fetch(
            `/api/buddyProfile/follow?followingId=${followingId}&amp;amp;followerId=${followerId}`,
            { method: 'DELETE' },
        );
    } else {
        await fetch(`/api/buddyProfile/follow`, {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify({
                followingId,
                followerId,
            }),
        });
    }

    setIsFollowing(!isFollowing);
};

return (
    &amp;lt;button
        className=&quot;absolute top-0 right-0 text-xl&quot;
        onClick={handleFollowToggle}
    &amp;gt;
        &amp;lt;span className={isFollowing ? 'text-main-color' : ''}&amp;gt;
            {isFollowing ? '&amp;hearts;' : '♡'}
        &amp;lt;/span&amp;gt;
    &amp;lt;/button&amp;gt;
);
</code></pre>
<p>}</p>
<p>export default HomePageRecommendBuddiesList;</code></pre></p>
<p data-ke-size="size16">&nbsp;</p>
<h2 data-ke-size="size26">문제의 원인</h2>
<p data-ke-size="size16">&lt;Link&gt; 컴포넌트 안에 클릭 이벤트가 발생할 수 있는 &lt;button&gt; 태그를 넣었기 때문에 이런 현상이 발생했다.</p>
<p data-ke-size="size16">&lt;button&gt; 태그 뿐만 아니라 &lt;a&gt; 태그 역시 이런 현상이 발생할 것이다.</p>
<p data-ke-size="size16">그렇다면 해결 방법은 보이는 것 같다.</p>
<p data-ke-size="size16">&lt;Link&gt; 컴포넌트, 즉 부모 요소를 클릭 이벤트가 발생하는 컴포넌트나 태그가 아니라</p>
<p data-ke-size="size16">그 자체로는 클릭 이벤트를 지원하지 않는 일반 &lt;div&gt; 태그로 변경하고,</p>
<p data-ke-size="size16">클릭을 했을 때 별도의 이벤트가 발생하도록 onClick 이벤트 핸들러로 함수를 연결하면 된다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">Next.js에서는 &lt;Link&gt; 컴포넌트와 사실상 같은 방법이 next/navigation에서 제공하는 useRouter 훅의 router.push('/') 기능이다.</p>
<p data-ke-size="size16">이것을 이용해서 이동만을 지원하는 함수를 만들고 연결하면 해결이 된다.</p>
<h2 data-ke-size="size26">해결</h2>
<pre id="code_1723738044409" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>import BuddyTemperature from '@/components/atoms/profile/BuddyTemperature';
import Image from 'next/image';
import { Buddy } from '@/types/Auth.types';
import MascotImage from '@/components/atoms/common/MascotImage';
import { getAgeFromBirthDate } from '@/utils/common/getAgeFromBirthDate';
import React, { useState, useEffect } from 'react';
import { useAuth } from '@/hooks';
import { useRouter } from 'next/navigation';
<p>function HomePageRecommendBuddiesList({
buddies,
className,
}: {
buddies: Buddy[];
className?: string;
}) {
const { buddy: currentBuddy } = useAuth();
const router = useRouter();</p>
<pre><code>const handleCardClick = (buddyId: string) =&amp;gt; {
    router.push(`/profile/${buddyId}`);
};

return (
    &amp;lt;&amp;gt;
        {buddies
            ? buddies.map((buddy: Buddy, index: number) =&amp;gt; (
                  &amp;lt;div
                      key={index}
                      className={`relative min-w-[200px] h-[75px] mx-1 rounded border border-gray-200 cursor-pointer flex items-center ${className}`}
                      onClick={() =&amp;gt; handleCardClick(buddy.buddy_id)}
                  &amp;gt;
                      &amp;lt;div className=&quot;flex items-center justify-center w-full h-full relative&quot;&amp;gt;
                          &amp;lt;div className=&quot;flex-shrink-0 w-[75px] h-[75px] flex items-center justify-center&quot;&amp;gt;
                              {buddy.buddy_profile_pic ? (
                                  &amp;lt;Image
                                      src={buddy.buddy_profile_pic}
                                      alt=&quot;profile&quot;
                                      width={60}
                                      height={60}
                                      className=&quot;rounded-lg w-[60px] h-[60px]&quot;
                                  /&amp;gt;
                              ) : (
                                  &amp;lt;MascotImage intent=&quot;happy&quot; /&amp;gt;
                              )}
                          &amp;lt;/div&amp;gt;
                          &amp;lt;div className=&quot;mx-1 flex flex-col w-full relative&quot;&amp;gt;
                              &amp;lt;span className=&quot;text-xs font-bold text-gray-500 whitespace-nowrap overflow-hidden text-ellipsis&quot;&amp;gt;
                                  {buddy.buddy_preferred_buddy1 &amp;amp;&amp;amp;
                                  buddy.buddy_preferred_buddy2
                                      ? `#${buddy.buddy_preferred_buddy1} #${buddy.buddy_preferred_buddy2}`
                                      : '#태그없음'}
                              &amp;lt;/span&amp;gt;
                              &amp;lt;div className=&quot;text-m font-bold whitespace-nowrap overflow-hidden text-ellipsis w-full&quot;&amp;gt;
                                  &amp;lt;span className=&quot;block truncate&quot;&amp;gt;
                                      {buddy.buddy_nickname}
                                      {typeof buddy.buddy_birth ===
                                      'string'
                                          ? ` / ${getAgeFromBirthDate(
                                                buddy.buddy_birth,
                                            )} 세`
                                          : null}
                                  &amp;lt;/span&amp;gt;
                              &amp;lt;/div&amp;gt;

                              &amp;lt;div className=&quot;w-full flex justify-between items-center&quot;&amp;gt;
                                  &amp;lt;BuddyTemperature
                                      isLabel={false}
                                      isTempText={false}
                                      temperature={
                                          buddy.buddy_temperature
                                      }
                                  /&amp;gt;
                              &amp;lt;/div&amp;gt;
                          &amp;lt;/div&amp;gt;
                      &amp;lt;/div&amp;gt;

                      &amp;lt;FollowButton
                          followingId={buddy.buddy_id}
                          followerId={currentBuddy?.buddy_id || ''}
                          onClick={(e) =&amp;gt; e.stopPropagation()} // 추가: 하트 버튼에서 이벤트 전파 중단
                      /&amp;gt;
                  &amp;lt;/div&amp;gt;
              ))
            : null}
    &amp;lt;/&amp;gt;
);
</code></pre>
<p>}</p>
<p>function FollowButton({
followingId,
followerId,
onClick,
}: {
followingId: string;
followerId: string;
onClick: (e: React.MouseEvent&lt;HTMLButtonElement&gt;) =&gt; void; // 추가: onClick 이벤트 전달
}) {
const [isFollowing, setIsFollowing] = useState(false);</p>
<pre><code>useEffect(() =&amp;gt; {
    // 기존 팔로우 여부 검사
    const checkFollowStatus: () =&amp;gt; Promise&amp;lt;void&amp;gt; = async () =&amp;gt; {
        const res = await fetch(
            `/api/buddyProfile/follow?followingId=${followingId}&amp;amp;followerId=${followerId}`,
        );
        const data = await res.json();
        setIsFollowing(data.originFollow.length &amp;gt; 0);
    };

    checkFollowStatus();
}, [followingId, followerId]);

const handleFollowToggle = async (
    e: React.MouseEvent&amp;lt;HTMLButtonElement&amp;gt;,
) =&amp;gt; {
    onClick(e); // 추가: onClick 이벤트 실행
    if (isFollowing) {
        await fetch(
            `/api/buddyProfile/follow?followingId=${followingId}&amp;amp;followerId=${followerId}`,
            { method: 'DELETE' },
        );
    } else {
        await fetch(`/api/buddyProfile/follow`, {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify({
                followingId,
                followerId,
            }),
        });
    }

    setIsFollowing(!isFollowing);
};

return (
    &amp;lt;button
        className=&quot;absolute top-0 right-0 text-xl&quot;
        onClick={handleFollowToggle}
    &amp;gt;
        &amp;lt;span className={isFollowing ? 'text-main-color' : ''}&amp;gt;
            {isFollowing ? '&amp;hearts;' : '♡'}
        &amp;lt;/span&amp;gt;
    &amp;lt;/button&amp;gt;
);
</code></pre>
<p>}</p>
<p>export default HomePageRecommendBuddiesList;</code></pre></p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">결과는? 아주 마음에 든다. 흡족하다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="394" data-origin-height="566"><span data-url="https://blog.kakaocdn.net/dn/3Q3fX/btsI6uvV0Y4/BLDBZy2okEPw1mOjkjd2o0/img.gif" data-phocus="https://blog.kakaocdn.net/dn/3Q3fX/btsI6uvV0Y4/BLDBZy2okEPw1mOjkjd2o0/img.gif"><img src="https://blog.kakaocdn.net/dn/3Q3fX/btsI6uvV0Y4/BLDBZy2okEPw1mOjkjd2o0/img.gif" srcset="https://blog.kakaocdn.net/dn/3Q3fX/btsI6uvV0Y4/BLDBZy2okEPw1mOjkjd2o0/img.gif" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="394" data-origin-height="566"/></span></figure>
</p>