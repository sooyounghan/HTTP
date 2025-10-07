-----
### Max-Forwards
-----
1. 이 헤더는 요청이 지나가는 프록시 혹은 다른 중개자들의 개수를 제한하기 위해 목적으로 오직 TRACE 메서드에 의해 사용
2. 이 헤더와 함께 TRACE 요청을 받는 각 애플리케이션은 이 요청을 전달하기 전 이 헤더의 값을 줄여야 함
3. 애플리케이션이 요청을 받았을 때, 이 값이 0이라면 원본 요청을 포함한 엔티티 본문과 함께 200 OK 응답을 반환해야 함
4. 만약 TRACE 요청에서 Max-Forwards 헤더가 빠져있다면, 전달 횟수에 제한이 없다고 가정
5. 그 외 HTTP 메서드에서는 이 헤더는 무시되어야 함
<div align="center">
<img src="https://github.com/user-attachments/assets/a9a57bef-4d88-4fae-888f-71f7df8a835e">
</div>

-----
### MIME-Version
-----
1. 몇몇 HTTP 서버는 MIME 명세상으로 올바른 메세지를 생성하는데, 이런 경우 MIME 버전 헤더가 서버에 의해 제공될 수 있음
2. 이 헤더는 HTT[/1.0 명세에서는 공식 명세의 일부였던 적은 없음
<div align="center">
<img src="https://github.com/user-attachments/assets/c8050695-dc0c-4421-9886-5a068c841fc9">
</div>
