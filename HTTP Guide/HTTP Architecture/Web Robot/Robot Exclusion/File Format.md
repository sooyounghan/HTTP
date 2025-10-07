-----
### robots.txt 파일 포맷
-----
1. robots.txt 파일은 매우 단순한 줄 기반 문법을 가짐
2. robots.txt 파일의 각 줄은 빈 줄, 주석줄, 규칙 줄 세 가지 종류가 존재
3. 규칙 줄은 HTTP 헤더처럼 생겼으며(```<필드>:<값>```) 패턴 매칭을 위해 사용
   - 예시
<div align="center">
<img src="https://github.com/user-attachments/assets/e0e9aba4-7fea-4902-b31f-b5d572f953f4">
</div>

4. robots.txt의 이 줄들은 레코드로 구분
   - 각 레코드는 특정 로봇들의 집합에 대한 차단 규칙의 집합을 기술하며, 이 방법을 통해 로봇별로 각각 다른 차단 규칙 적용 가능
   - 각 레코드는 규칙 줄들의 집합으로 되어있으며, 빈줄이나 파일의 끝(End-of-File) 문자로 끝남
   - 레코드는 어떤 로봇이 이 레코드에 영향을 받는지 지정하는 User-Agent 줄로 시작하며, 뒤이어 이 로봇들이 접근할 수 있는 URL들을 말해주는 Allow 줄과, Disallow 줄이 옴 (현실적 이유로, 로봇 소프트웨어는 줄바꿈 문자를 유연하게 받아들일 수 있어야하므로, CR, LF, CRLF 모두 지원해야 함)
   - 위 예는 robots.txt 파일이 Slurp과 Webcrawler 로봇들이 사적인 하위 디렉토리 안에 있는 것을 제외하면 어떤 파일이든 접근할 수 있도록 허용하는 것을 보여줌
   - 이 파일은 다른 로봇들이 이 사이트의 그 무엇에도 접근할 수 없도록 막음

4. User-Agent 줄 : 각 로봇의 레코드는 하나 이상의 User-Agent 줄로 시작하며 형식은 당므과 같음
```
User-Agent: <robot-name>
```
  - 혹은 다음과 같을 수 있음
```
User-Agent: *
```
  - 로봇의 이름(로봇 구현자에 의해 정해진)은 로봇의 HTTP GET 요청 안의 User-Agent 헤더를 통해 보내짐
  - robots.txt 파일을 처리한 로봇은 다음 레코드에 반드시 복종해야함
    + 로봇 이름이 자신 이름의 부분 문자열이 될 수 있는 레코들 중 첫 번쨰 것
    + 로봇 이름이 ```*```인 레코드들 중 첫 번째 것

  - 만약, 로봇이 자신의 이름에 대응하는 User-Agent 줄을 찾지 못하였고, 와일드카드를 사용한 User-Agent: ```*``` 줄도 찾지 못했다면, 대응하는 레코드가 없는 것이므로 접근에는 어떤 제한도 없음
  - 로봇 이름을 대소문자를 구분하지 않는 부분과 맞춰보도록, 의도치 않게 맞는 경우 경우도 주의 (예) User-Agent: bot은 Robot, Bottm-Feeder, Spambot, Dont-Bother-Me에 매치)

5. Allow와 Disallow 줄들
   - Disallow와 Allow 줄은 로봇 차단 레코드의 User-Agent 줄들 바로 다음에 옴
   - 이 줄들은 특정 로봇에 대해 어떤 URL 경로가 명시적으로 금지되거나 허용되는지 기술
   - 로봇은 반드시 요청하려고 하는 URL을 차단 레코드의 모든 Disallow와 Allow 규칙에 순서대로 맞춰보아야 함
   - 첫 번째 맞은 것이 사용되며, 만약 어떤 것도 맞지 앟으면 그 URL은 허용
   - URL과 맞는 하나의 Allow/Disallow 줄에 대해, 규칙 경로는 반드시 맞춰보고자 하는 경로의 대소문자를 구분하는 접두어야 함
   - 예) Disallow: /tmp는 다음 모든 URL 허용
<div align="center">
<img src="https://github.com/user-attachments/assets/59e01fb7-39eb-4cad-9caa-8e116cd0f22b">
</div>

6. Disallow/Allow 접두 매칭(Prefix Matching)
   - Disallow나 Allow 규칙이 어떤 경로에 적용되려면, 그 경로의 시작부터 규칙 경로의 길이만큼 문자열 규칙 경로와 같아야 함 (대소문자의 차이도 없어야 함)
     + User-Agent 줄과 달리 별표(*)는 특별한 의미를 갖지 않지만, 대신 빈 문자열을 이용해 모든 문자열에 매치되도록 할 수 있음
   - 규칙 경로나 URL 경로의 임의의 이스케이핑된 문자들(%XX)은 비교 전에 원래대로 복원됨(빗금(/)을 의미한느 %2F는 예외로, 반드시 그대로 매치되어야 함)
   - 만약 어떤 규칙 경로가 빈 문자열이면, 그 규칙은 모든 URL 경로와 매치
   - 규칙 경로와 URL 경로를 맞춰보는 예
<div align="center">
<img src="https://github.com/user-attachments/assets/e7a3e7d5-3efc-4c97-888c-5e79cd2d123a">
</div>

   - 접두 매칭은 꽤 잘 동작하지만, 그것만으로는 표현력이 충분하지 못한 경우가 몇 가지 존재
   - 어떤 경로 밑에 있느냐와 상관없이 특정 이름 디렉토리에 대해서는 크롤링을 못하고 싶은 경우가 존재할 수 있는데, robots.txt는 이를 표현할 수단을 제공해주지 않음
   - 예) RCS 버전 컨트롤 하위 디렉토리에 대해서는 크롤링을 못하게 하고 싶을 수 있지만, robots.txt 버전 1.0 스킴은 모든 경로 RCS 하위 디렉토리를 일일히 지정 외에는 지원할 방법을 제공하지 않음

