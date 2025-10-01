-----
### HTTPS
-----
1. HTTP를 안전하게 만드는 방식 중 가장 인기 있는 것
2. 넷스케이프 커뮤니케이션 주식 회사(Netscape Communications Corporation)에서 개척하였으며, 모든 주류 브라우저와 서버에서 지원
3. 웹 페이지에 HTTP가 아닌 HTTPS로 접근하고 있는 경우, URL이 ```http://``` 대신 ```https://```로 시작
<div align="center">
<img src="https://github.com/user-attachments/assets/f9bedf8e-c7cd-447d-810b-cd1ab9c9e35e">
</div>

4. HTTPS를 사용할 때, 모든 HTTP 요청과 응답 데이터는 네트워크로 보내지기 전 암호화
   - HTTPS는 HTTP 하부에 전송 레벨 암호 보안 계층을 제공함으로써 동작
   - 이 보안 계층은 안전 소켓 계층(Secure Sockets Layer, SSL) 혹은 그를 계승한 전송 계층 보안(Transport Layer Security, TLS)를 이용해 구현
<div align="center">
<img src="https://github.com/user-attachments/assets/a0c6fd76-b383-4976-8df9-e36c2df51540">
</div>

   - SSL과 TLS는 매우 비슷
   - 어려운 인코딩 및 디코딩 작업은 대부분 SSL 라이브러리 안에서 일어나므로, 보안 HTTP를 사용하기 위해 웹 클라이언트와 서버가 프로토콜을 처리하는 로직을 크게 변경할 필요가 없음
   - 대부분의 경우, TCP 입력 / 출력 호출을 SSL 호출로 대체하고, 보안 정보를 설정하고 관리하기 위한 몇 가지 호출을 추가하기만 하면 됨
