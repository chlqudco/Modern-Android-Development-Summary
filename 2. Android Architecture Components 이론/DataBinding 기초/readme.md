

- DataBinding
    - 선언적 형식으로 레이아웃의 UI 구성요소를 데이터와 결합할 수 있도록 도와주는 라이브러리
    - 간단히 말해 코틀린 코드와 xml 코드를 연결해줌
    - 매년 많은 발전을 해옴 

- DataBinding의 세가지 특징
    - Remove findViewById
        - 더이상 findViewById를 쓸 필요가 없어짐
    - Custom Binding Adapter
        - 속성 값을 바꿀 수 있는 어댑터를 커스텀 할 수 있음
    - Two-way Data Binding
        - 데이터를 뷰로 보내는것 뿐만 아니라 뷰가 데이터를 보내게 할 수도 있다
- xml이 데이터 바인딩을 사용할 수 있게 최상위를 layout 태그로 바꿔야함.
    - 그안에 data 태그를 통해 데이터를 받아올 수 있음
    - 코틀린 파일에서 lifecycleOwner과 뷰모델을 지정해주기
