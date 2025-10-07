-----
### 넷스케이프 확장 로그 포맷
-----
1. 넷스케이프가 상용 HTTP 애플리케이션이 되면서, 다른 HTTP 애플리케이션 개발자들이 사용하는 서버의 여러 로그 포맷 도입
2. 넷스케이프의 포맷은 NCSA 일반 로그 포맷에서 시작했지만, 프록시나 웹 캐시 같은 HTTP 애플리케이션과 연관이 있는 여러 환경을 지원하려고 포맷 확장
3. 첫 필드 일곱개는 일반 로그 포맷과 같으며, 추가된 확장 로그 포맷 필드는 다음과 같음
<div align="center">
<img src="https://github.com/user-attachments/assets/c27a400d-9502-4b95-9f8c-7550179f18f3">
</div>

4. 넷스케이프 확장 로그 포맷 엔트리의 예
<div align="center">
<img src="https://github.com/user-attachments/assets/b81f2cec-0643-4f89-a79b-423e1dfca040">
</div>

   - 확장 포맷에 저장된 값
<div align="center">
<img src="https://github.com/user-attachments/assets/5fdadc9b-5fc1-469d-bdb4-26e2551ab8b0">
</div>

-----
### 넷스케이프 확장 2 로그 포맷
-----
1. 또 다른 넷스케이프 로그 포맷은 확장 로그 포맷(Extended Log Format)에서 HTTP 프록시와 웹 캐시 애플리케이션과 관련한 더 많은 정보 포함
2. 이렇게 추가된 필드들은 HTTP 클라이언트와 HTTP 프록시 애플리케이션 간 통신 설계에 도움이 됨
3. 넷스케이프 확장 로그 포맷에서 파생되어서, 앞부분 필드들은 넷스케이프 확장 로그 포맷에 나열된 것과 같음
4. 넷스케이프 확장 2 로그 포맷에서 추가된 필드
<div align="center">
<img src="https://github.com/user-attachments/assets/9758c40d-13c5-4306-bdd8-75d7c42e1fe2">
</div>

5. 넷스케이프 확장 2 로그 포맷 엔트리
<div align="center">
<img src="https://github.com/user-attachments/assets/df581943-88d3-42c2-b5bf-604916ef39e1">
</div>

   - 확장 필드들에 저장된 값
<div align="center">
<img src="https://github.com/user-attachments/assets/379cfb9d-fec3-4104-8e67-cb3787b5601d">
</div>

6. 넷스케이프 종료 코드
<div align="center">
<img src="https://github.com/user-attachments/assets/1e797a48-ef93-432b-b2af-9adfafd758ea">
</div>

7. 넷스케이프 캐시 코드
<div align="center">
<img src="https://github.com/user-attachments/assets/63987eeb-5239-4256-848d-7e07bf75c469">
</div>

8. 넷스케이프 애플리케이션은 다른 많은 HTTP 애플리케이션과 마찬가지로 출력될 로그의 포맷을, 관리자가 수정할 수 있는 유연한 로그 포맷(Flexible Log Format)을 포함한 다양한 로그 포맷을 가지고 있음
   - 관리자는 추가적인 설정을 해서 로그에 기록할 HTTP 트랜잭션 (헤더, 상태, 크기 등) 특정 부분을 선택해 로그 최적화 가능

9. 관리자가 포맷을 기호에 맞게 수정할 수 있도록 하는 기능이 추가된 것은 로그에서 얻을 수 있는 정보 중 어떤 것을 필요로 하는지 예측하기 어렵기 때문임
10. 다른 많은 프록시와 서버 역시 로그에서 특정 정보만 추출하는 기능 제공
