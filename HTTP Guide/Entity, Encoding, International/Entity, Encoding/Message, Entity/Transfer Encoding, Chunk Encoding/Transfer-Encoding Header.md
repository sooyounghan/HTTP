-----
### Transfer-Encoding 헤더
-----
1. Transfer-Encoding : 안전한 전송을 위해 어떤 인코딩이 메세지에 적용되었는지 수신자에게 알려줌
2. TE : 어떤 확장된 전송 인코딩을 사용할 수 있는지 서버에게 알려주기 위해 요청 헤더에 사용
3. 예) chunk-encoded 메세지와 메세지 끝에 트레일러가 오는 것을 받아들일 수 있음을 서버에게 알려주기 위해 TE 헤더를 사용 (HTTP 1.1 애플리케이션이어야 함)
<div align="center">
<img src="https://github.com/user-attachments/assets/c742775e-399a-4dba-927d-659ab48e81d7">
</div>

   - 수신자에게 메세지가 청크 인코딩으로 전송 인코딩되었음을 알려주기 위해 Transfer-Encoding 헤더를 포함
<div align="center">
<img src="https://github.com/user-attachments/assets/dfd8606b-3490-4619-a9e2-dc60ea77b774">
</div>

   - 이 기초 헤더 뒤, 메세지 구조가 변할 것

4. 모든 전송 인코딩 값은 대소문자가 구별
   - HTTP/1.1은 Transfer-Encoding과 TE 헤더 필드에 전송 인코딩 값을 사용
   - 최신 HTTP 명세는 오직 하나의 전송 인코딩, 즉 청크 인코딩만을 정의

5. TE 헤더는 Accept-Encoding 헤더와 마찬가지로 어떠 형태의 전송 인코딩을 선호하는지 Q 값을 가질 수 있음
   - 그러나 HTTP/1.1 명세는 청크 인코딩에 대해 Q 값이 0.0을 갖는 것을 금지
