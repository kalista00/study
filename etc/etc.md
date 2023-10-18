## etc

#### 우분투(Ubuntu)

* 리눅스 기반의 오픈 소스 운영 체제(OS)
<br>

#### Sonatype

*  소프트웨어 개발 및 관리 도구 및 서비스를 제공
   *  Nexus Repository Manager (소스 코드, 라이브러리, 패키지 등을 중앙 집중식으로 저장하고 관리)
<br>

#### VM웨어 vs 레드햇 
*  VM웨어 ---> Spring 
    * Java EE (자카르타 EE)


* 레드햇 ---> Jboss
   * Jboss <--- Java EE (자카르타 EE) 스펙 준수
      * 하이버네이트(JPA)
<br>

#### 커널(Kernel)

#### MSA(MicroService Architecture)<br>
* 모놀리식(Monolithic Architecture)의 문제점을 보완하기 위해 등장<br>
 &nbsp; /WAR파일로 빌드되어 WAS에 배포하는 형태
* 정확한 정의는 없음
* MicroService 란 작고, 독립적으로 배포 가능한 각각의 기능을 수행하는 서비스로 구성된 프레임워크
* API를 통해서만 상호작용 가능

#### Maven 빌드시 주의
*  maven clean 후 install 해야됨

#### JavaEE 가 default 면 servlet 으로 개발했다는 말임

#### CDN(콘텐츠 전송 네트워크)

* 지리적으로 분산된 여러 개의 서버
* 웹 콘텐츠를 사용자와 가까운 곳에서 전송함으로써 전송 속도를 높임

#### 운영체제 (Operating System)

* 컴퓨터 시스템 자원들 효율적 관리
  * 주요 자원관리
    * 프로세스 관리
    * 기억장치 관리
    * 주변장치 관리
    * 파일 관리 

#### AS계정 최신화 방법
vpn 접속 -> teams/개발팀/GM/FNR환경 -> GM계정으로 로그인 apa\ -> 접속 경로에 적힌대로 -> 바꾸고 바뀐 패스워드 , 유효기간 최신화 (엑셀)

#### 라이브러리가 라이브러리를 의존

#### Dependency Hierachy 

#### JAR vs WAR

* JAR
  * JAVA 어플리케이션이 동작할 수 있도록 자바 프로젝트를 압축한 파일
  * Class(JAVA리소스, 속성 파일), 라이브러리 파일을 포함함
  * JRE(JAVA Runtime Enviroment)만 있어도 실행 가능

* WAR
  * Servlet / Jsp 컨테이너에 배치할 수 있는 웹 어플리케이션(Web Application) 압축파일 포맷
  * 웹 관련 자원을 포함함(정적리소스)
  * 사전 정의된 구조 사용(WEB-INF, META-INF)
  * 별도의 웹서버(WEB) or 웹 컨테이너(WAS) 필요
  * "즉, JAR 파일의 일종으로 웹 어플리케이션 전체를 패키징 하기 위한 JAR파일"
#### What is fully qualified classname?

* 해당 클래스가 속한 패키지명까지 붙여 쓴 클래스의 이름
