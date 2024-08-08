<h2 data-ke-size="size26">API Route 정의</h2>
<pre id="code_1722317039784" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>import { createClient } from '@/utils/supabase/server';
import { NextRequest, NextResponse } from 'next/server';
<p>export async function POST(req: NextRequest) {
try {
const supabase = createClient();
const tripData = await req.json();</p>
<pre><code>    const { data: trip, error } = await supabase
        .from('trips')
        .insert(tripData)
        .select();

    // 데이터베이스 에러 처리
    if (error) {
        console.error('게시글 업데이트 중 오류 발생:', error);
        return NextResponse.json(
            { trip: null, error: error?.message },
            { status: 500 },
        );
    }

    // 성공 시 응답
    return NextResponse.json({ trip }, { status: 200 });
} catch (error) {
    // 일반 에러 처리
    console.error('게시글 업데이트 중 오류 발생:', error);
    return NextResponse.json(
        { trip: null, error: '서버 오류' },
        { status: 500 },
    );
}
</code></pre>
<p>}</code></pre></p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>supabaseClient를 사용하여 인스턴스를 생성함.
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>인스턴스는 함수 내에서 생성해야 함.</li>
</ul>
</li>
<li>req.json()을 사용하여 요청 분문에서 데이터를 파싱함.</li>
<li><span></span>Supabase <span>insert</span> 메서드를 사용하여 <span>trips</span> 테이블에 데이터를 삽입함.</li>
<li>삽입된 데이터를 응답으로 반환하거나 오류 메시지를 반환함.</li>
</ul>
<h2 data-ke-size="size26">클라이언트에서 수집한 데이터를 API 엔드포인트로 전송</h2>
<pre id="code_1722317159742" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>type TripData = Tables&lt;'trips'&gt;;
// 파셜트립데이터는 데이터 컬럼을 선택적으로 쓰겠다
type PartialTripData = Partial&lt;TripData&gt;;
<pre><code>const handleWriteTrip = async () =&amp;gt; {
    const tripData: PartialTripData = {
        trip_title: '테스트제목',
        trip_content: '테스트내용',
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

        if (!response.ok) {
            const errorResult = await response.json();
            console.error('게시글 업데이트 중 오류 발생:', errorResult);
            showAlert('error', '게시글 업데이트 실패');
        }
        const result = await response.json();
        if (result.trip) {
            showAlert('success', '게시글 업데이트 성공', {
                onConfirm: () =&amp;gt; {
                    router.push('/');
                },
            });
        } else {
            showAlert('error', '게시글 업데이트 실패');
        }
    } catch (error) {
        console.error('게시글 업데이트 중 오류 발생:', error);
    }
};&lt;/code&gt;&lt;/pre&gt;
</code></pre>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>tripData 객체를 생성하여 API 요청에 필요한 데이터를 포함함.</li>
<li>fetch 함수를 사용하여 /api/write 엔드포인트로 POST 요청을 보냄.</li>
<li>Content-Type 헤더를 application/json으로 설정하여 JSON 데이터를 전송할 것을 명시함.</li>
<li>요청 본문에 tripData를 JSON 문자열로 변환하여 포함시킴.</li>
<li>응답을 JSON으로 파싱하고 결과를 처리함.</li>
<li>성공 시 알림을 표시하고 홈 페이지로 리디렉션함.</li>
<li>실패 시 오류 알림을 표시함.</li>
</ul>
<p data-ke-size="size16">결론적으로는 hanldler 함수 하나에 try...catch문으로 에러 처리까지 해서 이벤트 핸들러에 연결하는 형태이다.</p>
<h2 data-ke-size="size26">자세히 알아보기</h2>
<h3 data-ke-size="size23">supabase 인스턴스 생성</h3>
<pre id="code_1722317326880" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>ㅇ</code></pre>
<h3 data-ke-size="size23">JSON 파싱</h3>
<pre id="code_1722317340546" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>const tripData = await req.json();</code></pre>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>tripData라는 변수는 클라이언트에서 직접 값을 상태로 받아 관리하고 있다.</li>
<li>이것을 await 키워드를 사용하여 비동기 함수로 req라는 JSON(자바스크립트 객체)로 파싱하여 tripData라는 변수에 초기화한다.</li>
<li>이걸 하는 이유는 내가 보내는 HTTP 요청의 Content-Type이 application/json이기 때문에 필요하다.</li>
</ul>
<p data-ke-size="size16">클라이언트에서 수행하는 fetch 함수의 내용을 보면 아래와 같이 구성되어 있다.</p>
<pre id="code_1722317530010" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>await fetch('/api/write', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify(tripData),
});</code></pre>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>/api/write라는 엔드포인트로 POST 요청을 보낸다.</li>
<li>이 POST 요청이 왔을 때 수행할 로직은 app/api/write 폴더에서 정의하고 있다.</li>
<li>fetch 함수 본문(body)에 tripData라는 JSON을 실어 보내고 있다.</li>
</ul>