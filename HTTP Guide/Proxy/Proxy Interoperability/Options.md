-----
### OPTIONS : 어떤 기능을 지원하는지 알아보기
-----
1. HTTP OPTIONS 메서드는 서버나 웹 서버의 특정 리소스가 어떤 기능을 지원하는지(예를 들면 지원하는 메서드) 클라이언트(혹은 프록시)가 알아볼 수 있게 해줌
<div align="center">
<img src="https://github.com/user-attachments/assets/05c1368f-6d6f-40a0-994d-9c2eabc576c4">
</div>

2. 서로 다른 기능 수준의 서버와 프록시가 더 쉽게 상호작용할 수 있도록 클라이언트는 OPTIONS를 이용해 서버 능력을 먼저 알아낼 수 있음
3. 만약 OPTIONS 요청이 URI가 다음과 같이 별표(*)라면, 요청은 서버 전체 능력에 대해 묻는 것
```
OPTIONS * HTTP/1.1
```

4. 만약, URI가 실제 리소스라면, OPTIONS 요청은 특정 리소스에 대해 가능한 기능들을 묻는 것
<div align="center">
<img src="https://github.com/user-attachments/assets/9883be3e-76e6-45a6-b957-59f2f2230649">
</div>

5. 성공한다면, OPTIONS 메서드는 서버에서 지원하거나 지정한 리소스에 대해 가능한 선택적 기능들을 서술하는 여러 헤더 필드를 포함한 200 OK 응답 반환
6. 하지만 HTTP/1.1이 명시한 헤더는 서버에 의해 (혹은 서버의 특정 리소스를 위해) 어떤 메서드가 지원되는지 서술하는 Allow 헤더 하나 뿐임
7. 더 많은 정보를 위해 OPTIONS는 선택적 응답 본문을 허용하지만, 이에 대해 정의된 것은 없음
