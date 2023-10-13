## Spring

### Spring Profile

* phase(local, dev, prd..)에 따라 다른 resource를 바라봐야 할 경우 ex) dev db 와 prod db 가 다를 경우 <br> Spring Profile로 필요한 환경 활성화 가능

### SLF4J(Simple Logging Facade for Java)

* Logging : 디버깅, 모니터링 등 필요한 로그를 기록하는 것
*  SLF4J는 추상 로깅 프레임워크이기 때문에 단독으로는 사용x
* SLF4J api를 사용하면 구현체의 종류에 상관없이 일관된 로깅 코드를 작성 가능
* 배포할 때 원하는 Logging Framework를 선택 가능
* 교환 가능.
* SLF4J는 세 가지 모듈을 제공한다.


#### etc
* src/main/java == java 리소스
* src/main/resource == 그 외 리소스
* WEB-INF 안에 있는 리소스만 was동작함
