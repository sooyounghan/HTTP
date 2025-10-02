-----
### 메세지, 엔티티
-----
1. HTTP 메세지를 인터넷 운송 시스템 컨테이너라고 생각한다면, HTTP 엔티티는 메세지의 실질적 화물
2. HTTP 응답 메세지에 실려 전달되는 간단한 엔티티
<div align="center">
<img src="https://github.com/user-attachments/assets/eaeba813-a9c4-4add-8143-85f637a51485">
</div>

   - 엔티티 헤더는 겨우 18자에 불과한(Content-Length: 18) 플레인 텍스트 문서(Content-Type: text/plain)를 의미
   - 빈 줄(CRLF)은 헤더 필드와 분몬의 시작을 나눔

3. HTTP/1.1의 10가지 주요 엔티티
   - Content-Type : 엔티티에 의해 전달된 객체의 종류
   - Content-Length : 전달되는 메세지 길이나 크기
   - Content-Language : 전달되는 객체와 가장 잘 대응되는 자연어
   - Content-Encoding : 객체 데이터에 대해 행해진 변형 (압축 등)
   - Content-Location : 요청 시점 기준으로, 객체의 또 다른 위치
   - Content-Range : 만약 이 엔티티가 부분 엔티티라면, 이 헤더는 이 엔티티가 전체에서 어느 부분에 해당하는지 정의
   - Content-MD5 : 엔티티 본문의 콘텐츠에 대한 체크섬
   - Last-Modified : 서버에서 이 콘텐츠가 생성 혹은 수정된 날
   - Expires : 이 엔티티 데이터가 더 이상 신선하지 않은 것으로 간주되기 시작하는 날짜와 시각
   - Allow : 이 리소스에 대해 어떤 메서드가 허용되는지(예) GET, HEAD)
   - ETag : 이 인스턴스에 대한 고유한 검사기로, 이 헤더는 엔티티 헤더로 정의되어 있지 않지만, 엔티티와 관련된 많은 동작을 위한 중요 헤더
   - Cache-Control : 어떻게 이 문서가 캐시될 수 있는지에 대한 지시자, ETag 헤더와 마찬가지로 이 헤더도 엔티티 헤더로 정의되어 있지 않음
