-----
### 웹 클라이언트와 서버
-----
1. 웹 콘텐츠는 웹 서버에 존재
2. 웹 서버는 HTTP 프로토콜로 의사소통하므로 보통 HTTP 서버라 불림
   - 이들 웹 서버는 인터넷의 데이터를 저장하고, HTTP 클라이언트가 요청한 데이터를 제공

3. 클라이언트는 서버에게 HTTP 요청을 보내고 서버는 요청된 데이터를 HTTP 응답으로 돌려줌
  - HTTP 클라이언트와 HTTP 서버는 월드 와이드 웹의 기본 요소
<div align="center">
<img src="https://github.com/user-attachments/assets/c531b4c6-defb-4b11-ab95-212d02471e3f">
</div>

4. 예) ```http://www.oreilly.com/index.html``` 페이지를 열 때
   - 웹 브라우저는 HTTP 요청을 ```www.oreilly.com``` 서버로 보냄
   - 서버는 요청 받은 객체(이 경우 ```/index.html```)를 찾고, 성공했다면 그것의 타입, 길이 등의 정보와 함께 HTTP 응답에 실어서 클라이언트에게 보냄
