-----
### 문자집합과 HTTP
-----
1. HTTP Charset 값은, 어떻게 엔티티 콘텐츠 비트들을 특정 문자 체계의 글자들로 바꾸는지 말해줌
   - 각 Charset 태그는 비트들을 글자들로 변환하거나 혹은 그 반대의 일을 해주는 알고리즘을 명명
   - Charset 태그는 등록된 MIME 문자집합에 표준화되어있고, IANA가 관리 (```http://www.iana.org/assignments/character-sets```)

2. 예시) Content-Type 헤더는 수신자에게 콘텐츠가 HTML 파일임을 말해주고, charset 매개변수는 수신자에게 콘텐츠 비트들을 글자들로 디코딩하기 위해 ISO-8859-6 아랍 문자집합 디코딩 기법을 사용하라고 말해줌
<div align="center">
<img src="https://github.com/user-attachments/assets/3fab411a-a949-4639-8174-d0368bfaa97c">
</div>

   - ISO-8859-6 인코딩 구조는 8비트 값을 숫자와 구두점 그리고 다른 기호들을 포함한 라틴 문자와 아랍 문자로 매핑 (중국어, 일본어와 달리 아랍어는 28개 문자를 가지며, 8비트는 256개의 유일한 값을 제공하므로 라틴어, 아랍어, 그 밖의 유용한 기호들을 위한 충분한 공간 제공)

3. 예시) 강조된 비트 패턴은 코드 값 225를 갖고, 아랍 문저 FEH에 대응
<div align="center">
<img src="https://github.com/user-attachments/assets/e40f73e4-36ac-4a0c-a30f-d22873cb6171">
</div>

4. 몇몇 문자 인코딩(예) UTF-8와 ISO-2022-JP)은 글자 당 비트 수가 일정하지 않아 더 복잡한 가변길이 코드
   - 이러한 종류의 코딩은 중국어나 일본어와 같이 많은 글자로 이루어진 문자체계를 지원하기 위해 추가적인 비트를 사용할 수 있게 해줌
