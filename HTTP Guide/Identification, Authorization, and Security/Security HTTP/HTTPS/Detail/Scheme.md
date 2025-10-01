-----
### HTTPS 스킴
-----
1. 오늘날 보안 HTTP는 선택적으로, 웹 서버로의 요청을 만들 때, 웹 서버에게 HTTP의 보안 프로토콜 버전을 수행한다고 말해줄 방법 필요한데, 이는 URL 스킵을 통해 이루어짐
2. 보안이 없는 일반적인 HTTP는 URL의 스킴 접두사는 http
<div align="center">
<img src="https://github.com/user-attachments/assets/09611faf-49dc-416f-ba51-d4be73890fa9">
</div>

3. 보안이 되는 HTTPS 프로토콜에서 URL의 스킴 접두사는 https
<div align="center">
<img src="https://github.com/user-attachments/assets/9d843901-f96e-43c1-a92c-f2eea67d78ac">
</div>

4. 웹 브라우저 등의 클라이언트는 웹 리소스에 대한 트랜잭션 수행을 요청 받으면 URL 스킴을 검사
   - 만약 URL이 http 스킴을 갖고 있다면, 클라이언트는 서버에 80번(기본값) 포트로 연결하고 평범한 HTTP 명령 전송
   - 만약 URL이 https 스킴을 갖고 있다면, 클라이언트는 서버에 443번(기본값) 포트로 연결하고 서버와 바이너리 포맷으로 몇몇 SSL 보안 매개변수를 교환하면서 핸드쉐이크를 하고, 암호화된 HTTP 명령이 뒤를 이음
<div align="center">
<img src="https://github.com/user-attachments/assets/4235550a-5df9-45a8-a15b-f9aa26a18597">
</div>

5. SSL 트래픽은 바이너리 프로토콜이므로, HTTP와는 완전히 다름
   - 그 트래픽은 다른 포트(SSL은 보통 443 포트를 통해 전달)로 전달
   - 만약 SSL과 HTTP 트래픽 모두 80번 포트로 도착한다면, 대부분 웹브라우저는 바이너리 SSL 트래픽을 잘못된 HTTP로 해석하고 커넥션을 닫을 것
   - 보안 서비스가 HTTP 쪽으로 계층 통합이 되도록 하면 포트가 둘 이상 필요할 이유가 사라지겠지만, 이는 심각한 문제를 일으키지 않음
