-----
### Cache-Control
-----
1. 객체가 어떻게 캐시될 수 있는지 정보를 넘겨주기 위해 사용
2. 값은 객체를 어떻게 캐시할 것인지에 대한 특별한 지시를 하는 캐시 지시자
<div align="center">
<img src="https://github.com/user-attachments/assets/4085e95d-a49e-4a21-94b6-2460d205f4fb">
</div>

-----
### Client-ip
-----
: 클라이언트가 실행 중인 컴퓨터의 IP 주소를 전달하기 위해 몇몇 오래된 클라이언트와 프록시에 의해 사용되는 확장 헤더
<div align="center">
<img src="https://github.com/user-attachments/assets/f8d2b3fc-f3e3-4765-89c6-372e47b4a5b0">
</div>

-----
### 💡 Connection
-----
1. 이 헤더는 keep-alive 커넥션 확장을 지원하는 HTTP/1.0 클라이언트에서 제어 정보를 위해 사용
2. HTTP/1.1에서의 값은 헤더의 이름에 대응되는 토큰의 목록
   - Connection 헤더가 포함된 HTTP/1.1 메세지를 받는 애플리케이션은 그 목록을 파싱하고 얻은 헤더들을 메세지에서 지우도록 되어있음
   - 이 헤더는 주로 프록시를 위한 것으로, 홉과 홉 사이에서만 사용하므로 그 다음 홉으로 넘겨줘서는 안 될 헤더(Hop-By-Hop 헤더)들을 서버나 다른 프록시가 지정할 수 있게 해줌
   - 특별한 헤더 값 중 하나로 close가 존재 : 이 토큰은 응답이 완료되면 연결이 닫힐 것임을 의미
   - 지속 커넥션을 지원하지 않는 HTTP/1.1 애플리케이션은 모든 요청과 응답에 값이 close인 Connection 헤더를 집어넣을 필요가 있음
<div align="center">
<img src="https://github.com/user-attachments/assets/a4c99860-188d-4963-a78b-c8c9b3ed8dab">
</div>

-----
### Conetnt-Base
-----
1. 서버가 응답의 엔티티 본문에서 발견된 URL를 해석할 때 사용할 기저 URL를 명시
2. Content-Base 헤더 값은 엔티티 안에서 발견된 상대 URL을 해석할 때 사용할 수 있는 절대 URL
<div align="center">
<img src="https://github.com/user-attachments/assets/9c883391-0f95-4e16-9edf-3d2c3db290db">
</div>

-----
### Content-Encoding
-----
1. 객체에 어떤 인코딩이 수행될 수 있는지 명시하기 위해 사용
2. 콘텐츠 인코딩을 이용해, 서버는 응답을 보내기 전 먼저 압축할 수 있음
3. 이 헤더의 값은 클라이언트에게 어떤 유형 혹은 인코딩의 유형이 객체에 적용되는지 말해주며, 그 정보를 이용해 클라이언트는 메세지를 디코딩할 수 있음
4. 때로는 하나 이상의 인코딩이 엔티티에 적용될 수 있는데, 이런 경우 인코딩은 반드시 수행된 순서대로 배열되어야 함
<div align="center">
<img src="https://github.com/user-attachments/assets/757dedf1-69e4-46e4-ab58-009b3a89370d">
</div>

-----
### Content-Language
-----
1. 클라이언트에게 객체를 이해하기 위해 알고 있어야 하는 자연어가 무엇인지 말해줌
   - 예) 프랑스어로 쓰인 문서는 프랑스어를 가리키는 Content-Language 값을 가질 것

