-----
### Version 1 (RFC 2965) 쿠키
-----
1. 쿠키의 확장된 버전은 RFC 2965에 정의
   - Version 1 표준은 Set-Cookie2와 Cookie2 헤더를 소개하고 있으며, Version 0 시스템과도 호환

2. RFC 2965 쿠키 표준은 원 버전인 넷스케이프 표준보다 좀 더 복잡하며, 아직 모든 브라우저나 서버가 완전히 지원하지 않음 (RFC 2965는 폐기되어 더 이상 지원되지 않음)
3. 주요 변경 사항
   - 쿠키마다 그 목적을 설명하는 설명문 존재
   - 파기 주기에 상관없이 브라우저가 닫히면 쿠키를 강제로 삭제 가능
   - 절대 날짜 값 대신에 초 단위의 상대 값으로 쿠키의 생명 주기를 결정할 수 있는 Max-Age
   - 단순히 도메인과 경로 뿐 아니라 URL 포트번호로도 쿠키 제어 가능
   - 도메인 / 포트 / 경로 필터가 있으면 Cookie 헤더가 담겨 되돌려보냄
   - 호환되는 버전 번호
   - 사용자 이름과 추가적인 키워드 구별을 위해 Cookie 헤더에 $ 접두어 존재

4. Version 1 쿠키 문법
<div align="center">
<img src="https://github.com/user-attachments/assets/61b4aaf0-26e4-448e-9799-72491cc69ead">
</div>

5. Version 1 Set-Cookie2 헤더
<div align="center">
<img src="https://github.com/user-attachments/assets/6aa0f864-7a5b-49d6-9d85-d2334dcc63ed">
</div>

6. Cookie 헤더
   - 전송하려는 각 쿠키에 추가 정보를 담는데, 추가 정보에는 해당 쿠키가 가지고 있던 필터 중 현재의 사이트에 들어맞는 필터 기술
   - 서버가 응답과 함께 전송했던 Set-Cookie2 헤더에 있는 Domain, Port, Path 같은 속성 중, 들어맞는 필터를 함께 기술하여 쿠키를 전송
   - 예를 들어, 클라이언트가 과거에 ```www.joes-hardware.com``` 웹 사이트로부터 다섯 개의 Set-Cookie2를 응답받았다고 가정
<div align="center">
<img src="https://github.com/user-attachments/assets/4efd1b1b-aab5-4297-8389-fb6b53e5ab08">
</div>

   - 그 이후 클라이언트가 /tools/cordless/specials.html 경로로 요청을 새성하면, 다음과 같은 Cookie2 헤더 전송
<div align="center">
<img src="https://github.com/user-attachments/assets/f023e755-c1eb-4512-a516-5656872de56a">
</div>

   - 해당 쿠키의 Set-Cookie2 필터 중, 현재의 웹 사이트에 들어맞는 필터 정보에 달러 문자($)를 붙여서 쿠키와 함께 전송

7. Version 1 Cookie2 헤더와 버전 협상
   - Cookie2 요청 헤더는 각기 다른 쿠키 버전을 지원하는 클라이언트와 서버 간 호환성을 협상하는 용도로 사용
   - Cookie2 헤더는 사용자 에이전트가 새로운 형식의 쿠키를 지원하며, 해당 쿠키 표준 정보 (Cookie-Version)를 서버에게 제공
```
Cookie2: $Version="1"
```

   - 만약 서버가 새로운 형식의 쿠키를 인식하면, Cookie2 헤더를 받고 나서 Set-Cookie2(Set-Cookie가 아닌) 응답 헤더를 보내야 함
   - 만약 클라이언트가 같은 쿠키를 Set-Cookie와 Set-Cookie2 헤더에 기술해서 모두 보내면, 이전 방식인 Set-Cookie 헤더 무시
   - 클라이언트가 Version 0 쿠키와 Version 1 쿠키를 모두 지원하더라도 서버로부터 Version 0의 Set-Cookie 헤더를 받으면, 클라이언트는 Version 0 Cookie 헤더를 보내야만 함
   - 그러나 클라이언트를 해당 서버에 업그레이드할 수 있다는 의미로 Cookie2: $Version-"1"을 보내야 함
