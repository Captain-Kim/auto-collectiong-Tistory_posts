<p data-ke-size="size16">여러 이유로 유튜브에서 몇 시간짜리 영상을 검토해야 하는 일이 올 수 있다.</p>
<p data-ke-size="size16">그런데 몇 십분이면 그걸 다 보고 있겠지만 십 수 시간이 되는 경우 영상을 다 보고 있는 것도 고통스럽지 않겠는가.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">Whisper AI나 vrew 같은 툴을 써서 보다 정확한 자막을 추출해낼 수 있지만, 복잡하고 또 돈이 들기 때문에</p>
<p data-ke-size="size16">그 정도는 아니고 대강 정도만 파악이 필요한 경우 웹 브라우저의 개발자 도구만으로도 자막과 타임스탬프를 추출할 수 있다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">단 유튜브에서 자동자막을 생성해준 경우만 가능하다.</p>
<p data-ke-size="size16">웬만하면 자동자막이 잘 생성이 되지만, 여러 언어가 섞여 있거나 음질이 좋지 않은 경우에는 자동자막이 생성되지 않는 것 같다.</p>
<p data-ke-size="size16">그런데 우리나라 영상에서는 그런 경우를 잘 못 봤고 인도인 유튜브에서 그런 현상이 많았던 것 같다.</p>
<p data-ke-size="size16">&nbsp;</p>
<h2 data-ke-size="size26">유튜브 들어가기</h2>
<p data-ke-size="size16">먼저 본인이 자막을 추출해야 할 유튜브 동영상을 들어가보자.</p>
<p data-ke-size="size16">그리고 설명란에 보면 스크립트 보기라는 버튼이 있다.</p>
<p data-ke-size="size16">이것을 눌러보면 우측에 타임스탬프를 포함해서 자동생성된 자막이 뜬다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="2324" data-origin-height="748"><span data-url="https://blog.kakaocdn.net/dn/doMMDf/btsJdARWNXH/FAhXlAxckiWMeoFiIPguG1/img.png" data-phocus="https://blog.kakaocdn.net/dn/doMMDf/btsJdARWNXH/FAhXlAxckiWMeoFiIPguG1/img.png"><img src="https://blog.kakaocdn.net/dn/doMMDf/btsJdARWNXH/FAhXlAxckiWMeoFiIPguG1/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdoMMDf%2FbtsJdARWNXH%2FFAhXlAxckiWMeoFiIPguG1%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="2324" data-origin-height="748"/></span></figure>
<figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1206" data-origin-height="1490"><span data-url="https://blog.kakaocdn.net/dn/bDt2Jc/btsJdq9uMJs/yQUXKO98oMoeQNYx0INas0/img.png" data-phocus="https://blog.kakaocdn.net/dn/bDt2Jc/btsJdq9uMJs/yQUXKO98oMoeQNYx0INas0/img.png"><img src="https://blog.kakaocdn.net/dn/bDt2Jc/btsJdq9uMJs/yQUXKO98oMoeQNYx0INas0/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbDt2Jc%2FbtsJdq9uMJs%2FyQUXKO98oMoeQNYx0INas0%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" width="339" height="419" data-origin-width="1206" data-origin-height="1490"/></span></figure>
</p>
<p data-ke-size="size16">정확하게 무슨 말인지 알기 어렵지만 대략적으로 이 타이밍에 이런 말을 하고 있구나 정도는 파악할 수 있다.</p>
<p data-ke-size="size16">물론 내가 추출하고자 하는 영상이 시끄러운 환경이고 전문 방송인처럼 발음이나 오디오 녹음 품질이 좋은 것은 아니라</p>
<p data-ke-size="size16">좀 더 심각하게 보이긴 한다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">그러면 이것을 txt 파일로 다운로드 받아보도록 하자.</p>
<h2 data-ke-size="size26">개발자도구 열기</h2>
<p data-ke-size="size16">브라우저에서 마우스 우클릭을 해서 개발자도구를 열거나 F12를 눌러 개발자도구를 연다.</p>
<p data-ke-size="size16">MacOS에서는 검사라고 뜰 수 있다. Windows는 뭐라고 뜨는지 잘 모르겠는데 아마 위치도 비슷할 것이다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="868" data-origin-height="462"><span data-url="https://blog.kakaocdn.net/dn/bHSHka/btsJeOVDoRk/K22lsCpirZdO7GDT6S6KEk/img.png" data-phocus="https://blog.kakaocdn.net/dn/bHSHka/btsJeOVDoRk/K22lsCpirZdO7GDT6S6KEk/img.png"><img src="https://blog.kakaocdn.net/dn/bHSHka/btsJeOVDoRk/K22lsCpirZdO7GDT6S6KEk/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbHSHka%2FbtsJeOVDoRk%2FK22lsCpirZdO7GDT6S6KEk%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" width="415" height="221" data-origin-width="868" data-origin-height="462"/></span></figure>
<figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="3650" data-origin-height="1976"><span data-url="https://blog.kakaocdn.net/dn/mkCFk/btsJd6W6QDu/QGIckH5On1yMN0IA3NKMzk/img.png" data-phocus="https://blog.kakaocdn.net/dn/mkCFk/btsJd6W6QDu/QGIckH5On1yMN0IA3NKMzk/img.png"><img src="https://blog.kakaocdn.net/dn/mkCFk/btsJd6W6QDu/QGIckH5On1yMN0IA3NKMzk/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FmkCFk%2FbtsJd6W6QDu%2FQGIckH5On1yMN0IA3NKMzk%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="3650" data-origin-height="1976"/></span></figure>
</p>
<p data-ke-size="size16">위 사진을 보고 개발자도구에서 소스코드 패널까지 잘 뜨는지 확인한다.</p>
<p data-ke-size="size16">그리고 그 소스코드를 잘 살펴보면 아래와 같이 되어 있을 것이다.</p>
<p data-ke-size="size16">소스코드에 마우스 클릭을 하면 전체 선택이 된 것처럼 보이는데 ctrl+C로 복사가 가능하다.</p>
<pre id="code_1724405350389" class="html xml" data-ke-language="html" data-ke-type="codeblock"><code>&lt;div class="segment style-scope ytd-transcript-segment-renderer" role="button" tabindex="0" aria-label="5분 20초 죄송합니다 쉬지 않고 한 다섯 시간 가야"&gt;
  &lt;div class="segment-start-offset style-scope ytd-transcript-segment-renderer" tabindex="-1" aria-hidden="true"&gt;
    &lt;div class="segment-timestamp style-scope ytd-transcript-segment-renderer"&gt;
      5:20
    &lt;/div&gt;
  &lt;/div&gt;
  &lt;dom-if restamp="" class="style-scope ytd-transcript-segment-renderer"&gt;&lt;template is="dom-if"&gt;&lt;/template&gt;&lt;/dom-if&gt;
  &lt;yt-formatted-string class="segment-text style-scope ytd-transcript-segment-renderer" aria-hidden="true" tabindex="-1"&gt;죄송합니다 쉬지 않고 한 다섯 시간 가야&lt;/yt-formatted-string&gt;
  &lt;dom-if restamp="" class="style-scope ytd-transcript-segment-renderer"&gt;&lt;template is="dom-if"&gt;&lt;/template&gt;&lt;/dom-if&gt;
