- 데이터를 앱에 저장하는 방법
	- 파일 I/O (내부 또는 외부 저장소)
		- 접근 권한을 획득하고 파일을 열었다 닫았다 하는 수고가 필요함
	- 관계형 데이터베이스
		- SQLite 등을 이용해 복잡한 관계형 데이터를 저장할 수 있음
		- 간단한 데이터를 저장할거라면 구축과 관리에 많은 시간과 노력이 요구됨
	- SharedPreference
		- Key/Value 형태로 이용함
		- 내부적으로는 XML 파일로 저장됨
		- 파일을 열고 닫을 필요 없이 핸들러를 만들어서 간편하게 사용가능함
		- 환경설정 처럼 간단한 데이터를 저장하기에 적당한 공간

- DataStore의 발표
	- sharedPreference의 단점을 개선한 모델
	- Preferences DataStore
		- 키를 사용하여 데이터를 저장하고 데이터에 액세스합니다.
		- 이 구현은 유형 안전성을 제공하지 않으며 사전 정의된 스키마가 필요하지 않습니다.
		- 기본적으로는 얘가 shared를 바꾼거라고 생각하면 됨
		- 플로우를 도입했기 때문.
	- Proto Datastore
		- 맞춤 데이터 유형의 인스턴스로 데이터를 저장합니다.
		- 이 구현은 유형 안전성을 제공하며 프로토콜 버퍼를 사용하여 스키마를 정의해야 합니다.
