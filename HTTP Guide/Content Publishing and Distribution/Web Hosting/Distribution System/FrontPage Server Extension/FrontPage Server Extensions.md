-----
### FrontPage 서버 확장
-----
1. '어디서든 배포한다'라는 전략의 하나로, 마이크로소프트는 FrontPage 서버 확장(FrontPage Server Extensions, FPSE)이라는 서버 측 소프트웨어 제품군 출시
2. 서버 측 컴포넌트는 웹 서버와 통합되어 웹 사이트와 FrontPage를 구동시키는 클라이언트(그리고 이 확장을 지원하는 클라이언트) 사이에서 필요한 변환 작업 수행
3. FP 클라이언트와 FPSE 사이에서 사용하는 배포 프로토콜
   - 이 프로토콜은 HTTP의 기본 의미를 바꾸지 않고서도 핵심 서비스에서 HTTP를 그대로 사용할 수 있게 확장을 설계한 좋은 사례
   - FrontPage 배포 프로토콜은 HTTP POST 요청 위에 RPC 계층을 구현 : 이를 이용하면, 웹 사이트에 있는 문서를 갱신하고, 검색을 수행하고, 웹 개발자들 간 공동 작업을 할 수 있게 FrontPage 클라이언트가 서버에 명령을 보낼 수 있음
<div align="center">
<img src="https://github.com/user-attachments/assets/0225bd73-ba6a-47af-9ff8-28e3c8aef8da">
</div>

4. 웹 서버는 FPSE(마이크로소프트 IIS 서버가 아니면, CGI 구성으로 구현)에 맞춘 POST 요청을 받아 처리
5. 클라이언트와 서버 사이에 방화벽과 프록시 서버가 있더라도 POST 메서드 통신만 할 수 있다면 FrontPage는 서버와 통신을 계속할 수 있음

