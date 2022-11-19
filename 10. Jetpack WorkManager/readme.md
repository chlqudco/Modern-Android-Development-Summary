- 안드로이드의 백그라운드 작업을 하기 위해 만들어짐

- 백그라운드 작업 분류
	- 실행 시점에 따른 분류
		- Exact Timing : 즉시 처리되어야 하는 작업
		- Deferrable : 처리를 위한 조건이 만족될 때까지 기다릴 수 있는 작업
	- 실행 완료 여부에 따른 분류
		- Best-Effort : 처리를 위해 노력하지만 취소될 수도 있는 작업
		- Guaranteed Execution : 앱이 종료되거나 기기가 재부팅되어도 수행되어야 하는 작업
	- 안드로이드는 상황별로 죄선의 API를 제안한다
		- 그림 10 넣기


- 이미 백그라운드 작업 하는 방법이 있는데도 불구하고 왜 만들어졌는지 알기 위해 안드로이드 백그라운드 API의 변천 과정을 알아보자
	- API 18 : AlarmManager를 사용
	- API 19 : AlarmManager이 더이상 정확한 시간에 동작을 안하게 됨
	- Google I/O 2014 - Introduction to Project Volta, 전력소모를 위한 기술을 발표
		- Lazies first
		- JobScheduler,, 백그라운드 작업 시간을 앱이 아닌 시스템이 알아서 판단함.
		- The ART runtime
		- Battery Historian
		- Battery Saver mode
	- API 23(Marshmallow) : Doze and App Standby
	- API 24(Nougat) : Doze on-the-go, Limited implicit broadcasts
	- API 26(Oreo) : Background service limitations, Implicit Broadcast Exceptions, Release cached wakelocks
	- API 28(Pie) : App Standby Buckets, Battery Saver mode
	- API 29(Quince Tart) : Restrictions on starting activities
	- API 30(Red Velvet Cake) : Background location access
	- API 31(Snow Cone) : Foreground service launch restrictions, Phantom Processes
	- 버전마다 서로 다른 백그라운드 정책을 세우는건 말도 안되는 상황
	- 이런 문제를 해결하기 위해 구글이 잡디스패처를 발표


- Firebase JobDispatcher
	- API 9+에서 동작
	- AlarmManager 와 JobScheduler 를 알아서 선택
	- Google Play Service 필요함
	- 따라서 2018년 새로운 WorkManager를 발표함


- WorkManager의 발표
	- Guaranteed, constraint-aware execution : 실행이 보장되며 제약조건을 붙일 수 있습니다. 예를 들면 네트워크 연결시에만 작업이 처리되도록 할 수 있습니다.
	- Respectful of system background restrictions : 장치의 상태를 존중합니다. 예를들어 앱이 도즈모드일 경우 작업 처리를 위해 기기를 깨우지 않습니다.
	- Backwards compatible with or without Google Play Services : 구글 플레이 서비스와 관계없이 동작합니다.
	- Queryable : 작업이 실행/대기중인지? 성공/실패했는지 등의 상태조회를 할 수 있습니다.
	- Chainable : 작업 A, B 결과에 따라 처리되는 작업 C를 만들고, 다시 C의 결과에 의존하는 작업 D를 만들 수 있습니다.
	- Opportunistic : 사용자를 간섭하지 않아도 제약조건이 만족되면 작업이 즉시 실행됩니다.
	- 그림 11 넣기
	- 얘도 마찬가지로 적절한 백그라운드 서비스를 알아서 고르게 함
	- 그림 12 넣기


- WorkManager의 구조
	- 작업 정의: Worker 클래스 상속하여 백그라운드에서 할 일 정의
	- 제약조건 설정
	- WorkRequest 만들기 : 어떤 형식으로 실행되게 할건지, 주기적 or 한번만
	- WorkRequest 제출 : enqueue로 Workmanager에 제출
	- Work States 확인하기 : 작업의 형태에 따라 다른 상태값을 가질 수 있다

