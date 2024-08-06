## IPv4 주소의 기본 구조
- IPv4 주소는 32bit 주소 체계를 가지고 있는데, 이 말인 즉슨 8bit 가 네 개인 것!
	- 그래서 IP 주소의 한 영역은 255까지만 표기한다
	- 256은 이진수로 `11111111` 로 표현하는데, 이는 곧 Broadcast 를 의미할 수도 있어서 255까지만 쓴다
- IP 주소의 앞 세 영역은 네트워크의 ID, 마지막 영역은 Host 의 ID 를 표현한다
- 데이터를 전송할 때에는 먼저 네트워크 ID 로 식별한 뒤 Host ID 로 특정 호스트를 구분한다

## L3 IP Packet 으로 외워라
- Packet == L3 IP Packet
- 패킷은 헤더와 페이로드로 나뉜다
	- 헤더에는 소스 정보가 들어 있는데, 이건 데이터를 전송한 주소와 받는 주소가 들어있다
- 패킷의 최대 크기는 `MTU` 라고 한다
	- 보통 1500byte 의 크기이다
	- 대략 1.4xKB 정도...
	- 패킷은 정말 작은 데이터이기 때문에 직소 퍼즐의 퍼즐 조각 한 개 정도로 생각하면 된다

##   Encapsulation 과 Decapsulation
- Encapsulation 은 마트료시카 인형과 같다
- L2 에서 다루는 데이터인 Frame 의 페이로드에는 L3 패킷이 들어있다
	- 그리고 패킷 안에는 L4 Segment 가 들어있고...
- 아무튼 Encapsulation 이란, 데이터를 감싸는 것이라고 할 수 있다
	- 반대로 데이터를 차근 차근 꺼내는 것은 Decapsulation

## 패킷의 생성, 전달, 소멸
- 패킷 전달은 마치 택배와 비슷하다...

## 계층별 데이터 단위
- L1~L2 에서 다루는 데이터의 단위: Frame
- L3(IP) 에서 다루는 데이터의 단위: Packet
	- 데이터의 최대 크기(MTU, Maximum Transmission Unit)는 1460byte 정도
- L4(TCP) 에서 다루는 데이터의 단위: Segment
	- 데이터의 최대 크기(MSS, Maximum Segment Size)는 웬만하면 1500byte 정도
- Socket: Stream
	- 이름 그대로, 운영체제는 데이터의 시작은 존재하나 끝은 알 수 없다
	- 끝은 소켓의 데이터를 받아 처리하는 애플리케이션 계층에서 알 수 있다
- Socket Stream 이 Segment 화 될 때, Stream 의 크기가 MTU 보다 크다면 Segmentation 이 일어난다
	- 용어가 어렵지만, 그냥 User mode 인 소켓에서 Kernel mode 의 TCP 로 넘어갈 때 1500byte 의 데이터보다 더 큰 데이터를 넘긴다면, 데이터를 잘라서 보낸다는 말.
	- 데이터의 크기는 MSS 크기로 자른 뒤, MTU 의 사이즈에 맞게 패킷으로 감싸서 보낸당~