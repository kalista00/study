## 암호
<br>

### 대칭

#### 일반적인 password 방식

* des
* aes256  <= 256은 2진수 32자리

<br>

### 비대칭

#### public key(공개키) 와 private key(개인키)가 따로있음 (public key를 접근하려면 private key로 접근)

#### 암호화할 때랑 복호화 할 때 서로 다른 키를 의미

##### SSL/TLS 

* 웹사이트와 브라우저 사이 or 두 서버 사이에 전송되는 데이터를 암호화
<br>
&nbsp; -? 웹사이트와 브라우저 <br>
&nbsp;&nbsp;&nbsp;&nbsp; - 웹사이트 : 인터넷 상에서 제공되는 다양한 정보와 서비스를 제공하는 공간 <br>
&nbsp;&nbsp;&nbsp;&nbsp; ex) 네이버, 구글, 유튜브 
<br>
&nbsp;&nbsp;&nbsp;&nbsp; - 브라우저 : 웹사이트에 접속하기 위해 사용되는 소프트웨어 <br>
&nbsp;&nbsp;&nbsp;&nbsp; ex) 크롬, 파이어폭스, 엣지


* TLS은 SSL의 향상된, 더욱 안전한 버전 

* 네트워크 통신 단계 : 악수(handshake) -> 전송 -> 세션 종료

* 악수(handshake) 과정 <br>
 \/ client ---(랜덤데이터)---> server ---(랜덤데이터+인증서)---> 브라우저에 내장된 CA로 인증 <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - CA(Certificatie Authority) : 클라이언트가 접속한 서버가 클라이언트가 의도한 서버가 맞는지를 보장해주는 역할

참고<br>
https://velog.io/@dong5854/HTTPS%EC%99%80-SSL%EC%9D%B8%EC%A6%9D%EC%84%9C-%EB%8C%80%EC%B9%AD%ED%82%A4-%EA%B3%B5%EA%B0%9C%ED%82%A4%EB%B9%84%EB%8C%80%EC%B9%AD%ED%82%A4



