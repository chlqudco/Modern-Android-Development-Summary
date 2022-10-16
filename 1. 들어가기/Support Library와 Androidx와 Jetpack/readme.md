- Support Library
	- API의 하위 호환성 문제를 해결하기 위해 만들어짐
	- ex) RecyclerView
		- 롤리팝 부터 도입됨, 따라서 API 21이하 에서 작동 안되지만 서포트 라이브러리를 추가하면 작동 됨
	- 서포트 라이브러리의 종류
		- com.android.support 로 시작되는 라이브러리
		- 종류가 너무 많음
		- v가 붙은 패키지는 각각 사용가능한 최소 api 레벨을 의미함

- Support Library 문제점
	- 최소지원 API레벨 문제
		- 구글은 너무 오래된 기종의 사용을 막기 위해 최소 레벨을 대폭 상승시킴
		- v7이 붙어있어도 최소 레벨이 14인 이상한 현상이 생기게 됨
	- 필요없는 라이브러리 추가
		- 수많은 API를 통합한 라이브러리이기 때문에 사용하지 않는 기능도 같이 포함됨
		- 아주 큰 낭비
	- 버전통일 문제
		- 복수개의 라이브러리를 사용하는 경우 모두 동일한 버전을 유지해야만 함

- Androidx 체계의 도입
	- 이름체계의 혼란을 줄이기 위해 구글이 도입
	- 발표 이름은 2018년 Google I/O 세션 Android Jetpack: What’s new in Android Support Library
	- Support Library 이름이 Android Extension Libraries로 바뀜
	- androidx라는 네임스페이스를 부여받음
	- 아래와 같은 규칙하에 관리 됨
	
- 1. 라이브러리의 기능별 분리
	- 하나의 라이브러리가 여러개의 라이브러리로 쪼개지게 됨
	- 쓰지도 않은 나머지 기능들을 안써도 됨
	
- 2. 버저닝 방식의 변경
	- api 레벨과 동기화 되서 올라가던 방식이 1.0.0으로 리셋됨
	- Major.Minor.Patch 형식의 Semantic Versioning을 준수하게 됨
	- 따라서 RecyclerView의 업데이트가 이루어지면 RecyclerView 패키지만을 개별적으로 업데이트 가능
	
- 3. 패키징 방식 변경
	- 어떤 기능을 가졌는지 알수 없었던 Support library가
		- ex) android.support.v7.app
	- 패키지 이름이 기능을 나타내도록 변경됨
		- Java Package : androidx.<feature>.ClassName
		- Maven id : androidx.<feature>:<feature>-<sub-feature>
		- Class Mappings, Artifact Mappings 문서에서 어떻게 바꼈는지 확인 가능
	- 업데이트 확인가능
		- Androidx의 최신 릴리즈 내용 : Recent Release Notes에서 확인 가능
		- 개별 커밋은 Github에서 확인 가능

- Jetpack의 발표
	- 안드로이드 앱을 더 완성도 높게 만들 수 있는 라이브러리의 모음
	- 주로 androidx의 라이브러리가 포함됨
		- 물론 아닌 라이브러리도 있음
	- 같은 기능을 구현하더라도 숙련도에 따라 앱의 안정성이 달라지는 현상을 줄이기 위함
		- 구글에서 가이드라인을 만들었는데 그 가이드라인을 따르기 위해 사용하는 라이브러리의 모음

- Jetpack의 구성
	- 그림 3 넣기
	- 각 컴포넌트는 앱에서 개별적으로 사용 가능
	- 이전버전과 호환성 유지 가능

- Jetpack의 특징
	- Modern App Architecture, 최신식 앱 구조
	- Eliminate Boiler Plate Code, 필요 없는 코드 줄이기
	- Simplifying Complex Tasks, 복잡한 태스크 간결화
	- Robust Backwards Compatibility, 강력한 역호환성
	- 앞의 그림 외에도 수많은 컴포넌트가 있음
		- 공식 문서 보면 됨
