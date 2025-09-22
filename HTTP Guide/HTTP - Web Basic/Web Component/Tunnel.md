-----
### 터널
-----
1. 두 커넥션 사이 날(Raw) 데이터를 열어보지 않고 그대로 전달해주는 HTTP 애플리케이션
2. HTTP 터널은 주로 비 HTTP 데이터를 하나 이상의 HTTP 연결을 통해 그대로 전송해주기 위해 사용
3. HTTP 터널 활용 예) 암호화된 SSL 트래픽을 HTTP 커넥션으로 전송함으로써 웹 트래픽만 허용하는 사내 방화벽을 통과시키는 것
<div align="center">
<img src="https://github.com/user-attachments/assets/1751851c-ce8a-40ae-b787-297f456e31d7">
</div>

   - HTTP/SSL 터널은 HTTP 요청을 받아들여 목적지의 주소와 포트번호로 커넥션을 맺음
   - 이후부터는 암호화된 SSL 트래픽을 HTTP 채널을 통해 목적지 서버로 전송할 수 있게 됨
