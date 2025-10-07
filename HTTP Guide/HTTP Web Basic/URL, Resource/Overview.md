-----
### 인터넷의 리소스 탐색하기
-----
1. URL은 브라우저가 정보를 찾는데 필요한 리소스 위치를 가리키며, URL를 이용해 사람과 애플리케이션이 인터넷 상 수십억 개 리소스를 찾고 사용하며 공유할 수 있음
2. 그리고 URL을 통해 HTTP 및 다른 프로토콜을 통해 접근할 수 있음
3. 사용자는 브라우저에 URL를 입력하고 브라우저는 화면 뒤에서 사용자가 원하는 리소스를 얻기 위해 적절한 프로토콜을 사용해 메세지 전송
4. URL은 통합 자원 식별자(URI, Uniform Resource Identifier)라고 불리는 더 일반화된 부류의 부분집합
   - URI는 두 가지 주요 부분집합인 URL과 URN로 구성된 종합적 개념
   - URN은 현재 그 리소스가 어디에 존재하든 상관없이 그 이름만으로 리소스를 식별하는데 비해 URL은 리소스가 어디있는지 설명해서 리소스 식별

5. HTTP 명세에서는 URI를 더 일반화된 개념의 리소스 식별자로 사용
6. 실제로 HTTP 애플리케이션은 URL을 URI의 한 부분으로 취급
7. 예) ```http://www.joes-hardware.com/seasonal/index-fall.html```이라는 URL을 불러오고 싶다고 가정
   - URL의 첫 부분인 http : URL의 스킴(Scheme)으로, 스킴은 웹 클라이언트가 리소스에 어떻게 접근하는지 알려줌 (이 경우에는, URL이 HTTP 프로토콜 사용)
   - URL의 두 번째 부분인 ```www.joes-hardware.com``` : 서버의 위치로 웹 클라이언트가 리소스가 어디에 호스팅 되어 있는지 알려줌
   - URL의 세 번째 부분인 /seasonal/index-fall.html : 리소스의 경로로, 경로는 서버에 존재하는 로컬 리소스들 중 요청받은 리소스가 무엇인지 알려줌
<div align="center">
<img src="https://github.com/user-attachments/assets/0c2e52db-229b-4ae1-afe6-5abbacab743a">
</div>

   - URL은 HTTP 프로토콜이 아닌 다른 가용한 프로토콜을 사용할 수 있음
```
mailto:presiden@whitehouse.gov
```
   - 이는 메일 주소를 가리킴
```
ftp://ftp.lots-o-books.com/pub/complete-price-list.xls
```
   - 이는 FTP(File Transfer Protocol) 서버에 올라가 있는 파일을 가리킴
```
rtsp://www.joes-hardware.com:554/interview/cto_video
```
   - 이는 스트링을 제공하기 위해 비디오 서버에 호스팅하고 있는 영화를 가리킴
   - 이처럼 URL은 인터넷에 있는 어떤 리소스든지 가리킬 수 있음

8. URL을 상요하면 리소스를 일관된 방식으로 지정 가능
    - 대부분의 URL은 동일하게 ```스킴://서버위치/경로``` 구조로 이루어져 있음
    - 인터넷 상 모든 리소스를 가리키고 가져오기 위해, 모든 사람이 같은 방식으로 이름을 써서 리소스를 찾을 수 있도록, 단일 방식의 작명 규칙을 가진 것
      
