<h2 data-ke-size="size26"><span style="font-family: AppleSDGothicNeo-Regular, 'Malgun Gothic', '맑은 고딕', dotum, 돋움, sans-serif;"><b>구현하고자 하는 기능</b></span></h2>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">파티를 삭제하면 다른 테이블에 참조되어 외래 키로 연결된 테이블의 정보까지 모두 삭제하고자 함.</p>
<p data-ke-size="size16">&nbsp;</p>
<h2 data-ke-size="size26"><b>현재 상황</b></h2>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">파티를 모집하고 있다. 파티 자체는 trips라는 테이블에서 관리하고 있다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">그리고 trips에 참가하는 인원이 생기면 contract라는 테이블에 차곡차곡 기록이 된다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">테이블 구성과 구현한 로직은 이렇다.</p>
<p data-ke-size="size16">&nbsp;</p>
<ol style="list-style-type: decimal;" data-ke-list-type="decimal">
<li>사용자가 파티를 개설하면 trips 테이블에서 trip_id가 자동으로 생성되며 여러 데이터가 쭉 컬럼에 입력되며 하나의 레코드를 만들어 낸다.</li>
<li>그리고 contract라는 테이블에 contract_id가 자동으로 생성되며 trips_trip_id에 아까 만들어진 trips 테이블의 trip_id와 외래 키로 묶이고, 이는 자바스크립트로 입력된다.</li>
<li>그리고 파티를 만든 사람은 리더이기 때문에 contract_buddy_id에 사용자 uuid가 기록 됨과 동시에 contract_isLeader라는 테이블에 불리언 값으로 true를 토글한다.</li>
<li>여기에서 다른 사용자들이 이 파티에 참여하는 버튼을 누르면 contract라는 테이블에서 trips_trip_id에 해당 trip_id가 외래 키로 잡히면서 자바스크립트 코드로 컬럼에 기록한다.</li>
<li>그리고 참가자의 정보는 contract_buddy_id에도 입력되며 contract_isLeader 테이블에는 false로 입력된다.</li>
</ol>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">자 그러면 장원영이 파티를 만들었고, 안유진, 가을, 레이, 이서, 리즈가 파티에 참여했다고 가정하자.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">그러면 테이블은 아래처럼 생성이 된다.</p>
<p data-ke-size="size16">&nbsp;</p>
<table style="border-collapse: collapse; width: 100%;" border="1" data-ke-align="alignLeft">
<tbody>
<tr>
<td><span><b>trip_id</b></span></td>
<td><span><b>trip_master_id</b></span></td>
</tr>
<tr>
<td><span>1234abcd-&hellip;</span></td>
<td><span><span>장원영의</span> UUID</span></td>
</tr>
</tbody>
</table>
<p data-ke-size="size16">&nbsp;</p>
<table style="border-collapse: collapse; width: 100%;" border="1" data-ke-align="alignLeft">
<tbody>
<tr>
<td><span><b>contract_id</b></span></td>
<td><span><b>contract_buddy_id</b></span></td>
<td><span><b>contract_trip_id</b></span></td>
<td><span><b>contract_isLeader</b></span></td>
</tr>
<tr>
<td><span>5678efgh-&hellip;</span></td>
<td><span><span>장원영의</span> UUID</span></td>
<td><span>1234abcd-&hellip;</span></td>
<td><span>true</span></td>
</tr>
<tr>
<td><span>1234ehfj-&hellip;</span></td>
<td><span><span>안유진의</span> UUID</span></td>
<td><span>1234abcd-&hellip;</span></td>
<td><span>false</span></td>
</tr>
<tr>
<td><span>djzj3123-&hellip;</span></td>
<td><span><span>가을의</span> UUID</span></td>
<td><span>1234abcd-&hellip;</span></td>
<td><span>false</span></td>
</tr>
<tr>
<td><span>sjdkjf23-&hellip;</span></td>
<td><span><span>레이의</span> UUID</span></td>
<td><span>1234abcd-&hellip;</span></td>
<td><span>false</span></td>
</tr>
<tr>
<td><span>34jf1kw-&hellip;</span></td>
<td><span><span>이서의</span> UUID</span></td>
<td><span>1234abcd-&hellip;</span></td>
<td><span>false</span></td>
</tr>
<tr>
<td><span>381jsda-&hellip;</span></td>
<td><span><span>리즈의</span> UUID</span></td>
<td><span>1234abcd-&hellip;</span></td>
<td><span>false</span></td>
</tr>
</tbody>
</table>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">이렇게 테이블을 구성하면 해당 파티에 대한 참가자가 누군지 별도로 파악할 수 있고 리더인지 아닌지 여부를 판단해서 사용자 강퇴 등의 기능도 추가할 수 있다.</p>
<p data-ke-size="size16">또한 추후 방장의 권한이 주어지는 인가 기능이 추가된다면 역시 자유롭게 구현이 가능하다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">물론 별도의 contract 테이블을 개설하지 않고 trips 테이블 하나로도 관리할 순 있다. 다만 참가 인원 수가 고정되어 있지 않고 몇 명이 될 지 모른다면</p>
<p data-ke-size="size16">json 형태로 컬럼에 데이터를 담아야 하는데, 만약 레이가 장원영의 파티에서 나가고 싶다고 가정한다면, trips 테이블의 모든 컬럼을 다 검사해서 trip_id를 찾아오고 그 레코드 안에서</p>
<p data-ke-size="size16">json 컬럼을 또 다 검사해야 한다. 단일 컬럼을 검사하는 것보다 json 컬럼을 검사하는 것이 비용이 크다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">그리고 결정적으로 구현이 어려울 것 같은 것이 있는데, 회원 탈퇴 기능이 있다고 가정 했을 때 해당 회원이 탈퇴하면 일반적으로 해당 회원의 데이터는 삭제하거나 파기해야 할 텐데, 그 회원이 참여한 모든 컬럼에서 json 컬럼을 다 검사해야 하기 때문에</p>
<p data-ke-size="size16">상상하기도 싫은 끔찍한 비용이 발생하고 타임아웃이 발생할 확률이 높다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">따라서 테이블 개수가 늘어나는 것에 두려워 말고, 관계형 데이터베이스의 이점을 십분 활용해서 데이터 베이스의 목적을 명확하게 나누어 설계하고 외래 키 설정을 방향까지 제대로 맞추어서 설계하는 것이 중요하다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">여기서 내가 구현하고자 하는 기능은 방장인 장원영이 해당 파티를 삭제하면 contract에서 이 trip_id와 외래 키로 묶여 있는 모든 사용자의 레코드가 케스케이드 되며 전부 삭제 되는 로직을 구현해보고자 한다.</p>
<p data-ke-size="size16">&nbsp;</p>
<h2 data-ke-size="size26"><b>구현 과정</b></h2>
<p data-ke-size="size16">&nbsp;</p>
<h3 data-ke-size="size23"><b>외래 키 설정</b></h3>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">먼저 다른 것들은 미리 선행되었다고 보고, 외래 키를 제대로 연결 했는지만 점검해본다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">외래 키는 contract 테이블에서 contract_trip_id 컬럼을 -&gt; trips 테이블의 trip_id를 향해 연결해야 한다.</p>
<p data-ke-size="size16">그리고 이 내용과는 별개지만 contract_buddy_id는 -&gt; users 테이블의 user_id를 향해 연결하면 된다.</p>
<p data-ke-size="size16">&nbsp;</p>
<h3 data-ke-size="size23"><b>API 라우트 DELETE 메서드 구성</b></h3>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">서버에서 DELETE 요청을 받았을 때 수행할 API 라우트를 구성해야 한다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">내가 생각한 의사 코드는 이러하다.</p>
<p data-ke-size="size16">&nbsp;</p>
<ol style="list-style-type: decimal;" data-ke-list-type="decimal">
<li>클라이언트에서 함수를 통해서 DELETE 메서드를 보내어 삭제 로직을 수행해달라는 요청을 보낸다.</li>
<li>일단 삭제하려는 파티가 존재하는지 확인한다.</li>
<li>그리고 그 요청을 보낸 사용자가 파티장이 맞는지 확인한다.</li>
<li>그리고 그 파티를 데이터 테이블에서 삭제한다.</li>
<li>파티에 contract (참가자 정보 다루는 테이블)이 외래 키로 cascade 설정이 걸려있기 때문에 파티가 삭제되면 나머지는 알아서 같이 삭제된다.</li>
</ol>
<pre id="code_1723487032304" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>export async function DELETE(
    req: NextRequest,
    { params }: { params: { id: string } },
) {
    const supabase = createClient();
<pre><code>try {
    // URL에서 tripId를 가져옴.
    const { id: tripId } = params;
    const token = req.headers.get('Authorization')?.replace('Bearer ', '');

    if (!tripId || !token) {
        return NextResponse.json(
            { error: 'tripId와 토큰이 필요합니다.' },
            { status: 400 },
        );
    }

    const buddyId = token;

    // Step 1: trips 테이블에서 tripId를 기반으로 여정 찾기
    const {
        data: tripData,
        error: tripError,
    }: { data: Trip | null; error: PostgrestError | null } = await supabase
        .from('trips')
        .select('*')
        .eq('trip_id', tripId)
        .single();

    if (tripError || !tripData) {
        console.error('여정 데이터 오류 발생:', tripError || '데이터 없음');
        return NextResponse.json(
            { error: '여정 정보를 불러오는 데 실패했습니다.' },
            { status: 404 },
        );
    }

    // Step 3: trip_master_id와 buddyId 비교
    if (tripData.trip_master_id !== buddyId) {
        return NextResponse.json(
            { error: '본인이 작성한 여정 모집이 아닙니다.' },
            { status: 403 },
        );
    }

    // Step 7: trips 테이블에서 해당 레코드 삭제
    // 이 단계에서 여정을 삭제하면 관련된 contract 레코드도 자동으로 삭제됨 (ON DELETE CASCADE가 설정된 경우)
    const { error: deleteTripError } = await supabase
        .from('trips')
        .delete()
        .eq('trip_id', tripId);

    if (deleteTripError) {
        console.error('여정 삭제 오류 발생:', deleteTripError);
        return NextResponse.json(
            { error: '여정 정보를 삭제하는 데 실패했습니다.' },
            { status: 500 },
        );
    }

    // 성공 응답 반환
    return NextResponse.json(
        { message: '여정이 삭제되었습니다.' },
        { status: 200 },
    );
} catch (err) {
    console.error('서버 내부 오류:', err);
    return NextResponse.json(
        { error: '서버 내부 오류가 발생했습니다.' },
        { status: 500 },
    );
}
</code></pre>
<p>}</code></pre></p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">다소 로직이 복잡한데, 하나씩 뜯어 먹어 보겠다.</p>
<p data-ke-size="size16">&nbsp;</p>
<pre id="code_1723487101748" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>export async function DELETE(
    req: NextRequest,
    { params }: { params: { id: string } },
) {
    const supabase = createClient();</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16"><b>export async function DELETE</b></p>
<p data-ke-size="size16">&nbsp;</p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>DELETE HTTP 요청에 대한 실행 함수를 작성하겠다는 의미.</li>
</ul>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16"><b>req: NextRequest</b></p>
<p data-ke-size="size16">&nbsp;</p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>매개 변수 중 첫번째 인자로 요청 객체들을 말한다.</li>
<li>요청 객체란, 함수 내부에서 params를 이용해서 url에서 id를 가져올 건데, 이게 요청 객체다.</li>
<li>이 요청 객체의 타입은 Next에서 이미 만들어 놨고 NextRequest라는 타입으로 지정해주면 된다.</li>
</ul>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16"><b>{ prarams } : { params : { id: string } }</b></p>
<p data-ke-size="size16">&nbsp;</p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>두번째 매개 변수로 지정된 이것은, 클라이언트에서 전달해 준 URL에서 전달된 파라미터를 추출해낸다는 의미이다.</li>
<li>여기서 id는 클라이언트에서 삭제할 파티의 id를 의미한다.</li>
<li>이따가 클라이언트 코드를 보면 이해가 쉬울 것이다.</li>
</ul>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16"><span>&nbsp; &nbsp; </span>try {</p>
<p data-ke-size="size16"><span>&nbsp; &nbsp; &nbsp; &nbsp; </span>// URL에서 tripId를 가져옴.</p>
<p data-ke-size="size16"><span>&nbsp; &nbsp; &nbsp; &nbsp; </span>const { id: tripId } = params;</p>
<p data-ke-size="size16"><span>&nbsp; &nbsp; &nbsp; &nbsp; </span>const token = req.headers.get('Authorization')?.replace('Bearer ', '');</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16"><b>try&hellip;catch</b></p>
<p data-ke-size="size16">&nbsp;</p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>어떠한 이유로든 데이터 통신은 항상 실패할 수 있다는 것을 생각해야 한다.</li>
<li>클라이언트에서 유효하지 않은 정보를 전달해주었든, 백엔드 서버의 상태가 좋지 않든, 사용자의 네트워크 연결 상태가 좋지 않든 여러 이유로 실패할 수 있다.</li>
<li>따라서 예외 처리를 위해 try&hellip;catch문을 사용한다.</li>
</ul>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16"><b>const { id: tripId } = params;</b></p>
<p data-ke-size="size16">&nbsp;</p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>URL에서 파티의 id를 추출해서 tripId라는 변수에 새로 초기화 하겠다는 의미이다</li>
</ul>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16"><b>const token = req.headers.get(&lsquo;Authorization&rsquo;)?.replace(&lsquo;Bearer &rsquo;, &lsquo;&rsquo;);</b></p>
<p data-ke-size="size16">&nbsp;</p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>클라이언트가 DELETE 요청을 보낼 때 헤더에 유저의 토큰을 담아 보낼 것이다.</li>
<li>그러면 그 헤더에서 사용자 인증 토큰을 가져온다.</li>
<li>이 토큰은 사용자의 신원을 확인하는 데 사용되고, 사용자의 UUID가 token이라는 변수에 새로이 담기게 된다.</li>
</ul>
<p data-ke-size="size16">&nbsp;</p>
<pre id="code_1723487118663" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>        if (!tripId || !token) {
            return NextResponse.json(
                { error: 'tripId와 토큰이 필요합니다.' },
                { status: 400 },
            );
        }</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>그래서 여기까지 진행되었을 때 tripId와 token이 모두 존재하는지 확인하는 로직이다.</li>
<li>|| or 논리 연산자는<span>&nbsp;</span></li>
</ul>
<p data-ke-size="size16">&nbsp;</p>
<pre id="code_1723487132230" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>        // Step 3: trip_master_id와 buddyId 비교
        if (tripData.trip_master_id !== buddyId) {
            return NextResponse.json(
                { error: '본인이 작성한 여정 모집이 아닙니다.' },
                { status: 403 },
            );
        }</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16"><b>if (tripData.trip._master_id !== buddyId)</b></p>
<p data-ke-size="size16">&nbsp;</p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>tripData는 클라이언트에서 URL 파라미터로 전달해 준 tripId를 trips 테이블에서 검사해서 찾아 온 레코드를 담은 반환값이다. 전체 코드를 보면 이름은 내가 바꾸었다.</li>
<li>여기서 trip_master_id의 컬럼이 클라이언트에서 헤더에 토큰을 실어 전달 해 준 buddyId와 일치하는지 검사한다.</li>
<li>검사에 실패하면 본인의 여정이 아니라는 에러와 함께 403 상태 코드를 반환한다.</li>
</ul>
<pre id="code_1723487145032" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>const { error: deleteTripError } = await supabase
            .from('trips')
            .delete()
            .eq('trip_id', tripId);
<pre><code>    if (deleteTripError) {
        console.error('여정 삭제 오류 발생:', deleteTripError);
        return NextResponse.json(
            { error: '여정 정보를 삭제하는 데 실패했습니다.' },
            { status: 500 },
        );
    }&lt;/code&gt;&lt;/pre&gt;
</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">여기까지 모든 유효성 검사를 통과했다면 trips 테이블에서 trip_id 컬럼이 클라이언트가 전달해 준 tripId와 일치하는 레코드를 찾아와서 delete 수파베이스 내장 메서드로 레코드를 삭제해버린다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">사실! trips 테이블에서 RLS 정책 설정을 할 때 DELETE 요청은 해당 컬럼의 주인이 아니면 못하게 해두었기 때문에 위 유효성 검사 자체가 없어도 된다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">하지만 명시적으로 유효성 검사를 하고, 각 상황에 맞는 다양한 에러를 반환해주는 API route를 구성하기 위해 했다고 보면 된다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16"><b>const { error: deleteTripError } = await supabase</b></p>
<p data-ke-size="size16">&nbsp;</p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>DELETE 요청이기에 성공 반환 값은 필요 없다. 실패했을 때 반환되는 error 객체만 deleteTripError라는 이름으로 바꿔서 받는다.</li>
<li>그리고 파티 삭제 중에 어떤 이유로든 에러가 발생하면, 즉 error 객체 반환값이 존재한다면 500 상태 코드와 함께 에러 메시지를 보내준다.</li>
</ul>
<pre id="code_1723487179963" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>        // 성공 응답 반환
        return NextResponse.json(
            { message: '여정이 삭제되었습니다.' },
            { status: 200 },
        );
    } catch (err) {
        console.error('서버 내부 오류:', err);
        return NextResponse.json(
            { error: '서버 내부 오류가 발생했습니다.' },
            { status: 500 },
        );
    }
}</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">마지막으로 파티가 삭제가 되면 사용자에게 알림을 주어야 하니 200 상태 코드와 함께 성공 메시지를 반환해준다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">그리고 catch문은 위 모든 사항에 해당하지 않는 에러가 발생했을 때 500 상태 코드와 함께 에러 메시지를 전달해주는 것으로 API route 세팅은 끝이 난다.</p>
<p data-ke-size="size16">&nbsp;</p>
<h3 data-ke-size="size23"><b>fetch 함수 작성</b></h3>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">API 라우트를 만들었으니 이제 이 API 라우트를 향해 DELETE 요청을 보내는 함수를 제작하면 된다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">클라이언트에서 바로 함수를 작성하고 사용하는 것이 일반적이겠지만,</p>
<p data-ke-size="size16">본인의 경우에는 팀 프로젝트이고 호출해야 하는 컴포넌트가 본인이 작성한 컴포넌트가 아니기에</p>
<p data-ke-size="size16">이곳에서 코드를 추가했을 때 충돌이 예상되기 때문에 별도 유틸 함수로 제작했다.</p>
<p data-ke-size="size16">&nbsp;</p>
<pre id="code_1723487211360" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>import { showAlert } from '../ui/openCustomAlert';
import { NextRouter } from 'next/router';
<p>export async function deleteTrip(
tripId: string,
token: string,
router: NextRouter,
): Promise&lt;void&gt; {
try {
const response = await fetch(<code>/api/contract/trip/${tripId}</code>, {
method: 'DELETE',
headers: {
Authorization: <code>Bearer ${token}</code>,
'Content-Type': 'application/json',
},
});</p>
<pre><code>    if (!response.ok) {
        const errorData = await response.json();
        throw new Error(errorData.error || '여정 삭제에 실패했습니다.');
    }

    const data = await response.json();
    console.log(data.message);
    showAlert('success', '여정이 삭제되었습니다.');
    router.push('/trips');
} catch (error: unknown) {
    showAlert(
        'error',
        (error as Error).message || '여정 삭제에 실패했습니다.',
    );
}
</code></pre>
<p>}</code></pre></p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">import문에서 showAlert은 커스텀 alert이다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">이 fetch 함수를 작성할 때 유의해야 할 점은, 함수 내부에서는 리액트 훅을 사용할 수 없다는 점이다.</p>
<p data-ke-size="size16">여기서 말하는 리액트 훅이란 useRouter를 말하는데,</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">보통 const router = useRouter(); 형태로 인스턴스를 생성해서 사용하는 이 훅은</p>
<p data-ke-size="size16">사용자를 어딘 가로 리다이렉트 시킬 때 사용하는 리액트 훅이다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">본인은 DELETE가 완료되고 나면 현재 페이지에 머무를 이유가 없으니 다른 페이지로 이동시키기 위해서 이 훅이 필요하다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">그런데 이것은 함수형 컴포넌트도 아니고, 커스텀 훅도 아닌 일반 유틸 함수이니 리액트 훅이 사용 불가능하다. 따라서 함수를 호출하는 클라이언트에서 대신 인스턴스를 생성하고 매개 변수로 이 페칭 함수에 전달만 해주는 것으로 해결을 했다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">router 역시 리액트에서 미리 준비한 NextRouter라는 타입을 지정해주어야 한다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16"><b>const response = await fetch(`/api/contract/trip/${tripId}`)</b></p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">아까 작성했던 API Router의 엔드포인트이다.</p>
<p data-ke-size="size16">이렇게 url 파라미터에 ${tripId} 처럼 서버로 전달하는 것을 URL 쿼리 파라미터로 데이터를 전달해준다고 아까 표현한 것이다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">이것을 서버에서 추출해 내려면 params가 필요하다는 이야기였다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">마지막의 tripId는 호출하는 컴포넌트에서 url 파라미터로 실어서 전달해줄 것이다.</p>
<h3 data-ke-size="size23"><b>함수</b> <b>호출하기</b></h3>
<pre id="code_1723487233511" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// useRouter 호출하기
const router = useRouter();
<p>// delete 함수 await로 풀어주는 핸들러 함수 정의하기
const handleDelete = async () =&gt; {
if (trip &amp;&amp; buddy) {
await deleteTrip(
trip.trip_id,
buddy.buddy_id,
router as unknown as NextRouter,
);
} else {
showAlert('error', '오류가 발생했습니다.');
}
};</p>
<p>// 이벤트 핸들러에 핸들러 연결하기
if (mode === '삭제하기') {
return handleDelete();
}</code></pre></p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">마지막에 이벤트 핸들러에 연결하는 것이 onClick이 아닌 이유는 팀 프로젝트에서 버튼에 함수를 내리는 방식이 위와 같기 때문이고 일반적인 상황은 아니니 return 문에서 버튼 등에 이벤트 핸들러로 핸들러 함수를 연결해주면 된다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">&nbsp;</p>