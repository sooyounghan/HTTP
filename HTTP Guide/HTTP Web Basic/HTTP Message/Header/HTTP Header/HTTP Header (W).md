-----
### Warning
-----
1. 요청 중 어떤 일이 일어났는지에 대해 정보를 좀 더 주기 위해 사용
2. 이 헤더는 상태 코드나 사유 구절을 통해 전할 수 없는 추가 정보를 보낼 수 있는 수단을 서버에게 제공
3. HTTP/1.1에 정의된 몇 가지 경고 코드
   - 101 Response is Stale : 응답 메세지가 신선하지 않다고 알고 있으면(원 서버가 재검사를 할 수 없는 상황 등) 반드시 이 경고 메세지 포함
   - 111 Revalidation Failed : 만약 캐시가 원 서버와 함께 응답의 재검사를 시도했으나, 만약 캐시가 원 서버에 접근할 수 없었기 때문에 그 결과가 실패라면, 이 경고는 클라이언트에 대한 응답에 반드시 포함
   - 112 Disconnected Operation : 정보성 경고, 네트워크에 접근이 제거된 경우 사용해야 함
   - 113 Heuristic Expiration : 캐시가 경험적으로 선택한 신선도 수명이 24시간 보다 크면서, 응답의 나이 역시 24시간 보다 크다면 반드시 응답에 이 경고를 포함해야 함
   - 199 Miscellaneous Warning : 이 경고를 받은 시스템은 이 경고에 대해 어떠한 자동화된 대응도 절대로 해서는 안 되며, 메세지는 사용자를 위한 추가 정보와 함께 본문을 포함할 수 있어야 함
   - 214 Transform Applied : 프록시와 같은 중개자가 응답의 콘텐츠 인코딩에 변화를 줄만한 어떠한 변형 작업을 수행했다면, 반드시 추가
   - 299 Miscellaneous Persistent Warning : 이 경고를 받은 시스템은 이 경고에 대해 어떠한 자동화된 대응도 절대로 해서는 안 되며, 이 메세지는 사용자를 위한 추가 정보와 함께 본문 포함 가능
<div align="center">
<img src="https://github.com/user-attachments/assets/bef79ece-2bc4-4917-9a12-33e4c3539e0a">
</div>

-----
### WWW-Authenticate
-----
: 클라이언트에 대해 인증 스킴을 이용한 인증 요구를 하기 위해 401 Unauthorized 응답에서 사용
<div align="center">
<img src="https://github.com/user-attachments/assets/50972f27-bbb8-4722-98fe-63b10542ec1a">
</div>
