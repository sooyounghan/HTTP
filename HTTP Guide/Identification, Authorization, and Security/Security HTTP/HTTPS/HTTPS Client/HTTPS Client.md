-----
### HTTPS 클라이언트
-----
1. OpenSSL 패키지 사용
   - 이 클라이언트는 서버와 SSL 커넥션을 맺고, 그 사이트 서버로부터 가져온 신원 정보를 출력
   - HTTP GET 요청을 보안 채널을 통해 보내고, HTTP 응답을 받아 그 응답을 출력

2. OpenSSL을 이용해 구현한 간단한 HTTPS 클라이언트 (C 프로그램)
<div align="center">
<img src="https://github.com/user-attachments/assets/f7e4723a-b405-44c8-b033-c075dffd8fc3">
</div>

<div align="center">
<img src="https://github.com/user-attachments/assets/0ef077c8-013d-4ef3-a8de-5f9f086f2995">
</div>


<div align="center">
<img src="https://github.com/user-attachments/assets/bdefd7a7-1cc2-45e0-bd30-ffa1a745e6d7">
</div>

  - 프로그램의 제일 위 : TCP 네트워킹과 SSL을 지원하기 위해 필요한 지원 파일들 포함
  - 섹션 1 : SSL_CTX_new를 호출해 핸드쉐이크 매개변수와 그 외 SSL 커넥션에 대한 상태들을 추적할 로컬 컨텍스트 생성
  - 섹션 2 : 유닉스 gethostbyname 함수를 이용해 입력 호스트 명(명령줄 인수로 제공)을 IP 주소로 변환
  - 섹션 3 : 로컬 소켓을 생성해 서버의 443번 포트로 TCP 커넥션을 열고, 원격 주소 정보를 설정한 뒤, 원격 서버와 연결
  - 한번 TCP 커넥션이 수행되면, SSL_new와 SSL_set_fd를 사용해 SSL 레이어를 TCP 커넥션에 붙이고, SSL_connect를 호출해 서버와의 SSL 핸드쉐이크를 수행
  - 섹션 4가 완료되면 암호 선택 및 인증 교환이 완료되고 동작하는 SSL 채널을 수립
  - 섹션 5 : 선택된 대량 암호화 암호의 값 출력
  - 섹션 6 : 서버가 되돌려준 X.509 인증서에 포함된 정보들 중 일부 출력 (인증서 소지자 및 인증서를 발급한 기관 정보 등)
    + OpenSSL 라이브러리는 서버 인증서 정보에 대해서는 특별히 하는 일은 없음
    + 웹 브라우저와 같은 SSL 애플리케이션은, 그 인증서가 올바르게 성명되고 올바른 호스트에서 왔다는 것을 확인하기 위해 인증서에 대한 기본적 검사 실시

  - 이 시점에서, SSL 커넥션은 데이터 전송을 위해 사용할 준비가 되어 있음
  - 섹션 7 : SSL_write를 이용해 단순한 HTTP 요청 "GET / HTTP/1.0"을 SSL 채널을 통해 전송하고, 커넥션의 나가는 쪽 절반을 닫음
  - 섹션 8 : SSL_read를 사용해 커넥션으로부터 받은 응답을 읽고, 화면에 출력 (SSL 계층은 암호화와 해독을 모두 다루므로, HTTP 명령을 쓰고 읽기만 하면 됨)
  - 섹션 9 : 모든 것을 정리

-----
### OpenSSL 클라이언트 실행
-----
1. HTTP 클라이언트가 보안 서버에 접속했을 때 출력
<div align="center">
<img src="https://github.com/user-attachments/assets/1f384eb6-dbc4-4517-90e0-5f143d5b3135">
</div>

2. 처음 네 섹션이 완료되자마자, 클라이언트는 열린 SSL 커넥션을 갖게 됨
3. 클라이언트는 커넥션의 상태와 선택된 매개변수에 대해 물어보고 서버의 인증서 검증 가능
4. 이 예에서, 클라이언트와 서버는 DES-CBC3-MD5 대량 암호화 암호를 쓰는 것 합의
   - 이 인증서는 RSA 데이터 시큐리티에 의해 승인되었으며, 요청에 대응하는 호스트명은 ```clients1.online.msdw.com```

5. 한편 SSL 채널이 수립되고, 클라이언트 사이트 인증서를 안심하게 받아들이게 되면, 클라이언트는 자신의 HTTP 요청을 보안 채널을 통해 전송
   - 이 예에서는 클라이언트는 단순히 "GET / HTTP/1.0" HTTP 요청을 보내고, 사용자가 다른 URL로 이동하도록 요청하는 302 Redirect 응답을 받음
