-----
### 콘텐츠 인코딩 유형
-----
1. HTML는 몇 가지 표준 콘텐츠 인코딩 유형을 정의하고, 확장 인코딩으로 추가하는 것도 허용
2. 인코딩은 각 콘텐츠 인코딩 알고리즘에 고유한 토큰을 할당하는 IANA를 통해 표준화
3. Content-Encoding 헤더는 이러한 표준화 된 토큰 값을 이용해, 인코딩에 사용된 알고리즘에 대해 기술
4. 몇 가지 흔히 쓰이는 콘텐츠 인코딩 토큰
<div align="center">
<img src="https://github.com/user-attachments/assets/0684ec36-95cb-4f20-975d-28dcd0abebd5">
</div>

5. gzip, compress, deflate 인코딩은 전송되는 메ㅔ지의 크기를 정보의 손실 없이 줄이기 위한 무손실 압축 알고리즘
6. gzip은 일반적으로 가장 효율적이고 가장 널리 쓰이는 압축 알고리즘
