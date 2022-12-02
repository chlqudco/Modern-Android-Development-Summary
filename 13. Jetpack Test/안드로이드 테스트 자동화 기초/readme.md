- 테스트는 소프트웨어 개발과 함께 시작된 행위
	- 긴 역사를 갖고 있음

- 들어가기
	- The History of Software Testing
		- 1822년 찰스 베비지의 차분 엔진 제작에서 시작
		- 토마스 에디슨이 1878년 동료에게 보내는 편지에서 버그라는 단어 탄생
	- 테스트 방법론
		- 서로 대립하는 주장이 긴 시간 이어짐
		- 피라미드 vs 아이스크림 콘 형태
		- 테스트 커버리지 100% 를 목표? vs 100%를 목표하는건 무의미?
		- 테스트 먼저 vs 구현 먼저
	- 모든 주장은 나름의 논리가 있다. 그래서 그냥 테스트 하는 법만 설명함

- 테스트 자동화의 필요성
	- 안드로이드 코드를 작성하면 필연적으로 테스트를 수행해야 함
	- 앱을 실행하는 것도 당연히 테스트임

- 테스트 유형
	- 기능 테스트 : 내 앱이 기능을 수행합니까?
	- 성능 테스트 : 빠르고 효율적으로 수행합니까?
	- 접근성 테스트 : 접근성 서비스와 잘 작동합니까?
	- 호환성 테스트 : 모든 기기와 API 수준에서 잘 작동합니까?

- 수동 테스트
	- 앱의 기능이 많아지고 복잡해지면 이런 수동 테스트는 안좋음
	- 빌드시간 증가, 비용 증가함

- 자동 테스트를 하자!
	- 컴퓨터가 자동으로 테스트 해주는 것을 테스트 자동화라고 함
	- 장점 : 개발시간 감소, 비용 절감, 견고한 구조가 됨


- 자동 테스트의 분류
	- 테스터 입장에서의 분류
		- 블랙박스 테스트 : 소프트웨어의 구조나 작동원리를 모르는 상태에서 요구사항을 만족하는지 검사, 사용자 입장의 테스트
		- 화이트박스 테스트 : 블랙박스의 반대, 개발자 입장의 테스트
		- 테스트 자동화는 두 방식 모두 사용
 
	- 구글의 분류
		- 유닛테스트, 인테그레이션테스트, 엔드투엔트테스트, 앱 단위로 진화함
		- 뒤로 갈수록 충실도는 증가, 실행 시간 과 유지보수 및 디버깅 시간이 늘어감
		- 따라서 유닛테스트를 가장 많이 작성함

- 단위 테스트 (Unit Test)
	- 앱의 메서드 또는 클래스와 같은 작은 단위의 기능을 검증
	- 범위가 작아서 작성이 수월하고 속도가 빠름
	
- 로컬 단위 테스트 (Local Unit Test)
	- Android Framework에 의존하지 않고 로컬 JVM에서 실행되는 테스트
	- 실제 기기나 에뮬레이터를 사용하지 않으므로 테스트 속도가 빠름

- 계측 단위 테스트 (Instrumented Unit Test)
	- Android Framework에 의존하는 기능을 검증하는 단위 테스트
	- 실제 기기 또는 에뮬레이터에서 실행해야 하기 때문에 실행시간이 오래 걸림


- 통합 테스트 (Intergration Test)
	- 서로 다른 모듈 또는 클래스 간의 상호작용이 정상적으로 기능하는지를 검증
	- 단위 테스트는 각각 기능이 정상적인지 체크할 뿐
	- 동시에 모듈이 잘 작동하는지도 반드시 체크해야 함

- 종단간 테스트 (End-to-end Test)
	- 앱의 전체 화면 또는 여러 모듈에 걸친 사용자 흐름과 같은 큰 부분에 대한 기능 검증을 수행
	- UI 테스트라 부르기도 함


- 테스트 사이즈
	- 단위, 통합, 종단간 테스트는 모호하게 들릴 수도 있음
	- 따라서 구글은 사이즈를 기준으로 테스트를 구분함
	- 스몰, 미디움, 라지 


