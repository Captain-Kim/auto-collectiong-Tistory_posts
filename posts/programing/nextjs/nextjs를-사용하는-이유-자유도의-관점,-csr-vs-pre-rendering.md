<p data-ke-size="size16">지난 번 포스팅에서 Next.js를 사용하는 이유에 대해서 간단하게 작성해보았었다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">API 라우트 구축이 가능해서 풀스택 애플리케이션을 만들 수 있고... 프레임워크의 성격을 가지고 있어서 별도로 스타일링을 해주거나 라우팅을 하기에 더 빠르고 수월하다는 점... 등등 네 다섯 가지 예시를 들었던 것 같다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">그런데 사실 개념을 정리한 정도의 요약글이었고, 구체적인 개념들을 살펴보진 않았었다. 따라서 이번 글에서는 Next.js를 사용하는 그 이유에 대해서 심도있게 다뤄보고자 한다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">만약 이 글을 보고도 공감이 안 된다면 쓰지 않아도 된다. 마치 Next.js의 영업사원을 자처하는 것 같지만 리액트 단독으로 앱을 개발한다고 해서 문제가 되는 것은 아니다. 다만 Next.js의 이점을 누리지 못할 뿐.</p>
<h2 style="color: #000000; text-align: start;" data-ke-size="size26">리액트 공식문서에서도 설명하는 점</h2>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1742" data-origin-height="592"><span data-url="https://blog.kakaocdn.net/dn/bezaI3/btsJcP8ssCM/Ihd0PWrdeOonMpCUZSIdmk/img.png" data-phocus="https://blog.kakaocdn.net/dn/bezaI3/btsJcP8ssCM/Ihd0PWrdeOonMpCUZSIdmk/img.png"><img src="https://blog.kakaocdn.net/dn/bezaI3/btsJcP8ssCM/Ihd0PWrdeOonMpCUZSIdmk/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbezaI3%2FbtsJcP8ssCM%2FIhd0PWrdeOonMpCUZSIdmk%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1742" data-origin-height="592"/></span></figure>
</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">위 사진은 리액트 공식문서에 게재된 내용이다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">내용을 살펴보면 리액트는 라이브러리이고, 컴포넌트들을 만들어서 조합해낼 수는 있지만 라우팅을 하는 방법이나 데이터를 페칭하는 방법에 대해서는 특별히 솔루션을 주고 있지 않다고 설명하고 있다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">만약 이런 것들을 지원하는 풀스택 앱 만들고자 한다면 Next.js나 Remix라는 프레임워크를 사용하라고 안내하고 있다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">Remix 프레임워크는 생긴지 얼마 안 됐는데, Next.js의 고질병 같은 버그나 불안정한 것들을 많이 개선되었다고는 한다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">그런데 어쩄든 우리는 협업을 해야 하는 개발자들이니 좀 더 메이저한 것을 써야 하지 않을까.</p>
<h2 style="color: #000000; text-align: start;" data-ke-size="size26">Next.js로 구축한 국내 사이트</h2>
<p style="color: #333333; text-align: start;" data-ke-size="size16">생각보다 많이 사용하고 있어서 놀랐다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">너무 많아서 다 적기도 어려운데 유명한 곳들은...</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">카카오페이, 중고나라, 인프런(원래는 Vue.js였던 듯), 지마켓(12버전), 야놀자, 직방, 크몽 등...</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">리믹스는 자료가 없어서 확인이 안 된다.</p>
<h2 style="color: #000000; text-align: start;" data-ke-size="size26">자유도의 관점</h2>
<p style="color: #333333; text-align: start;" data-ke-size="size16">리액트는 라이브러리라고 스스로 부르고 있고, 넥스트는 프레임워크라고 하고 있다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">이 차이에 대해서는 잘 알고 있겠지만, 프레임워크는 개발주도권이 프레임워크에 있는 것이고 라이브러리는 개발 주도권이 개발자에게 있는 것을 말할 때 분류한다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">난 개발을 처음 배울 때 프레임워크가 주도권이 개발자에게 없다고 해서 패키지를 설치할 수 없는 건가했는데 그런 개념은 아니고,</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">라우팅, 데이터 페칭 등 굵직한 비즈니스 로직과 굵직한 영역에서 주도권이 어디 있느냐는 것으로 구분한다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">개발을 이제 막 시작했을 때는 자유도가 높은 게 좋은 거 아닌가? 생각했다. 하나의 기능을 놓고도 정말 다양한 로직이 나올 수 있고, 시시각각으로 변하는 유행을 따라가기 위해서는 보다 열려 있는 것이 좋지 않겠냐는 게 처음에 내가 한 생각이었다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">그런데 웹 개발을 배우면 배울수록 나의 자유를 빼앗아 가주길 바라는 나를 보고 "아" 하고 바로 Next.js가 왜 인기가 많은지 이해했다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">나도 마찬가지이지만, 리액트만으로 협업을 했을 때는 워낙 생각들이 다르니 팀 컨벤션이라는 것을 만들기도 힘들었고, 어찌저찌 만든다고 해도 내가 지금까지 페칭하는 방식은 axios 인스턴스를 사용해서 어쩌구... 였는데 팀 컨벤션에서는 axios를 사용하지 말자고 하니 나는 어쨌든 그것에 맞추기 위해서 또 시간을 써야 하는 상황이 계속 발생하게 되는 것이다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">그리고 어찌저찌 그렇게 수월하게 되는 것 같다고 하더라도 결국 후반부에 가서 시간에 쫓겨 작업을 하다 보면 팀 컨벤션은 다들 새까맣게 잊고 미래의 나에게 리팩토링을 맡기고 그냥 편한대로 작업해버리는 경우가 많았다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">특히 CSS는 대환장 파티 그 자체인데, 누구는 스타일드 컴포넌트를 사용하면서도 컴포넌트에 id를 일일이 부여하는 것이 편하다고 하고, 누구는 그럴 거면 스타일드 컴포넌트를 왜 쓰냐고 말하는 사람들도 있고 정말 다양하다. 누구는 rem으로 해놨고 누구는 px로 해놨고... 또 px은 1~2 차이로 화면에서 잘 차이가 안 나다 보니 코드를 유심히 들여다 보지 않으면 페이지마다 전부 다른 CSS의 대환장 파티를 맛볼 수 있었다는 것이다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">Next.js에서는 프레임워크를 세팅할 때 기본적으로 tailwindCSS를 편하게 세팅할 수 있게 도와주기 때문에 tailwindCSS를 사용하는 사람들이 많은데,</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">스타일드 컴포넌트와 같은 CSS-in-JS 방식의 스타일링을 사용하던 사람이 tailwindCSS를 보면 하나같이 하는 말이 코드가 너무 지저분하고 가독성이 떨어진다라는 점을 말했다. 그리고 HTML은 깔끔하게 가져가고 싶은데 너무 길어져서 그것도 싫다는 말을 많이 들었다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">나도 마찬가지였고 tailwindCSS는 죽어도 쓰기가 싫었는데 웬걸... 딱 한 달만 써보면 이것만큼 가독성이 좋은 게 없다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">가독성이 안 좋아보였던 건 내가 그 속성을 읽지 못해서 그런 것이었고 읽을 수 있는 단계가 되니 직관적으로 CSS가 이해되었다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">갑자기 테일윈드 이야기를 꺼내며 멀리 돌아왔지만, 테일윈드도 테일윈드에서 기본적으로 정해놓은 수치들이 있어서 커스터마이징 하지 않으면 자유도가 떨어지는 편이라고 볼 수 있겠는데,</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">결국 이렇게 자유도가 떨어지는 게 팀 컨벤션을 맞추기도 더 유리하고 프로젝트 규모가 커지면 커질 수록 오히려 편리하다는 것.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">즉 혼자 개인 프로젝트 작업을 하거나 프로젝트 규모가 작은 경우에는 자유도가 높은 게 좋을 수도 있지만, 규모가 커지면 커질 수록 프레임워크를 더 찾게 된다는 게 Next.js가 자유도가 낮음에도 인기가 있는 비결인 것 같다.</p>
<h2 style="color: #000000; text-align: start;" data-ke-size="size26">기존 React의 렌더링 방식(CSR)의 단점</h2>
<p style="color: #333333; text-align: start;" data-ke-size="size16">Next.js와 기존 React는 렌더링 방식에서 큰 차이가 있다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">그렇다고 넥스트에서 리액트의 렌더링 방식을 못 하는 건 아니고, 리액트의 CSR도 'use client' 선언을 해서 만들 수 있다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">즉 리액트에서는 넥스트에서 제공하는 SSR을 못하는데, 넥스트에서는 그거 다 하고 리액트의 CSR도 할 수 있는데</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">안 쓸 이유가 있을까?</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">렌더링 방식을 비교해보면 리액트 vs 넥스트에서는 넥스트를 안 쓸 이유가 없어 보인다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">그런데 SSR이 안 필요하면 이런 이야기를 할 필요도 없을 것이다. 문제는 SSR이 예전에 인기가 있었던 방식인데 리액트가 CSR을 들고 나와서 엄청난 붐을 일으켰는데 다시 SSR이 인기가 많아지는 이유가 무엇이냐는 것이다.&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">결론부터 이야기하자면 CSR에 몇 가지 문제가 있어서다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">그 전에 CSR, SSR이라고 하는데 이것이 뭘 의미하는 건지 자세히 알아보자.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">어? CSR은 Client Side Rendering이고 SSR은 Server Side Rendering 아닌가? 뭘 설명하려는 거지?</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">라고 생각하더라도 그럼 그것이 어떻게 작동하는지 설명할 수 있어야 하는데 나는 거기까지 단계에 못 미쳤었다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">Next.js가 뭐가 좋은 건지도 모르고 그냥 유행이라니까 쓴다면 의미 없지 않겠는가.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">독학이나 전공자들은 모르겠지만 부트캠프는 이런 문제가 좀 있다. 내가 부트캠프 출신이라 잘 안다. 리액트 배우는 주차니까 리액트를 썼고, 넥스트 배우는 주차니까 넥스트를 썼다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">아, 물론 부트캠프에서 안 알려주는 건 아니다. 근데 문제는 알려줘도 한 귀로 듣고 한 귀로 흘러간다는 것이 문제다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">부트캠프 수강생들이 멍청해서 그렇느냐, 그건 아니다. 강사들이 말하는 CSR의 그 불편한 '경험'을 못해봤기 때문에 금방 까먹는 거다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">여기서 경험까지 있다면 더 기억에 오래 남고 좋은 학습이 되겠지만 나는 일부러 경험을 만들 순 없을 것 같다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">그래서 렌더링 원리에 대해서 제대로 이해하고 넘어가려고 시도했던 것이다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<h3 style="color: #000000; text-align: start;" data-ke-size="size23">렌더링이란?</h3>
<p style="color: #333333; text-align: start;" data-ke-size="size16">일단 렌더링이라는 것은 두 가지 개념으로 사용된다. 하나는 자바스크립트(JSX)를 HTML로 변환하는 과정을 렌더링이라고 표현하고, 하나는 HTML을 웹 브라우저에 띄워주는 것도 렌더링이라고 한다.</p>
<h3 style="color: #000000; text-align: start;" data-ke-size="size23">클라이언트 사이드 렌더링의 과정</h3>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="996" data-origin-height="1016"><span data-url="https://blog.kakaocdn.net/dn/67Fb6/btsJcNiIxX6/GU09crHpqWpR77khQuvaMk/img.png" data-phocus="https://blog.kakaocdn.net/dn/67Fb6/btsJcNiIxX6/GU09crHpqWpR77khQuvaMk/img.png"><img src="https://blog.kakaocdn.net/dn/67Fb6/btsJcNiIxX6/GU09crHpqWpR77khQuvaMk/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F67Fb6%2FbtsJcNiIxX6%2FGU09crHpqWpR77khQuvaMk%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="996" data-origin-height="1016"/></span></figure>
</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">간단하다. 사용자가 웹 브라우저를 통해 도메인 주소를 입력하고 CDN이 웹 서버의 IP 주소를 찾아온 뒤 웹 서버에게 요청 내용을 전달해서 웹 서버는 요청이 유효하면 index.html을 보내준다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">어? 근데 리액트에 html이 있었나?</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="768" data-origin-height="568"><span data-url="https://blog.kakaocdn.net/dn/bBPqOk/btsJdyrqKg8/xII97cpNCwUxzNqEs8hzbk/img.png" data-phocus="https://blog.kakaocdn.net/dn/bBPqOk/btsJdyrqKg8/xII97cpNCwUxzNqEs8hzbk/img.png"><img src="https://blog.kakaocdn.net/dn/bBPqOk/btsJdyrqKg8/xII97cpNCwUxzNqEs8hzbk/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbBPqOk%2FbtsJdyrqKg8%2FxII97cpNCwUxzNqEs8hzbk%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="768" data-origin-height="568"/></span></figure>
</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">src 디렉토리에는 없지만 html이 없으면 화면을 어떻게 보여주겠는가.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">App.js 파일 내용을 보면 아래와 같다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1582" data-origin-height="624"><span data-url="https://blog.kakaocdn.net/dn/9OZ6i/btsJblnsRHU/sWCr8t9KFqQXYjbKbqkqs1/img.png" data-phocus="https://blog.kakaocdn.net/dn/9OZ6i/btsJblnsRHU/sWCr8t9KFqQXYjbKbqkqs1/img.png"><img src="https://blog.kakaocdn.net/dn/9OZ6i/btsJblnsRHU/sWCr8t9KFqQXYjbKbqkqs1/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F9OZ6i%2FbtsJblnsRHU%2FsWCr8t9KFqQXYjbKbqkqs1%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1582" data-origin-height="624"/></span></figure>
</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">ReactDOM.render라는 코드 한 줄이 적혀있는데, 두 개의 인자가 있다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16"> index.html에서 id가 root인 곳에 App 컴포넌트를 렌더링하라는 의미이다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1186" data-origin-height="1040"><span data-url="https://blog.kakaocdn.net/dn/9DYZC/btsJdx67Mks/3M3WvZymnThHveKp9PjoT1/img.png" data-phocus="https://blog.kakaocdn.net/dn/9DYZC/btsJdx67Mks/3M3WvZymnThHveKp9PjoT1/img.png"><img src="https://blog.kakaocdn.net/dn/9DYZC/btsJdx67Mks/3M3WvZymnThHveKp9PjoT1/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F9DYZC%2FbtsJdx67Mks%2F3M3WvZymnThHveKp9PjoT1%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1186" data-origin-height="1040"/></span></figure>
</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">앱 컴포넌트는 함수 컴포넌트, class 컴포넌트 뭐 이런 것으로 구성되어 있는 우리가 일반적으로 알고 있는 그 컴포넌트다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1552" data-origin-height="1182"><span data-url="https://blog.kakaocdn.net/dn/bb6LNp/btsJcmscD2D/HrpeUXMjxWCJ10vUajcNb1/img.png" data-phocus="https://blog.kakaocdn.net/dn/bb6LNp/btsJcmscD2D/HrpeUXMjxWCJ10vUajcNb1/img.png"><img src="https://blog.kakaocdn.net/dn/bb6LNp/btsJcmscD2D/HrpeUXMjxWCJ10vUajcNb1/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fbb6LNp%2FbtsJcmscD2D%2FHrpeUXMjxWCJ10vUajcNb1%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1552" data-origin-height="1182"/></span></figure>
</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">index.html을 보면 id가 root인 div가 보이지 않는가? 그거 말고는 아무 것도 없다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">즉 사용자가 브라우저를 통해 웹 서버에 사이트 접속을 요청하면 리액트에서는 index.html을 툭 던져주는데 index.html을 보면 아무 것도 없는 빈 div이기 때문에 사용자에게 빈 화면을 렌더링 해준다는 것이다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">그러면 우리가 보고 있는 이 화면은 뭔데?</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">일단 빈 div를 하나 던져주고 그 div, 즉 id가 root인 그 빈 화면에 &lt;App/&gt; 컴포넌트를 렌더링한다고 하지 않았는가?</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">빈 화면을 먼저 던져주고 나서 남은 자바스크립트를 번들링해서 화면을 그리게 된다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">잉 그런데 Bundling이란 무엇일까?</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">Webpack, Rollup, Browserify라는 툴을 들어본 적이 있는가? 프로젝트 여기저기에서 마치 밥알처럼 흩어져 있는 자바스크립트 코드를 주먹밥 뭉치듯이 조물조물 하나로 뭉쳐서 하나의 번들로 만드는 과정을 번들링이라고 한다. 즉 bundle이라는 하나의 파일로 만드는 과정을 말하는 것이다. 이 번들이 웹 사이트의 화면을 그려주기도 하고 버튼 클릭이나 데이터 페칭 같은 자바스크립트 코드도 포함시켜서 클라이언트에게 전달해주는 역할을 하는 것이다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">참고로 Next.js를 사용하면 Webpack이라는 유틸이 번들링을 자동으로 해준다. 다른 라이브러리는 직접 해야 하는 것들도 있다.</p>
<pre id="code_1724373104595" class="javascript" style="background-color: #f8f8f8; color: #383a42; text-align: start;" data-ke-type="codeblock" data-ke-language="typescript"><code>// math.js
export function add(a, b) {
  return a + b;
}</code></pre>
<pre id="code_1724373104596" class="pgsql" style="background-color: #f8f8f8; color: #383a42; text-align: start;" data-ke-type="codeblock" data-ke-language="typescript"><code>// app.js import { add } from './math.js'; console.log(add(16, 26)); // 42</code></pre>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">위와 같은 파일이 하나 있다고 가정해보자.<br /><br /></p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">math.js라는 파일에서 add라는 함수를<span>&nbsp;</span><span style="background-color: #ffffff; color: #1f1f1f; text-align: left;"> destructuring 해서 꺼내온 다음 콘솔에 찍어보는 것인데, 파일도 두 개고 함수도 두 개이다.</span></p>
<p style="color: #333333; text-align: start;" data-ke-size="size16"><span style="background-color: #ffffff; color: #1f1f1f; text-align: left;">그런데 우리가 프로젝트를 만들면서 만드는 파일들을 클라이언트에서 필요할 때마다 웹 서버에서 하나씩 받아가는 것이 아니라 흩어져 있는 파일과 코드들을 하나의 번들 파일로 아래처럼 뭉쳐서 웹 서버는 클라이언트한테 전달해주고, 클라이언트가 그 번들을 가지고 있다가 사용자가 요청하는 코드를 꺼내어 주는 것이다.</span></p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<pre id="code_1724373104596" class="oxygene" style="background-color: #f8f8f8; color: #383a42; text-align: start;" data-ke-type="codeblock" data-ke-language="typescript"><code>function add(a, b) {
  return a + b;
}
<p>console.log(add(16, 26)); // 42</code></pre></p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">본론에서 너무 멀어지긴 하지만 여기서 더 알아두면 좋은 게, 그러면 프로젝트가 크면 클 수록, 즉 밥알이 많으면 많을 수록 주먹밥을 뭉쳐서 보내주는 시간이 길어지지 않겠는가? 맞다. 그래서 프로젝트의 규모가 커지면 code splitting 기법을 활용해서 번들을 분할시키는 최적화 기법을 사용하기도 한다. 말이 길어지니<span>&nbsp;</span><a style="color: #0070d1;" href="https://legacy.reactjs.org/docs/code-splitting.html">리액트 공식 문서 링크</a>만 남기겠다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1552" data-origin-height="1328"><span data-url="https://blog.kakaocdn.net/dn/2ewfa/btsJb1ogXnm/daOgEGAGzWv2wWyxwkXKc1/img.png" data-phocus="https://blog.kakaocdn.net/dn/2ewfa/btsJb1ogXnm/daOgEGAGzWv2wWyxwkXKc1/img.png"><img src="https://blog.kakaocdn.net/dn/2ewfa/btsJb1ogXnm/daOgEGAGzWv2wWyxwkXKc1/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F2ewfa%2FbtsJb1ogXnm%2FdaOgEGAGzWv2wWyxwkXKc1%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1552" data-origin-height="1328"/></span></figure>
</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">아까 봤던 CSR의 초기 렌더링 과정 이후 번들링 과정이 추가되었다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">번들 파일이 클라이언트로 전달되고 나서는 클라이언트가 번들을 잘 가지고 있다가 사용자가 요청하는 페이지나 컴포넌트의 코드를 꺼내서 보여준다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">그런데 여기서 버튼 같이 사용자와의 인터렉션이 필요한 엘리먼트들도 담겨 있기 때문에&nbsp; 컨텐츠가 렌더링 되고 나서는 모든 상호작용도 즉시 발생한다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">이러한 CSR의 장점은, 번들링만 어찌저찌 완료되면 클라이언트가 그 번들 파일을 다 가지고 있기 때문에, 즉 이제부터는 클라이언트가 렌더링해줄 것이기 때문에 초기 로딩 속도만 기다리고 나면 그 뒤로는 웹 페이지 간 이동이 매우 빠르다. 이게 리액트라는 라이브러리가 가진 엄청난 장점이다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">그럼 도대체 뭐가 문제라는 걸까?</p>
<h3 style="color: #000000; text-align: start;" data-ke-size="size23">클라이언트 사이드 렌더링의 단점</h3>
<p style="color: #333333; text-align: start;" data-ke-size="size16">바로 위에서 말했던 '초기 로딩 속도'에 그 답이 있다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">아래의 두 개 사진을 보자.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="690" data-origin-height="236"><span data-url="https://blog.kakaocdn.net/dn/dxV9B3/btsJdw1tVNO/AbQyxzjAO2q77Ik4g0bxtk/img.png" data-phocus="https://blog.kakaocdn.net/dn/dxV9B3/btsJdw1tVNO/AbQyxzjAO2q77Ik4g0bxtk/img.png"><img src="https://blog.kakaocdn.net/dn/dxV9B3/btsJdw1tVNO/AbQyxzjAO2q77Ik4g0bxtk/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdxV9B3%2FbtsJdw1tVNO%2FAbQyxzjAO2q77Ik4g0bxtk%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" width="418" height="143" data-origin-width="690" data-origin-height="236"/></span></figure>
<figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="480" data-origin-height="174"><span data-url="https://blog.kakaocdn.net/dn/LwUsi/btsJc20ThGR/BmHosGkFEMCFYWZVDJM4u0/img.png" data-phocus="https://blog.kakaocdn.net/dn/LwUsi/btsJc20ThGR/BmHosGkFEMCFYWZVDJM4u0/img.png"><img src="https://blog.kakaocdn.net/dn/LwUsi/btsJc20ThGR/BmHosGkFEMCFYWZVDJM4u0/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FLwUsi%2FbtsJc20ThGR%2FBmHosGkFEMCFYWZVDJM4u0%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" width="452" height="164" data-origin-width="480" data-origin-height="174"/></span></figure>
</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">크롬 개발자도구 Light House 분석을 해보면 First Contentful Paint 즉, 처음에 화면에 그려지기까지 얼마나 시간이 소요되는 지에 대한 평가 지표를 보겠다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">위 0.4초는 본인이 최종 팀 프로젝트 Next.js로 개발한 웹 사이트의 FCP 수치이고 아래는 리액트만으로 만든 사이트인 뱅크샐러드의 FCP 수치이다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">초기 렌더링 때는 저 0.4초의 차이가 꽤 크게 느껴졌다. 하지만 뱅크샐러드의 0.8초는 심각한 문제는 아니고 그냥 Next.js에 비해 FCP가 아쉬울 수 있다는 것이다.&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">그런데 이것은 내가 500G 광랜을 사용하고 있고, M1 칩셋을 사용하고 있다는 점 등을 고려했을 때 클라이언트의 성능이 좋아서 그런 걸수도 있지 않겠는가! 웹 개발자라면 다양한 기기에도 대응을 해야 하는데, 저사양 기기 등 여건이 좋지 않은 상황에서 접속하는 경우에는 오로지 클라이언트에게 그 부담을 전가하는 CSR의 경우에는 FCP가 더 늘어날 것이다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">극단적인 비교를 위해 네트워크 속도제한을 3G로 변경한 뒤 동일하게 뱅크샐러드와 우리 사이트의 FCP를 측정해보면 우리 사이트는 0.4초 그대로 나왔고, 뱅크샐러드는 0.9와 1.0초로 두 번 다 소폭 증가했다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">뱅크샐러드와 우리 프로젝트의 규모가 같냐라고 이야기 할 수 있겠지만, 내 최종 프로젝트보다 1/4 규모의 리액트 프로젝트에서는 FCP가 0.3초 나왔다. 리액트로만 만들어서 넥스트와 비슷하게 FCP를 가져가려면 4배 즈음은 프로젝트 규모를 줄여야 한다고 단순하게 해석해볼 수도 있을 것 같다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">그러면 FCP가 얼마가 되어야 하는 걸까? 라이트하우스 지수도 초록색으로 표기되고 별로 문제처럼 보이지 않는데,</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">언제부터 문제가 되는 걸까? 일단<span>&nbsp;</span><a style="color: #0070d1;" href="https://web.dev/articles/fcp?hl=ko">참고 문서</a>를 하나 링크하겠다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">FCP는 아래와 같은 것이다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1280" data-origin-height="496"><span data-url="https://blog.kakaocdn.net/dn/dFxikl/btsJbIJaTVH/SSzdSRbFt9PDtMwY9pKdRK/img.png" data-phocus="https://blog.kakaocdn.net/dn/dFxikl/btsJbIJaTVH/SSzdSRbFt9PDtMwY9pKdRK/img.png"><img src="https://blog.kakaocdn.net/dn/dFxikl/btsJbIJaTVH/SSzdSRbFt9PDtMwY9pKdRK/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdFxikl%2FbtsJbIJaTVH%2FSSzdSRbFt9PDtMwY9pKdRK%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1280" data-origin-height="496"/></span></figure>
</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">두번째 사진에 FCP라고 표기되어 있는 것을 볼 수 있는데, 처음으로 화면에 요소가 그려지는 순간을 말하는 것이다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">FCP는 1.8초 이내로 유지해야 좋은 지수라고 말한다. 3초 이상부터는 화면이 뜨기 전에 사이트를 꺼버리는 사람들이 등장한다. FCP 3초 이상 부터는 이탈률이 32%로 시작해서 이후에는 초마다 수십 퍼센테이지 씩 이탈율이 증가한다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="384" data-origin-height="288"><span data-url="https://blog.kakaocdn.net/dn/v0fcX/btsJczESh8x/vtrbirGp36SlA0CTQ9WVV1/img.jpg" data-phocus="https://blog.kakaocdn.net/dn/v0fcX/btsJczESh8x/vtrbirGp36SlA0CTQ9WVV1/img.jpg"><img src="https://blog.kakaocdn.net/dn/v0fcX/btsJczESh8x/vtrbirGp36SlA0CTQ9WVV1/img.jpg" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fv0fcX%2FbtsJczESh8x%2FvtrbirGp36SlA0CTQ9WVV1%2Fimg.jpg" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="384" data-origin-height="288"/></span></figure>
</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">그런데 뱅크샐러드 웹 사이트 자체는 규모가 커 보이진 않는다. 네이티브 앱에 모든 기능이 있고 단순히 소개만 하는 페이지처럼 보이기 때문에 메뉴는 많아도 대부분 정적 페이지로 보인다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">만약 하나의 커뮤니티처럼 대규모 프로젝트를 리액트만으로 만들었다면 FCP를 개선하기 위해 엄청나게 스플리팅을 해야 할 것으로 보인다. 이런 것이 단점이기 때문에 Next.js가 인기가 많아졌다라는 것을 말하려고 여기까지 돌아왔다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">그러면 Next.js가 뭘 하길래 FCP가 빠른 걸까?</p>
<h2 style="color: #000000; text-align: start;" data-ke-size="size26">Next.js의 pre-rendering</h2>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1642" data-origin-height="1294"><span data-url="https://blog.kakaocdn.net/dn/cUF8ST/btsJdbKb7ac/CdP6h72s4KSl3ekPAE3yWk/img.png" data-phocus="https://blog.kakaocdn.net/dn/cUF8ST/btsJdbKb7ac/CdP6h72s4KSl3ekPAE3yWk/img.png"><img src="https://blog.kakaocdn.net/dn/cUF8ST/btsJdbKb7ac/CdP6h72s4KSl3ekPAE3yWk/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcUF8ST%2FbtsJdbKb7ac%2FCdP6h72s4KSl3ekPAE3yWk%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1642" data-origin-height="1294"/></span></figure>
</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">렌더링을 이해하기 위한 주요 개념은 CSR 부분에서 다 살펴 봤으니 프리렌더링 과정부터 빠르게 살펴보자. 우리 말로는 사전 렌더링 정도가 되겠다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">FCP, 즉 초기에 화면이 그려지기까지의 과정을 보자.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<ol style="list-style-type: decimal;" data-ke-list-type="decimal">
<li>사용자가 웹 브라우저를 통해 웹 서버에 사이트를 요청한다.</li>
<li>웹 서버는 JS를 실행해서 HTML을 만들어 낸다. 이 과정을 렌더링이라고도 말한다.</li>
<li>이렇게 렌더링 된 HTML을 클라이언트에 보여지면서 HTML이 화면에 그려진다. 즉 사용자가 페이지를 볼 수 있는 상태가 된다.</li>
</ol>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">미리 HTML을 웹 서버가 만들어 두고 브라우저에는 그 HTML을 던져 주니 초기 로딩 속도가 빠를 수밖에 없다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">그런데 이 화면은 화면만 보이는 거고, 자바 스크립트가 전달된 상태가 아니기 때문에 인터렉티브하지는 않다. 즉 버튼 같은 게 클릭이 안 되는 상태라는 의미다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">그래도 의미는 있다. FCP가 일단 빨라야 사용자 입장에서는 사이트가 빠르다고 느낄 것 아닌가? 사이트에 들어오자마자 3초 내에 버튼부터 누르는 사용자가 몇이나 될까? 일단 보여지는 게 중요하다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">그런데 궁금한 게 있다. 어떤 HTML을 렌더링해서 보여준다는 걸까? 모든 페이지를 다 말하는 걸까? 아니다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">Server Side Rendering으로 작동하는 페이지와 Static Side Generation 페이지만 서버가 미리 렌더링 해서 보내주는 것이다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">Next.js에서 'use client' 선언을 한 컴포넌트는 클라이언트가 렌더링 하는 페이지이기 때문에 서버가 렌더링 하지 않는다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">그럼 이런 경우는 어떨까? 페이지 자체는 서버사이드 렌더링 방식으로 제작되어 있는데 안에 import된 모듈 컴포넌트가 전부 client component라면?</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">일단 서버 컴포넌트인 그 페이지 자체는 프리 렌더링이 된다. 그런데 안에 있는 클라이언트 컴포넌트들은 아직 렌더링이 되지 않았으니 비어 있는 &lt;div&gt;로 잡히게 된다. 뭐... 이러면 의미 없다는 것이다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">그런데 여기서 생각해볼 만한 점은 처음 접속했을 때 보여지는 메인 페이지와 또 그 안에서 첫 뷰포트에 보여지는 영역만큼은 프리렌더링이 되는 컴포넌트로 제작해서 초기 로딩 속도가 굉장히 빠른 것처럼 보여지는 것도 하나의 전략이라고 볼 수 있다는 것이다.</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">&nbsp;</p>
<p style="color: #333333; text-align: start;" data-ke-size="size16">자, 그럼 이제 다음 단계로 넘어간다. 화면에 HTML만 보이는 이 상황에서 JS를 주입하여 인터렉티브한 페이지가 되게 하기 위한 과정이 이어서 진행된다. 마치 매말라있던 땅을 촉촉하게 적셔주는 것 같다고 하여 서구권에서는 이를 Hydration이라고 표현한다. 우리 말로는 수화, 수분 공급(?) 정도 되겠다. 이 하이드레이션이라는 단어를 미스트 같은 화장품이나 소화기에서 보던 단어인데 여기서 보니 어색했지만 이런 과정을 이해하고 나니 이해가 편했다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1476" data-origin-height="970"><span data-url="https://blog.kakaocdn.net/dn/6kY0X/btsJdjIbQLb/BAwGVguwDkThYQu2IfJKWk/img.png" data-phocus="https://blog.kakaocdn.net/dn/6kY0X/btsJdjIbQLb/BAwGVguwDkThYQu2IfJKWk/img.png"><img src="https://blog.kakaocdn.net/dn/6kY0X/btsJdjIbQLb/BAwGVguwDkThYQu2IfJKWk/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F6kY0X%2FbtsJdjIbQLb%2FBAwGVguwDkThYQu2IfJKWk%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1476" data-origin-height="970"/></span></figure>
</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">상호작용이 되지 않고 화면만 보이는 매마른 HTML만 있는 페이지에 JS 번들이 도착하고 나서는 인터렉티브한 페이지가 되는 것이다.</p>
<p data-ke-size="size16">즉 프리렌더링 과정에서는 FCP 화면이 처음 보이는 시점과 TTI, JS 번들이 도착하고 인터렉티브가 가능한 페이지가 되는 과정까지 끝나야 비로소 사용자가 웹 사이트를 자유롭게 이용할 수 있게 된다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">그러면 이것저것 다 합치면 결국 리액트 단독의 사이트나 넥스트로 프리렌더링 한 사이트나 사용자가 완전히 이용할 수 있는 시간까지는 같거나 비슷한 것 아니냐라고 생각할 수 있는데 맞다.</p>
<p data-ke-size="size16">하지만 그 시점의 차이일 뿐인데 리액트는 완전히 인터렉티브해서 사이트 이용이 가능할 때 브라우저에 화면을 그려주는 것이고 넥스트는 일단 화면 먼저 보여주고 시작한다는 것이다. 어차피 그게 그거라면 당연히 일단 화면부터 보여주고 시작하는 게 적어도 빨라 보이니 좋지 않겠는가?</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">그러면 JS Bundle이 도착하고 그 이후의 웹 페이지 이동 등의 작업에서는 어떻게 동작할까?</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1478" data-origin-height="972"><span data-url="https://blog.kakaocdn.net/dn/b0Ej42/btsJdqf5TSG/D0z4wVD7wBTGBB46EGTsq1/img.png" data-phocus="https://blog.kakaocdn.net/dn/b0Ej42/btsJdqf5TSG/D0z4wVD7wBTGBB46EGTsq1/img.png"><img src="https://blog.kakaocdn.net/dn/b0Ej42/btsJdqf5TSG/D0z4wVD7wBTGBB46EGTsq1/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fb0Ej42%2FbtsJdqf5TSG%2FD0z4wVD7wBTGBB46EGTsq1%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1478" data-origin-height="972"/></span></figure>
</p>
<p data-ke-size="size16">JS Bundle 파일을 클라이언트에서 가지고 있기 때문에 리액트와 똑같이 작동한다.</p>
<p data-ke-size="size16">사용자가 페이지 이동을 원하면 그 컴포넌트만 갈아 끼우면서 더이상 HTML, CSS, JS 관련해서는 웹서버를 거치지 않고</p>
<p data-ke-size="size16">굉장히 빠르게 동작한다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">여기까지만 보면 Next.js를 사용하지 않을 이유가 없어 보인다.</p>
<h2 data-ke-size="size26">마치며</h2>
<p data-ke-size="size16">다만 Next.js에 회의적인 의견을 접한 분들이라면 이 글에서 Next.js를 너무 찬양하는 듯한 기조를 보여 불편할 수도 있다.</p>
<p data-ke-size="size16">그런데 Next.js가 만능이라는 이야기를 하고 싶은 것이 아니라 "CSR이 가진 문제가 있어 이를 개선한 프레임워크인 Next.js가 인기가 상승중인 것"을 말하고 싶은 것이고,</p>
<p data-ke-size="size16">Next.js의 너무 빠른 버전업그레이드, app router에서 무언가 엉성한 버그가 투성인 것들, vercel에서 배포가 편한 것은 좋은데 반대로 AWS 등에 배포하기 위해서는 너무 고생스럽거나 하더라도 페칭 개수 제한이 있는 듯한 이상한 내용들 등... Next.js의 횡포 아닌 횡포에 remix 등의 프레임워크로 이탈하는 개발자들은 많아도, 이 pre-rendering 방식이 좋지 않다고 말하는 개발자는 그리 많지 않은 것 같다.</p>