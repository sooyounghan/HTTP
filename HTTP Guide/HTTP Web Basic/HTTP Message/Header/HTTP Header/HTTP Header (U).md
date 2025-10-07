-----
### UA-(CPU, Disp, OS, Color, Pixels)
-----
1. 사용자 에이전트에 대한 이 헤더들은 더 이상 흔히 쓰이지 않음
2. 이들은 클라이언트 장비에 대한 정보를 제공해, 서버가 더 나은 콘텐츠를 선택할 수 있도록 해줌
3. 예) 사용자의 장비가 8비트 컬러 디스플레이만 갖고 있다고 한다면, 서버는 그 유형의 디스플레이에 맞는 이미지를 선택할 수 있을 것
4. 다른 헤더들은 제공할 수 없는 클라이언트에 대한 정보를 제공하는 헤더들은 다소 보안 문제를 유발할 수 있음
<div align="center">
<img src="https://github.com/user-attachments/assets/49ad49dc-c6a1-4ef0-bdeb-aa7e0ea36df2">
</div>

<div align="center">
<img src="https://github.com/user-attachments/assets/4c8d0f6e-5db7-4625-b06e-e91397244bd8">
</div>

-----
### Upgrade
-----
1. 메세지를 발송하는 사람이 다른(완전히 다른) 프로토콜을 사용하고 싶다는 의사를 전달할 수 있게 해줌
2. 예를 들어, HTTP/1.1 클라이언트는 서버에게 값이 HTTP/1.1인 Upgrate 헤더를 포함한 HTTP/1.0 요청을 보낼 수 있으며, 이는 서버가 HTTP/1.1을 지원하는지 클라이언트가 미리 확인할 수 있게 해줄 것
3. 만약 서버가 지원한다면 서버는 클라이언트에게 새로운 프로토콜을 사용해도 되는지 알려주기 위해 적절한 응답을 보낼 수 있음
4. 이는 다른 프로토콜로 옮겨가기 위한 효율적 수단을 제공
   - 이 전략은 서버가 HTTP/1.1을 지원하는 것이 확인되지 않았을 때, 클라이언트가 너무 많은 HTTP/1.1 헤더로 서버를 혼란스럽게 만들지 않을 수 있도록 해줌
5. 서버가 101 Switching Protocols 응답을 보내는 경우에만 반드시 이 헤더를 포함해야 함
<div align="center">
<img src="https://github.com/user-attachments/assets/a41078b1-8604-486e-9a98-bdcfa1cb43d2">
</div>

-----
### User-Agent
-----
1. 서버가 Server 헤더를 사용하는 것과 마찬가지로, 클라이언트 애플리케이션이 자신의 신원을 밝히기 위해 사용
2. 이 헤더의 값은 제품의 이름과 (만약 가능하다면) 클라이언트 애플리케이션에 대한 코멘트
3. 포맷은 다소 자유로움 : 헤더의 값은 클라이언트 제품마다 다르고 버전마다 다름
   - 이 헤더는 때때로 클라이언트가 실행되고 있는 장치에 대한 정보를 포함하기도 함
<div align="center">
<img src="https://github.com/user-attachments/assets/eba64cdf-da67-49df-af7a-c24581264e53">
</div>