- 테스트 기본 원칙
	- Seven Testing Principles : 7가지 테스트의 원칙
		- Testing shows the presence of defects, not their absence : 테스팅은 결함의 존재를 보여주는 것이다.
		- Exhaustive testing is impossible : 완벽한 테스트는 불가능하다.
		- Early testing saves time and money : 테스트 구성은 가능한 빠르게 시작한다.
		- Defects cluster together : 결함은 군집되어 있다.
		- Beware of the pesticide paradox : 살충제 역설 - 비슷한 테스트가 반복되면 새로운 결함을 발견할 수 없다.
		- Testing is context dependent : 테스팅은 문맥에 의존적이다.
		- Absence-of-errors is a fallacy : 오류 부재의 궤변 - 사용되지 않는 시스템이나 사용자의 기대에 부응하지 않는 기능의 결함을 찾고 수정하는 것은 의미가 없다.

	- F.I.R.S.T Principles : 로버트 마틴이 만든 원칙
		- Fast : 단위 테스트는 빨라야 한다.
		- Isolated : 테스트가 다른 테스트 케이스에 의존하지 않아야 한다.
		- Repeatable : 테스트는 실행할 때마다 같은 결과를 만들어야 한다.
		- Self-validating : 테스트 결과는 성공이거나 실패여야 한다. 결과에 대한 해석이 필요해서는 안된다.
		- Timely : 단위 테스트는 기능이 출시된 후에도 언제든 작성할 수 있지만 적절한 시점은 프로덕션 코드를 구현하고 있는 와중에 테스트 코드를 작성하는 것이다.


- 테스트 코드 작성 스타일
	- Given-When-Then 스타일, 마틴 파울러가 제안
		- Given : 어떠한 상태하에서, x = 1
		- When : 어떠한 기능을 실행하면, 
		- Then : 어떠한 결과가 나와야 한다.


- Test Double
	- 실제 구성요소 대신 테스트를 수행하는 객체
	- xUnit Test Patterns의 저자인 제라드 메스자로스(Gerard Meszaros)가 만든 용어
	- F.I.R.S.T Principles의 Isolated의 원칙을 따르면 테스트 대상이 의존하는 것을 실제가 아닌 다른 것으로 대체
	- 어떤 순서로든 테스트 실행이 가능해야 함
	- 아래로는 Test Double의 구성요소

- Dummy
	- 가장 기본적인 Test Double
	- 기능을 구현하지 않은 객체
	- 인스턴스는 필요하지만 기능까지는 필요하지 않은 경우에 사용


- Stub
	- 더미가 실제로 동작하는 것처럼 만들어 놓은 객체
	- 인터페이스 혹은 클래스를 최소한으로 구현하고, 결과는 특정 상태를 가정해서 하드코딩된 값을 제공
	- 상태 기반 테스트(State-based testing)에 사용 : 객체에 함수를 적용하기 전과 후의 상태 비교


- Spy
	- Stub과 비슷한 객체인데 추가적인 정보를 더 기록할 수 있게 구성
	- 메소드가 잘 호출 되었는지, 몇번 호출되었는지 확인에 사용
	- 어떤 메소드 A가 호출 되었을 때 또 다른 메소드 B가 실행이 되었는지 확인하는 등의 행위 기반 테스트 (Interaction-based-testing)에 사용


- Fake
	- 동작하는 구현이 있기에 테스트에는 사용할 수 있지만 프로덕션 구현과 동일하지는 않은 객체
	- 가볍기 때문에 구글에서 추천

- Mock
	- 스파이 처럼 행위기반에 사용되는 테스트 더블
	- Spy는 메소드 A와 B의 실제 동작을 추적, Mock은 A가 실행되면 그냥 B의 정상 작동값을 반환하도록 구성
	- Mock 전용 라이브러리가 있다?

- 구글에서 제안하는 테스트 대상 항목
	- 단위 테스트 대상
		- ViewModels 또는 Presenter
		- 데이터 레이어
		- 유즈 케이스
		- 값을 계산하는 유틸리티 클래스
	- 엣지 케이스
		- 음수, 0 및 경계 조건 을 사용하는 수학 연산
		- 가능한 모든 네트워크 연결 오류
		- 형식이 잘못된 JSON과 같은 손상된 데이터
		- 파일 저장시 스토리지가 가득 찬 상황
		- 프로세스 중간에 다시 생성된 개체(예: 장치가 회전할 때의 액티비티)
	- UI 테스트
		- 스크린 UI
		- 유저 플로우
		- 내비게이션
	- 테스트 제외 대상
		- 프레임워크 자체의 동작
		- activities, fragments, 혹은 services에는 테스트가 필요한 로직을 가능한 배치하지 않음


