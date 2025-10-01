-----
### 요약 계산
-----
1. 다이제스트 인증의 핵심은 공개된 정보, 비밀 정보, 시한부 난스 값을 조합한 단방향 요약
2. 요약 알고리즘 입력 데이터
   - 단방향 해시 함수 H(d)와 요약 함수 KD(s, d) : 여기서 s는 비밀(Secret)을, d는 데이터(Data)를 의미
   - 비밀번호 등 보안 정보를 담고 있는 데이터 덩어리 : A1
   - 요청 메세지의 비밀이 아닌 속성을 담고 있는 데이터 덩어리 : A2
   - A1, A2 두 조각의 데이터는 요약을 생성하기 위해 H와 KD에 의해 처리

3. H(d)와 KD(s, d) 알고리즘
   - 다이제스트 인증은 여러 가지 요약 알고리즘 선택 가능
   - RFC 2617에서 제안된 두 알고리즘은 MD5, MD5-sess(session)이며, 만약 알고리즘이 정해지지 않았다면 MD5이 기본값
   - 둘 중 어느 것이 사용되더라도, H 함수는 MD5는 계산하고, KD 요약 함수는 콜론으로 연결된 비밀 데이터와 일반 데이터의 MD5 계산
<div align="center">
<img src="https://github.com/user-attachments/assets/3b4bb340-b821-4d7c-bfe7-5471de737c4a">
</div>

4. 보안 관련 데이터 (A1)
   - 사용자 이름, 비밀번호, 보호 영역, 난스와 같은 비밀 보호 정보로 이루어져 있음
   - A1은 메세지 자체가 아닌 비밀 정보와만 관련되어있고, H / KD / A2와 마찬가지로 요약을 계산하기 위해 사용
   - RFC 2617은 선택된 알고리즘에 따라 A1을 계산할 수 있는 두 가지 방법
     + MD5 : 모든 요청마다 단방향 해시 실행 (A1은 사용자 이름, 영역, 비밀번호를 콜론으로 연결)
     + MD5-sess : 사용자 이름, 영역, 비밀번호에 대한 해시 계산 결과 뒤 현재 난스와 클라이언트 난스(c난스)를 붙인 것이 A1이 됨 (CPU를 많이 사용하는 해시 게산은 처음 WWW-Authenticate 핸드쉐이크 할 때 단 한 번만 수행)
<div align="center">
<img src="https://github.com/user-attachments/assets/e96c6615-74eb-4368-b74f-dd3cd6a606cf">
</div>

5. 메세지 관련 데이터 (A2)
   - URL, 요청 메서드, 메세지 엔티티 본문과 같은 메세지 자체 정보를 나타냄
   - A2는 메서드, 리소스, 메세지 위조를 방지하기 위해 사용되며, 요약을 계산하기 위해 사용
   - RFC 2617은 선택된 보호 수준(Quality of Protection, QoP)에 따른 A2의 두 가지 사용법 정의
     + 첫 번째 방법 : HTTP 요청 메서드와 URL만을 포함하는 것 (기본값이기도 한 qop="auth"일 때 사용)
     + 두 번쨰 방법 : 메세지 무결성 검사를 제공하기 위해 메세지 엔티티 본문을 추가하는 것 (qop="auth-int"일 때 사용)
<div align="center">
<img src="https://github.com/user-attachments/assets/9f4a972d-4d61-4990-9d88-6e6b6f0f7f0e">
</div>

   - 요청 메서드는 HTTP 요청 메서드이며, uri 지시자 값은 요청줄에서 가져온 요청 URL(```*```, absoulteURL, abs_path 중 아무것이나 될 수 있지만, 반드시 요청 URL과 일치해야 하며, 특히 요청 URI가 absoluteURL이면, uri 지시자 값도 반드시 absoluteURL)
