## Servlet

#### 서블릿은 크게 두가지 존재

* JSP(템플릿 엔진)
  -  템플릿 엔진 == 특정 데이터 모델에 따른 입력 자료를 합성하여 결과 문서를 출력하는 소프트웨어

* 내장 객체(Implicit Object)<br>
  == "JSP 내에서 선언하지 않고 사용할 수 있는 객체"
  
  * request (사용자 요청)
  * response (사용자 응답)
  * session (토큰)
  * page
  * application (어플리케이션 전체 관리 객체)

### Component
* Filter (스프링 인터셉터와 유사)
  - 요청 필터 : 사용자 인증, 요청 관련 로그 작업, 인코딩
  - 응답 필터 : 응답 결과 암호화, 서비스 시간 측정
  - 관련 API 
    - javax.servlet.Filter, javax.servlet.FilterChain, javax.servlet.FilterConfig

* Listener (이벤트 리스너) / 이벤트가 발생하면 실행
 - 리스너 종류 (이벤트 발생 가능 객체는 3가지)
   * ServletContext 객체 > HttpSession 객체 > HttpServletRequest 객체
      * ServletContext (서버가 살아있는 동안)
      * HttpSession (브라우저가 살아있는 동안)
      * HttpServletRequest (요청/응답이 처리되는 동안, forwarding 관계일 때만)