## Layer 와 Layered 구조
- 계층 구조에서 각 요소들은 서로 존립한다
	- 하위 요소가 있어야 상위 요소가 존재할 수 있다

## 네트워크와 네트워킹 그리고 개념
- 요소가 상호작용을 하기 위해선 여러 전제 조건이 필요하다
- OSI 7 Layer 도 결국 요소들간 상호작용을 하기 위한 여러 전제 조건들을 설명할 뿐이당
- OSI 7 Layer 는 그저 개념일 뿐, 구현체는 아니다
	- 얘는 마치 철학 같은 것...
	- 멋모르고 OSI 7 Layer 공부하지 말라는 뜻
	- TCP/IP 를 공부하고 싶으면 OSI 7 Layer 부터 공부하지 말라 ㅋ

## User mode 와 Kernel 모드
- Network Interface Card(NIC) == LAN 카드
- 커널 모드의 TCP/IP 를 유저 모드에서 추상화한 것을 소켓이라고 한단다
	- OSI 7 Layer 에서 L5~L7 은 유저 모드의 어플리케이션이다
		- 즉 프로세스 레벨에서 설명이 가능하다
	- 결국 소켓도 그저 파일이다
- TCP/IP 
	- IP = L3 계층
	- TCP = L4 계층
	- TCP/IP 는 커널 모드에서 다룬다
- 드라이버, NIC 는 L1, L2 계층을 다룬다