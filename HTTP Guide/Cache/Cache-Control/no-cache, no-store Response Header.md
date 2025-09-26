-----
### no-cache와 no-store 응답 헤더
-----
1. HTTP/1.1은 신선도 관리를 위해 객체를 캐시하는 것을 제한하거나 캐시된 객체를 제공하는 여러 가지 방법 제공
2. no-store와 no-cache 헤더는 캐시가 검증되지 않은 캐시된 객체로 응답하는 것을 막음
<div align="center">
<img src="https://github.com/user-attachments/assets/91c5a7b5-5fc5-4ec1-b6c6-535b63f24cdd">
</div>

3. no-store가 표시된 응답 : 캐시가 그 응답의 사본을 만드는 것 금지
   - 캐시는 보통, 캐시가 아닌 프록시 서버가 그러는 것 처럼 클라이언트에게 no-store 응답을 전달하고 나면 객체를 할 것

4. no-cache가 표시된 응답 : 로컬 캐시 저장소에 저장될 수 있음
   - 다만 먼저 서버와 재검사를 하지 않고서는 캐시에서 클라이언트로 제공될 수 없을 뿐임
   - 이 헤더의 이름은 Do-Not-Serve-From-Cache-Without-Revalidation(재검사 없이 캐시에서 제공하지 마라)일 것

5. Pragma: no-cache 헤더는 HTTP/1.0+와 하위호환성을 위해 HTTP/1.1에 포함되어 있음
   - HTTP/1.1 애플리케이션은 Pragma: no-cache만 이해할 수 있는 HTTP/1.0 애플리케이션에 대응해야하는 경우가 아니라면 Cache-Control: no-cache를 사용해야함
   - Pragma: no-cache는 HTTP 요청과 응답 모두를 확장 헤더로 널리 쓰이고 있으나 엄밀히 말하면 HTTP 요청에서만 유효
