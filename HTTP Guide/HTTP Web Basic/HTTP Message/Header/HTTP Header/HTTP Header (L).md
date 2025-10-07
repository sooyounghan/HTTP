-----
### Last-Modified
-----
1. 그 엔티티가 마지막으로 변경된 시간에 대한 정보를 제공하고자 시도
2. 예를 들어, 리소스는 서버에 존재하는 파일인 경우가 흔하므로, Last-Modified 값은 서버의 파일 시스템이 제공해 준 최근 변경시각일 수 있음
   - 한 편, 스크립트에 의해 생성된 것과 같이 동적으로 생성된 리소스라면 Last-Modified 값은 응답이 만들어진 시간일 수 있음

3. 서버들은 Last-Modified 시간이 미래가 되지 않도록 신경써야 함
4. 만약 그 값이 보내려고 하는 Date 헤더 값 보다 이후라면 HTTP/1.1 서버는 Last-Modified 시간을 리셋해야 함
<div align="center">
<img src="https://github.com/user-attachments/assets/976bb2ba-7846-46d5-9e10-e5c794a4ce69">
</div>

-----
### Location
-----
: 요청한 리소스가 새로운 위치로 옮겨졌거나 아니면 요청으로 인해 리소스가 새로 만들어진 경우, 그 위치로 클라이언트를 보내기 위해 서버에 의해 사용
<div align="center">
<img src="https://github.com/user-attachments/assets/085bf861-d6d7-4b6a-ad0e-0f50fec6cf1d">
</div>

