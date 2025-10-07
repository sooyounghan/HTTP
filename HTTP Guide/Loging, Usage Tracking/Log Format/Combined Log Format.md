-----
### 혼합 로그 포맷 (Combined Log Format)
-----
1. 많이 사용하는 또 다른 로그 포맷
2. 아파치 같은 서버들이 지원하며, 일반 로그 포맷과 매우 유사
   - 추가된 필드 두 개를 제외하면 동일
   - Referer 필드 : 이 URL을 요청자가 어디서 찾았는지에 관한 정보 제공
   - User-Agent 필드 : 요청을 만든 HTTP 클라이언트 애플리케이션이 무엇인지 알아볼 때 유용
<div align="center">
<img src="https://github.com/user-attachments/assets/4fbcf0ef-43e8-4f1d-8bde-5ffb9482b9a7">
</div>

3. 혼합 로그 포맷 엔트리의 예
<div align="center">
<img src="https://github.com/user-attachments/assets/109129b0-2b6a-42df-afb0-59828e38ab9f">
</div>

   - Referer와 User-Agent 필드에 값 할당 (로그 엔트리 끝에 옴)
<div align="center">
<img src="https://github.com/user-attachments/assets/d40bad0a-61ab-4f93-8c5b-594db343897d">
</div>
