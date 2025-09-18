-----
### 메서드
-----
1. HTTP는 HTTP 메서드라고 불리는 여러 가지 종류의 요청 명령을 지원
2. 모든 HTTP 요청 메세지는 한 개의 메서드를 가지며, 메서드는 서버에게 어떤 동작을 취해져야하는지 말해줌(웹 페이지 가져오기, 게이트웨이 프로그램 실행하기, 파일 삭제하기 등)
3. 흔히 쓰이는 HTTP 메서드
<div align="center">
<img src="https://github.com/user-attachments/assets/8a556c50-e542-4f53-826b-d633cef865da">
</div>

-----
### 상태 코드
-----
1. 모든 HTTP 응답 메세지는 상태 코드와 함께 반환
2. 상태 코드는 클라이언트에게 요청이 성공했는지 아니면 추가 조치가 필요한지 알려주는 세 자리 숫자
3. 흔히 쓰이는 상태 코드
<div align="center">
<img src="https://github.com/user-attachments/assets/e821d916-0aec-433f-9d77-b4ccd18b110d">
</div>

4. HTTP는 각 숫자 상태 코드에 텍스트로 된 사유 구절(Reason Phrase)도 함께 보냄
   - 이 구문은 단지 설명만을 위해 포함된 것일 뿐 실제 응답 처리에는 숫자로 된 코드 사용

5. HTTP 소프트웨어는 열거된 상태 코드와 사유 구절을 모두 같은 것으로 취급
<div align="center">
<img src="https://github.com/user-attachments/assets/60447b3b-92b5-45e5-bb88-0328ce857f8b">
</div>
