-----
### 일반 로그 포맷 (Common Log Format)
-----
1. 요즘 사용하는 가장 일반적인 포맷 중 하나
2. NCSA가 정의했고, 많은 서버가 이 로그 포맷을 기본으로 사용
   - 대부분 상용 혹은 오픈 소스 서버는 이 포맷을 사용하게 설정할 수 있으며, 일반 로그 포맷을 구문 분석하는 수 많은 상용 혹은 무료 소프트웨어 도구가 있음

3. 일반 로그 포맷 필드
<div align="center">
<img src="https://github.com/user-attachments/assets/399ac63e-3e7d-4457-83ed-b403ba301197">
</div>

4. 일반 로그 포맷 엔트리의 몇 가지 예
<div align="center">
<img src="https://github.com/user-attachments/assets/bce36b5d-9ece-43bc-8970-e7c6dcd0fc39">
</div>

   - 필드
<div align="center">
<img src="https://github.com/user-attachments/assets/0b0d1db5-1c80-4e10-af51-4535e5a92241">
</div>

   - remotehost 필드에는 ```http-guide.com``` 같은 호스트 명이나 ```209.1.32.44```같은 IP 주소가 기술
   - username과 auth-username 필드의 대시는 필드가 비어 있다는 뜻 : ident 검색이나 인증을 수행하지(세 번째 필드가 비어있음) 않았다는 뜻