2. 만약 응답에 헤더가 존재하지 않는다면, 그 객체는 모든 청자를 위한 것
3. 헤더의 값에 복수 개의 언어가 있다면, 이는 객체가 나열된 각 언어의 사용자들에게 적합하다는 것을 의미
4. 💡 헤더의 값이 이 객체에 포함된 언어의 일부 혹은 전체를 의미하는 것이 아니라 그 객체가 어떤 언어 사용자를 위한 것인지를 의미하는 것
5. 또한, 이 헤더는 텍스트로 된 데이터 객체만을 위한 것이 아닌, 이미지 / 비디오 / 그 외 유형의 미디어에 어떤 언어의 사용자를 대상으로 하는지 태깅 가능
<div align="center">
<img src="https://github.com/user-attachments/assets/5b092a6b-d73f-4401-adee-4fdb4d48f9f4">
</div>

-----
### Content-Length
-----
1. 엔티티 본문의 길이나 크기를 알려주기 위한 것
2. 만약 응답 메세지의 헤더가 HEAD HTTP 요청이라면, 이 헤더의 값은 보내졌을 엔티티 본문의 크기 값
<div align="center">
<img src="https://github.com/user-attachments/assets/6df18888-2eeb-428a-82ab-b913f857c81c">
</div>

-----
### Content-Location
-----
1. 메세지의 엔티티에 대응하는 URL을 전달하기 위해 HTTP 메세지에 포함
2. 복수 개의 URL을 갖는 객체들을 위해, 응답 메세지는 응답을 생성하는 객체의 URL을 가리키는 Content-Location 헤더 포함 가능
3. 요청한 URL에 따라 달라질 수 있으며, 이 헤더는 클라이언트를 새 URL로 리다이렉트 하기 위해 서버가 사용
<div align="center">
<img src="https://github.com/user-attachments/assets/eca06091-6319-466f-b5ce-4e236337ae98">
</div>

-----
### Content-MD5
-----
1. 서버는 메세지 본문에 대한 무결성 검사를 제공하기 위해 사용
2. 오직 원 서버나 요청을 보낸 클라이언트만이 이 헤더를 메세지에 집어넣을 수 있음
3. 이 헤더의 갑은 메세지 본문(인코딩 된 후 일 수 있음)에 대한 MD5 요약
4. 이 헤더의 값은 전송 중 발생한 데이터에 대한 의도하지 않은 수정을 감지하는데 유용한, 데이터에 대한 종단간(End-To-End) 검사를 제공하지만, 보안 목적으로 사용하는 것은 의도하지 않음
5. RFC 1864는 이 헤더에 대해 더 자세히 정의
<div align="center">
<img src="https://github.com/user-attachments/assets/47cfb7a9-f395-48c2-a52a-d00714bc8763">
</div>

-----
### Content-Range
-----
1. 문서의 특정 범위를 전송해달라는 요청에 대한 응답
2. 이 헤더는 현재 전송하고 있는 엔티티가 원 엔티티에서 어디에 해당하는지 위치(범위)를 제공하며, 또한 전체 엔티티 길이도 알려줌
3. 만약 전체 엔티티의 길이 대신 ```*```이 존재한다면, 응답이 보내졌을 때 전체 길이를 알 수 없었음을 의미
<div align="center">
<img src="https://github.com/user-attachments/assets/b1cbda3f-ee3e-4ead-9a19-95ae391cf9d5">
</div>

-----
### Content-Type
-----
: 이 메세지에 담긴 객체의 미디어 타입을 알려줌
<div align="center">
<img src="https://github.com/user-attachments/assets/041ef06b-da1b-42ee-a725-b2e039936650">
</div>

-----
### Cookie
-----
: 클라이언트 신원 식별과 추적을 위해 사용되는 확장 헤더
<div align="center">
<img src="https://github.com/user-attachments/assets/5737e8c4-6618-49c1-83d5-69484df1e982">
</div>

-----
### Cookie2
-----
1. Cookie : 클라이언트 신원 식별과 추적을 위해 사용되는 확장 헤더
2. Cookie2 : 요청자가 이해하는 쿠키의 버전을 식별하기 위해 사용 (RFC 2965에 정의)
<div align="center">
<img src="https://github.com/user-attachments/assets/116e2cff-8b37-4170-a1fe-2ce289b97f2d">
</div>


 
