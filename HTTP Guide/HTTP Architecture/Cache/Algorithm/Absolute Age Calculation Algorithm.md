-----
### 완전한 나이 계산 알고리즘
-----
1. 이 응답이 캐시에 한 번 저장되면, 나이를 더 먹게 됨
2. 문서에 대한 요청이 캐시에 도착했을 때, 그 문서의 현재 나이를 계산하기 위해 그 문서가 캐시에 얼마나 오래 머물렀는지 알 필요가 있음
3. HTTP/1.1 나이 계산 알고리즘
<div align="center">
<img src="https://github.com/user-attachments/assets/56a32018-91d7-452e-bb81-dba0baf4ec0a">
</div>

   - 언제 문서가 도착했는지($응답을_받은_시각), 언제 현재 요청이 도착했는지(지금)
   - 따라서, 체류 시간은 둘의 차와 같음
<div align="center">
<img src="https://github.com/user-attachments/assets/f877ad8e-a5c1-4291-b152-35f49df9b4b5">
</div>

