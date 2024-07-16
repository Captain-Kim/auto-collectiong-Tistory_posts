<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="748" data-origin-height="431"><span data-url="https://blog.kakaocdn.net/dn/cqQhBq/btsIASy0dDO/Id5Yte1gZykXdVwfDJqwt0/img.png" data-phocus="https://blog.kakaocdn.net/dn/cqQhBq/btsIASy0dDO/Id5Yte1gZykXdVwfDJqwt0/img.png"><img src="https://blog.kakaocdn.net/dn/cqQhBq/btsIASy0dDO/Id5Yte1gZykXdVwfDJqwt0/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcqQhBq%2FbtsIASy0dDO%2FId5Yte1gZykXdVwfDJqwt0%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="748" data-origin-height="431"/></span></figure>
<figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1024" data-origin-height="785"><span data-url="https://blog.kakaocdn.net/dn/qgzlj/btsIBIoVIm5/91H1cHnW5KEII4596LktL0/img.png" data-phocus="https://blog.kakaocdn.net/dn/qgzlj/btsIBIoVIm5/91H1cHnW5KEII4596LktL0/img.png"><img src="https://blog.kakaocdn.net/dn/qgzlj/btsIBIoVIm5/91H1cHnW5KEII4596LktL0/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fqgzlj%2FbtsIBIoVIm5%2F91H1cHnW5KEII4596LktL0%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1024" data-origin-height="785"/></span></figure>
</p>
<p data-ke-size="size16">부트캠프 과정에서 User Flow를 처음 경험해보았다.</p>
<p data-ke-size="size16">UI/UX 디자이너와 함께 협업을 하면서 처음 접하게 된 개념인데, 사용자가 앱의 어디에서 시작해서 앱의 사용을 종료할 때까지 앱의 다양한 기능과 화면을 통해 어떤 흐름으로 페이지와 기능을 이용하는지 관계도를 나타내는 것이다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">사실 지금까지 웹 사이트를 제작하면서 이 user flow를 고려해가면서 페이지 구성을 하지는 않았다. 그러나 웹 사이트의 정형화된 패턴에서 크게 벗어나지 않게 제작했기 때문에 이 user flow를 후에 작성하더라도 큰 문제는 없었을 것이다. 하지만 user flow를 고려하면서 '분기'도 명시하면서 유저와의 인터렉션도 고려하게 되었다. 또한 user flow를 작성하다 보니 라우트 구조까지 머릿속에 그려졌는데 인증/인가와 관련된 부분까지 한 번에 해결 되는 느낌이라, 간단한 토이 프로젝트를 제작할 때도 이 user flow를 초기에 고려하는 것은 중요하다는 생각이 들었고 적용해보고자 한다.</p>
<p data-ke-size="size16">&nbsp;</p>
<h2 data-ke-size="size26">좋은 user flow란?</h2>
<p data-ke-size="size16">어떤 페이지에서 user의 action이 발생했을 때 여러 갈래로 뻗어 나갈 수 있는 flow를 제공하면 사용자 경험이 오히려 떨어질 수 있다. 특정 페이지나 기능에서 문어발 처럼 엮어 있는 flow를 발생시키면 개발자도 힘들고, 유저도 혼란스러운 결과가 나타나게 된다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">개발자는 웹 사이트에서 엄선된 부분만 제공해서 유저에게 적절한 이용 흐름을 제공하는 것이 중요하다.</p>
<p data-ke-size="size16">&nbsp;</p>
<h2 data-ke-size="size26">user flow를 작성하면 좋은 점</h2>
<p data-ke-size="size16"><b>1. 반복될 만한 작업이 눈에 보인다.</b></p>
<p data-ke-size="size16"><b>2. 이런 흐름을 제공하는 것은 적절하지 않아 보인다는 것이 시각적으로 보인다.</b></p>
<p data-ke-size="size16">이미 개발을 하고 나서 라우트를 바꾸는 것은 엄청난 소요가 발생하는데, 이번에 user flow를 작성하면서도 수차례 fix 과정이 있었다. 이것을 코드 작성하고 나서 발견하게 되었다면 어떤 일이 발생했을지 끔찍하다.</p>
<p data-ke-size="size16"><b>3. 사용자 경험을 높일 수 있다.</b></p>
<p data-ke-size="size16">사실 이 부분이 가장 중요할 것 같다. 개발자의 관점에서 짜기 좋고 편한 코드를 작성하는 것이 아니라 유저가 사이트에 입장하고 나서 부터의 흐름을 정리하다 보니, '유저가 우리 사이트에서 어떤 기능을 원할 것 같은지' 한 번 더 고민해보는 계기를 마련해준다.</p>
<p data-ke-size="size16">&nbsp;</p>
<h2 data-ke-size="size26">user flow를 작성할 때 참고할 만한 점</h2>
<p data-ke-size="size16">명확한 아이콘을 사용하면 좋다. 어떤 분기가 되는 action이 들어가는 것인지, 접근하는 곳이 페이지인지, 컴포넌트인지, 인가가 필요한 곳인지 등을 도형의 모양이나 색상으로 구분하면 보다 더 직관적이다. 개요도 작성해주면 좋다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1024" data-origin-height="836"><span data-url="https://blog.kakaocdn.net/dn/clLYg5/btsIBkvewhT/8uHKSdkCkweVqwcUkWa9EK/img.png" data-phocus="https://blog.kakaocdn.net/dn/clLYg5/btsIBkvewhT/8uHKSdkCkweVqwcUkWa9EK/img.png"><img src="https://blog.kakaocdn.net/dn/clLYg5/btsIBkvewhT/8uHKSdkCkweVqwcUkWa9EK/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FclLYg5%2FbtsIBkvewhT%2F8uHKSdkCkweVqwcUkWa9EK%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1024" data-origin-height="836"/></span></figure>
</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">현재 우리가 초안으로 작성하고 있는 과정은 아래와 같다.</p>
<p><figure class="imageblock alignCenter" data-ke-mobileStyle="widthOrigin" data-origin-width="1604" data-origin-height="888"><span data-url="https://blog.kakaocdn.net/dn/bZMSUc/btsIAVCAXFT/zMYmjRVBDl0GCD42K2pkG0/img.png" data-phocus="https://blog.kakaocdn.net/dn/bZMSUc/btsIAVCAXFT/zMYmjRVBDl0GCD42K2pkG0/img.png"><img src="https://blog.kakaocdn.net/dn/bZMSUc/btsIAVCAXFT/zMYmjRVBDl0GCD42K2pkG0/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbZMSUc%2FbtsIAVCAXFT%2FzMYmjRVBDl0GCD42K2pkG0%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1604" data-origin-height="888"/></span></figure>
</p>