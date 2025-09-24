-----
### 간단한 펄 웹 서버
-----
1. HTTP/1.1의 기능들을 지원하려면, 풍부한 리소스 지원 / 가상 호스팅 / 접근 제어 / 로깅 / 설정 / 모니터링 / 그 외 성능을 위한 각종 기능들이 필요
2. type-o-serve : 작은 펄 프로그램 (클라이언트와 프록시 간 상호 작용 테스트에 유용한 진단 툴)
<div align="center">
<img src="https://github.com/user-attachments/assets/a7b76d43-3ba5-4911-aec8-f34bcd76292a">
</div>

   - type-o-serve는 HTTP 커넥션을 기다리며, 요청 메세지를 받자마자 화면에 출력
   - 그리고 클라이언트에게 답해줄 응답 메세지를 타이핑 하기를(혹은 붙여넣기를) 기다림
   - type-o-serve가 웹 서버를 흉내 내는 이 방식은, HTTP 요청 메세지를 정확하게 기록하고 어떤 HTTP 응답 메세지라도 돌려보내줄 수 있도록 함
   - 텔넷으로 클라이언트 요청 메세지를 생성했던 것과 같은 방법으로 서버 응답 메세지를 생성할 수 있게 해주는 유용한 도구

3. type-o-serve를 이용해 어떻게 HTTP 테스트하는지 보여줌
<div align="center">
<img src="https://github.com/user-attachments/assets/15c51025-7431-47ab-b33f-4b31232f616b">
</div>

   - 먼저, 관리자는 특정 포트로 수신하는 type-o-serve 진단 서버를 시작
     + 이미 80번 포트로 수신하고 있는 웹 서버를 가지고 있으므로, 관리자는 ```# type-o-serve.pl 8080```를 입력해 type-o-serve 서버를 8080번 포트(사용하지 않는 아무 포트나 선택할 수 있음)로 시작
   - type-o-serve가 동작하기 시작하면, 이 웹 서버에 브라우저로 접근할 수 있음 : ```http://www.joes-hardware.com:8080/foo/bar/blah.txt```에 접근
   - type-o-serve 프로그램은 브라우저로부터 HTTP 요청 메세지를 받아 그 내용을 화면에 출력한 뒤, 관리자가 마침표 하나 뿐인 줄로 끝나는 간단한 응답 메세지를 입력할 때까지 기다림
   - type-o-serve는 HTTP 응다 메세지를 브라우저에게 돌려주고, 브라우저는 응답 메세지의 본문을 출력
