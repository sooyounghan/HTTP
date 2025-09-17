-----
### MIME (Multipurpose Internet Mail Extensions, 다목적 인터넷 메일 확장)
-----
1. 인터넷은 수천 가지 데이터 타입을 다루기 위해 HTTP는 웹에서 전송되는 객체 각각에 신중하게 MIME 타입이라는 데이터 포맷 라벨을 붙임
2. MIME는 원래 각기 다른 전자메일 시스템 사이에서 메세지가 오갈 때 겪는 문제점을 해결하기 위해 설계
3. MIME은 이메일에서 워낙 잘 동작하였으므로, HTTP에서도 멀티미디어 콘텐츠를 기술하고 라벨을 붙이기 위해 채택
4. 웹 서버는 모든 HTTP 객체 데이터에 MIME 타입을 붙임
<div align="center">
<img src="https://github.com/user-attachments/assets/698bc40c-ae91-4d55-b7d4-cbe075e22022">
</div>

   - 웹 브라우저는 서버로부터 객체를 돌려받을 때, 다룰 수 있는 객체인지 MIME 타입을 통해 확인
   - 대부분 웹 브라우저는 잘 알려진 객체 타입 수백 가지를 다룰 수 있으며, 외부 플러그인 소프트웨어를 실행

5. MIME 타입은 사선(/)으로 구분된 주 타입(Primary Object Type)과 부 타입(Specific Subtype)으로 이루어진 문자열 레벨
   - HTML로 작성된 텍스트 문서 : text/html 라벨이 붙음
   - Plain ASCII 텍스트 문서 : text/plain 라벨이 붙음
   - JPEG 이미지 : image/jpeg
   - GIF 이미지 : image/gif
   - 애플 퀵타입 동영상 : video/quicktime
   - 마이크로소프트 파워포인트 프레젠테이션 : application/vnd.ms-powerpoint

6. 수백 가지 잘 알려진 MIME 타입과, 그보다 더 많은 실험용 혹은 특정 용도의 MIME 타입 존재
   
