## hyper thread
- 얘도 가상화 기술이라 코어 한 개가 쓰는 자원을 여러개로 쪼개다보니 경합 문제가 발생할 수 있음
- cpu 많이 쓰는 작업에는 하이퍼스레드 쓰지 않는게 좋음
- cpu 사용률만으로 성능 분석을 할 수는 없다
	- 전용 도구를 쓰자
	- linux ki
	- perf
- performance counter 라는 것도 있따...
- cpu topdown 분석-클라부터 서버까지 cpu 병목을 분석하는 방법
- 스레드 병목을 판단할 수 없는 도구도 있다

## 무료 환전 서비스
- 금융업에서 오라클 쓰는게 강력한 트랜잭션 관리 기능때문이었는데 기술이 발전하면서 레디스 분산락이나 카프카를 이용한 saga 패턴 등등, 대체할 수 있는 기술이 많이 늘어남
- 커뮤니티가 강력한것도 오라클 장점이었는데 mysql또한 오랜 시간동안 커뮤니티 구축을 해옴
- 코어뱅킹 서비스가 오라클을 바라보고 있는 모놀리스 서버였지만 외환 서비스를 mysql 기반의 msa 로 구현하기로 결정
- 금원거래? 고객과 은행 계좌에서 잔액이 바뀌는 것
- 토뱅 원화예금에선 거래 중단 없이 자정이 되어도 금융 업무가 가능하다고 한다
- 다섯명이서 외화예금 msa 서버개발했다고;;;;;;;;;
- 거기에 테스트 자동화가 100%라한다;
	- 로컬에선 단위테스트
	- dev 에선 e2e
	- live 에선 이상거래탐지 서비스를 개발
- mysql쓴게 금융권 최초라한다
- 원화 송금보다 환전이 더 빠르다한다 ㅋㅋㅋㅋㅋㅋ

## SSE
- SSE 는 http 의 text stream event 형식으로 커넥션이 맺어져서 서버가 이벤트가 발생할 때 마다 연결된 클라이언트에 데이터를 전달해주는 방식
- 메세지 발행 방식에도 브로드캐스트/유니캐스트 방식으로 고민해봄
- 유니캐스팅
	- 클라이언트는 해당 클라이언트만 구독 가능한 메세지 채널을 생성, 해당 채널만 구독
	- 개인화 메세지 ㅇㅋ
- 세션 대신 redis pub/sub 활용했다함
- nats? golang 기반의 pub/sub 도구인듯하다
- SSE 는 클라이언트 커넥션이 언제 끊어졌는지 몰라서 heartbeat 를 주기적으로 확인해야함

## Node.js 웹 스크래핑
- 토뱅에서 Nest.js 써서 대출 문서 가져올때 스크래핑 한다함
- 웹뷰에 nest.js fmf dhfflsek...?

## Kernel
- stall? memory io
- page fault
- numa architecture?
	- multi socket cpu
	- remote access 에서 홉이 추가되어 사이클이 더 필요하단다
- cpu pinning? 

## 보상 트랜잭션
- 2 page commit
- saga pattern
- 둘 다 트랜잭션 커밋 기법임
- saga 는 대부분 메세지 브로커를 사용하여 구현한다
- 다만 토뱅에선 http 로 구현했다공..
- 환전 과정에서 보상 트랜잭션이 일어나야하는 경우, 사용자에게 에러 메세지를 보여주기까지의 과정이 메세징 방식보단 http 방식이 더 적합하다고 판단한듯
- 다만 출금 취소에 대한 보상 트랜잭션은 메세징 방식을 사용
- transactional messaging

## 차세대
- 여기서도 교살자패턴을 써서 개선한듯 하다
- 절차
	1. 대상 선정
		1. 사이드 이펙이 제일 작은 것 부터...
	2. 분석
		1. 연역적 분석
			1. 도메인 분석!
		2. 귀납적 분석
			1. 구체적 사례나 데이터를 통해 이론 도출
			2. 기존 시스템 분석 후 새 시스템 설계
	3. 설계
		1. 설계 문서만 봐도 모든 시스템을 이해할 수 있어야 한다
	4. 구현
		1. 인터페이스를 적극 활용하는 composite 패턴을 이용한 듯 하다
	5. 검증
		1. 검증 성공? 대상 선저응로 돌아감
		2. 검증 실패? 분석으로 돌아가 다시 분석

## 마이데이터
- 70000tps란다;
- 장애 대응
	- 외부 기관과 연계된 서비스라 장애 발생시 전파가 빠름
	- 장애가 발생했을 때 외부 기관에 api 호출을 할 수 없도록 제어해야 함
- 토스에선 25일 아침에 트래픽이 제일 많다고 ㅋㅋㅋㅋㅋ
	- 월급이슈
- 코루틴 채널?