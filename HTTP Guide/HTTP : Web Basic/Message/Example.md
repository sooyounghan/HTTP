-----
### 간단한 메세지의 예
-----
1. 간단한 HTTP 메세지를 주고 받는 트랜잭션
<div align="center">
<img src="https://github.com/user-attachments/assets/8836d0ea-9a0f-4dc3-91a6-3df3f274a423">
</div>

  - 웹 브라우저는 리소스 ```http://www.joes-hardware.com/tools.html```을 요청
  - 웹 브라우저는 HTTP 요청 메세지를 보냄
    + 요청 시작줄에 GET 메서드가 있으며, 로컬 리소스는 /tools.html
    + HTTP 프로토콜 1.0 버전으로 요청을 보내고 있음도 표시
    + 본문은 없음 : 서버에서 간단한 문서를 가져오는 데 요청 데이터가 필요 없음

  - 서버는 HTTP 응답 메세지를 돌려줌
    + 응답에는 HTTP 버전 번호 (HTTP/1.0), 성공 상태 코드(200), 사유 구절(OK), 응답 헤더 필드 영역, 마지막으로 요청한 문서가 담겨 있는 응답 본문이 들어있음
    + 응답 본문 길이는 Content-Length 헤더에, 문서의 MIME 타입은 Content-Type 헤더에 적혀있음
