-----
### 질의 문자열
-----
1. 데이터베이스 같은 서비스들은 요청받을 리소스 형식의 범위를 줄이기 위해 질문이나 질의를 받을 수 있음
2. 예시
<div align="center">
<img src="https://github.com/user-attachments/assets/6e9fd35b-4ac3-44fd-bda9-550bb1f6aefe">
</div>

   - 물음표(?) 우측에 있는 값들을 질의 컴포넌트라고 부름

2. URL의 질의 컴포넌트는 게이트웨이를 가리키는 URL 경로 컴포넌트와 함께 전달
   - 보통 게이트웨이는, 다른 애플리케이션에 접근하려고 할 때 거치는 통로라고 할 수 있음
3. 죠의 컴퓨터 가게에 재고 확인을 하기 위해 게이트웨이 서버로 전달하는 질의 컴포넌트 예 (제품번호 12731, 큰(Large) 치수에, 파란색인 물품 재고 확인)
<div align="center">
<img src="https://github.com/user-attachments/assets/96da99aa-6de7-4f17-8878-a436de94fd0c">
</div>

4. 질의 컴포넌트에는 특정 문자들을 제외하고는 제약사항이 없음 : 편의상 많은 게이트웨이가 &로 나뉜 이름=값 쌍의 형식의 질의 문자열을 원함
<div align="center">
<img src="https://github.com/user-attachments/assets/eb76effb-825d-4b8d-94a3-3e816653b76f">
</div>

   - 이 예에서는 이름과 값의 쌍으로 된 두 개의 질의 컴포넌트가 존재 (item=12731, color=blue)
