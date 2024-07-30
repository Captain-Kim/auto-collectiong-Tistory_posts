<h2 data-ke-size="size26">상황</h2>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>페이지 컴포넌트에서 자식 컴포넌트를 호출해서 시퀀스의 이동에 따라 페이지를 이동시키는 듯한 효과를 보여주는 Funnel Pattern으로 디자인하였다.</li>
<li>글쓰기 페이지이기 때문에 자식 컴포넌트들에서 사용자와의 인터렉션이 계속 발생하는 컴포넌트들이고, 사용자에게 입력 받은 값을 마지막 step에서 값을 서버에 전송해야 하는 로직으로 작성되어 있다.</li>
<li>자식 컴포넌트에서 입력한 값을 부모 컴포넌트가 참조하는 방법으로 전역 상태로 관리하는 방법이 가장 먼저 떠오르지만, 이건 개인 프로젝트가 아니라 팀 프로젝트이기 때문에 대부분의 컴포넌트가 재사용이 가능하도록 작성하였고, 실제로 검색 페이지에서 이 컴포넌트들을 사용하고 있다.</li>
<li>그렇다면 글쓰기 페이지에서 이 컴포넌트를 사용해서 사용자에게 값을 입력 받고 이어서 글쓰기 페이지로 이동하면 사용자는 글쓰기 페이지 방문이 처음임에도 전역 상태의 영향을 받아 옵션이 이미 선택된 것처럼 보이게 될 것으로 예상된다.</li>
<li>그러면 글쓰기 페이지와 검색 페이지에서 store를 다르게 만들어 관리하는 방법이 있겠는데, 완전히 다른 페이지와 서로 전역 상태를 참조해야 하는 상황도 아니고, 페이지 컴포넌트와 자식 컴포넌트 간에서 1~2개 정도의 depth로 상태를 공유받으면 되는 것이기 때문에 오히려 Props로 전달하는 방법이 더 명확할 것이라고 판단했다.</li>
<li>그렇게 대부분의 컴포넌트는 커스텀 훅으로 작성해서 state와 컴포넌트를 return하고, 그 커스텀 훅을 호출하는 페이지 컴포넌트에서는 그 값들을 꺼내어 자식 컴포넌트에 Props를 전달하는 방식으로 Funnel Pattern을 완성하였다.</li>
<li><b>그런데&nbsp;</b>다른 곳들은 잘 작동하는데 '글 제목'과 '글 내용', 즉 사용자에게 input을 통해 입력 받을 때 사용자가 한 글자를 입력할 때마다 포커스를 잃는 문제가 발생했다.</li>
</ul>
<pre id="code_1722325463339" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// 페이지 컴포넌트
// 이해를 돕기 위해 전체 코드 올림
<p>'use client';</p>
<p>import ProgressIndicator from '@/components/atoms/write/ProgressIndicator';
import CompletePage from '@/components/organisms/write/CompletePage';
import SelectAdditionalBuddyThemes from '@/components/organisms/write/SelectAdditionalBuddyThemes';
import SelectRegionPage from '@/components/organisms/write/SelectRegionPage';
import SelectTripThemesPage from '@/components/organisms/write/SelectTripThemesPage';
import SelectDatePage from '@/components/organisms/write/SelectDatePage';
import WelcomePage from '@/components/organisms/write/WelcomePage';
import useNextButton from '@/hooks/useFunnelNextStep';
import React from 'react';
import { useAuth } from '@/hooks/auth';
import useSelectBuddyCounts from '@/hooks/useSelectBuddyCounts';
import useCalendar from '@/hooks/useCalendar';
import useSelectRegion from '@/hooks/useSelectRegion';
import usePreferTheme from '@/hooks/usePreferTheme';
import { Tables } from '@/types/supabase';
import { showAlert } from '@/utils/ui/openCustomAlert';
import { useRouter } from 'next/navigation';
import useTripWrite from '@/hooks/MyPage/useTripWrite';
import WriteTrip from '@/components/organisms/write/WriteTrip';</p>
<p>const WritePage: React.FC = () =&gt; {
const router = useRouter();
const { NextButton, step } = useNextButton({
buttonText: '다음',
limit: 6,
});
const { buddy } = useAuth();
const { buddyCounts, SelectBuddyCounts } = useSelectBuddyCounts();
const { SelectCalendar, startDateTimestamp, endDateTimestamp } =
useCalendar();
const {
SelectRegion,
firstLevelLocation,
secondLevelLocation,
thirdLevelLocation,
} = useSelectRegion({ pxHeight: 30 });
const [PreferTripThemesToRender, selectedTripThemes] = usePreferTheme({
mode: 'trip',
});
const [PreferThemeToRender, selectedBuddyThemes] = usePreferTheme({
mode: 'buddy',
});
const {
tripTitle,
tripContent,
tripImage,
handleTitleChange,
handleContentChange,
} = useTripWrite();</p>
<pre><code>type TripData = Tables&amp;lt;'trips'&amp;gt;;
// 파셜트립데이터는 데이터 컬럼을 선택적으로 쓰겠다
type PartialTripData = Partial&amp;lt;TripData&amp;gt;;

const handleWriteTrip = async () =&amp;gt; {
    const tripData: PartialTripData = {
        trip_title: tripTitle,
        trip_content: tripContent,
        trip_thumbnail: tripImage,
        trip_master_id: buddy?.buddy_id ?? '',
        trip_max_buddies_counts: buddyCounts,
        trip_bookmarks_counts: buddyCounts,
        trip_start_date: startDateTimestamp,
        trip_end_date: endDateTimestamp,
        trip_final_destination: [
            secondLevelLocation ?? '',
            thirdLevelLocation ?? '',
        ].join(', '),
        trip_theme1: selectedTripThemes[0],
        trip_theme2: selectedTripThemes[1],
        trip_theme3: selectedTripThemes[2],
        trip_wanted_buddies1: selectedBuddyThemes[0],
        trip_wanted_buddies2: selectedBuddyThemes[1],
        trip_wanted_buddies3: selectedBuddyThemes[2],
    };
    try {
        const response = await fetch('/api/write', {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json',
            },
            body: JSON.stringify(tripData),
        });

        // const result = await response.json();
        if (response.ok) {
            showAlert('success', '게시글 업데이트 성공', {
                onConfirm: () =&amp;gt; {
                    router.push('/');
                },
            });
        } else {
            const errorResult = await response.json();
            console.error('게시글 업데이트 중 오류 발생:', errorResult);
            showAlert('error', '게시글 업데이트 실패');
        }
    } catch (error) {
        console.error('게시글 업데이트 중 오류 발생:', error);
    }
};

