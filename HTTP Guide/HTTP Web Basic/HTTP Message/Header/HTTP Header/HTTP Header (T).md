-----
### TE
-----
1. Accpet-Encoding 헤더처럼 기능하지만 전송 인코딩을 위한 것
2. 클라이언트가 청크 인코딩을 통해 보내진 응답의 트레일러에 들어있는 헤더를 다룰 수 있는지 여부를 알려주기 위해 사용될 수 있음
<div align="center">
<img src="https://github.com/user-attachments/assets/59210e76-aaf5-464c-9952-0a1ef902721e">
</div>

-----
### Trailer
-----
: 메세지의 끝에 어떤 헤더들이 나오게 되는지 나타내기 위해 사용
<div align="center">
<img src="https://github.com/user-attachments/assets/f133811d-7534-46d9-ad37-6b72e72a3d26">
</div>

-----
### Title
-----
1. 명세가 없는 헤더이지만, 엔티티 제목을 알려주는 것으로 알려져 있음
2. 이 헤더는 초기 HTTP/1.0 확장의 일부였고, 주로 서버가 사용할 수 있는 명확한 제목을 갖고 있는 HTML 페이지를 위해 사용
<div align="center">
<img src="https://github.com/user-attachments/assets/d0e5682a-f269-4ac7-bdd2-07c8a75f7dd5">
</div>

-----
### Transfer-Encoding
-----
1. HTTP 메세지를 안전하게 보내기 위해 몇 인코딩이 수행된다면, 이 메세지는 반드시 이 헤더를 포함
2. 이 값은 메세지 본문에 적용된 인코딩 목록으로, 만약 여러 인코딩이 적용되었다면, 그 인코딩들은 순서대로 나열
3. 💡 Content-Encoding 헤더와는 다름 : 전송 인코딩은 서버 혹은 다른 중개자 애플리케이션이 메세지를 전송하기 위해 적용하는 인코딩
<div align="center">
<img src="https://github.com/user-attachments/assets/dc019d84-933f-45ea-8d7a-a1cb8d5b376c">
</div>
