-----
### Accept-Encoding 헤더
-----
1. 서버에서 클라이언트가 지원하지 않는 인코딩을 사용하는 것을 막기 위해, 클라이언트는 자신이 지원하는 인코딩 목록을 Accept-Encoding 요청 헤더를 통해 전달
2. 만약 HTTP 요청에 Accept-Encoding 헤더를 포함하지 않는다면, 서버는 클라이언트가 어떤 인코딩이든 받아들일 수 있는 것으로 간주(Accept-Encoding: *을 전달한 것과 같음)
3. HTTP 트랜잭션에서 Accept-Encoding을 사용하는 예
<div align="center">
<img src="https://github.com/user-attachments/assets/90086233-acbc-4c5c-840c-99494aa15b43">
</div>

4. Accept-Encoding 필드는 지원되는 인코딩들의 쉼표로 구분된 목록을 저장
<div align="center">
<img src="https://github.com/user-attachments/assets/38cefcb2-6b44-4d3d-b502-450070850795">
</div>

5. 클라이언트는 각 인코딩에 Q(Quality) 값을 매개변수로 더해 선호도를 나타낼 수 있음
   - Q 값의 범위가 가장 원치 않음을 의미하는 0.0에서 가장 선호함을 의미하는 1.0까지 존재
   - 토큰 ```*```는 그 외 모두를 의미

6. 어떤 콘텐츠 인코딩을 적용할 것인지 선택하는 과정은, 클라이언트에게 돌려줄 응답에 담길 콘텐츠를 결정하는 더 일반적인 과정의 일부
7. identity 인코딩 토큰은 오직 Accept-Encoding 헤더에만 존재할 수 있고, 클라이언트에 의해 다른 콘텐츠 인코딩 알고리즘에 대한 상대적 선호도를 정의하는 데 이용 가능

