-----
### 프로토콜 게이트웨이
-----
1. 프록시에 트래픽을 바로 보내는 것과 같이 게이트웨이도 HTTP 트래픽을 바로 보낼 수 있음
   - 보통 브라우저에 명시적으로 게이트웨이를 설정해 자연스럽게 트래픽이 게이트웨이를 거쳐 가게 하거나, 게이트웨이를 대리 서버(리버스 프록시)로 설정할 수 있음

2. 브라우저에서 서버 측 FTP 게이트웨이를 사용하게 설정할 수 있는 방법
<div align="center">
<img src="https://github.com/user-attachments/assets/5be76ab7-d304-4692-be91-ada91aef78b4">
</div>

   - 브라우저는 ```gw1.joes-hardware.com```을 모든 FTP URL에 대한 HTTP/FTP 게이트웨이로 설정
   - 브라우저는 FTP 서버에 FTP 명령을 보내는 대신, HTTP/FTP 게이트웨이인 ```gw1.joes-hardware.com```의 8080포트에 HTTP 명령을 보낼 것

3. 게이트웨이 설정 후, 브라우저의 동작 방식
<div align="center">
<img src="https://github.com/user-attachments/assets/c6dbfb99-cee5-4df8-ba23-fa5ead412153">
</div>

   - 일반적인 HTTP 트래픽에는 영향을 미치지 않으며, 브라우저는 HTTP 트래픽은 원 서버로 바로 보냄
   - 하지만 FTP URL을 포함한 요청은 ```gw1.joes-hardware.com``` 게이트웨이로 HTTP 요청을 보냄
   - 게이트웨이는 클라이언트 측 요청을 FTP 요청으로 변환하여 처리한 뒤 클라이언트에게 그 결과를 HTTP로 전송
