## 설치 경로  
```shell  
/opt/homebrew/Cellar/kafka/3.8.1/libexec/bin  
```  
  
## 서버 설정 변경  
```shell  
$ vim /opt/homebrew/etc/kafka/server.properties  
  
# host 정보 수정 필요  
34 | listeners=PLAINTEXT://localhost:9092  
...  
38 | advertised.listeners=PLAINTEXT://localhost:9092  
```  
  
## 실행  
```shell  
# 1. brew 를 통한 실행  
$ brew services start kafka  
  
# 2-1. sh 를 통한 실행(zookeeper)  
/opt/homebrew/opt/kafka/bin/zookeeper-server-start /opt/homebrew/etc/kafka/zookeeper.properties  
  
# 2-2. sh 를 통한 실행(kafka)  
/opt/homebrew/opt/kafka/bin/kafka-server-start /opt/homebrew/etc/kafka/server.properties  
```  
  
## 토픽 생성  
```shell  
$ /opt/homebrew/opt/kafka/bin/kafka-topics --create --topic topic-example-1 --bootstrap-server localhost:9092  
  
# 파티션이나 레플리케이션같은 주요 설정을 해준다고 함  
$ kafka-topics --describe --topic topic-example-1 --bootstrap-server localhost:9092  
  
# 프로듀서를 통해 메세지 작성  
$ kafka-console-producer --topic topic-example-1 --bootstrap-server localhost:9092  
```