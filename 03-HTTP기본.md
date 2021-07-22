

http 메세지에 모든것을 전송  

이미지, 파일, 영상..등 거의 모든 형태의 데이터 전송 가능. 



#### http 역사 

http/1.1 : 현재 가장 많이 사용하는, 가장 중요한 버전 (http의 주요한 기능을 포함한 원형)  



#### 기반 프로토콜 

- http/1.1, http/2 : TCP

- http/3: UDP
  - TCP는 속도나 성능 측면에서 아쉬운 부분들이 있음



### http 특징

- 클라이언트-서버 구조
- 무상태 프로토콜(스테이스리스), 비연결성
- http 메세지
- 단순함, 확장 가능



### 클라이언트-서버 구조

- Request, Response 구조
- 클라이언트는 서버에 요청을 보내고, 응답을 대기
- 서버가 요청에 대한 결과를 만들어서 응답



-> 클라이언트와 서버가 각자 독립적으로 진화할 수 있다.



### 무상태 프로토콜

- 서버가 클라이언트의 상태를 보존하지 않는다.
  - stateful(상태를 유지한다.)

    - 중간에 다른 서버로 바뀌면 안된다. 

  - Stateless(상태를 유지하지 않는다.)

    - 갑자기 요청이 증가해도 서버를 대거 증설할 수 있다.

    -> 무한 서버 증설 가능!

stateless

- 스케일 아웃 -> 서버 수평 확장
- 한계
  - 무상태로 설계할 수 없는 경우도 있다.
  - 성태유지가 필요한 경우가 있다.
    - 로그인 (session, cookie ...)
- 상태유지는 가능한 최소화



### 비연결성

- 연결을 유지하는 모델은?
  - 여러개의 클라이언트가 요청과 응답을 통해 연결이 되면, 연결이 유지되면서 자원을 비효율적으로 사용 .
- 비연결성
  - http는 기본이 연결을 유지하지 않는 모델
  - 일반적으로 초단위 이하의 빠른 속도로 응답
  - 1시간동안 수천명이 서비스를 사용해도, 실제 서버에 동시에 처리하는 요청은 수십개 이하로 매우 작다 (요청에대한 응답이 되면 연결을 종료하기 ㄸ때문이다.)
  - 서버자원을 효율적으로 사용
- 한계/극복
  - Tcp/ip 연결을 새로 맺어야 한다.
    - 3 way handshake 시간 추가
  - 웹 브라우저로 사이트를 요청하면 html 뿐만 아니라 자바스크립트, css 추가이미지 등 수많은 자원이 함께 다운로드
  - 극복: http 지속연결(Persistent Connections)로 문제 해결
    - 연결-요청-응답-종료를 반복하지 않고, 연결-(반복: 요청-응답)-종료로 지속 연결하게 된다.



### HTTP메세지

- 모든것이 HTTP이다.

- http 메시지 구조

  - Start-line 시작라인
  - header 헤더
  - Empty line 공백라인(CRLF)
  - Message body

- 공식 스펙

  - HTTP-message = start-line

    ​								*( header-field CRLF )

    ​								CRLF

    ​								[ meesage-body ]

-  http 요청 메세지

  - 시작라인start-line = <strong>request-line</strong> / status-line
  - Request-line = method SP(공백) request-target SP HTTP-version CRLF(엔터)
  - EX)  GET /search?q=hello HTTP/1.1

  1. method 메서드
     - 서버가 수행해야 할 동작 지정
     - GET, POST, PUT, DELETE...

  2. request-target (요청대상)
     - 절대경로="/"로 시작하는 경로
     - 참고: http://.... 와 같이 다른 유형의 경로지정 방법도 있다.

  3. HTTP-version

- http 응답메세지

  - 시작라인start-line = request-line / <strong>status-line</strong>
  - status-line = HTTP-vsersion SP status-code SP reason-phrase CRLF
  - ex) HTTP/1.1 200 OK

- HTTP 헤더

  - Header-field = field-name: OWS field-value (OWS 띄어쓰기 허용)
  - 용도
    - http 전송에 필요한 모든 부가정보
    - 메세지 바디의 내용, 메시지 바디의 크기, 인증, 요청 클라이언트 정보, 캐시관리정보 ...



### https는 단순하고 확장성이 좋다.

- 크게 성공하는 표준 기술은 단순하면서 확장성이 좋다.
- 스펙이 단순하여 문서도 쉽게 읽어볼만 하다고 한다.

