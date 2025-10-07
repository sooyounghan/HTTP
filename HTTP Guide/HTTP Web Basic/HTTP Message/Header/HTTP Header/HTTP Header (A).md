-----
### Accept
-----
1. 서버에게 자신이 받을 수 있는 미디어 타입이 무엇인지 알려주기 위해 클라이언트가 사용
2. Accept 헤더의 필드 값은 클라이언트가 사용할 수 있는 미디어 타입 목록
   - 예) 웹 브라우저는 웹의 멀티미디어 객체의 모든 유형을 보여줄 수 없으므로, 요청에 Aceept 헤더를 포함시킴으로써, 브라우저는 사용할 수 없는 유형의 비디오나 객체를 다운로드 받는 상황 피할 수 있음
3. 서버가 미디어 타입의 여러 버전을 갖고 있는 경우를 위해, Accept 헤더 필드는 또한 서버에게 어떤 미디어 타입을 선호하는지 말해주는 품질 값(q 값) 목록을 포함할 수 있음
<div align="center">
<img src="https://github.com/user-attachments/assets/8cf7ac1e-e7c1-49d4-82a5-55a51d0240e1">
</div>

-----
### Accept-Charset
-----
1. 클라이언트가 서버에게 어떤 문자 집합을 받아들일 수 있는지 선호하는지 말해주기 위해 사용
2. 이 요청 헤더 값에는 문자 집합들과, 선택적으로 각 문자 집합에 대한 품질 값들도 올 수 있음
3. 서버가 각기 다른 문자 집합(물론, 모두가 클라이언트가 받아들일 수 있는 문자 집합이어야 함)으로 된 여러 문서를 갖고 있는 경우를 위해, 품질값들은 서버에게 어떤 문자 집합이 가장 선호되는지 말해줌
<div align="center">
<img src="https://github.com/user-attachments/assets/322e3d3c-1429-43bf-a2a9-70bfd0716c97">
</div>

-----
### Accept-Encoding
-----
1. 서버에게 어떤 인코딩을 받아들일 수 있는지 말해주기 위해 클라이언트가 사용
2. 만약, 서버가 갖고 있는 콘텐츠가 인코딩되어 있다면(아마 압축되어있을 것), 이 요청 헤더는 서버에게 클라이언트가 그것을 받아들일 것인지 여부를 알 수 있게 해줌
<div align="center">
<img src="https://github.com/user-attachments/assets/edf1725c-56d8-44bb-beda-945e7bfab562">
</div>

-----
### Accept-Language
-----
: 다른 Accept 헤더처럼 기능하여, 클라이언트가 서버에게 어떤 언어(예) 콘텐츠에 대한 자연어)가 받아들여질 수 있고 선호되는지 알려줄 수 있게 함
<div align="center">
<img src="https://github.com/user-attachments/assets/ce85b7ec-1e4c-4e2a-a7fa-d65dacbd188a">
</div>

-----
### Accept-Ranges
----
1. 💡 다른 Accpet와 다르게, 서버가 리소스의 특정 범위에 대한 요청을 받아들일 수 있음을 클라이언트에게 말해주기 위해 사용하는 응답 헤더
2. 주어진 리소스에 대해 서버가 받아들일 수 있는 범위의 유형
3. 클라이언트는 이 헤더를 받지 않은 리소스에 대해 범위 요청을 시도할 수 있음
   - 만약, 서버가 그 리소스에 대해 범위 요청을 지원하지 않으면, 서버는 Accept-Ranges에 none이란 값을 담아서 적절한 상태 코드로 응답할 수 있음
   - 서버는 클라이언트가 나중에라도 범위 요청을 하는 것을 단념시키기 위해 보통 요청에도 none 값을 보낼 수 있음
<div align="center">
<img src="https://github.com/user-attachments/assets/181e48db-92b0-4f89-bc33-c187b04fb532">
</div>

-----
### Age
-----
1. 수신자에게 응답이 얼마나 오래되었는지 말해줌
2. 그 응답이 얼마나 오래전에 만들어졌는지 혹은 원 서버에 의해 재검사되었는지에 대해 발송자가 추정한 것
3. 헤더의 값은 초 단위의 변화량
<div align="center">
<img src="https://github.com/user-attachments/assets/43862e42-59b2-4516-93ac-3366bdf0b320">
</div>

-----
### Authorization
-----
1. 클라이언트는 자신을 인증하기 위해 서버에게 인가(Authorization) 헤더를 보냄
2. 클라이언트는 서버로부터 401 Unauthorized Required 응답을 받은 뒤 이 헤더를 요청에 포함시킬 것
3. 이 헤더의 값은 사용되는 인증 스킴에 달려 있음
<div align="center">
<img src="https://github.com/user-attachments/assets/7ac02f09-e769-4bb9-90de-a98a78097e5a">
</div>
