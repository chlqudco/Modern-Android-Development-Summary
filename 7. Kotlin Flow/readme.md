- Flow란
	- 중간 중간 갱신되는 코루틴 중에 갱신되는 값까지 반환받기 위함
	- suspend 가능한 Iterator
	
- Flow의 동작
	- 프로듀서가 비동기 적으로 값을 생성하면 컨슈머는 전달받은 값을 소모한다


- Flows are cold
	- 코루틴에서 flow는 콜드스트림, 채널은 핫스트림이라고 말함
	- 값을 요청하지 않는 한 값을 방출하지 않는다. 이걸 콜드 스트림이라고 함
	- 청취자가 듣던 말던 방송은 일단 하는 라디오는 핫스트림, CD같이 듣는 사람이 직접 재생해야 하는게 콜드 스트림

- Flow vs Livedata
	- 플로우는 Coroutine Scope 안에서 사용해야 함
	- 플로우는 풍부한 Operator가 있어서 필요에 따라 데이터를 유연하게 변환할 수 있음
	- 코틀린에 포함된 기능이라 Android Dependency가 필요 없음



- Flow vs Livedata
	- Livedata
		- 생명주기를 가진 데이터 홀더
		- 메인스레드에서 동작
		- 안드로이드와 밀접하게 연결되어 있음, 테스트가 까다로움.
	- Flow
		- CoroutineScope 안에서 동작, 필요에 따라 적당한 쓰레드를 고를 수 있음
		- 안드로이드 라이프사이클 감지가능
		- 안드로이드 의존성 제거가능
		- Cold stream
		- 상태가 없음


- Sharedflow로 Livedata 대체하기
	- 핫스트림으로 동작하게 만든 플로우의 한 종류
	- SharedFlow
	- StateFlow, 플로우에 상태를 부여한 데이터홀더, 요즘 부상하는 친구.
