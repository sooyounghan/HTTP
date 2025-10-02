-----
### 미디어 타입과 차셋(Charset)
-----
1. Content-Type 헤더 필드는 엔티티 본문의 MIME 타입 기술 (HEAD 요청의 경우라면, Content-Type은 GET 요청이었다면 보내주었을 유형을 알려줌)
2. MIME 타입은 전달되는 데이터 매체의 기저 형식(HTML 파일, 마이크로소프트 워드 문서, MPEG 비디오 등)의 표준화된 이름
3. 클라이언트 애플리케이션은 콘텐츠를 적절히 해독하고 처리하기 위해 MIME 타입 이용
4. Content-Type의 값은 인터넷 할당 번호 관리 기간(Internet Assgined Numbers Authority, IANA)에 등록된 표준화된 MIME 타입
   - 주 미디어 타입(텍스트, 이미지, 오디오 등)으로 시작해 뒤이어 빗금(/), 그리고 미디어 타입을 더 구체적으로 서술하는 부 타입(Subtype)으로 구성
5. Content-Type 헤더에서 흔히 쓰이는 MIME 타입
<div align="center">
<img src="https://github.com/user-attachments/assets/aba820f8-ef2e-4fe0-856d-e3238a3fc721">
</div>

6. Content-Type 헤더가 원본 엔티티 본문의 미디업 타입을 명시하는 것은 중요
   - 예를 들어, 엔티티가 콘텐츠 인코딩을 거친 경우에도 Content-Type 헤더는 여전히 인코딩 전 엔티티 본문 유형을 명시할 것
