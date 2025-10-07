-----
### 하이퍼텍스트 캐싱 프로토콜
-----
1. ICP는 HTTP/0.9를 염두에 두고 설계되었으므로, 캐시가 리소스 존재 여부를 질의할 때 URL만 보내도록 설계
   - HTTP 버전 1.0과 1.1은 URL과 더불어 문서 매칭에 대한 판단을 내릴 때 사용될 수 있는 많은 헤더 도입
   - 따라서, 요청의 URL만을 보내는 것은 정확한 응답을 가져오지 못하는 결과를 가져올 수 있음

2. 하이퍼텍스트 캐싱 프로토콜(Hyper Text Caching Protocol, HTCP)은 형제들이 URL과 모든 요청 및 응답 헤더를 사용하여 서로에게 문서의 존재 여부에 대한 질의를 할 수 있게 해줌으로써 적중이 아님에도 적중으로 잘못 처리될 확률을 줄임
   - 더 나아가, HTCP는 형제 캐시들이 서로의 캐시 안에 있는 선택된 문서의 추가 및 삭제를 모니터링 할 수 있게, 그리고 서로의 캐시된 문서에 대한 캐싱 정책을 변경할 수 있게 해줌

3. 만약 근처 캐시가 그 문서를 갖고 있다면, 요청 캐시는 그 캐시에 HTTP 커넥션을 열고 그 문서를 가져옴
4. HTCP 메세지의 구조
<div align="center">
<img src="https://github.com/user-attachments/assets/845bcc2d-37dc-4ded-b711-476a1f6785e7">
</div>

   - 헤더 부분은 메세지 길이와 메세지 버전을 포함
   - 데이터 부분은 OP 코드를 포함한 데이터 길이로 시작하여, 응답 코드, 몇몇 태그들과 아이디들이 이어지며 실제 데이터로 끝남

5. 메세지 필드의 상세
   - 헤더 : 32비트 메세지 길이, 8비트 주 프로토콜 버전, 8비트 부 프로토콜 버전으로 구성
     + 메세지 길이는 모든 헤더, 데이터, 인증 크기를 포함

   - 데이터 : HTCP 메세지를 포함
     + 데이터 구성 요소
<div align="center">
<img src="https://github.com/user-attachments/assets/93385625-66fc-4e52-a57c-d6154da639a2">
</div>

   - HTCP OP 코드
<div align="center">
<img src="https://github.com/user-attachments/assets/db25b5b6-ac7b-435f-b41b-899d5b6a22c0">
</div>
