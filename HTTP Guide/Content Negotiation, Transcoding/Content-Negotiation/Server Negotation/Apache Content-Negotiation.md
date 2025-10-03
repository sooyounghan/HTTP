-----
### 아파치의 내용 협상
-----
1. 아파치 웹 서버가 내용 협상을 지원하는 방법
   - 내용 협상은 웹 사이트 콘텐츠의 제공자에게 달려있으므로, 만약 색인 페이지를 여러 가지 버전으로 제공해주려고 한다면, 우선 콘텐츠 제공자가 각 버전에 해당하는 파일들을 아파치 서버에 적절한 디렉토리에 모두 넣어줘야 함
  
2. 두 가지 방법 중 하나의 방법으로 내용 협상 동작 가능
   - 웹 사이트 디렉토리에서, 배리언트(Variant)를 갖는 웹 사이트의 각 URI를 위한 type-map 파일을 만들며, 이 파일은 모든 배리언트와 그들 각각에 대응하는 내용 협상 헤더들을 나열
   - 아파치가 그 디렉토리에 대해 자동으로 type-map 파일을 생성하도록 하는 MultiViews 지시어 작동

3. type-map 파일 사용하기
   - 아파치 서버의 type-map 구조 : 이를 설정하기 위해서는, 서버 설정 파일에 type-map 파일들을 위한 파일 접미사를 명시한 핸들러 추가
```
AddHandler type-map .var
```
   - 이 줄은 .var 확장자를 가진 type-map 파일임을 의미
   - type-map 파일의 예
<div align="center">
<img src="https://github.com/user-attachments/assets/d0fbade0-4dd5-4193-b4ab-2abdc871412b">
</div>

   - 이 type-map 파일을 통해, 아파치 서버는 영어로 요청한 클라이언트에게는 joes-hardware.en.html 파일을, 프랑스어로 요청한 클라이언트에게는 joes-hardware.fr.de.html 파일을 보낼 수 있음
   - 품질 값 또한 지원됨

4. MultiViews 사용하기
   - 이를 사용하려면, access.conf 파일의 적절한 절(```<Directory>, <Location>, 혹은 <Files>```)에 Options 지시어를 이용해 웹 사이트를 포함한 디렉토리에 Multiviews를 반드시 작동시켜야 함
   - 만약, 켜져있고 브라우저가 joes-hardware라는 이름의 리소스를 요청했다면, 서버는 이름에 ```joes-hardware```가 들어 있는 모든 파일을 살펴보고, 그들에 대한 type-map 파일을 생성
   - 이름에 근거해서 서버는 각 파일에 대응하는 적절한 내용 협상 헤더를 추측
   
