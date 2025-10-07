-----
### 유효기간과 나이
-----
1. 서버는 응답 본문과 함께 하는, HTTP/1.0+ Expires나 HTTP/1.1 Cache-Control: max-age 응답 헤더를 이용해 유효기간 명시
   - Expires와 Cache-Control: max-age 헤더는 기본적으로 같은 일을 하지만, 절대 시간은 컴퓨터의 시계가 올바르게 맞춰져 있을 것 요구
<div align="center">
<img src="https://github.com/user-attachments/assets/d1d33d05-7a89-4940-9bf6-7676e44821cf">
</div>

2. 예) 동부 표준시로 2002년 6월 29일 오전 9시 30분이라고 가정
   - 죠의 하드웨어 가게는 미국 독립기념일(7월 4일) 할인 판매를 할 준비가 되었다고 가정(딱 5일 간)
   - 죠는 특별한 웹 페이지를 운영하는 웹 서버에 그 페이지가 2002년 7월 5일에 만료되는 것을 보고 싶음
   - 옛날 방식의 Expires 헤더를 상요하면, 다음 헤더 포함
```
Expires: Fri, 05 Jul 2002, 05:00:00 GMT
```
   - 만약 죠의 서버가 새로운 Cache-Contorl: max-age 헤더를 사용한다면, 서버 응답 메세지는 다음 헤더 포함
```
Cache-Control: max-age=484200
```
   - 484200 : 2002년 6월 29일 오전 9시 30분부터 2002년 7월 5일 자정 사이의 시간을 초로 환산한 것


