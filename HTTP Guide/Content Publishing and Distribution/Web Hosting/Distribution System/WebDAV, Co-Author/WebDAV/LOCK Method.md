-----
### LCOK 메서드
-----
1. WebDAV의 강력한 기능은 한 개의 LOCK 요청으로 여러 개의 리소스를 잠글 수 있음
   - WebDAV의 잠금은 클라이언트가 서버에 연결되어 있지 않아도 됨
   - 예) 다음과 같은 LOCK 요청 존재
<div align="center">
<img src="https://github.com/user-attachments/assets/012cb689-6be2-4332-bead-2088067204cb">
</div>

   - 전송된 XML에는 기본 요소로 ```<lockinfo>```를 가짐

2. ```<lockinfo>``` 구조 안의 세 개의 하위 요소
   - ```<locktype>``` : 잠금 형식 (현재는 단 한개의 write만 가짐)
   - ```<lockscope>``` : 배타적 잠금인지, 공유된 잠금인지 가리킴
   - ```<owner>``` : 현재 잠금을 가지고 있는 사람이 기술되어 있는 필드

3. LOCK 요청에 대해 성공한 응답
<div align="center">
<img src="https://github.com/user-attachments/assets/dc0b4a09-5791-481e-8c16-d5549b10a65e">
</div>

   - ```<lockdiscovery>``` 요소는 잠금에 관한 정보를 담는 컨테이너 역할
     + 요소에 포함된 ```<activelock>```는 요청과 함께 전송된 정보(```<locktype>, <lockscope>, <owner>```)를 담는 하위 요소

   - ```<activelock>```의 하위 요소
     + ```<locktoekn>``` : URI 스킴에서 opaquelocktoken라 부르는 토큰으로 잠금을 식별하는 데 사용 (HTTP는 기본적으로 상태가 없어서(Stateless), 이후에 보내는 요청에 잠금의 소유자를 식별자를 식별하는 이 토큰을 보냄)
     + ```<depth>``` : Depth 헤더와 같은 값을 가짐
     + ```<timeout>``` : 잠금에 대한 타임아웃을 가리킴

   - opaquelocktoken 스킴 : 언제든 모든 리소스에 유일한 토큰을 제공하기 위해 설계 (유일성 보장을 위해, WebDAV는 ISO-11578에 기술되어 있는 UUID 메커니즘 사용)
     + 서버는 각 LOCK 요청에 UUID 생성하는 방식이나, 한 개의 UUID를 만들고 그 끝에 다른 문자들을 덧붙여 유일성을 방지하는 방식 중 하나 선택
     + 성능상 후자가 더 좋지만, 서버가 후자 방식을 구현하려면, 추가된 확장들을 모두 재사용하지 말아야 함
       
   - ```<lockdiscovery>``` XML 요소 : 활성화되어 있는 잠금을 찾는 메커니즘을 제공
     + 만약 다른 이가 이미 잠겨져 있는 파일을 잠그려고 하면, 현재 주인을 가리키는 ```<lockdiscovery>``` XML 요소를 받게 될 것
     + 이 요소에는 자체 속성과 함께 아직 처리되지 않은 모든 잠금이 기술

   - 잠금 갱신과 Timeout 헤더
     + 잠금을 갱신하려면, 클라이언트는 If 헤더에 잠금 토큰과 함께 잠금 요청을 다시 보내야 함
     + 반환된 timeout 값은 이전 timeout 값과는 다를 것
     + 서버에게서 온 timeout 값을 받는 대신, 클라이언트는 LOCK 요청 안에 필요한 timeout 값을 기술하며, 그 값은 Timeout 헤더에 기술
     + Timeout 헤더 문법은 클라이언트가 콤마로 구분해 몇 가지 옵션을 나열
<div align="center">
<img src="https://github.com/user-attachments/assets/028e9df7-e054-4c0f-a580-834f88ceaf40">
</div>

   - 서버가 옵션들을 다 지원해야 하는 것은 아니지만, ```<timeout>``` XML 요소에 잠금 파기 시간을 제공해야 함
   - 모든 경우에, 잠금 타임아웃은 어디까지나 지침일 뿐 서버와 연동될 필요는 없음