&lt;/div&gt;</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">여기에서 우리에게 필요한 것은</p>
<p data-ke-size="size16">&nbsp;</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1976" data-origin-height="824"><span data-url="https://blog.kakaocdn.net/dn/cjQt9k/btsJfkfvI5m/p1LpISGpHSSbi4vQNlMwX1/img.png" data-phocus="https://blog.kakaocdn.net/dn/cjQt9k/btsJfkfvI5m/p1LpISGpHSSbi4vQNlMwX1/img.png"><img src="https://blog.kakaocdn.net/dn/cjQt9k/btsJfkfvI5m/p1LpISGpHSSbi4vQNlMwX1/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcjQt9k%2FbtsJfkfvI5m%2Fp1LpISGpHSSbi4vQNlMwX1%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1976" data-origin-height="824"/></span></figure>
</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">이렇게 세 개이다.</p>
<p data-ke-size="size16">웹 페이지를 구성하는 HTML이라는 이 마크업 언어에 대해서 잘 모르시는 분들을 위해 간단하게만 설명하자면,</p>
<p data-ke-size="size16">위에서 표시한 것들은 화면에서 특정 정보들을 구분해주는 고유한 이름 같은 것으로 사용되는 것이라고 보면 된다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">그러니까 자막이 매번 다른 내용이고 시간도 전부 다른데, 그 자막들의 내용들을 추출하려면 그 자막들을 가리키는 이름이 있어야 한다는 것이다.</p>
<p data-ke-size="size16">맨 위에 긴 class는 시간: 자막내용 이 전체의 이름을 말하는 것이고,</p>
<p data-ke-size="size16">아래 segment-timestamp, segment-text는 시간과 자막 내용을 말하는 것이다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">우리는 사긴과 자막을 각각 같이 저장할 것이기 때문에 이 둘이 필요한 것이고 타임스탬프가 필요 없으면 안 써도 된다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">저것을 아래 소스코드에 갈아 끼우면 된다.</p>
<p data-ke-size="size16">그런데 저것 그대로 쓰는 것이 아니라 공백 없이 붙여 쓰고 또 class를 지칭할 때는 마침표를 붙여주기 때문에</p>
<p data-ke-size="size16">실제 본인이 사용했던 소스코드를 그대로 넣겠다. 잘 보고 지금 본인의 상황과 다르다면 바꿔 끼워 주시길 바란다.</p>
<h2 data-ke-size="size26">자바스크립트 소스 코드</h2>
<pre id="code_1724404472310" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// 타임스탬프와 자막을 담을 배열
const subtitles = [];
<p>// 각 자막 세그먼트를 선택
const elements = document.querySelectorAll('.segment.style-scope.ytd-transcript-segment-renderer');</p>
<p>// 각 요소에서 타임스탬프와 자막 텍스트를 추출
elements.forEach((element) =&gt; {
const timestamp = element.querySelector('.segment-timestamp').textContent.trim();
const text = element.querySelector('.segment-text').textContent.trim();
subtitles.push(<code>${timestamp}: ${text}</code>);
});</p>
<p>// 배열을 문자열로 변환, 각 줄은 새로운 자막
const subtitlesText = subtitles.join('\n');</p>
<p>// 텍스트 파일로 저장하는 함수
function saveTextAsFile(text, filename) {
const blob = new Blob([text], { type: 'text/plain' });
const link = document.createElement('a');
link.href = URL.createObjectURL(blob);
link.download = filename;
link.click();
URL.revokeObjectURL(link.href);  // 다운로드 후 URL 해제
}</p>
<p>// 자막을 &quot;subtitles.txt&quot;라는 이름으로 저장
saveTextAsFile(subtitlesText, 'subtitles.txt');</code></pre></p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">파일 이름도 본인이 설정할 수 있으니 설정하시고,</p>
<p data-ke-size="size16">배열을 문자열로 변환하고 텍스트 파일로 저장하는 부분을 보면 뭐 여러가지 응용을 할 수 있을 것 같아 보이는데,</p>
<p data-ke-size="size16">파일 이름을 영상 제목으로 바꾸고 싶어졌다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">위에서 했던 방법을 그대로 응용해서 영상 제목 부분을 가리키는 고유한 이름인 class명을 가져오면 된다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="2678" data-origin-height="1456"><span data-url="https://blog.kakaocdn.net/dn/N1wVs/btsJeaybYWS/nFYXvqdy0CSVef2Uk2wi3K/img.png" data-phocus="https://blog.kakaocdn.net/dn/N1wVs/btsJeaybYWS/nFYXvqdy0CSVef2Uk2wi3K/img.png"><img src="https://blog.kakaocdn.net/dn/N1wVs/btsJeaybYWS/nFYXvqdy0CSVef2Uk2wi3K/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FN1wVs%2FbtsJeaybYWS%2FnFYXvqdy0CSVef2Uk2wi3K%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="2678" data-origin-height="1456"/></span></figure>
</p>
<p data-ke-size="size16">&nbsp;</p>
<h2 data-ke-size="size26">최종 소스코드</h2>
<pre id="code_1724406564103" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>// 모든 해당 클래스의 요소를 선택
const dateElements = document.querySelectorAll('span.style-scope.yt-formatted-string.bold');
<p>// 파일 제목을 생성 (제목 요소를 정확하게 선택)
const youtubeTitle = document.querySelector('yt-formatted-string.style-scope.ytd-watch-metadata').textContent.trim();
const fileName = <code>${youtubeTitle}.txt</code>;</p>
<p>// 타임스탬프와 자막을 담을 배열
const subtitles = [];</p>
<p>// 각 자막 세그먼트를 선택
const elements = document.querySelectorAll('.segment.style-scope.ytd-transcript-segment-renderer');</p>
<p>// 각 요소에서 타임스탬프와 자막 텍스트를 추출
elements.forEach((element) =&gt; {
const timestamp = element.querySelector('.segment-timestamp').textContent.trim();
const text = element.querySelector('.segment-text').textContent.trim();
subtitles.push(<code>${timestamp}: ${text}</code>);
});</p>
<p>// 배열을 문자열로 변환, 각 줄은 새로운 자막
const subtitlesText = subtitles.join('\n');</p>
<p>// 텍스트 파일로 저장하는 함수
function saveTextAsFile(text, filename) {
const blob = new Blob([text], { type: 'text/plain' });
const link = document.createElement('a');
link.href = URL.createObjectURL(blob);
link.download = filename;
link.click();
URL.revokeObjectURL(link.href);  // 다운로드 후 URL 해제
}</p>
<p>// 생성된 파일 이름으로 자막을 저장
saveTextAsFile(subtitlesText, fileName);</code></pre></p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">이걸 콘솔창에 넣고 엔터를 치면 파일 탐색기가 열리면서 로그가 잘 다운로드 되는 것을 볼 수 있다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1196" data-origin-height="744"><span data-url="https://blog.kakaocdn.net/dn/bg9vi8/btsJeNCxems/TSZW8QoVaxAkBiyC77sLl0/img.png" data-phocus="https://blog.kakaocdn.net/dn/bg9vi8/btsJeNCxems/TSZW8QoVaxAkBiyC77sLl0/img.png"><img src="https://blog.kakaocdn.net/dn/bg9vi8/btsJeNCxems/TSZW8QoVaxAkBiyC77sLl0/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fbg9vi8%2FbtsJeNCxems%2FTSZW8QoVaxAkBiyC77sLl0%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1196" data-origin-height="744"/></span></figure>
</p>