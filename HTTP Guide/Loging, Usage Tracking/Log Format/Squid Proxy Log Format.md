-----
### 스퀴드(Squid) 프록시 로그 포맷
-----
1. 스퀴드 프록시 캐시(```http://www.squid-cache.org```)는 웹 분야에서 권위 있는 프로젝트
   - 기원 : 초기 웹 프록시 캐시 프록젝트 중 하나로 올라감
   - 스퀴드는 수년간 오픈 소스 커뮤니티를 통해 확장 및 개선되어 온 프로젝트
   - 스퀴드 애플리케이션을 관리하는데 도움(처리 / 추적 / 로그 분석)이 되는 수 많은 도구들이 개발되었음
   - 많은 차세대 프록시 캐시들이 이러한 도구를 활용하려고 자체 로그 포맷으로 스퀴드 포맷 적용

2. 스퀴드 로그 엔트리 포맷 필드
<div align="center">
<img src="https://github.com/user-attachments/assets/a66f9c19-eccc-4037-8c5d-847ad8f727ca">
</div>

3. 스퀴드 로그 포맷 엔트리 예
<div align="center">
<img src="https://github.com/user-attachments/assets/ab9a9b35-2f6b-47c7-9c65-1b54630c5179">
</div>

   - 각 필드에 기술된 값
<div align="center">
<img src="https://github.com/user-attachments/assets/74773d0f-7bf6-4aa9-b943-575d4ac5e3e1">
</div>

4. 스퀴드 결과 코드 (스퀴드 프록시 캐시 내부 동작과 관련한 것들이 많아서, 스퀴드 로그 포맷을 지원하는 프록시라 하더라도 이 모든 코드를 지원하지 않음)
<div align="center">
<img src="https://github.com/user-attachments/assets/fa984648-5c5d-4942-988e-7c08c761fd0c">
</div>

