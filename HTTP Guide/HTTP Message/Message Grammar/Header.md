-----
### 헤더
-----
1. 시작줄 다음에는 0개, 1개 혹은 여러 개의 HTTP 헤더가 옴
2. HTTP 헤더 필드는 요청과 응답 메세지에 추가 정보를 더함
3. 기본적으로 이름/값 쌍의 목록
4. 예시) 다음 헤더줄은 Content-Length 헤더 필드에 19라는 값 할당
<div align="center">
<img src="https://github.com/user-attachments/assets/96d5a455-66cb-432f-93eb-2be316ebea5c">
</div>

5. 헤더 분류 : HTTP 헤더 명세는 여러 헤더 필드로 정의되며, 애플리케이션은 또한 자유롭게 자신만의 헤더를 만들어낼 수 있음
   - 일반 헤더 : 요청과 응답 양쪽에 모두 나타날 수 있음
   - 요청 헤더 : 요청에 대한 부가 정보 제공
   - 응답 헤더 : 응답에 대한 부가 정보 제공
   - Entity 헤더 : 본문 크기와 콘텐츠, 혹은 리소스 그 자체 서술
   - 확장 헤더 : 명세에 정의되지 않은 새로운 헤더

6. 각 HTTP 헤더는 간단한 문법을 가짐
   - 이름, 쉼표, 공백(없어도 됨), 필드 값, CRLF가 순서대로 옴
   - 흔히 쓰이는 헤더의 예
<div align="center">
<img src="https://github.com/user-attachments/assets/20bf0998-4fb5-49f8-9fe4-c16ba8c25c54">
</div>

7. 헤더를 여러 줄로 나누기
   - 긴 헤더 줄은 그들을 여러 줄로 쪼개서 더 읽기 좋게 만들 수 있는데, 추가 줄 앞에는 최소 하나의 스페이스 혹은 탭 문자가 와야 함
<div align="center">
<img src="https://github.com/user-attachments/assets/d12170b9-a217-42e5-a224-e5c9968dbafd">
</div>

   - 이 예에서 응답 메세지는 여러 줄로 값이 쪼개진 Server 헤더를 포함하고 있음
   - 그 헤더의 완전한 값은 Test Server Version 1.0
     
