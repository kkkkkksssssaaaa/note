## OSI 7 Layer 와 식별자
- 암기해야 할 것
	- L2: Ethernet 에도 식별자가 있다
		- 그거시 MAC 주소
		- LAN 카드 식별자 ㅋ
	- L3: 식별자는 IP 주소
	- L4: 식별자는 포트 번호...?
		- 네트워크 공사하시는 분들에게 포트 번호는 인터페이스 식별자라고 한다
			- LAN 케이블이 꽂히는 단자
		- 네트워크 관리하는 분들에게 포트는 웹 서비스 식별자로 인지한다고..
		- 평범한 애플리케이션 개발자들에겐 프로세스의 식별자로 인지
- 물론, OSI 7 Layer 말고 다른 네트워크 계층도 있다
	- 미국에서 쓰는 DoD 라는 계층 소개

## Host 는 이렇게 외우자!
- 컴퓨터가 네트워크에 연결되는 순간... `호스트` 라고 표현한다
	- 걍 인터넷 연결된 컴터라고 생각하면 된다고..
- 호스트라는 개념은 아래의 두 가지 개념을 포괄한다
	- End-point
		- 네트워크 이용 주체
		- 네트워크를 이루는 인프라 스트럭처를 사용하는 주체
	- Switch
		- 얘는 네트워크 그 자체로 봐야한다고...
		- 라우터나 IPS 같은 보안 장치같은 것이 스위치로 분류된다

## 스위치가 하는 일과 비용
- 고속도로와 네트워크는 매우 닮아있다
	- 운전자는 목적지로 가기 위해 경로를 선택해야 한다
		- 교차로를 만났을 때 어느 쪽으로 갈 것인지
		- 그 선택에는 근거가 있어야 한다...
		- 그 근거란? 이정표!
	- 결국 이정표를 잘 따라가다 보면 목적지에 도착할 수 있다
- 위 비유처럼, 데이터는 목적지로 가기 위해 관문을 지나야 하는데, 교차로는 스위치, 경로는 인터페이스를 선택하는 것이다
	- 자동차는 데이터, 즉 패킷
	- 경로를 선택하는 행위를 스위칭이라고 표현한다
	- 이정표 역할은 IP 주소가 대신한다
	- IP 주소를 기반으로 스위칭하는 것을 L3 스위칭이라고 한다
		- 라우터는 L3 스위치의 일종이다
	- 라우터에는 IP 주소를 가지고 있는 라우팅 테이블이라는 것이 있는데, 패킷이 목적지까지 갈 수 있도록 이정표를 제시하는 역할을 한다
- L2 계층에 존재하는 MAC 주소를 스위칭하는 것을 L2 스위칭이라고 한다고..!
- HTTP 를 통해 스위칭을 하는 것을 L7 스위칭...
- 스위칭도 결국 비용이다
	- 패킷이 최적의 경로로 목적지에 도착할 수 있어야 한다
	- 스위칭 비용을 매트릭 값이라고 하고, 패킷은 매트릭 값이 낮은 곳으로 향하게 되어 있다공