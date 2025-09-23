-----
### 신뢰할 수 있는 데이터 전송 통로인 TCP
-----
1. HTTP 커넥션은 몇몇 사용 규칙을 제외하고 TCP 커넥션에 불과 : TCP 커넥션은 인터넷을 안정적으로 연결
2. TCP는 HTTP에게 신뢰할 만한 통신 방식을 제공하며, TCP 커넥ㄴ션의 한쪽에 있는 바이트들은 반대쪽으로 순서에 맞게 정확히 전달
<div align="center">
<img src="https://github.com/user-attachments/assets/5c48d2d2-3cb6-4301-ad16-086890a8be47">
</div>

-----
### TCP 스트림은 세그먼트로 나뉘어 IP 패킷을 통해 전송
-----
1. TCP는 IP 패킷(혹은 IP 데이터그램)이라 불리는 작은 조각을 통해 데이터를 전송
<div align="center">
<img src="https://github.com/user-attachments/assets/d65c72b5-c4b0-4dd0-9cfa-b41060426129">
</div>

2. HTTP는 위 4-3a과 같이 IP, TCP, HTTP로 구성된 프로토콜 스택에서 최상위 계층
3. HTTP에 보안 기능을 더한 HTTPS는 TLS 혹은 SSL이라 불리기도 하며, HTTP와 TCP 사이에 있는 암호화(Cryptographic Encryption) 계층 (4-3b)
4. HTTP가 메세지를 전송하고자 할 경우, 현재 연결되어 있는 TCP 커넥션을 통해 메세지 데이터 내용을 순서대로 보내고자 함
   - TCP는 세그먼트라는 단위로 데이터 스트림을 잘게 나누고, 세그먼트를 IP 패킷이라 불리는 봉투에 담아 인터넷을 통해 전달
<div align="center">
<img src="https://github.com/user-attachments/assets/a1aa1054-ece5-4b99-b509-e0a09c8fb6a6">
</div>

   - 모든 것은 TCP/IP 소프트웨어에 의해 처리되며, 그 과정은 HTTP 프로그래머에게 보이지 않음
   - 각 TCP 세그먼트는 하나의 IP 주소에서 다른 IP 주소로 IP 패킷에 담겨 전달
   - IP 패킷은 다음을 포함
     + IP 패킷 헤더 (보통 20바이트)
     + TCP 세그먼트 헤더 (보통 20바이트)
     + TCP 데이터 조각(0 혹은 그 이상 바이트)

5. IP 헤더는 발신자와 목적지 IP 주소, 크기, 기타 플래그를 가짐
6. TCP 세그먼트 헤더는 TCP 포트 번호, TCP 제어 플래그, 그리고 데이터 순서와 무결성 검사를 위해 사용하는 숫자 값 포함
