- 아이템을 클릭했을 때 url을 웹뷰로 띄우게 해보자

- safe args로 전달할 클래스는 직렬화가 가능해야 함
	- 클래스를 Parcelable로 만들어서 전달해보자
	- Serialize 보다 속도는 빠르지만 보일러플레이트 코드를 구현해야 한다는 단점이 있음
	- 그러나 Parcelable implementation generator를 사용하면 단점을 없애줌 
