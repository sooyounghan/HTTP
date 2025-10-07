-----
### 상대 URL
-----
1. URL은 상대 URL과 절대 URL로 구분
   - 절대 URL은 리소스를 접근하는데 필요한 모든 정보를 가지고 있음
   - 상대 URL은 모든 정보를 담고 있지 않으며, 상대 URL로 리소스를 접근하는데 필요한 모든 접오를 얻기 위해 기저(Base)라고 하는 다른 URL를 사용해야 함

2. 상대 URL은 URL를 짧게 표기하는 방식
3. 예시
<div align="center">
<img src="https://github.com/user-attachments/assets/7f2812e6-9041-4048-bcd3-db126a265e4e">
</div>

  - ```http://www.joes-hardware.com/tools.html```가 가리키는 리소스인 HTML 문서의 내용
  - 해당 HTML 문서에는 ```./hammers.html``` URL을 가리키는 하이퍼링크가 있음
  - 이 URL은 미완성처럼 보이지만, 올바른 문법의 상대 URL
    + 이는 문서의 URL를 기준으로 상대경로로 해석될 수 있음
    + ```./tool.html``` 리소스를 기준으로 상대 경로 명시

4. 상대 URL 문법에 따르면, HTML 작성자는 URL에 스킴과 호스트 그리고 다른 컴포넌트들을 모두 입력하지 않아도 됨
   - 그 정보는 컴포넌트가 포함된 리소스의 기저 URL에서 알아낼 수 있으며, 다른 리소스에 대한 URL 역시 상대 URL로 기술할 수 있음
   - 위 예의 기저 URL
<div align="center">
<img src="https://github.com/user-attachments/assets/929fca45-0041-4cc1-a54c-acebc5537fb5">
</div>

   - 이 URL을 기저 URL로 사용하며, 상대 URL에서는 기술하지 않은 정보를 추측할 수 있음
   - 필요한 리소스가 ```./hammers.html```이라는 것을 알지만 스킴이나 호스트는 모름
   - 기저 URL을 사용하면 스킴은 http이고, 호스트는 ```www.joes-hardware.com```임을 추측 가능
<div align="center">
<img src="https://github.com/user-attachments/assets/b672286b-b1a7-4b3d-af5b-e220990bc541">
</div>

5. 상대 URL은 프래그먼트이거나 URL 일부
   - URL을 처리하는 브라우저 같은 애플리케이션은 상대 URL과 절대 URL 간에 상호 변환을 할 수 있어야함

6. 상대 URL을 사용하면 리소스 집합(HTML 페이지와 같은)을 쉽게 변경 가능
   - 문서 집합의 위치를 변경하더라도, 새로운 기저 URL에 의해 해석될 것이므로 위치를 변경해도 잘 동작
   - 이는 마치 다른 서버에 있는 콘텐츠를 미러링할 수 있게 허용하는 것과 유사

7. 변환 과정
   - 기저 URL : 변환 과정의 첫 단계로, 기저 URL를 찾는 것임 (기저 URL은 상대 URL의 기준이 되고, 몇 가지 방법 존재)
   - 리소스에서 명시적으로 제공 : 어떤 리소스들은 기저 URL을 명확하게 기술하기도 함 (예) HTML 문서에서는 그 안에 있는 모든 상대 URL을 변경하기 위해 기저 URL을 가리키는 ```<BASE> HTML``` 태그 기술 가능
   - 리소스를 포함하고 있는 기저 URL : 만약 상대 URL이 기저 URL이 명시되지 않은 리소스에 포함된 경우, 해당 리소스의 URL을 기저 URL로 사용 가능
   - 기저 URL이 없는 경우 : 절대 URL로만 이루어져 있다는 뜻이거나 불완전하거나 깨진 URL일 수 있음
   - 상대 참조 해석하기
     + 상대 URL을 절대 URL로 변환하기 위한 다음 단계는 상대 URL과 기저 URL을 각 컴포넌트 조각으로 나누는 것
     + 이는 URL을 파싱하는 것에 불과하지만, 컴포넌트 단위로 분리한다는 점에서 URL 분해하기 작업이라고도 불림
     + 기저 URL과 상대 URL을 컴포넌트로 분해하고 나면, 변환을 위한 다음 알고리즘 사용 가능
<div align="center">
<img src="https://github.com/user-attachments/assets/ee9e17d0-d629-4422-9ad7-bba0076a6303">
</div>

   - 이 알고리즘은 상대 URL을 리소스를 참조하는데 사용할 수 있는 절대 경로 형태로 변환 (RFC 1808에 최초 기술, RFC 2396에 포함)
   - ./hammers.html의 경우
     + 경로는 ./hammers.html, 기저 URL은 ```http://www.joes-hardware.com/tools.html```
     + 스킴은 비어 있으며, 도표의 왼쪽을 따라 내려가면, 알고리즘에 따라 기저 URL의 스킴을 상속받음(HTTP)
     + 적어도 한 개의 컴포넌트는 비어 있지 않으므로, 아래로 내려가 호스트와 포트 컴포넌트를 상속받음
     + 상대 URL(경로 : ./hammers.html) 컴포넌트와 상속받은 컴포넌트를(스킴 : http, 호스트 : ```www.joes-hardware.com/tools.html```, 포트 : 80)를 합치면, 새로운 절대 URL인 ```http://www.joes-hardware.com/hammers.html```를 얻음
