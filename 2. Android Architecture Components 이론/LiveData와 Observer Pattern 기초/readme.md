
    - LiveData와 Observer Pattern 기초
	- LiveData
        - 값의 변경을 감지할 수 있는 데이터 홀더
		- 값이 1에서 2로 변하는 순간을 시스템이 감지할 수 있음
		- 뷰모델과 결합할 때 시너지를 발휘할 수 있음
		- 라이브데이터를 사용하면 값의 변화를 감지하여 UI를 알아서 변화시키게 할 수 있음
 		
	- observer 패턴
		- Observer 가 Subject의 변화를 관찰하고 있음
		- subject의 상태변화를 초래하는 이벤트가 발생하면 객체가 이벤트를 직접 Observer에게 통지해줌
		- 유튜부를 예로 들면 채널 운영자는 subject이고 구독자는 Observer임
		- 채널 운영자가 새동영상을 등록하면 자동으로 구독자에게 알림 이벤트가 전달되어 구독자가 알림을 알게 됨

- Observable vs LiveData
    - 옵저버에 의해 값의 변경을 감시할 수 있는 데이터 홀더
  - 옵저버블은 특수한 타입을 사용하고 싶다면 직접 구현해야 함
    - 라이브데이터는 라이프사이클오너를 전달함
    - 뭐라는거야
    - 옵저버블은 lifecycle을 알 수 없으므로 콜백이 상시 작동되어야 함
    - 라이브데이터는 활성화 상태일 때만 자동으로 작동함
- LiveData의 이점
    - UI와 데이터 상태의 일치를 보장
    - 메모리 누수가 없음
    - 중지된 활동으로 인한 비정상 종료 없음
    - 생명주기를 수동으로 처리하지 않음
    - 최신 데이터 유지
    - 등등 문서에 많이 나와 있음
- Transformations로 LiveData 값 변경하기
    - LiveData는 값을 변경할 수 없는 타입임
    - 뷰모델에서 값을 바꾸면 뷰모델과 라이브데이터의 결합도가 강해짐
    - 이런 경우에 Trans를 사용하면 됨
    - 새로운 라이브데이터를 만드는 방식
    - map
    - switchMap
