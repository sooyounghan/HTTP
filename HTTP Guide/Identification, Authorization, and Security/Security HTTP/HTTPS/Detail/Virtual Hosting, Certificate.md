-----
### 가상 호스팅과 인증서
-----
1. 가상 호스트(하나의 서버에 여러 호스트 명)로 운영되는 사이트의 보안 트래픽을 다루는 것은 까다로운 경우가 많음
2. 몇몇 인기 있는 웹 서버 프로그램은 오직 하나의 인증서만을 지원하므로, 사용자가 인증서의 이름과 정확히 맞지 않지 않는 가상 호스트 명에 도착했다면 경고 상자가 나타날 것
3. 예) ```Cajun-shop.com```의 사이트가 있다고 가정
   - 이 사이트의 호스팅 제공자는 공식 이름 ```cajun-shop.securesites.com```을 제공
   - 사용자가 ```https://www.cajun-shop.com```으로 접속했을 때, 서버 인증서에 나열된 공식 호스트 명(```*.securesites.clom```)은 사용자가 브라우징했던 가상 호스트 명(```www.cajun-shop.com```)과 맞지 않으므로 경고 발생
<div align="center">
<img src="https://github.com/user-attachments/assets/ff998d6a-6c01-411b-914f-131b63bd03ae">
</div>

  - 이러한 문제를 피하기 위해, 이 소유자는 보안 트랙잭션을 시작하는 모든 사용자를 ```cajun-shop.securesites.com```으로 리다이렉트