return (
    &amp;lt;&amp;gt;
        {/* &amp;lt;div className=&quot;mt-4 xl:mt-20 ml-5 xl:ml-64&quot;&amp;gt; */}
        &amp;lt;ProgressIndicator step={step} counts={7} /&amp;gt;
        {/* &amp;lt;/div&amp;gt; */}
        &amp;lt;section className=&quot;h-dvh flex flex-col&quot;&amp;gt;
            &amp;lt;div className=&quot;flex flex-col&quot;&amp;gt;
                {step === 0 &amp;amp;&amp;amp; (
                    &amp;lt;WelcomePage SelectBuddyCounts={SelectBuddyCounts} /&amp;gt;
                )}
                {step === 1 &amp;amp;&amp;amp; (
                    &amp;lt;SelectRegionPage
                        SelectRegion={SelectRegion}
                        pxHeight={60}
                    /&amp;gt;
                )}
                {step === 2 &amp;amp;&amp;amp; (
                    &amp;lt;SelectDatePage
                        startDateTimestamp={startDateTimestamp}
                        endDateTimestamp={endDateTimestamp}
                        SelectCalendar={SelectCalendar}
                    /&amp;gt;
                )}
                {step === 3 &amp;amp;&amp;amp; (
                    &amp;lt;SelectTripThemesPage
                        PreferThemeToRender={PreferTripThemesToRender}
                    /&amp;gt;
                )}
                {step === 4 &amp;amp;&amp;amp; (
                    &amp;lt;SelectAdditionalBuddyThemes
                        PreferThemeToRender={PreferThemeToRender}
                    /&amp;gt;
                )}
                {step === 5 &amp;amp;&amp;amp; (
                    &amp;lt;WriteTrip
                        tripTitle={tripTitle}
                        tripContent={tripContent}
                        handleTitleChange={handleTitleChange}
                        handleContentChange={handleContentChange}
                    /&amp;gt;
                )}
                {step === 6 &amp;amp;&amp;amp; &amp;lt;CompletePage /&amp;gt;}
            &amp;lt;/div&amp;gt;
            &amp;lt;div className=&quot;flex justify-center&quot;&amp;gt;
                &amp;lt;NextButton
                    className=&quot;text-2xl bg-main-color font-bold py-2 px-4 mt-4 rounded w-full&quot;
                    onClick={step === 5 ? handleWriteTrip : undefined}
                /&amp;gt;
            &amp;lt;/div&amp;gt;
        &amp;lt;/section&amp;gt;
    &amp;lt;/&amp;gt;
);
</code></pre>
<p>};</p>
<p>export default WritePage;</code></pre></p>
<h2 data-ke-size="size26">문제점</h2>
<p data-ke-size="size16">&nbsp;</p>
<h2 data-ke-size="size26">해결방법</h2>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>커스텀 훅에서 컴포넌트를 정의하고 해당 커스텀 훅과 컴포넌트를 return 하는 패턴으로 내내 커스텀 훅을 작성하였는데</li>
<li>공유용은 아니고 글쓰기 페이지의 state 값이 필요하여 혼자 사용할 커스텀 훅으로 변경하여 제작하였더니</li>
<li>return한 컴포넌트 내부의 입력필드 (제목, 글내용)에서 한 글자를 칠 때마다 포커스를 잃는 기괴한 현상 발생</li>
<li><b>문제의 원인은</b> 커스텀 훅 내부에서 컴포넌트를 정의하였기 때문. 훅 내부에 컴포넌트를 정의하면 컴포넌트가 리렌더링 될 때마다 컴포넌트의 인스턴스가 새롭게 생성됨. 이것 때문에 한 글자를 칠 때마다 -&gt; setState에 의해 컴포넌트 리렌더링이 발생하고 -&gt; 컴포넌트의 인스턴스가 새롭게 생성되면서 -&gt; 이 컴포넌트의 모든 DOM 요소들이 새롭게 생성됨 -&gt; 입력필드 또한 DOM 요소이므로 포커스를 잃게 됨</li>
<li><b>해결한 방법은</b> 커스텀 훅을 정의할 때 컴포넌트를 훅 외부에서 별도로 정의해서 컴포넌트가 재정의되는 것을 방지함.
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>훅에서는, state와 handler만 return. 컴포넌트는 별도로 작성</li>
<li>컴포넌트에서는, 커스텀 훅을 호출해서 state와 handler를 props로 받아서 사용</li>
</ul>
</li>
<li>시도해보진 않았지만 컴포넌트에서 state와 handler를 다 정의하면 편하지 않느냐? -&gt; 자식 컴포넌트에서 부모 컴포넌트로 props를 올리는 행위는 패륜이기 때문에 시도해보지 않음</li>
</ul>
<pre class="javascript"><code>// 커스텀 훅
'use client';
<p>import React, { useState } from 'react';</p>
<p>function useTripWrite() {
const [tripTitle, setTripTitle] = useState('');
const [tripContent, setTripContent] = useState('');
const [tripImage, setTripImage] = useState('');</p>
<pre><code>const handleTitleChange = (e: React.ChangeEvent&amp;lt;HTMLInputElement&amp;gt;) =&amp;gt; {
    setTripTitle(e.target.value);
};
const handleContentChange = (e: React.ChangeEvent&amp;lt;HTMLTextAreaElement&amp;gt;) =&amp;gt; {
    setTripContent(e.target.value);
};

return {
    tripTitle,
    tripContent,
    tripImage,
    handleTitleChange,
    handleContentChange,
};
</code></pre>
<p>}</p>
<p>export default useTripWrite;</code></pre></p>
<pre class="django"><code>// 컴포넌트
'use client';

