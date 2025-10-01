-----
### 요약 알고리즘 전반
-----
1. RFC 2617은 주어진 H, KD, A1, A2로 요약을 계산하는 두 가지 방법 정의
   - 첫 번째 방법 : 예전 명세인 RFC 2069와 호환을 염두에 둔 것으로, qop 옵션이 빠졌을 때 사용 - 비밀 정보와 난스가 붙은 메세지 데이터의 해시를 이용해 요약 계산
   - 두 번째 방법 : 현대적이면서 보다 선호되는 접근법으로, 난스 횟수 집계 및 대칭 인증 지원 포함 - 이 접근법은 qop가 auth일 때와 auth-int일 때 모두 사용되며, 난스 횟수, qop, c난스 데이터를 요약에 추가

2. 다이제스트 함수에 대한 정의
<div align="center">
<img src="https://github.com/user-attachments/assets/ebbbfaa8-5d23-419c-852d-9fcbd916eb0e">
</div>

<div align="center">
<img src="https://github.com/user-attachments/assets/408282ec-fdd7-4395-a044-ce40a0fd1cf3">
</div>

