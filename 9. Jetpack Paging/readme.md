- Paging이란
	- Paging : 하나의 문서를 분리된 페이지로 나누는 것
	- 취급해야 하는 데이터가 너무 클 때, 작은 단위로 쪼개서 사용
	- 직접 구현하려면 힘드므로 제트팩 라이브러리로 발표함

- Jetpack Paging의 구성요소
	- 그림 8 넣기


- Jetpack Paging의 구성요소
	- Repository
		- PagingSource : 데이터 소스와 그 소스에서 데이터를 검색하는 방법을 정의.
		- RemoteMediator : 로컬 데이터베이스에 네트워크 데이터를 캐시하는 동작을 관리.
	- ViewModel
		- Pager : Repository에서 정의한 PagingSource와 PagingConfig를 생성자로 받아 PagingData를 반환하는 API를 제공.
		- PagingData : Pager에 의해 페이징 된 데이터를 담는 컨테이너.
	- UI
		- PagingDataAdapter : PagingData를 표시할 수 있는 RecyclerView 어댑터.


- Jetpack Paging의 동작원리
	- 그림 9 넣기
