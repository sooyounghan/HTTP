-----
### ETag
-----
1. 메세지에 담겨있는 엔티티를 위한 엔티티 태그 제공
2. 기본적으로 엔티티 태그는 리소스를 식별할 수 있는 수단
<div align="center">
<img src="https://github.com/user-attachments/assets/bd9f8a49-0bb6-4782-835f-fd5fab70ed22">
</div>

-----
### Expect
-----
1. 서버에게 어떻게 동작하기를 기대하고 있는지 알려주기 위해 클라이언트가 사용
2. 이 헤더는 현재 응답 코드 100 Continue와 깊이 관련 있음
3. 만약, 서버가 Expect 헤더의 값을 이해하지 못한다면 417 Expectation Failed 상태 코드로 응답
<div align="center">
<img src="https://github.com/user-attachments/assets/f14715d9-8e9d-46f1-8ac0-1dd6e8e52a54">
</div>

-----
### Expires
-----
1. 응답이 더 이상 유효하지 않게 되는 일시를 알려줌
2. 이 헤더는 클라이언트(사용하는 웹 브라우저와 같은)가 사본을 캐시할 수 있게 해주며, 클라이언트는 그 일시가 만료되기 전까지 서버에게 캐시된 사본이 여전히 유효한지 물어보지 않아도 됨
<div align="center">
<img src="https://github.com/user-attachments/assets/b3f73b4c-b106-4248-8132-84c28ae20fc2">
</div>