import React from 'react';
import Left2xlBoldText from '@/components/atoms/write/Left2xlText';

const WriteTrip: React.FC&lt;{
    tripTitle: string;
    tripContent: string;
    handleTitleChange: (e: React.ChangeEvent&lt;HTMLInputElement&gt;) =&gt; void;
    handleContentChange: (e: React.ChangeEvent&lt;HTMLTextAreaElement&gt;) =&gt; void;
}&gt; = ({ tripTitle, tripContent, handleTitleChange, handleContentChange }) =&gt; {
    return (
        &lt;div className="p-4"&gt;
            &lt;header className="mb-5"&gt;
                &lt;Left2xlBoldText text="모집 글을 작성해봐요!" /&gt;
            &lt;/header&gt;

            &lt;form className="space-y-4"&gt;
                &lt;div&gt;
                    &lt;label className="block mb-1 text-sm font-medium text-gray-700"&gt;
                        대표 이미지
                    &lt;/label&gt;
                    &lt;button className="flex items-center justify-center w-20 h-20 bg-gray-200 border border-gray-300 rounded"&gt;
                        &lt;span className="text-gray-400"&gt; &lt;/span&gt;
                    &lt;/button&gt;
                &lt;/div&gt;
                &lt;div&gt;
                    &lt;label className="block mb-1 text-sm font-medium text-gray-700"&gt;
                        제목
                    &lt;/label&gt;
                    &lt;input
                        type="text"
                        value={tripTitle}
                        onChange={handleTitleChange}
                        placeholder="제목"
                        maxLength={20}
                        className="w-full px-3 py-2 border border-gray-300 rounded"
                    /&gt;
                    &lt;span className="block text-right text-sm text-gray-500"&gt;{`${tripTitle.length}/20`}&lt;/span&gt;
                &lt;/div&gt;
                &lt;div&gt;
                    &lt;label className="block mb-1 text-sm font-medium text-gray-700"&gt;
                        글 내용
                    &lt;/label&gt;
                    &lt;textarea
                        value={tripContent}
                        onChange={handleContentChange}
                        placeholder="내용을 입력해주세요."
                        className="w-full h-96 px-3 py-2 border border-gray-300 rounded resize-none"
                    /&gt;
                &lt;/div&gt;
            &lt;/form&gt;
        &lt;/div&gt;
    );
};

export default WriteTrip;</code></pre>
<pre class="pf"><code>// 페이지 컴포넌트에서 컴포넌트를 호출할 때
// 커스텀 훅을 먼저 호출해서 state 등을 꺼내온 후
// 호출한 state, 함수는 전부 컴포넌트에 Props로 내려주어야 함
&lt;WriteTrip
    tripTitle={tripTitle}
    tripContent={tripContent}
    handleTitleChange={handleTitleChange}
    handleContentChange={handleContentChange}
/&gt;</code></pre>