-----
### MKCOL 메서드
-----
1. 클라이언트가 지정된 URL에 해당하는 콜렉션을 서버에 생성하게 하는 메서드
2. 콜렉션을 생성할 목적으로 PUT이나 POST 사용 : 클라이언트는 요청 안에 추가적인 정보(Semantic Glue)를 더해보는 식으로 프로토콜을 만들어야 함 (이렇게 사용할 수 있지만, 즉석으로 프로토콜을 정의하는 것은 번거롭고 오류를 발생시키기 쉬움)
3. 대부분 접근 메커니즘은 메서드 타입에 기반하여 동작 : 몇 가지 메서드만이 저장소에 있는 리소스를 생성하고 삭제할 수 있음 (만약 다른 메서드들을 본래 용도와 다르게 사용하면 접근 제어 메커니즘은 잘 동작하지 않을 것)
4. 요청과 응답의 예
<div align="center">
<img src="https://github.com/user-attachments/assets/a65ed46f-3261-4d16-9f0f-ab5ba40e6f49">
</div>

<div align="center">
<img src="https://github.com/user-attachments/assets/4b574414-0955-4fa6-a798-47d59a130cdd">
</div>

5. 단적인 예
   - 콜렉션이 이미 존재한다고 가정 : 만약 MKCOL /colA를 요청을 보냈지만, colA가 존재한다면, 그 요청은 405 Method Not Allow 상태 코드와 함께 실패
   - 쓰기 권한이 없다면, MKCOL 요청은 403 Forbidden 상태 코드와 함께 실패할 것
   - MKCOL /colA/colB 같은 요청을 보냈지만, colA가 존재하지 않으면 409 Conflict 상태 코드와 함께 실패

6. 일단 파일이나 콜렉션이 생성되면, DELETE 메서드로 지울 수 있음
