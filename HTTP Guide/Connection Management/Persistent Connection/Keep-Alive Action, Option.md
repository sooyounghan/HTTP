-----
### Keep-Alive 동작
-----
1. keep-alive는 사용하지 않기로 결정되어 HTTP/1.1 명세에서 제외
   - 하지만, 아직도 브라우저와 서버 간 Keep-Alive 핸드쉐이크가 널리 사용되고 있으므로, HTTP 애플리케이션은 그것을 처리할 수 있게 개발해야 함
   - keep-alive 핸드세이크에 대한 설명은 RFC 2608 또는 HTTP/1.1 이전 버전 명세 참조

2. HTTP/1.0 keep-alive 커넥션을 구현한 클라이언트는 커넥션을 유지하기 위해 요청에 Connection: Keep-Alive 라는 헤더 포함
   - 이 요청을 받은 서버는 그 다음 요청도 이 커넥션을 통해 받고자 한다면, 응답 메세지에 같은 헤더를 포함시켜 응답
<div align="center">
<img src="https://github.com/user-attachments/assets/a90edbb5-d372-47b0-a81a-3fde1bf3d665">
</div>

   - 응답에 Connection: Keep-Alive 헤더가 없으면, 클라이언트는 서버가 keep-alive를 지원하지 않으며, 응답 메세지가 전송되고 나면 서버 커넥션을 끊을 것으로 추정

-----
### Keep-Alive 옵션
-----
1. Kepp-Alive 헤더는 커넥션을 유지하길 바라는 요청일 뿐이며, 클라이언트나 서버가 keep-alive 요청을 받았다고해서 무조건 그것을 따를 필요는 없음
2. 언제든지 현재 keep-alive 커넥션을 끊을 수 있으며, keep-alive 커넥션에서 처리되는 트랜잭션 수를 제한 가능
3. keep-alive의 동작은 Keep-Alive 헤더의 쉼표로 구분된 옵션들로 제어 가능
   - timeout 파라미터 : Keep-Alive 응답 헤더를 통해 보내며, 이는 커넥션이 얼마간 유지될 것인지 의미하지만, 그대로 동작한다는 보장 없음
   - max 파라미터 : Keep-Alive 응답 헤더를 통해 보내며, 커넥션이 몇 개의 HTTP 트랜잭션을 처리할 때까지 유지될 것인지 의미하지만, 그대로 동작한다는 보장 없음
   - Keep-Alive 헤더는 진단이나 디버깅을 주 목적으로 하는, 처리되지 않는 임의의 속성들을 지원하기도 하며, 그 문법은 이름[=값] 같은 식

4. Kepp-Alive 헤더 사용은 선택 사항이지만, Connection: Keep-Alive 헤더가 있을 때만 사용 가능
5. 예) 서버가 약 5개의 추가 트랜잭션이 처리될 동안 트랜잭션을 유지하거나 2분 동안 커넥션을 유지하라는 내용의 Keep-Alive 응답 헤더
<div align="center">
<img src="https://github.com/user-attachments/assets/e7fbe9b6-22d9-48f5-990b-a77839f7348d">
</div>
