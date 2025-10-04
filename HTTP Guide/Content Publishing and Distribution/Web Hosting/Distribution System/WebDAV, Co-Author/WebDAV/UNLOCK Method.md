-----
### UNLCOK 메서드
-----
1. 리소스에 있는 잠금 제거
<div align="center">
<img src="https://github.com/user-attachments/assets/68e2e611-0372-45ca-b72d-a7ab1838e263">
</div>

2. 대부분 리소스 관리 요청에서, WebDAV에서 UNLCOK이 성공하기 위한 두 가지 조건
   - 다이제스트 인증을 성공적으로 완료하는 것
   - Lock-Token 헤더에 보내는 잠금 토큰이 맞는지 검사하는 것

3. 만약 잠금 해제에 성공한다면, 204 No Content 상태 코드를 클라이언트에게 반환
4. LOCK과 UNLOCK 메서드와 함께 사용할 수 있는 상태 코드
<div align="center">
<img src="https://github.com/user-attachments/assets/83f753db-3d01-4a6b-b759-a2bc098f9b5f">
</div>
