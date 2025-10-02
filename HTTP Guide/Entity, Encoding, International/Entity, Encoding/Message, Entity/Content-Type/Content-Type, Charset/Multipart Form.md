-----
### 멀티파트 폼
-----
1. HTTP 폼을 채워서 제출하면, 가변 길이 텍스트 필드와 업로드 될 객체는 각각이 멀티파트 본문을 구성하는 하나의 파트가 되어 보내짐
2. 멀티파트 본문은 여러 다른 종류와 길이의 값으로 채워진 폼을 허용
   - HTTP는 이러한 요청을 Content-Type: multipart/form-data나 Content-Type: multipart/mixed 헤더에 멀티파트 본문을 함께 보냄
<div align="center">
<img src="https://github.com/user-attachments/assets/4db8029e-558e-41ed-b4b0-0a156a546d84">
</div>

   - 이 때, boundary는 본문의 서로 다른 부분을 구분하기 위한 구분자로 쓰임

3. 예) multipart/form-data 인코딩 묘사
<div align="center">
<img src="https://github.com/user-attachments/assets/fa8017b1-06fa-40c0-9155-553976ab37c1">
</div>

   - 사용자가 텍스트 입력 필드에 'Sally'라고 입력하고, 'essayfile.txt'를 선택했다면, 사용자 에이전트는 다음과 같은 데이터를 돌려보낼 것
<div align="center">
<img src="https://github.com/user-attachments/assets/3c041f6e-e1ca-4363-a149-0b598dbdc9bf">
</div>

   - 사용자가 두 번째 (이미지) 파일로 imagefile.gif를 선택했다면, 사용자 에이전트는 그 부분을 다음과 같이 생성
<div align="center">
<img src="https://github.com/user-attachments/assets/3ae233cb-cc33-4259-bb03-55230aef0c6b">
</div>

-----
### 멀티파트 범위 응답
-----
1. 범위 요청에 대한 HTTP 응답 또한 멀티파트가 될 수 있음
2. 이러한 응답은 Content-Typr: multipart/byteranges 헤더 및 각 다른 범위를 담고 있는 멀티파트 본문이 함꼐 옴
3. 어떤 문서의 다른 범위에 대한 요청의 멀티파트 응답 예
<div align="center">
<img src="https://github.com/user-attachments/assets/df11d258-931d-420c-8664-ecfc1803c9e8">
</div>
