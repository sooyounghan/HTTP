-----
### FrontPage RPC 프로토콜
-----
1. FrontPage 클라이언트와 FPSE는 자체 RPC 프로토콜을 사용해 통신
   - 이 프로토콜은 RPC 메서드와 그와 관련한 변수를 POST 요청의 본문에 기술해 HTTP POST를 감쌈

2. 통신을 시작하려면, 클라이언트는 서버에 있는 대상 프로그램의 이름과 위치를 결정해야 함(POST 요청을 실행시킬 수 있는 FPSE 패키지의 일부)
   - 이를 위해 클라이언트는 특별한 GET 요청을 보냄
<div align="center">
<img src="https://github.com/user-attachments/assets/9c8d4ce8-1bad-4764-8e5d-a60e7db88461">
</div>

   - 파일이 변환되면, FrontPage 클라이언트는 응답을 읽고 FPShtmlScriptUrl, FPAuthorScriptUrl, FPAdminScriptUrl와 관련된 값을 찾는데, 보통 다음과 같은 값이 기술
<div align="center">
<img src="https://github.com/user-attachments/assets/9ef022b3-ca73-4357-87a3-7709800b175c">
</div>

   - FPShtmlScriptUrl : 탐색 시간(Browse Time) 명령에 관한 POST 요청을 보낼 위치를 클라이언트에게 알려줌 (예) FPSE의 버전 얻기)
   - FPAuthorScriptUrl : 저작 시간(Authoring Time) 명령에 관한 POST 요청을 보낼 위치를 클라이언트에게 알려줌
   - FPAdminScriptUrl : 관리 동작에 관한 POST 요청이 실행되어야 할 위치를 알려줌

3. 요청
   - POST 요청의 본문에는 ```method=<command>``` 형식의 RPC 명령과 함꼐 필요한 모든 매개변수가 기술
   - 예) RPC 메세지가 문서 리스트를 요청한다고 가정
<div align="center">
<img src="https://github.com/user-attachments/assets/f32052f2-af16-43cf-8025-86ba309e0148">
</div>

   - POST 명령 본문에는 FPSE에 보내는 RPC 명령이 기술
   - CGI 프로그램과 같이, 메서드 내 빈칸은 더하기 문자(+)로 인코딩
   - 메서드 안에서 알파벳의 문자는 모두 %XX(XX는 문자의 아스키(ASCII) 표현)으로 인코딩
   - 그 기호들을 바꿔서 본문을 더 가독성있게 만들면 다음과 같음
<div align="center">
<img src="https://github.com/user-attachments/assets/3c3b1668-9503-4368-bba1-89f09f999d6d">
</div>

4. 나열되어 있는 요소들의 의미
   - service_name : 메서드가 수행되어야 할 웹 사이트의 URL로, 폴더나 한 단계 아래 폴더가 존재해야만 함
   - listHiddenDocs : 값이 true면 웹에 있는 숨겨진 문서가 보임 (hidden 문서는 _로 시작하는 경로 컴포넌트가 기술된 URL)
   - listExploreDocs : 값이 true면 태스크 리스트 나열

5. 응답
   - RPC 프로토콜 메서드 대부분은 반환 값이 있음
   - 가장 일반적인 반환 값 : 성공 메서드와 에러
   - 어떤 메서드는 세 번째 세부항목인 Sample Return Code를 포함
   - FrontPage는 사용자에게 정확한 응답을 주려고 코드를 적절히 해석
   - FPSE는 list+documents 요청을 처리하고 필요한 정보를 반환
<div align="center">
<img src="https://github.com/user-attachments/assets/05beb7b2-77b0-4522-a337-54c3be8d3039">
</div>

   - 응답에서 볼 수 있듯이, 웹 서버에서 유효한 문서의 목록을 특정 형식에 맞추어 작성해 FP 클라이언트에게 반환
