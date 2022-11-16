- SQLite
	- 많고 많은 DBMS 중 하나
	- 무료이며 오픈소스 이므로 안드로이드와 IOS가 둘다 채택
	- 미해군의 구축함에서 이용하기 위해 만들어짐
	- 전세계에서 1조개가 넘는 SQLite DB가 운용되고 있음
	- 근데 구글이 SQLite를 직접 쓰는걸 권장하질 않음, 그래서 Room을 도입

- Room
	- SQLite를 안전하게 다루기 위해!
	- Entity : 테이블 구조를 정의 
	- Dao : 쿼리를 간접적으로 사용하여 접근
	- RoomDatabase : Dao를 다루는 애
	- 그림 7 넣기

- Room의 장점
	- Less boilerplate code
	- Compile-time checked queries
	- Ease of implementing migrations
	- High degree of testability
	- Keep database work away from the main thread
