-----
### 다이제스트 인증 헤더
-----
1. 기본, 다이제스트 인증 프로토콜 양쪽 모두 WWW-Authenticate 헤더에 담겨 전달되는 인증 요구와, Authorization 헤더에 담겨 전달되는 인가 응답을 포함
2. 다이제스트 인증은 여기에 선택적인 Authenticate-Info 헤더를 추가 : 이 헤더는 3단계 핸드쉐이크를 완성하고, 다음번 사용할 난스를 전달하기 위해 인증 성공 후 전송
3. 기본 및 다이제스트 인증에서 사용되는 헤더들
<div align="center">
<img src="https://github.com/user-attachments/assets/b2ece9f0-3189-4a3a-a480-1c8707dc200a">
</div>
