-----
### CONNECT로 HTTP 터널 커넥션 맺기
-----
1. 웹 터널은 HTTP의 CONNECT 메서드를 사용해 커넥션을 맺음
2. CONNECT 프로토콜은 HTTP/1.1 명세에 나와있지는 않지만(CONNECT 메서드를 예약했지만, 그 기능에 대해 설명하지 않음), 많이 구현하는 확장
3. CONNECT 메서드는 터널 게이트웨이가 임의의 목적 서버와 포트에 TCP 커넥션을 맺고 클라이언트와 서버 간에 오는 데이터를 무조건 전달하기를 요청
4. CONNECT 메서드를 통한 게이트웨이과 터널 연결 과정
<div align="center">
<img src="https://github.com/user-attachments/assets/a5f699ec-5a14-46db-bb0f-fa0de0bfd3c4">
</div>

   - 8-10a : 클라이언트는 게이트웨이에 터널을 연결하려고 CONENCT 요청을 보내며, 클라이언트의 CONENCT 메서드는 TCP 커넥션을 위해 게이트웨이에 터널 연결 요청(여기서는 SSL 포트인 443 포트에 호스트명이 ```orders.joes-hardward.com```인 곳으로)
   - TCP 커넥션은 8-10b, 8-10c와 같이 생성
   - TCP 커넥션이 맺어지면, 게이트웨이는 클라이언트에게 HTTP 200 Connection Established 응답을 전송(8-10d)하여 연결되었음을 알림
   - 이 시점에 터널 연결 : HTTP 터널을 통해 전송된 클라이언트의 모든 데이터는 위에서 맺은 TCP 커넥션으로 바로 전달될 것이며, 서버로부터 전송된 모든 데이터 역시 HTTP 터널을 통해 클라이언트에게 전달

5. CONNECT 메서드는 모든 서버나 프로토콜에 TCP 커넥션을 맺는데 사용 가능
6. CONNECT 요청
   - CONNECT 문법은 시작줄을 제외하고 다른 HTTP 메서드와 같음
   - 요청 URI는 호스트 명이 대신하여 콜론에 이어 포트 기술
   - 호스트와 포트는 다음과 같이 기술
<div align="center">
<img src="https://github.com/user-attachments/assets/312ac889-52d2-4543-9b47-11c65435aeea">
</div>

   - 시작줄 다음에는 다른 HTTP 메세지와 같이, 추가적인 HTTP 요청 헤더 필드가 있거나 없음
   - 보통 각 행은 CRLF로 끝나고, 헤더 목록의 끝은 빈 줄의 CRLF로 끝남

7. CONNECT 응답
   - 클라이언트는 요청을 전송한 다음, 게이트웨이 응답을 기다림
   - 일반 HTTP 메세지와 같이 200 응답 코드는 성공을 뜻함
   - 편의상 응답에 있는 사유 구절은 Connection Established로 기술
<div align="center">
<img src="https://github.com/user-attachments/assets/29741b28-20eb-4f95-88c3-8677f2e62686">
</div>

   - 일반적인 HTTP 응답과는 달리 Content-Type 헤더를 포함할 필요는 없음 : 커넥션이 메세지를 전달하는 대신 바이트를 그대로 전달하므로 콘텐츠 형식을 기술하는 Content-Type 헤더를 포함할 필요가 없음
