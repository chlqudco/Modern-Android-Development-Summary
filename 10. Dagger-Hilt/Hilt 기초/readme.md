- 안드로이드 의존성 주입 라이브러리 역사
	- 2007년 Guice, 느린 속도와 메모리 문제 발생
	- 2012년 Dagger v1, 속도 느림, 런타임 중에 의존성 주입을 처리한다는 단점
	- 2016년 Dagger v2, 속도 개선, 어노테이션 사용해서 컴파일 타임의 오류를 잡음, 그러나 너무 어려움
	- 2020년 Dagger-Hilt, 쓰기 쉽게 만드는 힐트를 만듬


- Hilt의 구조
	- 동작방식
		- 그림 13 넣기
		- 생명주기를 따르는 컴포넌트라는 보관함을 만들고 그 안에 의존 객체를 생성
	
- Component
	- 3가지 어노테이션을 이용
	- @HiltAndroidApp
		- Application
	- @HiltViewModel
		- ViewModel
	- @AndroidEntryPoint
		- Activity
		- Fragment
		- View
		- Service
		- BroadcastReceiver

- Scope
	- 힐트가 제공하는 객체는 unScoped 상태임, 객체를 요청할 때마다 만듬.
	- 이를 방지하기 위해 Scope라는 생명주기 지정 가능
	- 그림 14 넣기

- 의존성 주입
	- inject 어노테이션을 사용하는 방식에 따라 나뉨
	- Field injection
	- Constructor injection


- Module
	- 정의
		- @Module
		- @InstallIn
	- 생성
		- @Provides
		- @Binds
