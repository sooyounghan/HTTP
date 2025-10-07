-----
### X 헤더
-----
: X 헤더들은 모두 확장 헤더

-----
### X-Cache
-----
: 클라이언트가 어떤 리소스가 캐시되어 있는지 알려주기 위해 Squid에서 사용
<div align="center">
<img src="https://github.com/user-attachments/assets/397be2f2-b828-4af8-aa6f-10360caffe3d">
</div>

-----
### X-Forward-For
-----
1. 이 헤더는 요청이 누구를 위해 포워딩되는지 표시하기 위해 상당히 많은 프록시 서버에서 사용(예) Squid)
2. Client-ip 헤더와 같이, 이 요청 헤더는 요청 근원지의 주소를 언급
<div align="center">
<img src="https://github.com/user-attachments/assets/e4f18cb4-6be3-4aa0-be56-9191c6ce054a">
</div>

-----
### X-Pad
-----
1. 이 헤더는 응답 헤더 길이와 관련된 몇몇 브라우저의 버그를 극복하기 위해 사용
2. 이 헤더는 응답 메세지 헤더에 몇 개의 추가 바이트들을 더해 버그를 회피
<div align="center">
<img src="https://github.com/user-attachments/assets/5c1d25d2-d88e-4eca-b924-d9928bebc2c8">
</div>

-----
### X-Serial-Number
-----
1. 확장 헤더로서, 라이센스를 받은 소프트웨어의 일련번호를 HTTP 메세지에 삽입하기 위해 몇몇 오래된 HTTP 애플리케이션에 의해 사용
2. 현재는 사용하지 않음
<div align="center">
<img src="https://github.com/user-attachments/assets/6309cb32-704c-4c04-9e88-89e0bd9c5e7e">
</div>
