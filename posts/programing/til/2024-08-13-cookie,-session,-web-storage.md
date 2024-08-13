<p data-ke-size="size16">쿠키, 세션, 웹 스토리지의 공통점은 모두 웹 사이트가 어떠한 정보를 기억할 수 있도록 도와주는 장치라는 점이다.</p>
<p data-ke-size="size16">사용자가 웹 사이트를 다시 방문했을 때 기존에 입력했던 내용을 기억하거나 로그인 상태를 유지할 수 있게 도와준다.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">그러나 각각의 차이는 아래와 같이 존재한다.</p>
<p data-ke-size="size16">&nbsp;</p>
<h2 data-ke-size="size26">1. 쿠키(Cookie)</h2>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>쿠키는 웹 사이트가 컴퓨터에 저장하는 아주 작은 파일.</li>
<li>로그인한 상태를 유지시키거나 이전에 장바구니에 담아 둔 물건을 기억하는 데 주로 사용됨.</li>
<li>쿠키는 보통 만료 날짜가 있어서 그 시간이 지나면 자동으로 삭제됨.</li>
<li>다른 웹 사이트에서도 사용자의 쿠키를 볼 수 있는 경우가 있어서 사용자의 활동을 추적할 수 있음.</li>
</ul>
<h2 data-ke-size="size26">2. 세션(Session)</h2>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>세션은 웹 사이트가 사용자가 접속해 있는 동안만 정보를 저장하는 방법.</li>
<li>예를 들어 쇼핑몰에서 장바구니에 물건을 담을 때 그 정보는 세션에 저장 됨. 브라우저를 닫거나 일정 시간이 지나면 세션이 끝나고 정보도 사라짐.</li>
<li>세션은 사용자가 웹 사이트를 떠나거나 브라우저를 닫으면 없어진다. 그래서 보안이 중요한 정보(로그인 상태)는 세션에 저장되는 경우가 많다.</li>
</ul>
<h2 data-ke-size="size26">3. 웹 스토리지(Web Storage)</h2>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>웹 스토리지는 웹 사이트가 브라우저 안에 정보를 저장할 수 있는 공간이다.</li>
<li>여기엔 로컬 스토리지와 세션 스토리지 두 가지가 있다.
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li><b>로컬 스토리지(Local Sotrage)</b> : 로컬 스토리지는 정보를 오랫동안 저장할 수 있다. 브라우저를 닫아도 남아 있고 컴퓨터나 기기기에서 웹 사이트에 다시 들어가면 그 정보를 다시 사용할 수 있다.</li>
<li><b>세션 스토리지(Session Storage)</b> : 세션 스토리지는 세션과 비슷하게 브라우저를 닫으면 정보가 사라진다.</li>
</ul>
</li>
<li>웹 스토리지는 쿠키보다 더 많은 정보를 저장할 수 있고, 다른 웹 사이트에서 그 정보를 볼 수 없다. 그래서 조금 더 안전하게 사용할 수 있다.</li>
</ul>