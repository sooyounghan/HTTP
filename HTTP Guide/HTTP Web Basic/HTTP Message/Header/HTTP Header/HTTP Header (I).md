-----
### If-Modified-Since
-----
1. 조건부 요청을 보내기 위해 사용
2. 클라이언트는 이 헤더와 GET 메서드를 이용해 서버로부터 리소스를 요청할 수 있는데, 그 리소스가 클라이언트가 마지막으로 요청한 이후 변경이 있었는지 여부에 따라 응답이 달라짐
3. 만약 그 객체가 아직 변경되지 않았다면, 서버는 리소스를 보내지 않고 304 Not Modified로 응답할 것
4. 만약 객체가 수정되었다면, 서버는 비 조건부 GET 요청을 받았을 때 처럼 응답
<div align="center">
<img src="https://github.com/user-attachments/assets/4b70f429-9df1-4c7f-a025-6315173e87f5">
</div>

-----
### If-Match
-----
1. 조건적인 요청을 보내기 위해 사용
2. 이 요청은 날짜 대신 엔티티 태그를 사용
3. 서버는 If-Match 헤더에 들어있는 엔티티 태그를 리소스의 현재 엔티티 태그와 비교해 태그가 매치된다면, 리소스를 돌려줌
4. If-Match 값이 ```*```라면, 서버는 이를 요청받은 리소스의 모든 엔티티 태그와 매치되는 것으로 받아들여야 함 (```*``` : 서버가 그 리소스를 갖고 있지 않는 이상 언제나 매치)
5. 이 헤더는 클라이언트나 캐시가 이미 갖고 있는 리소스를 갱신할 때 유용
   - 그 리소스는 변경이 있을 때만 반호나되며, 이는 이전에 요청한 객체의 엔티티 태그가, 서버에 있는 현재 버전의 엔티티 태그와 매치되지 않는 것을 의미
<div align="center">
<img src="https://github.com/user-attachments/assets/bb4f840b-62a3-43b5-8575-fa7a48791a8c">
</div>

-----
### If-None-Match
-----
1. If 헤더들과 마찬가지로 요청을 조건적으로 만들기 위해 사용될 수 있음
2. 클라이언트는 엔티티 태그의 목록을 서버에게 공급하고, 서버는 그 태그들을 자신이 그 리소스에 대해 갖고 있는 엔티티 태그들과 비교해서, 아무것도 매치되지 않은 경우에만 반환
3. 이는 캐시에서 변경이 일어난 리소스만 갱신할 수 있도록 해줌
4. 이 헤더를 이용해서, 캐시는 갖고 있는 엔티티들을 무효화하고 응답으로 새 엔티티를 가져오는 일을 한 번에 할 수 있음
<div align="center">
<img src="https://github.com/user-attachments/assets/9d3345dd-17f9-464c-8d88-31d3a63b62ab">
</div>

-----
### If-Range
-----
: 요청을 조건적으로 만들기 위해 사용 가능
<div align="center">
<img src="https://github.com/user-attachments/assets/828a4dde-e4f7-4615-8583-9972ba866fa3">
</div>

-----
### If-Unmodified-Range
-----
1. If-Modified-Since 헤더의 쌍둥이로서, 요청에 이 헤더를 포함시키는 것은 요청을 조건적으로 만듬
2. 서버는 이 헤더의 날짜 값을 보고 그 날짜 이후 변경이 없을 때에만 그 객체를 반환
<div align="center">
<img src="https://github.com/user-attachments/assets/0b9ee5ed-45ac-4acc-81af-9a12afd1d3ae">
</div>
