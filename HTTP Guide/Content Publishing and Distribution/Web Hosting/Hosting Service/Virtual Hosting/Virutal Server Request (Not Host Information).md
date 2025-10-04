-----
### 호스트 정보가 없는 가상 서버 요청
-----
1. HTTP/1.0에는 가상 호스팅에 관한 설계 관련 결함이 존재 : HTTP/1.0 명세는 공용 웹 서버가 호스팅하고 있는 가상 웹 사이트가 누가 접근하고 있는지 식별하는 기능을 제공하지 않음
2. HTTP/1.0 요청은 요청 메세지에 URL 경로 컴포넌트만 전송함
   - 만약, ```http://www.joes-hardware.com/index.html```을 요청하면, 브라우저는 ```www.joes-hardware.com```에 연결을 하지만, HTTP/1.0 요청은 호스트 명에 별다른 언급 없이 GET /index.html이라는 요청을 함
   - 서버가 여러 개의 사이트를 가상 호스팅 하고 있으면, 사용자가 어떤 가상 웹 사이트를 접근하려고 하는 것인지 아는 데 필요한 정보가 충분하지 않음
<div align="center">
<img src="https://github.com/user-attachments/assets/7e69204c-d967-41b2-bf37-13cc442982ec">
</div>

   - 클라이언트 A가 ```http://www.joes-hardware.com/index.html```에 접속하려고 하면, GET /index.html 요청이 공용 웹 서버에 전송
   - 클라이언트 B가 ```http://www.marys-antiques.com/index.html```에 접속하려고 한다면, 위와 같은 GET /index.html 요청이 ```joes-hardware.com```과 공유하고 있는 공유 웹 서버에 전송

3. 웹 서버는 사용자가 어떤 웹 사이트로 접근하려고 하는지 아는데 필요한 정보가 충분하지 않음
4. 두 요청이 (서로 다른 웹 사이트에) 완전히 다른 문서를 요청하더라도, 요청 자체는 똑같이 생겼으므로, 문제는 웹 사이트 호스트 정보가 요청에서 제거됨
5. HTTP 대리 서버(리버스 프록시)와 인터셉트 프록시 또한 어떤 사이트를 요청하는지에 관한 정보가 필요
