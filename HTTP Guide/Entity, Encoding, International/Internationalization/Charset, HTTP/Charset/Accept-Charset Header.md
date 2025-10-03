-----
### Accept-Charset 헤더
-----
1. 수십 년간 개발되어 온 수천 가지 정의된 문자 인코딩과 디코딩 방법 존재
2. 대부분 클라이언트는 모든 종류의 문자 코딩과 매핑 시스템을 지원하지 않음
3. HTTP 클라이언트는 서버에게 정확히 어떤 문자 체계를 그들이 지원하는지 Accept-Charset 요청 헤더를 통해 알려줌
   - Accept-Charset 헤더의 값은 클라이언트가 지원하는 문자 인코딩 목록을 제공

4. 예) HTTP 요청 헤더는 클라이언트가 서유럽 ISO-8859-1 문자 시스템을 UTF-8 가변길이 유니코드 호환 시스템만큼 잘 받아들일 수 있음을 말해줌
   - 이 문자 인코딩 구조 중 어떤 것으로 콘텐츠를 반환할지는 서버의 자유
<div align="center">
<img src="https://github.com/user-attachments/assets/05a60355-05cf-49bc-ba4f-0966dbb00663">
</div>

   - Accept-Charset 요청 헤더에 대응하는 Content-Charset 응답 헤더는 존재하지 않음
   - 응답 문자집합은 MIME과의 호환을 위해 Content-Charset 응답 헤더의 charset 매개변수를 통해 서버로부터 돌려받음
   - 대칭적이지는 않음
