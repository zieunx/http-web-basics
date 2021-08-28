

## HTTP 메서드 활용

### 클라이언트에서 서버로 데이터 전송

### 2가지 방법

1. 쿼리 파라미터를 통한 데이터 전송
   - GET
   - 주로 정렬 필터(검색어)

2. 메세지 바디를 통한 데이터 전송



### 4가지 상황

- 정적 데이터 조회
- 동적 데이터 조회
- Html form 데이터 전송
  - Html form submit 시 POST 전송
  - Content-Type: application/x-www-form-urlencoded 사용
    - form의 내용을 메세지 바디를 통해서 전송(key=value, 쿼리 파라미터 형식)
    - 전송 데이터를 uri 인코딩 처리
      - ex) abc김 -> abc%EA%B9%80
  - Html form은 GET 전송도 가능
  - Content-Type: multipart/form-data
    - 파일 업로드같은 바이너리 데이터 전송 시 사용
    - 다른 종류의 여러 파일과 폼의 내용을 함께 전송 가능하다.
  - 참고) GET,POST만 지원
- http api 데이터 전송
  - 서버 to 서버
  - 앱 클라리런트
    - 아이폰, 안드로이드
  - 웹 클라이언트
    - Html 에서 form 전송 대신 자바스크립트를 통한 통신에 사용 (ajax)
    - ex) react, vuejs 같은 웹 클라이언트와 api 통신
  - Content-Type: application/json



## HTTP API 설계 예시

- **POST** 신규자원 등록 특징
  - ex) POST /members 
    - response: locaiton: members/100

  - 클라이언트는 등록될 리소스의 URI를 모른다.
  - 서버가 새로 등록된 리소스URI를 생성해준다.
  - **컬렉션**
    - 서버가 관리하는 리소스 디렉토리
    - 서버가 리소소의 URI를 생성하고 관리
    - 여기서 컬렉션은 /members

- **PUT** 기반 등록
  - 클라이언트가 리소스의 URI를 알고있어야 한다.
  - 클라이언트가 직접 리소스의 URI를 지정한다.
  - **스토어**
    - 클라이언트가 관리하는 리소스 저장소
    - 클라이언트가 리소의 URI를 알고 관리



### HTML FORM 사용

- GET, POST만 지원
- 컨트롤 URI
  - 동사로 된 리소스 경로 사용
    -  /new, /edit, delete
  - HTTP 메서드로 해결하기 애매한 경우 사용



### 정리

### 참고하면 좋은 URI 설계 개념

- 문서
  - 단일개념
  - /members/100, /fiiles/start.jpg
- 컬렉션
  - 서버가 관리하는 리소스 디렉토리
  - /memeber
- 스토어
  - 클라이언트가 관리하는 자원 저장소
  - /files

- 컨트롤러, 컨트롤 URI
  - 문서, 컬렉션, 스토어로 해결하기 어려운 추가 프로세스 실행
  - 동사를 직접 사용
  - /members/{id}/delete



참고 사이트 : [REST API Tutorial > REST Resource Naming Guide](https://restfulapi.net/resource-naming)

