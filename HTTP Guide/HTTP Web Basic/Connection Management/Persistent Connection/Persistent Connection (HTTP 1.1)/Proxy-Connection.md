-----
### Proxy-Connection
-----
1. 넷스케이프 브라우저 및 프록시 개발자들은 모든 웹 애플리케이션이 HTTP 최선 버전을 지원하지 않아도 모든 헤더를 무조건 전달하는 문제 해결하는 기발한 차선책 개발
2. 클라이언트 요청이 중개서버를 통해 이어지는 경우 모든 헤더를 무조건 전달해야 하는 문제 해결을 위해 Proxy-Conneciton이라는 헤더 사용 (하지만 모든 상황에서 동작하지 않음)
3. Proxy-Connection은 프룍시를 별도로 설정할 수 있는 현대의 브라우저들에서 지원하고 있으며, 많은 프록시들도 이를 인식
4. 멍청한 프록시는 Connection: Keep-Alive 같은 홉별 헤더를 무조건 전달하므로 문제를 일으킴
   - 홉별 헤더들은 한 개의 특정 커넥션에서 쓰이고 그 이후에는 전달하면 안 됨
   - 홉별 헤더를 전달받은 서버가 그 헤더를 자신과 프록시 간의 커넥션에 대한 것으로 오해하면서 문제가 생기는 것

5. 넷스케이프는 멍청한 프록시 문제를 해결하기 위해 브라우저에서 일반적으로 전달하는 Connection 헤더 대신 비 표준인 Proxy-Connection 확장 헤더를 프록시에게 전달
   - 프록시가 Proxy-Connection 헤더를 무조건 전달하더라도 웹 서버는 그것을 무시하기 때문에 문제가 되지 않음
   - 하지만 영리한 프록시(지속 커넥션 핸드세이킹을 이해할 수 있는)라면, 의미 없는 Proxy-Connection 헤더를 Connection 헤더로 바꿈으로써 효과를 얻음

6. Proxy-Connection 헤더가 웹 서버에 전달 될 경우
<div align="center">
<img src="https://github.com/user-attachments/assets/3b04489d-93b9-4c56-b221-9cea1c5cbb72">
</div>

  - a ~ d : Proxy-Connection 헤더가 웹 서버에 전달되더라도 클라이언트와 프록시 사이 혹은 프록시와 서버 사이에 keep-alive 커넥션이 맺어지지 않게 됨
  - e ~ h : 영리한 프록시는 Proxy-Connection 헤더가 keep-alive를 요청하는 것임을 인식해, keep-alive 커넥션을 맺기 위해 자체적으로 Conneciton: Keep-Alive 헤더를 웹 서버에 전송
  - 💡 이 방식은 클라이언트와 서버 사이에 한 개의 프락시만 있는 경우 동작

7. 💡 하지만 멍청한 프록시 양 옆 영리한 프록시가 있다면, 잘못된 헤더를 만들어내는 문제가 다시 발생
<div align="center">
<img src="https://github.com/user-attachments/assets/b5a2b588-edea-42f0-a6bc-8e685537c23f">
</div>

  - 게다가 문제를 발생시키는 프록시들은 방화벽, 캐시 서버, 혹은 리버스 프록시 서버 가속기와 같이 네트워크 상에서 보이지 않는 경우가 많음
  - 브라우저는 이러한 기기들을 볼 수 없으므로 Proxy-Connection 헤더를 보내지 못하며, 보이지 않는 웹 애플리케이션들이 지속 커넥션을 명확히 구현하는 것이 중요
