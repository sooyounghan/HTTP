-----
### PROPFIND 메서드
-----
1. PROPFIND(Propery Find, 속성 찾기) 메서드는 주어진 파일이나 파일 그룹(콜렉션이라고도 부름)의 속성을 읽는 데 사용
2. 세 가지 형식 동작 지원
   - 모든 속성과 그 값 요청
   - 선택된 속성과 그 값의 집합 요청
   - 모든 속성 이름 요청
   - 예시
<div align="center">
<img src="https://github.com/user-attachments/assets/f679b617-9fae-4c5f-9025-646c423a308a">
</div>

   - ```<propfind>``` 요청 요소는 PROPFIND 메서드로부터 반환될 속성들을 기술

3. PROPFIND 요청과 함께 사용되는 몇몇 XML 요소
   - ```<allprop>``` : 반환될 모든 속성의 이름과 값을 기술
     + 모든 속성과 그들의 값을 요청하기 위해 WebDAV 클라이언트는 ```<propfind>``` 요소의 자식 요소로 ```<allprop>``` XML 요소를 보내거나, 본문 없이 요청을 보냄

   - ```<propname>``` : 반환될 속성 이름의 집합 기술
   - ```<prop>``` : ```<propfind>```의 하위 요소로, 반환될 값의 속성 기술
   - PROPFIND 요청에 대한 응답의 예
<div align="center">
<img src="https://github.com/user-attachments/assets/6db29b25-84ca-4a71-b4fb-2a45c9e0a94a">
</div>

   - 이 예에서 서버는 207 Multi-Status 코드로 응답
   - WebDAV는 동시에 여러 리소스를 다루고 각 리소스에 대해 다른 응답을 하는 몇몇 다른 WebDAV 메서드들과 PROPFIND에 대해 207 응답을 사용

4. 응답에 있는 XML 요소
   - ```<multistatus>``` : 여러 응답을 담는 컨테이너
   - ```<href>``` : 리소스의 URI를 가리킴
   - ```<status>``` : 특정 요청에 대한 HTTP 상태 코드 기술
   - ```<prostat>``` : ```<status>``` 요소 한 개와 ```<prop>``` 요소 한 개로 이루어져 있는 집합으로, ```<prop>``` 요소는 리소스에 대한 속성의 이름 / 값 쌍을 한 개 이상 포함

5. 위 기술한 응답의 예는, ```http://minstar/ch-publish.fm```에 대한 응답
   - ```<propstat>``` 요소는 ```<status>``` 요소 한 개와 ```<prop>``` 요소 한 개를 포함
   - 서버는 해당 URI에 대한 응답인 200 OK를 ```<status>``` 요소에 기술해서 반환
   - ```<prop>``` 요소는 여러 개의 하위 요소를 포함하여, 그 일부만 기술한 것

6. 활용의 한 가지 예 : 디렉토리 목록을 얻는 것
   - 호출 한 번으로 목록의 계층 관계 전체와 그 안에 있는 개별 엔티티의 모든 속성까지 읽어올 수 있음
