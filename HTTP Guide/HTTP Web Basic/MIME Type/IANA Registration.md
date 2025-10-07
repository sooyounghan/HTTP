-----
### MIME 타입 IANA 등록
-----
1. MIME 미디어 타입 등록 절차는 RFC 2048에 설명
2. 등록 절차 목적은 새로운 미디어 타입 등록을 쉽게 해줄 뿐 아니라, 그 미디어 타입이 다른 문제가 없는지 검사
3. 등록 트리
   - MIME 타입 토큰은 등록 트리라고 부르는 4개의 클래스로 나뉘며, 각 등록 규칙이 따로 존재
   - IETF, 벤더, 개인, 실험으로 이루어진 4개의 트리
<div align="center">
<img src="https://github.com/user-attachments/assets/2c51500d-1677-485a-a07d-3e8b0c73c33e">
</div>

4. 등록 절차 (RFC 2048)
   - 기본 등록 절차는 형식적 표준 절차라기보다 커뮤니티에서 새로운 타입에 특별한 문제가 없는지 정도를 검토하고, 너무 지연되지 않게 등록소에 저장하는 행정절차에 가까움
<div align="center">
<img src="https://github.com/user-attachments/assets/735233eb-6fd8-420b-90cb-cf00085f4645">
</div>

5. 등록 규칙
   - IANA는 지정된 등록이 승인되었다고, IESG에서 응답이 올 경우에만 IETE 트리에 미디어 타입 등록
   - 벤더 타입과 퍼스널 타입은 다음 조건들만 충족시키면 공식적 검토 없이 IANA에 의해 자동 등록될 것
<div align="center">
<img src="https://github.com/user-attachments/assets/82488f04-6728-4fc2-bfe1-ac4e187b880d">
</div>

6. 등록 견본
   - 실제 IANA 등록은 이메일로 이루어짐
   - 아래 예시의 견본을 이용해 등록 양식을 작성한 뒤 ```ietf-type@iana.org```로 메일을 보내면 됨
<div align="center">
<img src="https://github.com/user-attachments/assets/080efcf5-fe48-4244-9185-ea3e084459ec">
<img src="https://github.com/user-attachments/assets/d6909080-08f4-45f5-b3b1-0e7ea5bcba45">
</div>

7. MIME 미디어 타입 등록
   - 제출된 양식은 IANA 웹사이트에서 찾아볼 수 있음
   - MIME 미디어 타입 실제 데이터베이스는 ISI 웹 서버에 저장
   - 주요 타입과 서브 타입으로 이루어져 있는 미디어 타입들은 하나의 미디어 타입 당 하나의 파일로 디렉토리 트리에 저장
   - 각 파일은 양식에 맞춰 제출된 MIME 미디어 타입 등록 요청서를 포함
     + 다만 사람마다 조금씩 다르게 등록 견본을 작성하므로, 정보의 품질과 형식이 제출에 따라 다름
