<p data-ke-size="size16">페이지 라우터든 앱 라우터든 Next.js에서 프로젝트를 생성하고 나면 Next.js에서 기본적으로 작성해 놓은 페이지가 보이게 된다. 이것들을 먼저 제거해주는 것부터 시작해서 페이지 라우터 방식에서는 프로젝트 초기 세팅을 어떻게 하는지 살펴보겠다.</p>
<h2 data-ke-size="size26">index.tsx 내용 제거</h2>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="2264" data-origin-height="1342"><span data-url="https://blog.kakaocdn.net/dn/bSRu3P/btsJgzsdSuD/WG5f5PusTqYemFtXZmGpN1/img.png" data-phocus="https://blog.kakaocdn.net/dn/bSRu3P/btsJgzsdSuD/WG5f5PusTqYemFtXZmGpN1/img.png"><img src="https://blog.kakaocdn.net/dn/bSRu3P/btsJgzsdSuD/WG5f5PusTqYemFtXZmGpN1/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbSRu3P%2FbtsJgzsdSuD%2FWG5f5PusTqYemFtXZmGpN1%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="2264" data-origin-height="1342"/></span></figure>
</p>
<p data-ke-size="size16">dev 명령어로 개발 서버를 실행시켜 보면 이러한 페이지가 나온다. 내가 만든 페이지가 아니므로 index.tsx 파일에서 제거해주겠다. 아래 사진에서는 import문을 지우지 않았는데 import문과 inter까지 전부 지워주면 된다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1016" data-origin-height="700"><span data-url="https://blog.kakaocdn.net/dn/beFPnl/btsJhEe3NYf/t8ZygBvKxhBPERvnJkmuk1/img.png" data-phocus="https://blog.kakaocdn.net/dn/beFPnl/btsJhEe3NYf/t8ZygBvKxhBPERvnJkmuk1/img.png"><img src="https://blog.kakaocdn.net/dn/beFPnl/btsJhEe3NYf/t8ZygBvKxhBPERvnJkmuk1/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbeFPnl%2FbtsJhEe3NYf%2Ft8ZygBvKxhBPERvnJkmuk1%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1016" data-origin-height="700"/></span></figure>
</p>
<p data-ke-size="size16">그러면 이렇게 된다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="990" data-origin-height="446"><span data-url="https://blog.kakaocdn.net/dn/bubJjb/btsJgQmMQEt/w4b0gwqWVIFdtg5Is3E2qK/img.png" data-phocus="https://blog.kakaocdn.net/dn/bubJjb/btsJgQmMQEt/w4b0gwqWVIFdtg5Is3E2qK/img.png"><img src="https://blog.kakaocdn.net/dn/bubJjb/btsJgQmMQEt/w4b0gwqWVIFdtg5Is3E2qK/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbubJjb%2FbtsJgQmMQEt%2Fw4b0gwqWVIFdtg5Is3E2qK%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="990" data-origin-height="446"/></span></figure>
</p>
<h2 data-ke-size="size26">global.css 제거</h2>
<p data-ke-size="size16">배경에 깔린 이상한 줄무늬가 맘에 들지 않는다. 이런 전역 스타일을 제거해준다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="934" data-origin-height="372"><span data-url="https://blog.kakaocdn.net/dn/EjpA2/btsJgwI9odm/TiCwUT4pZNtbgobjqUtKm0/img.png" data-phocus="https://blog.kakaocdn.net/dn/EjpA2/btsJgwI9odm/TiCwUT4pZNtbgobjqUtKm0/img.png"><img src="https://blog.kakaocdn.net/dn/EjpA2/btsJgwI9odm/TiCwUT4pZNtbgobjqUtKm0/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FEjpA2%2FbtsJgwI9odm%2FTiCwUT4pZNtbgobjqUtKm0%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="934" data-origin-height="372"/></span></figure>
</p>
<p data-ke-size="size16">그러면 이렇게 된다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="878" data-origin-height="392"><span data-url="https://blog.kakaocdn.net/dn/Y4xJZ/btsJhP8stqx/lCRptfBAQMNtyFFVrHEEN1/img.png" data-phocus="https://blog.kakaocdn.net/dn/Y4xJZ/btsJhP8stqx/lCRptfBAQMNtyFFVrHEEN1/img.png"><img src="https://blog.kakaocdn.net/dn/Y4xJZ/btsJhP8stqx/lCRptfBAQMNtyFFVrHEEN1/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FY4xJZ%2FbtsJhP8stqx%2FlCRptfBAQMNtyFFVrHEEN1%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="878" data-origin-height="392"/></span></figure>
</p>
<h2 data-ke-size="size26">새로운 라우트(페이지) 만들기</h2>
<p data-ke-size="size16">페이지 라우터 방식에서는 기본적으로 파일 이름을 기반으로 라우트가 생성된다. 그러나 폴더 이름으로 만들어도 된다. 그래서 여러가지 방법이 존재할 수 있는데, 라우팅을 중첩해서 타고 타고 들어가는 라우트를 만들려면 폴더를 만들어서 관리하면 된다. 그 모든 방법을 한 번 소개해보겠다.</p>
<h3 data-ke-size="size23">기본방식 : 파일 이름으로 라우트 만들기</h3>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1736" data-origin-height="580"><span data-url="https://blog.kakaocdn.net/dn/HQTM3/btsJhRFcedN/5bG80b1Prx2TsANnksnHkk/img.png" data-phocus="https://blog.kakaocdn.net/dn/HQTM3/btsJhRFcedN/5bG80b1Prx2TsANnksnHkk/img.png"><img src="https://blog.kakaocdn.net/dn/HQTM3/btsJhRFcedN/5bG80b1Prx2TsANnksnHkk/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FHQTM3%2FbtsJhRFcedN%2F5bG80b1Prx2TsANnksnHkk%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1736" data-origin-height="580"/></span></figure>
</p>
<p data-ke-size="size16">이렇게 mypage.tsx라는 파일을 만들었다. 그러면 /mypage 라는 경로로 접속했을 때 h1 태그로 My Page라는 텍스트가 보여야 한다. 진짜로 그런지 한 번 개벌 서버에서 접속해보겠다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="714" data-origin-height="246"><span data-url="https://blog.kakaocdn.net/dn/8HT6G/btsJg5KXmxO/ExLqFMtU5Q6uZs5WWP7Zc0/img.png" data-phocus="https://blog.kakaocdn.net/dn/8HT6G/btsJg5KXmxO/ExLqFMtU5Q6uZs5WWP7Zc0/img.png"><img src="https://blog.kakaocdn.net/dn/8HT6G/btsJg5KXmxO/ExLqFMtU5Q6uZs5WWP7Zc0/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F8HT6G%2FbtsJg5KXmxO%2FExLqFMtU5Q6uZs5WWP7Zc0%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="714" data-origin-height="246"/></span></figure>
</p>
<h3 data-ke-size="size23">폴더 이름으로 라우트 만들기</h3>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1728" data-origin-height="622"><span data-url="https://blog.kakaocdn.net/dn/cURI3N/btsJgBXUiXz/KFrkRjAkYcI2tA4jffimp1/img.png" data-phocus="https://blog.kakaocdn.net/dn/cURI3N/btsJgBXUiXz/KFrkRjAkYcI2tA4jffimp1/img.png"><img src="https://blog.kakaocdn.net/dn/cURI3N/btsJgBXUiXz/KFrkRjAkYcI2tA4jffimp1/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcURI3N%2FbtsJgBXUiXz%2FKFrkRjAkYcI2tA4jffimp1%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1728" data-origin-height="622"/></span></figure>
</p>
<p data-ke-size="size16">mypage라는 폴더를 만들고 mypage.tsx가 아니라 index.tsx로 만들면 src/pages/mypage.tsx를 만든 것과 동일하게 라우트가 만들어진다.</p>
<h3 data-ke-size="size23">폴더 이름으로 중첩 라우팅</h3>
<p data-ke-size="size16">만약 여기서 mypage/setting까지 만들려면 어떻게 해야 할까?</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1498" data-origin-height="684"><span data-url="https://blog.kakaocdn.net/dn/uYApI/btsJhEMUo4A/prfWMK1pSjNzdkCEg6f1k0/img.png" data-phocus="https://blog.kakaocdn.net/dn/uYApI/btsJhEMUo4A/prfWMK1pSjNzdkCEg6f1k0/img.png"><img src="https://blog.kakaocdn.net/dn/uYApI/btsJhEMUo4A/prfWMK1pSjNzdkCEg6f1k0/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FuYApI%2FbtsJhEMUo4A%2FprfWMK1pSjNzdkCEg6f1k0%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1498" data-origin-height="684"/></span></figure>
</p>
<p data-ke-size="size16">mypage/index.tsx는 /mypage로 접속했을 때 보여지는 페이지로 두고, mypage/setting.tsx를 만들면 /mypage/setting 으로 접속했을 때 보여지는 페이지로 만들 수 있다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1498" data-origin-height="684"><span data-url="https://blog.kakaocdn.net/dn/9ubAm/btsJhPm4SQ5/TBEqVpiFrLtubGTAbb3qwK/img.png" data-phocus="https://blog.kakaocdn.net/dn/9ubAm/btsJhPm4SQ5/TBEqVpiFrLtubGTAbb3qwK/img.png"><img src="https://blog.kakaocdn.net/dn/9ubAm/btsJhPm4SQ5/TBEqVpiFrLtubGTAbb3qwK/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F9ubAm%2FbtsJhPm4SQ5%2FTBEqVpiFrLtubGTAbb3qwK%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1498" data-origin-height="684"/></span></figure>
</p>
<p data-ke-size="size16">또는 이왕 폴더로 정리한 김에 페이지 파일은 index.tsx로만 통일하는 방법도 있겠다. /mypage/index.tsx는 /mypage로 접속했을 때 보여지는 페이지, /mypage/setting/index.tsx는 /mypage/setting으로 접속했을 때 페이지를 만들면 된다.</p>
<h2 data-ke-size="size26">쿼리스트링 사용 방법</h2>
<p data-ke-size="size16">Query String이란 URL의 매개 변수를 이야기한다. URL을 통해서 데이터를 주고 받는 HTTP 통신의 한 방법인데, URL에 어떠한 값이 들어가다 보니 "이것도 라우트인가?" 생각할 수 있지만 라우트는 아니다. 그냥 단순히 데이터만 주고 받는 것이다.</p>
<p data-ke-size="size16">아이디나 패스워드 같은 중요한 정보를 주고 받으면 안 되고, 검색어나 글 번호, 유저 닉네임 같은 간단한 정보를 URL에 실어 주고 받도록 하는 데 많이 사용되고 있다.</p>
<p data-ke-size="size16">네이버에 검색을 아무거나 해보면 ? 물음표 뒤에 나오는 것들이 실제 페이지의 라우트 주소가 아니라 쿼리스트링인 것이다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1636" data-origin-height="328"><span data-url="https://blog.kakaocdn.net/dn/pndJG/btsJgRTzaW2/x5IWNZy6GNbUSGhwlodBQ1/img.png" data-phocus="https://blog.kakaocdn.net/dn/pndJG/btsJgRTzaW2/x5IWNZy6GNbUSGhwlodBQ1/img.png"><img src="https://blog.kakaocdn.net/dn/pndJG/btsJgRTzaW2/x5IWNZy6GNbUSGhwlodBQ1/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FpndJG%2FbtsJgRTzaW2%2Fx5IWNZy6GNbUSGhwlodBQ1%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1636" data-origin-height="328"/></span></figure>
</p>
<p data-ke-size="size16">쿼리 스트링을 자세히 보면 &amp; 기호로 여러 개를 실어서 보낼 수 있다는 특징이 있고, = 기호를 통해서 좌항, 우항의 값이 다르다는 걸 볼 수 있다. 좌항, 우항은 key=value가 페어로 되어 있다는 내용이다.</p>
<p data-ke-size="size16">query string의 max length, 즉 최대 몇 자까지 URL로 데이터를 주고 받을 수 있냐는 것은 브라우저 마다 다르다. 아래는 인터넷 익스플로러 제외하고는 공식적인 수치는 아니고 개발자들이 일일이 테스트 해 본 수치이다. 뭐 결론적으로는 꽤 많은 양을 주고 받을 수 있다는 이야기다.</p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>Edge : 81,578자</li>
<li>Chrome : 64,000자까지 브라우저에서 표시 가능. 그러나 실제로는 100,000자까지 사용 가능.</li>
<li>Firefox : 65,536자까지 브라우저에서 표시 가능, 그러나 실제로는 100,000자까지 사용 가능.</li>
<li>Safari : 80,000자까지 브라우저에서 표시 가능.</li>
<li>Internet Explorer : 2,048자</li>
</ul>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="944" data-origin-height="72"><span data-url="https://blog.kakaocdn.net/dn/cY0ZGE/btsJgR69KIs/j1vRSCV6p7OXX41EobPMz1/img.png" data-phocus="https://blog.kakaocdn.net/dn/cY0ZGE/btsJgR69KIs/j1vRSCV6p7OXX41EobPMz1/img.png"><img src="https://blog.kakaocdn.net/dn/cY0ZGE/btsJgR69KIs/j1vRSCV6p7OXX41EobPMz1/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcY0ZGE%2FbtsJgR69KIs%2Fj1vRSCV6p7OXX41EobPMz1%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="944" data-origin-height="72"/></span></figure>
</p>
<p data-ke-size="size16">주소창에 이렇게 key를 nickname으로, value를 장원영으로 입력했다고 가정해보겠다. 사용자가 이렇게 입력해서 들어올 일은 없고 보통 다른 페이지에서 버튼을 누르거나 했을 때 쿼리스트링까지 담아서 같이 페이지로 넘겨주는 형태가 될 것이다. 이렇게 URL에 있는 쿼리스트링을 mypage에서 꺼내 오려면 Next.js에서 기본적으로 제공하는 훅인 useRouter 훅을 사용하면 된다.</p>
<pre id="code_1724760915561" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>import React from 'react'
import { useRouter } from 'next/router'
<p>function MyPage() {</p>
<p>const router = useRouter()
const nickname = router.query.nickname;</p>
<p>return (
&lt;div&gt;
&lt;h1&gt;My Page&lt;/h1&gt;
&lt;h2&gt;유저의 닉네임은 {nickname}입니다.&lt;/h2&gt;
&lt;/div&gt;
)
}</p>
<p>export default MyPage</code></pre></p>
<p data-ke-size="size16">next/router에서 useRouter 훅을 꺼내 오고, router라는 변수로 useRouter 훅을 호출한 다음, router 변수가 router 객체로 만들어지면 router 객체에 담겨 있는 값 중 query에 접근해서 nickname이라는 key를 꺼내오면 된다. 그 값을 꺼내와서 nickname에 담아주면 리턴문에서도 데이터를 바인딩하여 값을 사용할 수 있다.</p>
<p data-ke-size="size16">위에 거나 아래 거나 결과적으로 같긴 한데, destructuring 해서 꺼내 와도 된다.</p>
<pre id="code_1724761083757" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>import React from 'react'
import { useRouter } from 'next/router'
<p>function MyPage() {</p>
<p>const router = useRouter()
const { nickname } = router.query;</p>
<p>return (
&lt;div&gt;
&lt;h1&gt;My Page&lt;/h1&gt;
&lt;h2&gt;유저의 닉네임은 {nickname}입니다.&lt;/h2&gt;
&lt;/div&gt;
)
}</p>
<p>export default MyPage</code></pre></p>
<p data-ke-size="size16">주의할 점이 있다. useRouter 훅을 import 할 때 자동완성에 보면 next/router와 next/navigation 두 개가 뜨는 것을 볼 수 있다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1218" data-origin-height="280"><span data-url="https://blog.kakaocdn.net/dn/ckFOYD/btsJhFd3NxF/wB8kS4ig5VzCAQnhw8yhjK/img.png" data-phocus="https://blog.kakaocdn.net/dn/ckFOYD/btsJhFd3NxF/wB8kS4ig5VzCAQnhw8yhjK/img.png"><img src="https://blog.kakaocdn.net/dn/ckFOYD/btsJhFd3NxF/wB8kS4ig5VzCAQnhw8yhjK/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FckFOYD%2FbtsJhFd3NxF%2FwB8kS4ig5VzCAQnhw8yhjK%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1218" data-origin-height="280"/></span></figure>
</p>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>next/router : Pages Router 방식에서 사용하는 useRouter 훅</li>
<li>next/navigation : App Router 방식에서 사용하는 useRouter 훅</li>
</ul>
<p data-ke-size="size16">useRouter 훅에서 어떤 값을 제공하는지 콘솔에서 확인해보겠다.</p>
<pre id="code_1724761497800" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>const router = useRouter()
  const { nickname } = router.query;
  console.log(router);</code></pre>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="824" data-origin-height="760"><span data-url="https://blog.kakaocdn.net/dn/7nfmX/btsJgHKnKG1/TvB4qsWMhJCPaHOitNJrK1/img.png" data-phocus="https://blog.kakaocdn.net/dn/7nfmX/btsJgHKnKG1/TvB4qsWMhJCPaHOitNJrK1/img.png"><img src="https://blog.kakaocdn.net/dn/7nfmX/btsJgHKnKG1/TvB4qsWMhJCPaHOitNJrK1/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F7nfmX%2FbtsJgHKnKG1%2FTvB4qsWMhJCPaHOitNJrK1%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="824" data-origin-height="760"/></span></figure>
