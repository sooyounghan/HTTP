-----
### 로봇 차단 펄 코드
-----
1. robots.txt 파일과 상호 작용하는 공개된 펄(Perl) 라이브러리가 몇 개 존재
2. 한 예) CPAN 공개 펄 아카이브의 ```WWW::RobustRules``` 모듈
   - 파싱된 robots.txt 파일이 담겨 있는 ```WWW::RobotsRules``` 객체는 주어진 URL에 대한 접근이 금지되어 있는지 확인할 수 있는 메서드 제공
   - ```WWW::RobotsRules``` 객체로 여러 robots.txt 파일 파싱 가능

3. ```WWW::RobotsRules``` API 주요 메서드
<div align="center">
<img src="https://github.com/user-attachments/assets/609708ef-7562-41c9-acec-9d91554f8586">
</div>

4. ```WWW::RobotsRules``` 사용 예시
<div align="center">
<img src="https://github.com/user-attachments/assets/23944a2a-73c5-4f34-a5cd-ae56ccca6947">
</div>

5. ```www.marys-antique.com```을 위한 가상의 robots.txt 파일
<div align="center">
<img src="https://github.com/user-attachments/assets/d5fe5386-3c52-4066-bf68-d218fa91cb7e">
</div>

   - 이 robots.txt 파일은 SuzySpider에 대한 레코드, FurnitureFinder에 대한 레코드, 그리고 그 외 다른 로봇들에 대한 기본 레코드를 갖고 있음
   - 각 레코드는 각각 다른 로봇에 대한 각각 다른 접근 정책 집합 허용
     + SuzySpider에 대한 차단 레코드는 그 로봇이 URL이 /dynamic으로 시작하는 가게의 재고 게이트웨이를 크롤링 할 수 없게 하고, 수지를 위해 예약된 영역을 제외한 다른 사적인 사용자 데이터에 접근할 수 없게 함
     + FurnitureFinder 로봇에 대한 레코드는 그 로봇이 가구 재고 게이트웨이 URL를 크롤링할 수 있도록 허락 : 메리의 게이트웨이 포맷과 규칙을 이해하고 있을 것
     + 그 외 다른 모든 로봇들은 동적이거나 사적 웹페이지에 접근할 수 없게 하며, 그 외 URL은 크롤링 가능

   - 로봇별로 접근이 허락되거나 그렇지 않은 URL의 예
<div align="center">
<img src="https://github.com/user-attachments/assets/d68c26f7-bcd6-4788-8bfe-f44dd98fa3ca">
</div>
