-----
### 기본 인증의 예
-----
1. 예시
<div align="center">
<img src="https://github.com/user-attachments/assets/88237394-1634-411e-91f3-0b023739e6cb">
</div>

   - 12-2a : 사용자가 자신의 가족 사진인 /family/jeff.jpg 요청
   - 12-2b : 서버가 WWW-Authenticate 헤더와 함께 개인 가족 사진에 접근하는 데 필요한 비밀번호를 요구하는 401 Authorization Required 응답 반환
   - 12-2c : 브라우저가 401 응답을 받고, Family 영역에 관한 사용자 이름과 비밀번호를 요구하는 대화 상자를 띄우며, 사용자가 사용자 이름과 비밀번호를 입력하면, 브라우저는 콜론으로 이어 붙이고, base-64 방식으로 인코딩 후, Authorization 헤더에 그 값을 담아 서버로 다시 보냄
   - 12-2d : 서버가 사용자 이름과 비밀번호를 디코딩하고, 그 값이 정확한지 검사한 후, 문제가 없으면 HTTP 200 OK 메세지와 함께 요청받았던 문서를 보냄

2. HTTP 기본 인증의 WWW-Authenticate 헤더와 Authorization 헤더
<div align="center">
<img src="https://github.com/user-attachments/assets/cde04469-529d-494c-96b9-214f497ba9bb">
</div>

  - 💡 기본 인증 프로토콜은 Authentication-Info 헤더를 사용하지 않음
