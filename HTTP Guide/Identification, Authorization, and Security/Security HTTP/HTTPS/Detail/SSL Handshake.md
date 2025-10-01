-----
### SSL 핸드쉐이크
-----
1. 암호화된 HTTP 메세지를 보내기 전, 클라이언트와 서버는 SSL 핸드쉐이크 필요
   - 프로토콜 버전 번호 교환
   - 양쪽이 알고 있는 암호 선택
   - 양쪽 신원 인증
   - 채널을 암호화하기 위한 임시 세션 키 생성

2. 암호화된 HTTP 데이터가 네트워크를 오가기도 전에, SSL은 통신을 시작하기 위해 상당한 양의 핸드쉐이크 데이터를 주고 받음
3. SSL 핸드쉐이크 핵심
<div align="center">
<img src="https://github.com/user-attachments/assets/d56bc64e-99f3-4888-9232-d55f6fed7c45">
</div>