</p>
<p data-ke-size="size16">많은 값이 담겨 있는데, 라우트를 이동시킬 때 사용하는 push, 뒤로가기 기능인 back, 새로고침 기능인 reload, 현재 경로를 나타내는 pathname 등 자주 사용하는 값들도 보인다. 우리는 이 중에서 query의 값을 사용하는 것이다.</p>
<p data-ke-size="size16">query string에 많은 값이 담겨 있으면 어떻게 될까?</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="3172" data-origin-height="1302"><span data-url="https://blog.kakaocdn.net/dn/ctDFK8/btsJhkOvNBp/nImnajVkFdNPQpE4hKZP10/img.png" data-phocus="https://blog.kakaocdn.net/dn/ctDFK8/btsJhkOvNBp/nImnajVkFdNPQpE4hKZP10/img.png"><img src="https://blog.kakaocdn.net/dn/ctDFK8/btsJhkOvNBp/nImnajVkFdNPQpE4hKZP10/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FctDFK8%2FbtsJhkOvNBp%2FnImnajVkFdNPQpE4hKZP10%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="3172" data-origin-height="1302"/></span></figure>
</p>
<pre id="code_1724761745046" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>import { useRouter } from 'next/router';
import React from 'react'
<p>function MyPage() {
const router = useRouter()
const { nickname, age, location } = router.query;
console.log(router);</p>
<p>return (
&lt;div&gt;
&lt;h1&gt;My Page&lt;/h1&gt;
&lt;h2&gt;유저 닉네임 : {nickname}&lt;/h2&gt;
&lt;h2&gt;유저 연령 : {age}&lt;/h2&gt;
&lt;h2&gt;유저 거주지 : {location}&lt;/h2&gt;
&lt;/div&gt;
)
}</p>
<p>export default MyPage</code></pre></p>
<p data-ke-size="size16">많은 값이 담겨 있어도 구조 분해 할당으로 잘 꺼내올 수 있고, query에도 잘 담기는 것을 볼 수 있다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="906" data-origin-height="366"><span data-url="https://blog.kakaocdn.net/dn/us7ru/btsJgC3raWh/lX9dvnl0kvubHE2GkcZcYK/img.png" data-phocus="https://blog.kakaocdn.net/dn/us7ru/btsJgC3raWh/lX9dvnl0kvubHE2GkcZcYK/img.png"><img src="https://blog.kakaocdn.net/dn/us7ru/btsJgC3raWh/lX9dvnl0kvubHE2GkcZcYK/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fus7ru%2FbtsJgC3raWh%2FlX9dvnl0kvubHE2GkcZcYK%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="906" data-origin-height="366"/></span></figure>
</p>
<p data-ke-size="size16">데이터를 잘 받아오는 것을 잘 나오는 것을 확인할 수 있다.</p>
<h2 data-ke-size="size26">동적 라우팅 설정 방법</h2>
<p data-ke-size="size16">동적 라우팅은 쿼리 스트링과 비슷한 성격인 것 같지만, 그 구조가 다르다. 예를 들어서 마이페이지에서 '장원영'이라는 데이터를 받아 오려면 쿼리스트링으로는 ?nickname=장원영 이런 형태로 받아 왔지만 동적 라우팅으로 받아 오려면 /mypage/장원영 이런 형태로 하나의 라우트를 차지하게 설정해야 한다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1794" data-origin-height="840"><span data-url="https://blog.kakaocdn.net/dn/cEkXSX/btsJg9T10F5/iWIcv1I1BnorgCdG5rFr91/img.png" data-phocus="https://blog.kakaocdn.net/dn/cEkXSX/btsJg9T10F5/iWIcv1I1BnorgCdG5rFr91/img.png"><img src="https://blog.kakaocdn.net/dn/cEkXSX/btsJg9T10F5/iWIcv1I1BnorgCdG5rFr91/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcEkXSX%2FbtsJg9T10F5%2FiWIcv1I1BnorgCdG5rFr91%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1794" data-origin-height="840"/></span></figure>
</p>
<p data-ke-size="size16">보통 동적 라우팅은 대괄호로 감싸서 [id] 처럼 표현하지만, 안의 파일명이 뭐가 됐든 자유작명이고 [] 대괄호로 감싼다는 게 포인트이다. 대괄호로 감싸게 되면 그 파일명으로는 별도의 라우팅이 생성되진 않고, 위 폴더 구조를 보았을 때 /mypage와 /mypage/setting 까지는 라우팅이 되어 있는데, setting 말고 다른 게 붙으면 그것들을 모두 nickname이라는 Key에 담긴 value라고 보겠다는 의미이다. 따라서 위 구조에 따르면 /mypage로 접속해도 페이지가 보이고, /mypage/장원영 으로 접속해도 보이고 /mypage/안유진 으로 접속해도 보이고, /mypage/setting으로 접속해도 보인다.</p>
<p data-ke-size="size16">하지만 위와 같은 구조에서 조심해야 할 것은 /mypage/setting이라는 라우트를 별도로 갖고 있기 때문에 진짜 유저의 닉네임이 setting이라고 하더라도 그 페이지로는 접속할 수 없고 /mypage/setting 페이지가 우선되어 이 쪽으로 접속된다는 것이다. 위와 같은 구조를 피하는 것이 가장 좋겠지만 불가피하다면 setting과 같이 이미 라우트로 설정되어 있는 키워드는 닉네임으로 설정하지 못하게 막아두어야 한다.</p>
<p data-ke-size="size16">쿼리 스트링에서 값을 꺼내올 때와 똑같이 useRouter 훅을 사용하고 있는데, 아래 사진을 보자.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="3184" data-origin-height="1256"><span data-url="https://blog.kakaocdn.net/dn/bmkOyM/btsJgIibs82/6HXKKCL8AQtK27NWw3hkbK/img.png" data-phocus="https://blog.kakaocdn.net/dn/bmkOyM/btsJgIibs82/6HXKKCL8AQtK27NWw3hkbK/img.png"><img src="https://blog.kakaocdn.net/dn/bmkOyM/btsJgIibs82/6HXKKCL8AQtK27NWw3hkbK/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbmkOyM%2FbtsJgIibs82%2F6HXKKCL8AQtK27NWw3hkbK%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="3184" data-origin-height="1256"/></span></figure>
</p>
<p data-ke-size="size16">nickname이라는 쿼리스트링을 넘겨 받은 것처럼 nickname이라는 키에 값이 자동으로 할당되는 것을 볼 수 있다. 그리고 pathname으로 현재 경로를 보면 대괄호로 묶여 있는 동적라우팅 형태를 띄고 있는 것이 보인다.</p>
<p data-ke-size="size16">그러면 쿼리스트링을 사용할 것이냐, 동적 라우팅을 사용할 것이냐? 어쨌든 결과는 같기 때문에 헷갈릴 수 있는데 검색 페이지에서 검색창에 입력된 값처럼 수많은 데이터를 전달하는 게 아니라 마이페이지처럼 페이지 자체는 정적이고 받아오는 값이 많지 않다면 dynamic route로 설정하는 것이 좋다. 쿼리스트링은 매개 변수일 뿐이고 실제 URL 주소가 아니기 때문에 SEO에 잡히지 않는다. 따라서 SEO에 이러한 방식이 유리하고, 또 프로젝트의 디렉토리를 보았을 때 [] 대괄호로 동적 라우팅 설정을 해두면 개발자가 '아, 이 페이지는 라우트를 동적으로 받는구나'하고 이해하기가 쉽다. 이 부분은 별도로 다루겠다.</p>
<h2 data-ke-size="size26">Catch All Segment Dynimic Routing</h2>
<p data-ke-size="size16">그런데 하나 문제가 있다. [nickname].tsx는 /mypage/장원영 이렇게 하나의 동적인 데이터만 받아올 수 있는데, /mypage/아이브/장원영 이렇게 중첩된 동적 라우트에 전부 대응하려면 어떻게 해야 할까? 이 때 Catch All Segment Dynamic Routing 방식으로 파일명을 만들면 된다.</p>
<p data-ke-size="size16">사용법은 쉽다. 구조 분해 할당 하듯이 [...nickname].tsx 이런 식으로 spread operator를 사용해서 파일 이름을 지으면 된다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="3186" data-origin-height="1314"><span data-url="https://blog.kakaocdn.net/dn/bsLECp/btsJg4L3KtF/FJFqypA370GCnkk0wkalX1/img.png" data-phocus="https://blog.kakaocdn.net/dn/bsLECp/btsJg4L3KtF/FJFqypA370GCnkk0wkalX1/img.png"><img src="https://blog.kakaocdn.net/dn/bsLECp/btsJg4L3KtF/FJFqypA370GCnkk0wkalX1/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbsLECp%2FbtsJg4L3KtF%2FFJFqypA370GCnkk0wkalX1%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="3186" data-origin-height="1314"/></span></figure>
</p>
<p data-ke-size="size16">[nickname].tsx 일 때는? 당연히 404 not found가 뜬다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1964" data-origin-height="966"><span data-url="https://blog.kakaocdn.net/dn/DAkQm/btsJiJzHRsE/16OmEoT0kC8kKdtd7hhkZk/img.png" data-phocus="https://blog.kakaocdn.net/dn/DAkQm/btsJiJzHRsE/16OmEoT0kC8kKdtd7hhkZk/img.png"><img src="https://blog.kakaocdn.net/dn/DAkQm/btsJiJzHRsE/16OmEoT0kC8kKdtd7hhkZk/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FDAkQm%2FbtsJiJzHRsE%2F16OmEoT0kC8kKdtd7hhkZk%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1964" data-origin-height="966"/></span></figure>
<figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="3178" data-origin-height="1380"><span data-url="https://blog.kakaocdn.net/dn/bmGaVe/btsJiK6jFwm/ICsj9vYtiakFgA2F33kYZ0/img.png" data-phocus="https://blog.kakaocdn.net/dn/bmGaVe/btsJiK6jFwm/ICsj9vYtiakFgA2F33kYZ0/img.png"><img src="https://blog.kakaocdn.net/dn/bmGaVe/btsJiK6jFwm/ICsj9vYtiakFgA2F33kYZ0/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbmGaVe%2FbtsJiK6jFwm%2FICsj9vYtiakFgA2F33kYZ0%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="3178" data-origin-height="1380"/></span></figure>
</p>
<p data-ke-size="size16">[...nickname].tsx 일 때는? 접속이 잘 된다.</p>
<p data-ke-size="size16">오잉? 근데 왜 아이브장원영 이렇게 다 붙어서 나올까? 콘솔을 보니 슬래시 기준으로 세그먼트들이 nickname이라는 key 안에 배열로 순서대로 할당된 것을 볼 수 있다.</p>
<pre id="code_1724764043943" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>import { useRouter } from 'next/router'
import React from 'react'
<p>function MyPage() {</p>
<p>const router = useRouter();
const { nickname } = router.query;
console.log(router);</p>
<p>const groupName = nickname ? nickname[0] : '';
const nickName = nickname ? nickname[0] : '';</p>
<p>return (
&lt;div&gt;
&lt;h2&gt;유저의 그룹은 {groupName}입니다.&lt;/h2&gt;
&lt;h2&gt;유저의 닉네임은 {nickName}입니다.&lt;/h2&gt;
&lt;/div&gt;
)
}</p>
<p>export default MyPage</code></pre></p>
<p data-ke-size="size16">이렇게 각 인덱스에 접근해주면 각각의 데이터를 바인딩 할 수 있다. nickname : nickname[0] : ''; 처럼 조건문을 표현식으로 쓴 이유는 nickname에서 각 인덱스에 값이 undefined 일 수 있기 때문에 타입스크립트 컴파일 에러가 떠서 그렇다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="856" data-origin-height="334"><span data-url="https://blog.kakaocdn.net/dn/bFhLhy/btsJgR7aLOU/JPMGvrnvLmKFfjKyffSLWK/img.png" data-phocus="https://blog.kakaocdn.net/dn/bFhLhy/btsJgR7aLOU/JPMGvrnvLmKFfjKyffSLWK/img.png"><img src="https://blog.kakaocdn.net/dn/bFhLhy/btsJgR7aLOU/JPMGvrnvLmKFfjKyffSLWK/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbFhLhy%2FbtsJgR7aLOU%2FJPMGvrnvLmKFfjKyffSLWK%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="856" data-origin-height="334"/></span></figure>
</p>
<p data-ke-size="size16">잘 받아 온다.</p>
<h2 data-ke-size="size26">Optional Catch All Segment</h2>
<p data-ke-size="size16">그런데 또 문제가 있다. 그만 문제가 생겼으면 좋으련만 아무튼 문제가 또 있다.</p>
<p data-ke-size="size16">/mypage로 접속하는 거나 /mypage/장원영 으로 접속하는 거나 페이지 구조가 어차피 똑같다면 굳이 /mypage/index.tsx를 만들 필요가 없지 않을까? 만약 /mypage 자체는 아무 페이지도 아니어서 의도적으로 /mypage로 접속했을 때 404 not found를 띄우는 경우라면 모를까, /mypage가 /mypage/장원영과 다른 구조의 페이지가 아니라면 모를까, 같은 컴포넌트를 렌더링 하는 페이지라면 굳이 닉네임 하나 받아오겠다고 /mypage/index.tsx와 /mypage/[nickname].tsx로 파일을 두 개를 만들 필요가 없어 보인다.</p>
<p data-ke-size="size16">그런데 아래 폴더 구조를 보자.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="688" data-origin-height="178"><span data-url="https://blog.kakaocdn.net/dn/dN5yuG/btsJh63daa2/rZar4znDRUxVadHX8rCeN1/img.png" data-phocus="https://blog.kakaocdn.net/dn/dN5yuG/btsJh63daa2/rZar4znDRUxVadHX8rCeN1/img.png"><img src="https://blog.kakaocdn.net/dn/dN5yuG/btsJh63daa2/rZar4znDRUxVadHX8rCeN1/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdN5yuG%2FbtsJh63daa2%2FrZar4znDRUxVadHX8rCeN1%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="688" data-origin-height="178"/></span></figure>
</p>
<p data-ke-size="size16">폴더 구조를 이렇게 만들면 /mypage/장원영, /mypage/아이브/장원영/21/인천시 뭐 아무리 길게 써도 전부 대응이 가능하지만, 정작 /mypage 세그먼트로는 접속이 안 된다.</p>
<p data-ke-size="size16">이것까지 모두 대응하는 방법이 Optional Catch All Segment 방식의 dynamic routing이고, [[...nickname]].tsx 처럼 대괄호를 이중으로 감싸주면 /mypage 뒤에 세그먼트가 붙든 붙지 않든 모두 대응이 가능한 동적 라우팅이 된다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="688" data-origin-height="178"><span data-url="https://blog.kakaocdn.net/dn/dwuzIC/btsJgxORHPb/FHs30w7wxCpt5q5mdaTrik/img.png" data-phocus="https://blog.kakaocdn.net/dn/dwuzIC/btsJgxORHPb/FHs30w7wxCpt5q5mdaTrik/img.png"><img src="https://blog.kakaocdn.net/dn/dwuzIC/btsJgxORHPb/FHs30w7wxCpt5q5mdaTrik/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdwuzIC%2FbtsJgxORHPb%2FFHs30w7wxCpt5q5mdaTrik%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="688" data-origin-height="178"/></span></figure>
</p>
<p data-ke-size="size16">위 폴더 구조를 보면 index.tsx 파일이 없기 때문에 /mypage/아이브/장원영/... 으로는 접속이 가능하지만 /mypage로는 404 not found가 떠야 하는 게 맞다. 그런데 optional catch all segement를 사용하는 dynamic routing을 했기 때문에 /mypage로도 접속이 되고 /mypage/... 로도 접속이 될 것이다. 진짜인지 확인해보겠다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="780" data-origin-height="320"><span data-url="https://blog.kakaocdn.net/dn/zwALb/btsJh9lnTTg/MOGxaKKo2vkEkcvKB1dHe0/img.png" data-phocus="https://blog.kakaocdn.net/dn/zwALb/btsJh9lnTTg/MOGxaKKo2vkEkcvKB1dHe0/img.png"><img src="https://blog.kakaocdn.net/dn/zwALb/btsJh9lnTTg/MOGxaKKo2vkEkcvKB1dHe0/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FzwALb%2FbtsJh9lnTTg%2FMOGxaKKo2vkEkcvKB1dHe0%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="780" data-origin-height="320"/></span></figure>
</p>
<p data-ke-size="size16">잘 된다.</p>
<h2 data-ke-size="size26">404 Not Found Page</h2>
<p data-ke-size="size16">마지막으로 알아볼 것은 404 Not Found 메시지를 출력해주는 페이지를 만드는 방법이다. 404 에러는 유저가 없는 경로를 입력했을 때 보여주는 페이지인데, 별도로 설정하지 않아도 Next.js에서 기본적으로 보여주는 페이지가 있다. 그런데 우리가 국내 서비스를 만들 거라면 영어로 뜨는 이런 페이지는 사용자 경험이 떨어질 수 있기 떄문에 직접 커스터마이징 해주는 게 좋다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1810" data-origin-height="1228"><span data-url="https://blog.kakaocdn.net/dn/QJ0eL/btsJhMYk2Iw/PJXD2msi1PnSeaOP7ZvzB0/img.png" data-phocus="https://blog.kakaocdn.net/dn/QJ0eL/btsJhMYk2Iw/PJXD2msi1PnSeaOP7ZvzB0/img.png"><img src="https://blog.kakaocdn.net/dn/QJ0eL/btsJhMYk2Iw/PJXD2msi1PnSeaOP7ZvzB0/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FQJ0eL%2FbtsJhMYk2Iw%2FPJXD2msi1PnSeaOP7ZvzB0%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1810" data-origin-height="1228"/></span></figure>
</p>
<p data-ke-size="size16">위 이미지가 Next.js에서 기본적으로 제공하는 404 페이지이다.</p>
<p data-ke-size="size16">이것을 직접 만드는 방법은 간단한다. pages/404.tsx 파일을 만들어주면 된다. 파일명은 저렇게 해야 하고 컴포넌트 이름은 그냥 page해도 되고 자유작명이다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1472" data-origin-height="738"><span data-url="https://blog.kakaocdn.net/dn/bnJv6z/btsJiFxh5Z7/zFrYNucm2QBl7PHeLhaeOK/img.png" data-phocus="https://blog.kakaocdn.net/dn/bnJv6z/btsJiFxh5Z7/zFrYNucm2QBl7PHeLhaeOK/img.png"><img src="https://blog.kakaocdn.net/dn/bnJv6z/btsJiFxh5Z7/zFrYNucm2QBl7PHeLhaeOK/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbnJv6z%2FbtsJiFxh5Z7%2FzFrYNucm2QBl7PHeLhaeOK%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1472" data-origin-height="738"/></span></figure>
<figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="698" data-origin-height="242"><span data-url="https://blog.kakaocdn.net/dn/brkv8O/btsJgHDDJII/rWh93Kh8NjkKgEk1QwbH50/img.png" data-phocus="https://blog.kakaocdn.net/dn/brkv8O/btsJgHDDJII/rWh93Kh8NjkKgEk1QwbH50/img.png"><img src="https://blog.kakaocdn.net/dn/brkv8O/btsJgHDDJII/rWh93Kh8NjkKgEk1QwbH50/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fbrkv8O%2FbtsJgHDDJII%2FrWh93Kh8NjkKgEk1QwbH50%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="698" data-origin-height="242"/></span></figure>
</p>
<p data-ke-size="size16">잘 작동한다. 나중에 더 예쁘게 만들어주면 될 것 같다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">끝.</p>