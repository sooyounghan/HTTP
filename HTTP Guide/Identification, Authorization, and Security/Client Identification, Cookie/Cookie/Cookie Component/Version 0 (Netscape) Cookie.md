-----
### Version 0(넷스케이프) 쿠키
-----
1. 최초의 쿠키 명세는 넷스케이프가 정의
2. Version 0 쿠키는 Set-Cookie 응답 헤더와 Cookie 요청 헤더와 쿠키를 조작하는데 필요한 필드 정의
3. 형태
<div align="center">
<img src="https://github.com/user-attachments/assets/f0819592-a157-4748-8cc2-4e654a847f7d">
</div>

4. Set-Cookie 헤더 : 쿠키의 이름과 값을 가져야 하며, 쿠키 옵션 속성들에 세미콜론으로 이어 기술
<div align="center">
<img src="https://github.com/user-attachments/assets/64834521-59ef-4820-ad4d-7799548b2d61">
</div>

5. Cookie 헤더 : 클라이언트가 서버에 요청을 보낼 때는 Domain / Path / Secure 필터들이 현재 요청하려고 하는 사이트에 들어맞으면서 아직 파기되지 않은 쿠키들을 함꼐 보내며, 모든 쿠키는 Cookie 헤더에 이어 붙여 보냄
<div align="center">
<img src="https://github.com/user-attachments/assets/8aaf163b-c7d6-40d9-a2c3-d6ccdbd9fd3b">
</div>
