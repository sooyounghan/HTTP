-----
### HTTP-EQUIV를 통한 HTML 캐시 제어
-----
1. HTTP 서버 응답 헤더는 문서의 만료와 캐시 제어 정보를 돌려주기 위해 사용
2. 웹 서버는 제공할 문서에 올바른 캐시 제어 헤더들을 부여하기 위해 설정 파일들과 상호작용
3. 저자가 웹 서버 설정 파일과 상호작용이 없어도 쉽게 HTML 문서에 HTTP 헤더 정보를 부여할 수 있도록 하기 위해, HTML 2.0은 ```<META HTTP-EQUIV>``` 태그를 정의
   - 이 선택적 태그는 HTML 문서 최상단 위치하여 문서와 연동되어야 하는 HTTP 헤더를 정의
   - HTML 문서를 캐시하지 않도록 설정하는 ```<META HTTP-EQUIV>``` 태그 예시
<div align="center">
<img src="https://github.com/user-attachments/assets/3c000bfe-ad6e-4f90-9b14-6e2fc4400a57">
</div>

4. 이 HTTP-EQUIV 태그는 원래 웹 서버에서 사용하도록 의도된 것으로, 웹 서버는 HTML에서 ```<META HTTP-EQUIV>``` 태그를 파싱하여 HTTP 응답에 정해진 헤더를 삽입
5. 이 동작에 대해서 RFC 1866에 다음과 같이 문서화 : HTTP 서버는 문서를 처리하는 과정에서 이 정보를 사용하며, 특히, 서버는 이 문서에 대한 요청의 응답에 헤더 필드를 포함할 것이며, 이름은 HTTP-EQUIV의 속성 값에서 얻고, 헤더의 값은 CONTENT 속성의 값에서 얻음
6. 불행히도 이 기능을 지원하는 웹 서버나 프록시는 거의 없음 : 이 기능은 서버의 부하를 가중시키고, 설정값이 정적이며, HTML을 제외한 다른 타입의 파일은 지원하지 않기 떄문임
7. 그러나 몇몇 브라우저는 HTML 콘텐츠 내 HTTP-EQUIV 태그를 파싱하고 실제 HTTP 헤더처럼 다룸
<div align="center">
<img src="https://github.com/user-attachments/assets/3ff7adca-b80b-466d-9e3b-8af753a169ea">
</div>

   - HTTP-EQUIV를 지원하는 HTML 브라우저들은 중간의 프록시 캐시와는 다른 캐시 제어 규칙을 적용할 것이므로, 캐시 만료에 대한 동작에 혼란 초래
   - 일반적으로 ```<META HTTP-EQUIV>``` 태그는 문서의 캐시 동작을 제어하는 서투른 방법이며, 문서의 캐시 제어 요청과 커뮤니케이션하는 유일하게 확실한 방법은 올바르게 설정된 서버가 보내온 HTTP 헤더를 이용하는 것
