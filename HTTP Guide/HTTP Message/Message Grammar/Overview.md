-----
### 메세지 문법
-----
1. 모든 HTTP 메세지는 요청 메세지나 응답 메세지로 분류
   - 요청 메세지는 웹 서버에 비해 어떤 동작을 요구
   - 응답 메세지는 요청의 결과를 클라이언트에게 돌려줌
   - 요청과 응답 모두 기본적으로 구조가 같음

2. 예) GIF 이미지를 가져오기 위한 요청과 응답 메세지
<div align="center">
<img src="https://github.com/user-attachments/assets/4059a4cc-d549-4b7a-9d3f-8bfd2f3b2f18">
</div>

3. 요청 메세지의 형식
<div align="center">
<img src="https://github.com/user-attachments/assets/c416a087-4181-4bde-816c-6ea35cdc1e4c">
</div>

4. 응답 메세지의 형식 (시작줄에서만 요청 메세지와 문법이 다름)
<div align="center">
<img src="https://github.com/user-attachments/assets/eb465b4d-cd2e-4c68-b6b2-436f0ca125b9">
</div>

5. 각 부분에 대한 설명
   - 메서드 : 클라이언트 측에서 서버가 리소스에 대해 수행해주길 바라는 동작 (GET, HEAD, POST와 같이 한 단어로 구성)
   - 요청 URL : 요청 대상이 되는 리소스를 지정하는 완전한 URL 혹은 URL의 경로 구성 요소
     + 완전한 URL이 아닌 URL의 경로 구성요소라고 해도, 클라이언트가 서버와 직접 대화하고 있고, 경로 구성 요소가 리소스를 가리키는 절대 경로이기만 하면, 대체로 문제 없음
     + 서버는 URL에서 생략된 호스트/포트가 자신을 가리키는 것으로 간주

   - 버전 : 이 메세지에서 사용 중인 HTTP 버전 (메이저와 마이너는 모두 정수)
<div align="center">
<img src="https://github.com/user-attachments/assets/89d371ff-f70d-41ad-9775-4e72250a8870">
</div>

   - 상태 코드 : 요청 중에 무엇이 일어났는지 설명하는 세 자리 숫자
     + 각 코드의 첫 번째 자릿수는 상태의 일반적 분류(성공, 에러 등)를 나타냄

   - 사유 구절(Reason-Phrase)
     + 숫자로 된 상태 코드의 의미를 사람이 이해할 수 있게 설명해주는 짧은 문구
     + 상태 코드 이후부터 줄바꿈 문자열까지가 사유 구절
     + 사유 구절은 오로지 사람에게 읽히기 위한 목적으로 존재
     + 예) HTTP/1.0 200 NOT OK와 HTTP/1.0 200 OK는 사유 구절이 전혀 달라보임에도 불구하고, 동등하게 성공을 의미하는 것으로 처리되어야 함

   - 헤더들 : 이름, 콜론(:), 선택적 공백, 값, CRLF가 순서대로 나타나는 0개 이상 헤더들, 이 헤더들의 목록은 빈 줄(CRLF)로 끝나 헤더 목록의 끝과 엔티티 본문의 시작을 표시
     + HTTP/1.1과 같은 일부 버전 HTTP는 요청이나 응답에 어떤 특정 헤더가 포함되어야만 유효한 것으로 간주

   - 엔티티 본문 : 임의의 데이터 블록을 포함
     + 모든 메세지가 엔티티 본문을 갖는 것은 아니므로, 떄떄로 CRLF로 그냥 끝나게 될 수 있음
     + 가상의 요청과 응답 메세지의 예
<div align="center">
<img src="https://github.com/user-attachments/assets/1f16402d-11b6-47b8-bff3-62ed3ab778cc">
</div>

   - 💡 헤더나 엔티티 본문 없이도 HTTP 헤더 집합은 항상 빈 줄(그냥 CRLF)로 끝나야 함
