-----
### 헤더
-----
1. 헤더와 메서드는 클라이언트와 서버가 무엇을 해야하는지 결정하기 위해 함께 사용
2. 헤더에는 특정 종류 메세지에만 사용할 수 있는 헤더와, 더 일반 목적으로 사용할 수 있는 헤더, 그리고 응답과 요청 메세지 양쪽 모두에서 정보를 제공하는 헤더 존재
3. 일반 헤더(General Header)
   - 클라이언트와 서버 양쪽 모두가 사용
   - 클라이언트, 서버 그리고 어딘가에 메세지를 보내는 다른 애플리케이션을 위해 다양한 목적으로 사용
   - 예를 들어, Date 헤더는 서버와 클라이언트를 가리지 않고 메세지가 만들어진 일시를 저장하기 위해 사용하는 일반 목적 헤더
<div align="center">
<img src="https://github.com/user-attachments/assets/28658c06-91e9-4b8f-99d5-43d2f49ef3f6">
</div>

4. 요청 헤더(Request Header)
   - 요청 메세지를 위한 헤더
   - 서버에게 클라이언트가 받고자 하는 데이터와 타입이 무엇인지와 같은 부가 정보를 제공
   - 예를 들어, Accept 헤더는 서버에게 클라이언트가 자신의 요청에 대응하는 어떠한 미디어 타입도 받아들일 것을 의미
<div align="center">
<img src="https://github.com/user-attachments/assets/76076c91-3642-46b3-86ca-299fe1b01e9b">
</div>

5. 응답 헤더(Response Header)
   - 응답 메세지는 클라이언트에게 정보를 제공하기 위한 자신만의 헤더를 갖고 있음 (예) 클라이언트가 어떤 종류의 서버와 대화하고 있는가)
   - 예를 들어, Servwr 헤더는 클라이언트에게 그가 Tiki-Hut 서버 1.0 버전과 대화하고 있음을 알려줌
<div align="center">
<img src="https://github.com/user-attachments/assets/bd842cc4-a6df-45d3-8b7a-1d166fd644cd">
</div>

6. 엔티티 헤더 (Entity Header)
   - 엔티티 본문에 대한 헤더
   - 예를 들어, 엔티티 헤더는 엔티티 본문에 들어잇는 데이터 타입이 무엇인지 말해줄 수 있음
   - 예를 들어, Content-Type 헤더는 애플리케이션에서 데이터가 iso-latin-1 문자집합으로 된 HTML 문서임을 알려줌
<div align="center">
<img src="https://github.com/user-attachments/assets/1f40d0eb-202d-4174-aaac-d1a9fd439b06">
</div>

7. 확장 헤더(Extension Header)
   - 애플리케이션 개발자들에 의해 만들어졌지만, 아직 승인된 HTTP 명세에는 추가되지 않은 비표준 헤더
   - HTTP 프로그램은 확장 헤더들에 대해 설령 그 의미를 모른다 할지라도 용인하고 전달해야 할 필요가 있음
