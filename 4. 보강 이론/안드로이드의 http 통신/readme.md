- 안드로이드의 HTTP 통신

- 앱에서 가장 많이 하는 처리중 하나는 서버에 데이터를 요청하고 받아온 데이터를 화면에 표시하는 것
	- 클라이언트와 서버가 통신하는 방식은 크게 소켓 연결과 http 연결로 나눌 수 있다

- 소켓 연결
	- 특정 포트로 연결을 유지하는 시스템, 실시간으로 양방향 통신을 할 수 있음
	- 주로 동영상 스트리밍이나 온라인 게임에서 사용하는 방식
	- 소켓 : 네트워크 상의 두 프로그램 사이에서 일어나는 양방향 통신중 한 쪽의 엔드 포인트
	- 클라이언트와 서버가 특정 포트를 통해 연결을 계속 유지

- HTTP 연결
	- 정의 : HyperText Transfer Protocol의 약자
	- 80번 포트를 사용하여 웹 상에서 정보를 주고받을 수 있는 프로토콜
	- 동작방식
		- 클라이언트가 서버에 헤더(header)와 바디(body)로 이루어진 메시지를 요청(request)
		- 서버는 이 요청을 처리하고 응답코드와 함께 응답(response)을 반환
	- 특징
		- Connectionless : 용건이 끝나면 바로 연결을 끊음, 서버에 여유가 생겨서 더 많은 접속을 처리할 수 있음
		- Stateless : 서버가 클라이언트를 식별할 수 없음. 기억해야 할 경우 쿠키나 세션, 토큰이란 기술을 사용해야 함


- HTTP Method
	- 클라이언트가 서버에 메세지를 보낼 때 어떤 목적으로 가졌는지 밝히는 걸 의미함
	- GET 서버에 리소스를 요청합니다. 서버를 수정하지 않기 때문에 safe method로 분류.
	- HEAD GET과 같지만 서버가 본문(body)을 포함하지 않음.
	- POST 클라이언트에서 요청한 URL에 본문의 내용으로 새로운 리소스를 생성.
	- PUT 클라이언트가 요청한 내용으로 서버의 리소스를 수정.
	- DELETE 서버의 리소스를 삭제.
	- CONNECT 요청 리소스에 대해 양방향 연결을 수립, 예로 프록시를 통한 SSL 연결수립에 사용될 수 있음.
	- OPTIONS 서버가 어떤 HTTP 메소드를 지원하는지 물어봄.
	- TRACE 메시지의 변조여부 확인을 위해, 서버가 수신한 클라이언트의 메시지를 반환하도록 함.
	- PATCH PUT은 리소스 전체를 수정하나, PATCH는 해당 리소스의 일부만을 수정.

- RESTful API
	- 구글 카카오 네이버 등은 자기 회사의 서비스를 이용할 수 있도록 REST Api 라는걸 제공한다
	- REST API란?
		- REST는 HTTP 기반으로 필요한 자원에 접근하는 방식을 정해놓은 네트워크 아키텍처
	- 다음과 같은 기준을 만족하면 RESTful 하다고 말함
		- 클라이언트와 서버의 분리
		- 무상태(Stateless)
		- 캐시 처리가 가능해야 함
		- 시스템이 계층화(Layered) 되어있어야 함
		- 일관성 있는 인터페이스

---

- Android HTTP Client의 역사
	- 안드로이드는 HTTP 통신을 구현하는 여러가지 라이브러리가 있었다.

- HttpClient
	- Apache에서 제작한 라이브러리
	- 안드로이드 초기에 주로 사용되었으며 실제로는 HttpClient를 래핑한 DefaultHttpClient나, 안드로이드에 맞게 개수한 AndroidHttpClient가 사용됨.
	- 변경점을 안드로이드 SDK에 일괄적으로 즉시 반영할 수 없었음
	- 따라서 버전이 뒤쳐지면서 계속 버그가 발생하였다
	- Android 5.1에서 Deprecated 되며 6.0에서는 아예 삭제되었음
	- 이 시기 클라이언트의 버그는 네이버 D2 블로그 Android의 HTTP 클라이언트 라이브러리에 잘 정리되어 있음


- HttpUrlConnection
	- HttpClient를 삭제하면서 구글에서 제시한 대안
	- 기존의 URLConnection에 HTTP를 다루는데 필요한 메서드를 추가한 클래스

- Volley
	- HttpUrlConnection 사용에 많은 불편함이 있어 만든 라이브러리
		- ANR 을 피하기 위해 백그라운드 쓰레드를 만들어야 함
		- 버퍼를 통한 입출력을 준비
		- 캐시나 예외처리를 한땀한땀 준비해야 함
	- 많은 특징을 갖고 있다

- OkHttp
	- http 클라이언트 라이브러리
	- 특징
		- HTTP/2 support allows all requests to the same host to share a socket.
		- Connection pooling reduces request latency (if HTTP/2 isn’t available).
		- Transparent GZIP shrinks download sizes.
		- Response caching avoids the network completely for repeat requests.

- Retrofit
	- Okhttp 만든 회사에서 개발한 라이브러리
	- HttpURLConnection 를 사용하기 편하게 매핑한게 Volley 라면
	- OkHttp를 매핑한것이 Retrofit

- Ktor
	- 제트브레인에서 개발
	- 코틀린을 이용해 비동기 서버와 클라이언트를 구축할수 있게 해주는 라이브러리
	- 활발한 업데이트가 이루어지고 있다

```

Volley or Retrofit?

둘다 꾸준히 업데이트를 하고 있다
속도 만으로 어느 한쪽을 선택하는건 어렵다
가독성은 대부분 레트로핏이 높다는 평가가 있다

Function 			Volley 		Retrofit
Automatic Parsing 		No 		Yes
Caching 				Yes 		No
Retrying 				Yes 		No
Post Requests & Multipart uploads	Yes 		Partly
Image Loading 			Built-in 		No

```
