-----
### Content-Type Charset 헤더와 META 태그
-----
<div align="center">
<img src="https://github.com/user-attachments/assets/7cd4b254-b359-4ee6-b864-484d5bb3fa4a">
</div>

1. 웹 서버는 클라이언트에게 MIME Charset 태그를 charset 매개변수와 함께 Content-Type 헤더에 담아 보냄
2. 만약 문자집합이 명시적으로 나열되지 않았다면, 수신자는 문서의 콘텐츠로부터 문자집합을 추측하려 시도
   - HTML 콘텐츠에서 문자집합은 문자집합을 서술하는 ```<META HTTP-EQUIV="Content-Type">``` 태그에서 찾을 수 있음

3. 예) HTML META 태그가 문자집합을 일본어 인코딩 ISO-2022-JP로 설정하는지 보여줌
   - 만약 문서가 HTML이 아니라면, 혹은 META Content-Type 태그가 없다면, 소프트웨어는 언어와 인코딩에 대한 일반적인 패턴을 찾기 위해 실제 텍스트를 스캐닝하여 문자 인코딩을 추측
<div align="center">
<img src="https://github.com/user-attachments/assets/e5ce6313-21a9-4420-aa5e-1d4a9c89d756">
</div>

   - 만약 클라이언트가 문자 인코딩을 추측하지 못했다면, ISO-8859-1 인 것으로 가정
