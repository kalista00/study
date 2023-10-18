# Servlet

### 서블릿을 크게 두가지로 보면

* JSP(템플릿 엔진)
  - \*템플릿 엔진 : 특정 데이터 모델에 따른 입력 자료를 합성하여 결과 문서를 출력하는 소프트웨어

* 내장 객체( Implicit Object / "JSP 내에서 선언하지 않고 사용할 수 있는 객체")  
  
  * request (웹 브라우저의 요청 정보를 저장하고 있는 객체)
  * response (웹 브라우저의 요청에 대한 응답 정보를 저장하고 있는 객체)
  * session (웹 브라우저의 정보를 유지하기 위한 세션 정보를 저장하고 있는 객체)
  * page (JSP)
  * application (웹 어플리케이션 Context의 정보를 저장하고 있는 객체)

### Component (web.xml)
#### "web.xml : 웹 컴포넌트의 설정 정보를 포함"
* Filter (스프링 인터셉터와 유사)
  * 요청 필터 : 사용자 인증, 요청 관련 로그 작업, 인코딩
  * 응답 필터 : 응답 결과 암호화, 서비스 시간 측정
  * 관련 API 
    * javax.servlet.Filter, javax.servlet.FilterChain, javax.servlet.FilterConfig

* Listener (이벤트 리스너) / 이벤트가 발생하면 실행
 * 리스너 종류 (이벤트 발생 가능 객체는 3가지)
   * ServletContext 객체 > HttpSession 객체 > HttpServletRequest 객체
      * ServletContext (서버가 살아있는 동안)
      * HttpSession (브라우저가 살아있는 동안)
      * HttpServletRequest (요청/응답이 처리되는 동안, forwarding 관계일 때만)

* Servlet (서블릿 컨테이너)
  * 웹서버와의 통신 지원
  * 서블릿 생명주기 관리
  * 서블릿 생명주기 매서드
    * 초기화 : init()
    * 작업 수행 : doGet(), doPost()
    * 종료 : destroy()
  * 멀티쓰레드 지원 및 관리
  * 선언적인 보안 관리

### [[목차]](https://gitlab.theuber.co.kr:8989/study/ch.kim/-/blob/main/study/index.md)