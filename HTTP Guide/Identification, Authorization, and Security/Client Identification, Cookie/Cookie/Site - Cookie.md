-----
### 사이트마다 각기 다른 쿠키들
-----
1. 브라우저는 수백 수천 개의 쿠키를 가질 수 있지만, 브라우저는 쿠키 전부를 모든 사이트에 보내지 않음
2. 브라우저는 보통 각 사이트에 두 개 혹은 세 개의 쿠키만을 보냄
   - 쿠키를 모두 전달하면 성능이 크게 저하되므로, 쿠키를 모두 전달하면 브라우저는 실제 콘텐츠의 바이트보다 더 많은 쿠키를 전달하게 될 것
   - 이 쿠키들 대부분은 서버에 특화된 이름/값 쌍을 포함하므로, 대부분 사이트에서는 인식하지 못하는 무의미한 값
   - 모든 사이트에 쿠키 전체를 전달하는 것은, 특정 사이트에서 제공한 정보를 신뢰하지 않는 사이트에서 가져갈 수 있으므로, 잠재적 개인정보 문제 발생 가능

3. 보통 브라우저는 쿠키를 생성한 서버에게만 쿠키에 담긴 정보를 전달
   - ```joes-hardware.com```에서 생성된 쿠키는 ```joes-hardware.com```에만 보내고, ```bobs-books.com```이나 ```marys-movie.com```에는 보내지 않음

4. 많은 웹 사이트들은 광고를 관리하는 협력업체와 계약하는데, 이 광고들은 웹 사이트 자체의 일부인 것 처럼 제작되고, 지속 쿠키를 만들어냄
   - 같은 광고사에서 제공하는 서로 다른 웹 사이트에 사용자가 방문하면, 브라우저는 앞서 만든 지속 쿠키를 다시 광고사 서버에 전송 (지속 쿠키 도메인이 동일하기 때문임)
   - 광고사는 이 기술에 Referer 헤더를 접목해 사용자의 프로필과 웹 사이트를 사용하는 습관에 대한 방대한 데이터 구축 가능

5. 쿠키 Domain 속성
   - 서버는 쿠키를 생성할 때 Set-Cookie 응답 헤더에 Domain 속성을 기술해서 어떤 사이트가 쿠키를 읽을 수 있는지 제어 가능
   - 예) 다음 HTTP 응답 헤더는 브라우저가 user=mary17이라는 쿠키를 ```.alrtavebargain.com``` 도메인을 가지고 이쓴 모든 사이트에 전달
<div align="center">
<img src="https://github.com/user-attachments/assets/0af1a49b-b8f1-4fbb-9066-cdd17730a2ef">
</div>

   - 만약 사용자가 ```www.alrtavebargain.com``` 또는 ```specials.alrtavebargain.com``` 같이 ```.alrtavebargain.com``` 으로 끝나는 사이트를 방문하면 다음 Cookie 헤더가 항상 적용
```
Cookie: user="mary17"
```

6. 쿠키 Path  속성
   - 웹 사이트 일부에만 쿠키 적용이 가능
   - URL 경로의 앞부분을 가리키는 Path 속성을 기술해 해당 경로에 속하는 페이지에만 쿠키 전달 가능
   - 예) 각 쿠키를 별도로 가지는 두 개의 조직이 한 개의 웹 서버를 공유한다고 가정 : ```www.alrtavebargain.com``` 사이트는 자동차를 대여하는 페이지인 ```http://www.alrtavebargain.com/autos/```에서 사용자가 좋아하는 자동차 크기를 기록하려고 쿠키 사용
<div align="center">
<img src="https://github.com/user-attachments/assets/f06e8b8e-dc29-41e3-a35f-cea0cd1c1c79">
</div>

   - 만약 사용자가 ```http://www.alrtavebargain.com/autos/cheapo/index.html```로 접근하면 두 가지 쿠키를 받게 됨
<div align="center">
<img src="https://github.com/user-attachments/assets/cf44bcce-323f-4b03-98f2-f90488698cf6">
</div>

   - 따라서 쿠키는 일종의 상태 정보라고 볼 수 있으며, 서버가 생성하여 클라이언트에 전달하고, 클라이언트는 그 쿠키를 유효한 사이트에만 다시 전달하고 관리