- 안드로이드에서 쓸 수 있음 테스트 라이브러리
	- Testing Framework
		- JUnit4 : Java의 단위 테스트 코드를 작성하기 위해 만들어진 프레임워크로 Jetpack Test 라이브러리는 JUnit4를 기준으로 만들어져 있음. 현재 최신 버전은 JUnit5이나, 안드로이드를 완벽히 지원하지 않음.
		- Kotest : Kotlin의 단위테스트 코드를 작성하기 위해 만들어진 프레임워크.
		- Roboletric : JVM 만으로 안드로이드 프레임워크를 테스팅하기 위해 만들어진 프레임워크.

	- Assertion : 테스트된 값이 맞는지 아닌지..
		- JUnit은 표현력이 부족함. 그 단점을 메워줌
		- Assertion의 표현력이 부족한 JUnit의 단점을 메워주는 라이브러리
		- AssertJ
		- Truth
		- Hamcrest
	- Mocking
		- Mockito : Java 테스트를 위한 Mocking 라이브러리
		- MockK : Kotlin 테스트를 위한 Mocking 라이브러리
	- UI Testing
		- Espresso : 단일 안드로이드 앱의 UI를 테스트하는 프레임워크
		- Kaspresso : KasperskyLab에서 제작한 안드로이드 앱 UI 테스트 프레임워크
		- Appium : iOS와 Android를 모두 테스트 할 수 있는 UI 테스트 프레임워크
		- UI Automator : 복수 앱 간의 UI 기능을 테스트하는 프레임워크


- 구글의 안드로이드 테스팅 환경
	- 구글은 테스팅의 중요성을 계속 강조, 전략이나 새로운 라이브러리를 꾸준히 발표해 옴
		- Testing Related Video from Android Developers
		- Android Testing (Android Dev Summit 2015)
		- Test-driven development on Android with the Android Testing Support Library (Google I/O '17)
		- Frictionless Android testing: Write once, run everywhere (Google I/O '18)
		- Testing rebooted (with AndroidX Test) (Android Dev Summit '18)
		- Testing Android apps at scale with Nitrogen (Android Dev Summit '18)
		- Build testable apps for Android (Google I/O’19)
		- What’s new in Android testing tools | Session


	- Jetpack Test Library
		

	- UI/Application Exerciser Monkey
		- 원숭이 처럼 임의 동작을 통해서 테스트 하는 방식
		- Monkey는 에뮬레이터 또는 장치에서 실행되고 클릭, 터치 또는 제스처와 같은 사용자 이벤트의 의사 무작위 스트림과 여러 시스템 수준 이벤트를 생성
		- 여러가지 옵션을 지정 가능

	- Unified Test Platform
		- Android Studio와 CI서버의 테스트 결과가 다르게 보고될 수 있음
		- Android Studio Bumblebee 이상의 버전에서는 모든 계측 테스트가 통합된 Gradle Test Runner에서 실행
		- 서로 다른 OS의 테스트를 모듈 방식으로 추가할 수 있고 병렬로 테스트를 수행할 수 있어서 테스트의 대규모화가 가능


- Code Coverage
	- 내 코드가 얼마만큼 테스트 되고 있는지 평가할 수 있는 지표
	- Java Code Coverage Library(JaCoCo)
	- 안스에는 기본적으로 이 기능이 포함되어 있다
		- 100%를 위해 매달릴 필요가 없다. 테스트 하면 안되는 것도 존재한다.

- 어떤 코드가 테스트 하기 좋은 코드인가?
	- 코드 커버리지를 높이기 위해 결국 테스트 하기 좋은 구조로 만들어야 함
	- 간단히 말할 주제가 아님
	- OKKYCON: 2018 - The Real TDD

- CI/CD
	- 프로덕트의 빌드 과정 : 맨 위에 있던건데?
		- 연관된 의존성 다운로드
		- 소스 코드를 바이너리 코드로 컴파일
		- 바이너리 코드 링크하여 실행가능 파일로 패키징
		- 테스트 수행
		- 프로덕션 시스템에 배포
	- 개발자는 코드를 작성할 때마다 테스트 하고 커밋해야 됨. 여러 사람이 있다면 복잡해짐

- 지속적 통합(Continuous Integration, CI)
	- 개발자가 코드를 작성하고 저장소에 커밋하면 자동으로 컴파일과 테스트를 수행
	- 깃헙액션 등등

- 지속적 제공(Continuous delivery, CD)
	- CI가 완료되어 배포할 수 있는 상태의 빌드 결과물을 저장소에 업로드 하는 것

- 지속적 배포(Continuous Deployment, CD)
	- 지속적 제공 과정이 완료된 결과물을 최종 사용자가 사용할 수 있는 환경까지 자동으로 배포하는 솔루션

- CI/CD를 도입하면 코드 작성에 집중할 수 있다
