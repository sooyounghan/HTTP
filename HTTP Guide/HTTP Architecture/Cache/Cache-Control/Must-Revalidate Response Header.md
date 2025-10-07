-----
### Must-Revalidate 응답 헤더
-----
1. 캐시는 성능을 개선하기 위해 신선하지 않은(만료된) 객체를 제공하도록 설정될 수 있음
2. 만약 캐시가 만료 정보를 엄격히 따르길 원한다면, 원 서버는 다음과 같은 Cache-Control을 붙일 수 있음
<div align="center">
<img src="https://github.com/user-attachments/assets/c09e68e4-9810-4f58-b664-8b43b54dcc9e">
</div>

3. Cache-Control: must-revalidate 응답 헤더는 캐시가 이 객체의 신선하지 않은 사본을 원 서버와의 최초 재검사 없이는 제공해서는 안 됨 의미
4. 캐시는 자유롭게 신선한 사본을 제공할 수 있으며, 만약 캐시가 must-revalidate 신선도 검사를 했을 때 원 서버가 사용할 수 없는 상태라면, 캐시는 반드시 504 Gateway Timeout Error를 반환해야 함
