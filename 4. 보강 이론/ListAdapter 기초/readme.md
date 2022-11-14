- 정작 리스트 어댑터 설명은 안하고 notify 설명으로 시작하는 레전드 강의

- DiffUtil
	- 두 개의 데이터 셋을 받아서 차이를 계산해주는 클래스
	- Eugene W. Myers의 difference 알고리즘을 이용해서 O(N + D^2)시간 안에 리스트의 비교를 수행
	- N: 추가 및 제거된 항목의 갯수
	- D: 스크립트의 길이
	
- DiffUtil구현
	- areItemsTheSame() : 두 객체가 동일한 객체인지 확인
	- areContentsTheSame() : 내용까지 동일한 객체인지 확인

- AsyncListDiffer
	- DiffUtil은 아이템 개수가 많을 경우 연산 시간이 길어질 수 있으니 백그라운드 스레드에서 처리되어야 함
	- DiffUtil에 대해 자체적으로 스레드 처리를 해주는 클래스

- ListAdapter
	- AsyncListDiffer를 더 쓰기 편하도록 랩핑한 클래스
	- 리사이클러뷰 어댑터를 만들 때 ListAdapter를 상속하게 하고 초기화시 DiffUtil 콜백 객체를 넘겨주면 된다
	- submitList()로 전체 데이터를 넘겨주면 어댑터가 백그라운드 스레드를 사용해 리스트 차이를 계산하여 화면을 갱신시켜줌
