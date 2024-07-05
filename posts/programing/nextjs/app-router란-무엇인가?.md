<h2 data-ke-size="size26">App Router란?</h2>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>Next.js가 페이지 라우팅을 하는 방법.</li>
<li>Next.js 13버전 부터 기존의 Pages Router 방식에서 완전히 새로운 App Router 방식이 도입됨.</li>
<li>프로젝트 내부 app 폴더 내에서 새 디렉토리를 만들면 그것이 url 세그먼트가 됨.</li>
<li>App Router에서는 공통 레이아웃, 중첩 라우팅, 에러 처리 방법 등을 제공함.</li>
<li>만약 pages router와 app router를 한 프로젝트에서 혼용하는 경우 앱 라우터가 우선됨. 따라서 충돌이 발생할 수 있음.</li>
<li>개발자가 page.tsx 파일에서 "use client"를 최상단에서 명시하지 않으면 기본적으로 리액트 서버 컴포넌트로 동작함.</li>
<li>리액트만 배우고 온 경우에는 서버 컴포넌트 방식이 생소할 수 있어서 러닝 커브가 있을 수 있음.</li>
</ul>
<h2 data-ke-size="size26">폴더와 파일의 역할</h2>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1600" data-origin-height="594"><span data-url="https://blog.kakaocdn.net/dn/z6IjD/btsIn6jhOOV/BJ1ssPnpbgnwHFVKf6hHc1/img.png" data-phocus="https://blog.kakaocdn.net/dn/z6IjD/btsIn6jhOOV/BJ1ssPnpbgnwHFVKf6hHc1/img.png"><img src="https://blog.kakaocdn.net/dn/z6IjD/btsIn6jhOOV/BJ1ssPnpbgnwHFVKf6hHc1/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fz6IjD%2FbtsIn6jhOOV%2FBJ1ssPnpbgnwHFVKf6hHc1%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1600" data-origin-height="594"/></span></figure>
</p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>Next.js의 앱 라우터는 파일 시스템 기반의 라우팅 방식임.</li>
<li>이 말은 app 폴더 내에 폴더를 만들면 그것이 세그먼트가 되고, 그 폴더 안에 page.tsx를 만들면 그 세그먼트에 접속할 때 렌더링 할 페이지를 만든다는 의미임.</li>
<li>폴더를 계속 중첩해서 만들면 세그먼트가 계속해서 늘어나고, 최종적으로 리프 세그먼트 폴더(최종 경로, 더 이상 children이 없는 폴더)에 있는 파일을 렌더링 하게 됨.
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>예) app/singer/idol/ive/wonyoung/page.tsx</li>
</ul>
</li>
</ul>
<h2 data-ke-size="size26">컴포넌트의 계층 구조(특수 파일)</h2>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1600" data-origin-height="641"><span data-url="https://blog.kakaocdn.net/dn/y7MmK/btsInODbd9c/fL6DfQcWIf3NpVin3k4Yy0/img.png" data-phocus="https://blog.kakaocdn.net/dn/y7MmK/btsInODbd9c/fL6DfQcWIf3NpVin3k4Yy0/img.png"><img src="https://blog.kakaocdn.net/dn/y7MmK/btsInODbd9c/fL6DfQcWIf3NpVin3k4Yy0/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fy7MmK%2FbtsInODbd9c%2FfL6DfQcWIf3NpVin3k4Yy0%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1600" data-origin-height="641"/></span></figure>
</p>
<p data-ke-size="size16">위 파일들은 Next.js의 파일 구조를 다루는 포스트에서 다루었다.</p>
<p data-ke-size="size16">위 파일을 한 꺼번에 사용한다면 계층 구조는 오른쪽과 같다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1600" data-origin-height="863"><span data-url="https://blog.kakaocdn.net/dn/cz1Mkv/btsIpgZgVBf/qAJMoNdBGbNLfUg0GoWeA0/img.png" data-phocus="https://blog.kakaocdn.net/dn/cz1Mkv/btsIpgZgVBf/qAJMoNdBGbNLfUg0GoWeA0/img.png"><img src="https://blog.kakaocdn.net/dn/cz1Mkv/btsIpgZgVBf/qAJMoNdBGbNLfUg0GoWeA0/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fcz1Mkv%2FbtsIpgZgVBf%2FqAJMoNdBGbNLfUg0GoWeA0%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1600" data-origin-height="863"/></span></figure>
</p>
<p data-ke-size="size16">폴더를 중첩해서 만들 때에는, 완전히 새로운 파일들을 만드는 것이 아니라 그 폴더의 계층 구조에 따라서 종속된다.</p>
<h2 data-ke-size="size26">Colocation(특수 폴더)</h2>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1600" data-origin-height="1011"><span data-url="https://blog.kakaocdn.net/dn/qWeiv/btsIo9FVN4j/OxoKpfk1ot8Bn4KIIKWWOk/img.png" data-phocus="https://blog.kakaocdn.net/dn/qWeiv/btsIo9FVN4j/OxoKpfk1ot8Bn4KIIKWWOk/img.png"><img src="https://blog.kakaocdn.net/dn/qWeiv/btsIo9FVN4j/OxoKpfk1ot8Bn4KIIKWWOk/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FqWeiv%2FbtsIo9FVN4j%2FOxoKpfk1ot8Bn4KIIKWWOk%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1600" data-origin-height="1011"/></span></figure>
</p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>정확한 명칭은 Co-location인데, 쉽게 이야기해서 코로케이션이란 관심사 별로 비슷한 파일들을 한 군데에 그룹핑해서 모아두는 것을 의미함.</li>
<li>Next.js에서는 컴포넌트, 스타일링 파일, 테스트 파일 등을 폴더를 만들어서 모아둘 수 있음.</li>
<li>여기에 사용되는 폴더의 이름도 저 위의 특수 파일 처럼 특수 폴더라고 이해하면 됨.</li>
<li>이것을 특수 폴더라고 하는 이유가, app 폴더 내부에 폴더를 만들면 자동으로 url 세그먼트를 얻고 라우팅이 되지만, 위 특수 폴더들은 라우팅이 될 수도 안 될 수도 있음.
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>components
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>이 폴더는 라우팅이 안 됨.</li>
<li>페이지를 모아두는 폴더가 아니라 컴포넌트들을 모아두는 폴더임.</li>
<li>여기서 컴포넌트를 모아서 작성하고, 페이지 말고 컴포넌트에서 import해서 사용하면 됨.</li>
</ul>
</li>
<li>lib
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>이 폴더는 라우팅이 안 됨.</li>
<li>라이브러리 파일을 모아두는 폴더.</li>
<li>이곳에 라이브러리를 모아두고, 페이지 말고 컴포넌트에서 import해서 사용하면 됨.</li>
</ul>
</li>
<li>dashboard
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>이 폴더에는 두 가지 파일이 오는데, 파일에 따라 라우팅 여부가 갈림.&nbsp;
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>page.ts
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>이 파일은 라우팅이 됨.</li>
<li>/dashboard로 접근 가능.</li>
</ul>
</li>
<li>nav.ts
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>이 파일은 라우팅이 안 됨.</li>
<li>내비게이션 컴포넌트 파일이고, 다른 페이지나 컴포넌트에서 import해서 사용하면 됨.</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
<li>api
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>이 폴더에는 두 가지 파일이 오는데, 파일에 따라 라우팅 여부가 갈림.
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>route.ts
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>이 파일은 라우팅이 됨.</li>
<li>/api로 접근 가능.</li>
<li>API 엔드포인트 파일임.</li>
</ul>
</li>
<li>db.ts
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>이 파일은 라우팅이 안 됨.</li>
<li>데이터베이스 관련 유틸리티 파일임.</li>
<li>위 route.ts, 즉 API 엔드포인트 파일에서 import해서 사용하면 됨.</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
</ul>
<h2 data-ke-size="size26">고급 라우팅 기술 가능</h2>
<p data-ke-size="size16">Next.js의 App Router를 이용하면 Parallel Routes(병렬 라우트), Intercepting Routes(가로채기 라우트)가 가능하다. 이는 나중에 자세히 다룬다.</p>
<p data-ke-size="size16">패러렐 라우츠는 한 페이지에서 두 개 이상의 페이지를 보여주는 기술. 예를 들어 라이브러리의 기술 문서 등을 보면 왼쪽에 사이드 내비게이션 메뉴가 있고, 오른쪽에는 body를 보여주는 것.</p>
<p data-ke-size="size16">인터셉팅 라우츠는 현재 페이지의 컨텍스트를 유지하면서 이 페이지 안에 다른 페이지를 표시하는 기능임. 예를 들어 소셜미디어에서 글을 보다가 글 리스트에서 수정 버튼을 누르면 글 수정 페이지로 넘어가는 것이 아니라 모달로 뜨면서 배경에 현재 보고 있는 페이지의 맥락을 유지시키면서 글 수정 페이지를 모달로 띄우는 것.</p>