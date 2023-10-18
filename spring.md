# 4. Spring

## 1) IOC/DI(제어 역전)

#### "개발자가 아닌 툴이 제어권을 가져 클래스가 의존 객체를 직접 만드는 것들이 아니라 주입받아서 사용"

* ApplicationContext와 BeanFactory(ApplicationContext는 BeanFactory를 상속받음) 인터페이스 덕분에 Bean으로 지정한 모든 클래스를 인스턴스로 등록해주어 다른 클래스에서 의존관계가 필요하다면 이 Bean(스프링 IoC 컨테이너가 관리 하는 객체)으로 등록된 인스턴스들을 전달해주어 의존성 주입이 가능

## 2) PSA(추상화 서비스) : 탬플릿

#### "POJO로 사용할 수 있도록 일종의 껍데기를 씌워 추상화한 것"
* POJO : 순수한 자바로 작성된 객체

## 3) AOP(관점 지향 프로그래밍)

#### "여러 개의 핵심 비즈니스 로직 외에 공통으로 처리되어야 하는 로그 출력, 보안처리, 예외 처리와 같은 코드를 모아서 처리를 편리하게 해줌"
* 대표적으로 @Transactional 로 트랜잭션 처리를 공통으로 넣어줄 수 있음

### AOP 구현 방법
1. 컴파일 이용방법
2. 바이트 코드 조작
3. 프록시 패턴

#### 위의 3가지중 스프링은 프록시 패턴을 기반으로 AOP를 지원 하고 있음.
* 프록시를 통해 핵심 로직을 구현한 객체에 접근하게 되면 핵심 로직을 실행하기 전 , 후에 공통된 기능을 적용하는 방식으로 AOP를 구현함.

### AOP 용어
* Advice : 언제 공통 기능을 적용할 지를 정의.(메서드를 호출하기 전/후)
* Weaving : Advice를 핵심 로직 코드에 적용하는 것을 말함.
* Jointpoint : Aspect를 적용할 타겟
* Pointcut : Jointpoint 의 부분 집합으로 실제로 Advice가 적용되는 Jointpoint 를 나타낸다. 스프링에서는 정규표현식이나 AspectJ 문법을 이용하여 정의.
* Aspect : 여러 객체에 공통으로 적용되는 기능을 트랜잭션이나 보안 등이 * Aspect의 예시
* Around, Before,Aft

## 4) etc..

### Spring Profile

* phase(local, dev, prd..)에 따라 다른 resource를 바라봐야 할 경우 ex) dev db 와 prod db 가 다를 경우 <br> Spring Profile로 필요한 환경 활성화 가능

### SLF4J(Simple Logging Facade for Java)

* Logging : 디버깅, 모니터링 등 필요한 로그를 기록하는 것
*  SLF4J는 추상 로깅 프레임워크이기 때문에 단독으로는 사용x
* SLF4J api를 사용하면 구현체의 종류에 상관없이 일관된 로깅 코드를 작성 가능
* 배포할 때 원하는 Logging Framework를 선택 가능
* 교환 가능.
* SLF4J는 세 가지 모듈을 제공한다.

### etc
* src/main/java == java 리소스
* src/main/resource == 그 외 리소스
* WEB-INF 안에 있는 리소스만 was동작함

### [[목차]](https://gitlab.theuber.co.kr:8989/study/ch.kim/-/blob/main/study/index.md)