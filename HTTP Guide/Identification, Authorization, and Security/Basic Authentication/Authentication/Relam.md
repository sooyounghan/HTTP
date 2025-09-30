-----
### 보안 영역
-----
1. 웹 서버는 기밀 문서를 보안 영역(Relam) 그룹으로 나누며, 보안 영역은 저마다 다른 사용자 권한을 요구
2. 예) 웹 서버가 보안 영역을 두 개 가진다고 가정
   - 한 개의 회사의 재정 정보, 다른 하나는 개인의 가족 문서
   - 각 사용자는 서로 다른 영역으로 접근
<div align="center">
<img src="https://github.com/user-attachments/assets/e5e00cfc-0e3f-4310-9ee3-0a80ebea6dea">
</div>

3. realm 파라미터가 함께 기술된 기본 인증의 예
<div align="center">
<img src="https://github.com/user-attachments/assets/4ec0ac24-0a4e-4ea8-a86d-2f36f0fd6bf5">
</div>

   - relam은 ""Corporate Financials(회사 재무)" 같이 해설 형식으로 되어 있어서, 사용자 이름과 비밀번호를 가지고 있는 사용자가 권한의 범위를 이해하는 데 도움이 되어야 함
   - realm에 ```"executive-committee@bigcompany.com"```와 같은 서버의 호스트 명을 넣는 것도 유용할 수 있음
