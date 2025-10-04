-----
### 향상된 HTTP/1.1 메서드
-----
1. WebDAV는 HTTP 메서드인 DELETE, PUT, OPTIONS의 의미를 수정
   - GET과 HEAD의 의미는 바뀌지 않고 그대로 둠
   - POST 요청이 수행하는 작업은 항상 특정 서버 구현에 따라서 다르며, WebDAV는 POST의 의미를 전혀 수정하지 않았음
  
2. PUT 메서드
   - WebDAV가 PUT 메서드를 따로 정의하지는 않지만, PUT 메서드는 저작자가 공용 사이트에 콘텐츠를 전송하는 유일한 방법
   - WebDAV는 잠금을 지원하기 위해 동작 수정
<div align="center">
<img src="https://github.com/user-attachments/assets/c0381342-b55b-49a3-8d55-fd32517edb2d">
</div>

   - 잠금을 제공하려고, WebDAV는 PUT 요청에 If 헤더를 추가
   - 위 트랜잭션에서 If 헤더에 기술되어 있는 잠금 토큰이 리소스에 있는 것과 일치한다면, PUT 작업이 수행되어야 함
   - If 헤더는 PROPPATCH, DELETE, MOVE, LOCK, UNLOCK 등과 같은 다른 메서드들과 함께 사용

3. OPTIONS 메서드
   - WebDAV를 사용하는 클라이언트가 보내는 첫 요청에 쓰임
   - 클라이언트는 OPTIONS 메서드를 사용해서 WebDAV 서버가 어떤 것들을 제공하는지 알아볼 수 있음
   - 요청과 응답의 예
<div align="center">
<img src="https://github.com/user-attachments/assets/0586c024-84b1-4760-ae33-56abf5e235f8">
</div>

<div align="center">
<img src="https://github.com/user-attachments/assets/b102ab2c-8dee-44ec-9f05-c03cbabc8193">
</div>

   - OPTIONS 메서드에 대한 응답의 결과 헤더
     + DAV 헤더 : DAV 지원 클래스에 대한 정보 제공 (두 가지 지원 클래스 존재)
     + Class 1 지원 : 서버는 RFC 2518의 모든 절에 있는 모든 MUST 요구사항을 지원해야 하며, 만약 리소스가 Class 1 수준만 지원한다면, DAV 헤더 값으로 1을 보낼 것
     + Class 2 지원 : Class 1 요구사항 모두 지원하는 것에 더해 LOCK 메서드를 지원하며, LOCK과 함께 Class 2를 지원하려면 Timeout과 Lock-Token 헤더를 지원해야 하고, ```<supportedlock>```과 ```<lockdiscovery>``` XML 요소를 지원해야 함, DAV 헤더에 기술되어 있는 2는 Class 2를 지원한다는 뜻

   - 위 예에서 DAV 헤더는 Class 1과 Class 2를 지원한다는 것을 의미
     + Public 헤더에는 서버에서 지원하는 모든 메서드가 기술
     + Allow 헤더는 보통 Public 헤더에 기술되어 있는 메서드 일부가 기술 (여기에는 해당 리소스(ch-publish.fm)에 허락된 메서드들만 기술)
     + DASL 헤더는 SEARCH 메서드에서 사용하는 질의 문법 형식이 기술 (이 예에서는 sql)
    
