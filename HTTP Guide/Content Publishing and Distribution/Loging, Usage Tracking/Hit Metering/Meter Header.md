-----
### Meter 헤더
-----
1. 적중 계량 확장은 Meter 라는 새로운 헤더 추가
2. Cache-Control 헤더에 다양한 캐시 지시자를 기술할 수 있듯이, 캐시나 서버에 Meter 헤더에 사용량이나 보고에 관한 지시자 기술 가능
3. Meter 헤더에 기술할 수 있는 지시자와 이를 보낼 수 있는 주체(서버 혹은 캐시) 기술
<div align="center">
<img src="https://github.com/user-attachments/assets/ca4ba093-4d28-4599-8ef7-9b69b114ffc5">
</div>

4. 실제 적중 계량의 예
<div align="center">
<img src="https://github.com/user-attachments/assets/c4cb4bce-c827-47e2-a69e-d3e0bbac2094">
</div>

   - 트랜잭션의 첫 부분은 클라잉너트와 프록시 캐시 간에 이루어지는 일반적인 HTTP 트랜잭션과 같지만, 프록시가 보내는 요청과 서버의 응답에 Meter 헤더가 추가로 기술
   - 여기서 프록시가 적중 계량을 할 수 있다고 서버에게 알리고, 서버는 프록시에 적중 횟수를 요구

5. 클라이언트 관점에서 요청은 여느 때와 같이 처리되고, 프록시는 서버에 속해있는 리소스를 추적하기 시작
   - 그 다음 프록시는 서버에 리소스에 대한 재검사를 함
   - 프록시는 서버로 보내는 조건적 요청에 추적하고자 하는 리소스 정보를 기술
  
