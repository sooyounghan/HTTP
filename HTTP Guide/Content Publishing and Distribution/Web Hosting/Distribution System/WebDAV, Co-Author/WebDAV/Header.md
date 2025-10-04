-----
### WebDAV 헤더
-----
1. WebDAV는 새로운 메서드들의 기능을 더 넓혀주는 여러 HTTP 헤더 도입
2. DAV : WebDAV를 제공하는 서버와 통신할 때 사용
   - WebDAV에서 지원하는 모든 리소스는 OPTIONS 요청에 대한 응답에 이 헤더를 포함시켜야 함
<div align="center">
<img src="https://github.com/user-attachments/assets/820cd4f0-5ba8-45da-a5fc-87d994f8d200">
</div>

3. Depth : 여러 수준의 계층 구조로 분류된 리소스에 WebDAV를 사용하기 위한 중요한 요소
<div align="center">
<img src="https://github.com/user-attachments/assets/fedf554d-8f0d-46d8-bd63-107248bce415">
</div>

   - file_1.html과 file_2.html가 있는 DIR_A 디렉토리가 존재
     + Depth: 0이면, 메서드는 DIR_A 디렉토리만 제공
     + Depth: 1이면, DIR_A와 그 안의 file_1.html, file_2.html 모두 제공
   - Depth 헤더는 WebDAV가 정의하고 있는 여러 메서드를 수정 (Depth 헤더를 사용하는 메서드 : LOCK, COPY, MOVE)

4. Destination : COPY나 MOVE 메서드가 목적지 URI를 식별하는데 쓰임
<div align="center">
<img src="https://github.com/user-attachments/assets/719bd97b-e753-43d4-aebd-852ee4cc0c53">
</div>

5. If : 정의되어 있는 상태 토큰은 lock 토큰 뿐인데, If 헤더는 조건 집합을 정의
   - 만약 그 조건들에 모두 맞지 않으면 요청은 실패
   - COPY나 PUT 같은 메서드는 If 헤더에 전제 조건을 기술해서 적용하는데 필요한 조건을 명시
   - 실제로, 가장 흔하게 만족시켜야 하는 전제 조건은 잠금(lock)을 사전에 획득하는 것
<div align="center">
<img src="https://github.com/user-attachments/assets/5f8a5b6c-1035-44cb-9065-e4c7eea8e6e7">
</div>

6. Lock-Token : 제거되어야 할 잠금(lock)을 명시하는 용도로 UNLOCK 메서드에서 사용
   - LOCK 메서드에 대한 응답은 lock 토큰에 필요한 정보를 전달하는 Lock-Token 헤더를 포함
<div align="center">
<img src="https://github.com/user-attachments/assets/b5c10969-016a-46c7-ad51-5dd5bb08f422">
</div>

7. Overwrite : 대상을 덮어쓸 것인지 아닌지 기술하는데 사용
   - COPY나 MOVE 메서드에서 사용
<div align="center">
<img src="https://github.com/user-attachments/assets/4d3c07b9-5b23-47c3-ba23-dd81417c2c39">
</div>

8. Timeout : 클라이언트가 필요한 잠금 타임아웃 값을 기술하는데 사용하는 요청 헤더
<div align="center">
<img src="https://github.com/user-attachments/assets/c9d01a34-e552-49b3-9682-7ab411c3b191">
</div>

