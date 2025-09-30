-----
### 인증 프로토콜과 헤더
-----
1. HTTP는 필요에 따라 고쳐 쓸 수 있는 제어 헤더를 통해, 다른 인증 프로토콜에 맞추어 확장할 수 있는 프레임워크 제공
2. 네 가지 인증 단계
   - 헤더 형식과 내용은 인증 프로토콜에 따라 달라지며, 인증 프로토콜은 HTTP 인증 헤더에 기술
<div align="center">
<img src="https://github.com/user-attachments/assets/4951f190-e7e0-40ed-bfd7-81e8b3d65a44">
</div>

3. HTTP에는 기본 인증과 다이제스트 인증이라는 두 가지 공식 인증 프로토콜 제공
   - 현대의 HTTP 인증 요구 / 응답 프로토콜을 사용하는 인증 프로토콜로는 OAuth가 존재 : 모바일 기기 같은 다양한 애플리케이션에서 API 인증을 위해 사용하는 최신 인증 프로토콜

4. 기본 인증의 예
<div align="center">
<img src="https://github.com/user-attachments/assets/60e4ca76-515b-46ed-a066-23eb0c6e658b">
</div>

   - 서버가 사용자에게 인증 요구를 보낼 때, 서버는 401 Unauthorized 응답과 함꼐 WWW-Authenticate 헤더를 기술해 어디서 어떻게 인증할지 설명
   - 다음으로 클라이언트가 서버로 인증하려면, 인코딩된 비밀번호와 그 외 인증 파라미터들을 Authorization 헤더에 담아 요청을 다시 보냄
   - 인증 요청이 성공적으로 완료되면, 서버는 정상적인 상태 코드(예) 200 OK)를 반환
   - 추가적인 인증 알고리즘에 대한 정보를 Authentication-Info 헤더에 기술 가능
