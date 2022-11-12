- 코루틴의 개념
	- 이전까지는 AsyncTask를 사용해서 손쉬운 비동기 프로그래밍을 했다
	- 그러나 얘는 메모리 누수등 여러가지 문제가 있었다
	- 따라서 deprecated 되었다. API 30 부터.
	- 대체재로 코루틴을 권장!

- 루틴이란?
	- 프로그램의 흐름 그 자체를 말함
	- 메인루틴 : main 함수에 의해 실행되는 흐름으로 비유
	- 서브루틴 : main 함수에서 실행되는 개별 함수가 실행하는 흐름
	- 코루틴 : 일직선 적인 흐름을 suspend로 지연을 시키고 재시작 하는 것이 가능함, 한 루틴이 다른 루틴이 일을 처리하는 동안 잠시 멈춰 있을 수 있는 비동기 프로그래밍 방식
	- 결국 함수도 하나의 루틴이다

- 코루틴과 스레드
	- 코루틴은 쓰레드가 아님, 이 둘의 차이를 알아보자
	- 메모리 구조의 차이
		- 코루틴은 쓰레드 스택을 할당받지 않고 힙메모리를 공유
		- 코루틴은 그래서 함수에 더 가까움
	- 수행방식의 차이
		- 코루틴은 비선점형, 쓰레드는 선점형 멀티태스킹이다
		- 쓰레드는 멀티코어로 동시에 작업이 가능하다. 병렬성이라고 한다
		- 코루틴은 두개의 코루틴이 같이 실행되지는 않는다. 코루틴이 전환되면서 수행되는 속도가 빠르기 때문에 외부에서는 동시에 수행되는 것처럼 보인다. 따라서 동시성은 있지만 병렬성은 없다.
	- 코루틴의 장점
		- 3개의 쓰레드가 필요한 작업을 3개의 코루틴으로 대체한다고 생각해보자
		- 쓰레드마다 할당해야 했던 스택을 할 필요가 없어진다. 따라서 메모리 사용량이 적어짐
		- 또한 컨텍스트 스위칭이 필요 없으므로 오버헤드가 줄어든다
	- 하나의 스레드에서 여러개의 코루틴을 돌게 할 수 있으므로 쓰레드 개수를 적게 생성할 수도 있다.
	- 코틀린에서의 사용법
		- 함수 앞에 suspend를 붙이면 된다
		- suspend 붙은 함수는 중간에 멈추고 다른 일을 하다가 다시 시작할 수 있음
		- CPS로 변환됨, OS가 관리하도록 위임함

- 코루틴 구조
	- 제일 큰 범위는 코루틴 스코프, 그 다음이 컨텍스트, 맨 아래가 빌더
	- CoroutineScope
		- 코루틴이 어떤 범위에서 동작하는지 규정
	- CoroutineContext
		- 어떤 쓰레드에서 코루틴을 돌릴지
	- CoroutineBuilder
		- 작업을 수행하고 리턴을 결정하는 곳

- CoroutineScope
	- 코루틴이 동작하는 범위 규정
	- CoroutineScope : 코루틴 컨텍스트를 갖고 있는 인터페이스임
	- GlobalScope : 사용 X, 싱글톤이기 때문에 최상위 레벨에서 생성됨. 쓰고 버리고 하는 방식이 불가능함.

- CoroutineContext
	- 코루틴은 컨텍스트 안에서 실행되어야 함
	- 디스패쳐와 잡으로 구성되어 있음
	- Dispatchers
		- 코루틴이 실행되는 쓰레드를 지정
		- Default : CPU 연산 작업용
		- IO : 파일이나 네트워크 접근 용
		- Main : UI 작업용
		- Unconfined : 무시
	- Job&Deferred
		- 코루틴 작업을 Job이나 Deferred 라는 오브젝트로 다룸
		- Deferred는 결국 결과를 갖고 있는 Job일 뿐임
		- 코루틴이라는 추상적인 흐름을 Job이라는 오브젝트로 만들어서 사용함
		- 취소나 예외처리를 함으로써 흐름제어를 용이하게 할 수 있다. 
		- States : 여러 상태로 관리할 수 있다. isActive, isCompleted, inCancelled 플래그를 통해 현재 코루틴 상태가 어떤지 볼 수 있다
		- methods
			- cancel ,join ,start


- CoroutineBuilder
	- 이제 코루틴을 만들고 시작해보자
	- launch
		- Job 객체 반환
	- async
		- Deferred객체 반환
	- runBlocking
		- 사용 X, 돌아가는 메인쓰레드를 블럭시켜 버리고 지가 할일 함
		- 테스트 용도로만 사용
	- withContext
		- Dispatcher switch용도


- 코루틴을 지연하자
	- delay, 인자로 보낸 시간동안 해당 코루틴을 실행안함. 해당 쓰레드를 멈추는게 아님.
	- join, launch로 실행한 코루틴을 끝날 때까지 기다리게 하자
	- await, async용 join


- 코루틴 취소
	- cancel : Job을 캔슬링 State로 변화시킨다
	- cancelAndJoin : 캔슬링 다음인 캔슬드 상태까지 가게 해준다
	- withTimeout : 설정된 시간이 지나면 실패! 취소하고 예외 반환
	- withTimeoutOrNull : 예외가 아닌 널을 반환


- 예외 처리
	- CoroutineExceptionHandler를 이용하여 코루틴 내부의 기본 catch block으로 사용할 수 있다.
	- launch,actor : exception발생시 바로 예외가 발생.
	- async,produce : 중간에 exception이 발생해도 await를 만나야 예외 발생
	- Job.cancel()을 제외한 다른 exception이 발생하면 부모의 코루틴까지모두 취소시킴.이는 structured concurrency를 유지하기 위함으로 CoroutineExceptionHandler를 설정해도 막을 수 없다.
	- 여러개의 exception이 발생하면 가장 먼저 발생한 exception이 handler로 전달되며 나머지는 무시된다.


- 정리
	- 코루틴은 쓰레드가 아님. 경량의 비동기 프로그래밍 도구임
	- 코루틴을 사용하기 위해 CoroutineScope, 컨텍스트, 빌더를 사용해야 함
	- 디스패처 선택 : CPU 작업인가 IO 작업인가? Default or IO
	- 코루틴 처리후 값이 나와야 하는가 ? launch or async
