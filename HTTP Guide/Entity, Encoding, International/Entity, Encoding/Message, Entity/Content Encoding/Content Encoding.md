-----
### 콘텐츠 인코딩 과정
-----
1. 웹 서버가 원본 Content-Type과 Content-Length 헤더를 수반한 원본 응답 메세지를 생성
2. 콘텐츠 인코딩 서버(원 서버 또는 다운스트림 프록시일 것)가 인코딩 메세지를 생성
   - 인코딩된 메세지는 Content-Type은 같지만 (본문이 압축되었거나 했다면) Content-Length는 다름
   - 콘텐츠 인코딩 서버는 Content-Encoding 헤더를 인코딩 된 메세지에 추가하여, 수신 측 애플리케이션이 그것을 디코딩할 수 있도록 함
  
3. 수신 측 프로그램은 인코딩 된 메세지를 받아 디코딩하고 원본을 얻음

4. 콘텐츠 인코딩의 예
<div align="center">
<img src="https://github.com/user-attachments/assets/4962238a-8e93-40b4-a530-37bc62ecb01e">
</div>

   - 더 작은 압축된 본문을 만들기 위해 gzip 콘텐츠 인코딩 기능으로 인코딩 된 HTML 페이지 존재
   - 압축된 본문은 gzip 인코딩 플래그가 붙어서 네트워크를 통해 전송
   - 수신 측 클라이언트는 그 엔티티를 gzip 디코더를 사용해 압축 해제
   - 인코딩된 응답의 한 예 (압축된 이미지)
<div align="center">
<img src="https://github.com/user-attachments/assets/8e1410df-2440-49b2-87c5-38d24947e470">
</div>

   - 여전히 Content-Type 헤더가 메세지에 존재할 수 있고, 또한 그래야 함
   - 이 헤더는 엔티티의 원래 포맷을 기술하며, 이는 디코딩 된 엔티티를 보여주기 위해 필요한 정보
   - Content-Length은 이제 인코딩 된 본문의 길이를 나타냄
