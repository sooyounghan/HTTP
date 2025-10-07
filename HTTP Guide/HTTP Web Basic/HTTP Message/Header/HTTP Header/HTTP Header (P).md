-----
### Pragma
-----
1. 메세지와 함께 지시자를 넘겨주기 위해 사용
2. 이들 지시자들은 어느 것이든 될 수 있지만, 보통 그들은 캐시 동작을 제어하기 위해 사용
3. 💡 프록시와 게이트웨이는 절대 Pragma 헤더를 지워서 안 되는데, 메세지를 받는 모든 애플리케이션을 위한 것으로 의도했던 것일 수 있기 때문임
4. 가장 흔한 형태 : Pragma: no-cache
   - 신선한 사본이 캐시에 존재하더라도 원 서버로부터 문서를 요청하거나 혹은 재검사를 하도록 강제하는 요청 헤더
   - 사용자가 Reload / Refresh 버튼을 클릭했을 때 브라우저는 이 요청을 보냄
   - 많은 서버가 응답 헤더로 이 형태를 보내는데, 널리 사용되고 있지만 엄밀하게 정의되지 않음
5. 모든 애플리케이션이 Pragma 응답 헤더를 지원하는 것은 아님
<div align="center">
<img src="https://github.com/user-attachments/assets/14a3cb6c-f1ec-4b30-ae4f-6ab71550c6c1">
</div>

-----
### Proxy-Authenticate
-----
1. WWW-Authenticate 헤더처럼 기능
2. 이 헤더는 프록시가 애플리케이션에게 자신의 신원 증명이 담긴 요청을 보내라는 인증 요구를 할 때 사용
3. 만약 HTTP/1.1 프록시 서버가 407 Proxy Authenticate Required 응답을 보내고 있다면, 반드시 Proxy-Authenticate 헤더를 포함해야 함
4. 💡 프록시와 게이트웨이는 반드시 프록시와 관련된 헤더들의 해석에 주의해야 함
   - 이 헤더들은 일반적으로 홉과 홉 사이 현재 커넥션에만 적용되는 헤더(Hop-by-Hop 헤더)
   - 즉, 이 헤더는 현재 커넥션에 대한 인증을 요구
<div align="center">
<img src="https://github.com/user-attachments/assets/401741ef-6433-43ab-945f-f1ca64facebe">
</div>

-----
### Proxy-Authorization
-----
1. Authorization 헤더처럼 기능
2. 이 헤더는 Proxy-Authenticate 인증 요구에 응답하기 위해 클라이언트 애플리케이션에 의해 사용
<div align="center">
<img src="https://github.com/user-attachments/assets/d3c60d9d-7180-495d-a3db-7880b9aa07a2">
</div>

-----
### Proxy-Connection
-----
1. HTTP/1.0 Connection 헤더와 비슷한 의미를 갖고 있음
2. 이 헤더는 클라이언트와 프록시 사이에서 커넥션(주로 keep-alive 커넥션)에 대한 옵션을 명시하기 위해 사용
   - 표준 헤더는 아니며, 임시로 만든 헤더로 간주하고 있지만, 브라우저들과 프록시들 사이에서 널리 쓰임

3. 브라우저 구현자들은 멍청한(Dumb) 프록시에 의해 맹목적으로 전달된 HTTP/1.0 커넥션 헤더를 보내는 클라이언트 문제를 해결하기 위해 이 헤더를 만듬
   - 맹목적으로 전달되는 Connection 헤더를 받은 서버는 커넥션에 대한 프록시 능력을 클라이언트 능력으로 오해할 가능성 존재

4. 이 헤더가 프록시를 통과하게 되리라는 것을 클라이언트가 알고 있다면, 클라이언트는 Connection 헤더 대신 Proxy-Connection 헤더를 보냄
   - 서버들은 Proxy-Connection 헤더를 인식하지 못하므로, 이를 무시할 것이고 ,따라서 이는 멍청한 프록시가 서버에 아무런 영향을 미치지 않고 맹목적으로 그 헤더를 전달할 수 있게 해줌

5. 이 해결책은 클라이언트에서 서버로의 경로에서 프록시가 둘 이상 존재하는 경우 문제 발생
   - 첫 번째 프록시가 이 헤더를 두 번째 프록시로 전달했는데, 그 두 번째 프록시가 이 헤더를 이해한다면, 서버가 Connection 헤더에 대해 겪은 것과 같은 혼란을 겪음

6. HTTP 작업 그룹은 이 해결책이 단일 프록시 한해서만 문제 해결이 가능하다고 보아, 문제가 있는 것으로 간주
   - 하지만 이는 흔히 발생할 수 있는 문제를 상당 부분 해결해주며, 이 헤더는 오래된 버전의 넷스케이프와 네비게이터와 마이크로소프트 인터넷 익스플로러에 의해 구현되었으므로, 프록시 구현자들 역시 이 헤더를 처리해줄 필요가 있음
<div align="center">
<img src="https://github.com/user-attachments/assets/0c3eca59-85e3-473d-8066-443d79efdc9a">
</div>

-----
### Public
-----
1. 서버가 클라이언트에게 자신이 지원하는 메서드를 말해줄 수 있게 해줌
2. 이들 메서드들은 클라이언트가 나중에 요청을 보낼 때 사용될 수 있음
3. 프록시들은 서버로부터 Public 헤더를 포함한 응답을 받을 때 주의가 필요
   - 이 헤더들은 프록시가 아닌 서버 능력을 알려주므로, 프록시는 이 응답을 클라이언트에게 보내기 전 이 헤더들에 있는 메서드 목록을 고치거나 제거할 필요가 있음
<div align="center">
<img src="https://github.com/user-attachments/assets/9e8af944-3af5-4b51-a7cb-97863693ca9b">
</div>

