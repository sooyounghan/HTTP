-----
### HTML 로봇 제어 META 태그
-----
1. robots.txt 파일은 사이트 관리자가 로봇들을 웹 사이트 일부 또는 전체에 접근할 수 없게 함
2. robots.txt 파일 단점 중 하나는 그 파일을 콘텐츠 작성자 개인이 아니라 웹 사이트 관리자가 소유한다는 것
3. HTML 페이지 저자는 로봇이 개별 페이지에 접근하는 것을 제한하는 좀 더 직접적인 방법을 가지고 있음
   - HTML 문서에 직접 로봇 제어 태그를 추가할 수 있으며, 로봇 제어 HTML 태그에 따르는 로봇들은 여전히 문서를 가져올 수 있겠지만, 로봇 차단 태그가 존재한다면 그 문서를 무시
   - 예를 들어, 터넷 검색 엔진 로봇은 그들의 검색 색인에 그 문서를 추가하지 않을 것
   - robots.txt 표준과 마찬가지로 따라는 것이 권장되지만 강제하지는 않음

4. 로봇 차단 태그는 HTML META 태그를 이용해 다음과 같이 구현
<div align="center">
<img src="https://github.com/user-attachments/assets/0f39d726-5de3-451c-a663-d709d76a8bb3">
</div>

   - 로봇 META 지시자 : 몇 가지 종류가 있으며, 시간이 지나면서 점차 검색엔진과 그들의 로봇이 활동과 기능 집합을 확장함에 따라 새 지시자가 추가될 가능성이 높음
   - 가장 널리 쓰이는 로봇 META 지시자 : NOINDEX, NOFOLLOW
   - NOINDEX : 로봇에게 이 페이지를 처리하지 말고 무시하라고 말해주는 것 (예) 이 페이지의 콘텐츠를 색이나 데이터베이스에 포함시키지 말것)
<div align="center">
<img src="https://github.com/user-attachments/assets/be1012f2-8642-4ea5-97bd-cf6f9e53551b">
</div>

   - NOFOLLOW : 로봇에게 이 페이지가 링크한 페이지를 크롤링하지 말라고 말해줌
<div align="center">
<img src="https://github.com/user-attachments/assets/7d938903-04c0-455b-a233-2756ab46f780">
</div>

   - INDEX : 로봇에게 이 페이지의 콘텐츠를 인덱싱해도 된다고 말해줌
   - FOLLOW : 로봇에게 이 페이지가 링크한 페이지를 크롤링해도 된다고 말해줌
   - NOARCHIVE : 로봇에게 이 페이지의 캐시를 위한 로컬 사본을 만들어서 안 된다고 말해줌
   - ALL : INDEX, FOLLOW와 동일
   - NONE : NOINDEX, NOFOLLOW와 동일

5. 로봇 META 태그는 다른 모든 HTML META와 마찬가지로 반드시 HTML 페이지 HEAD 섹션에 나타나야 함
<div align="center">
<img src="https://github.com/user-attachments/assets/f490ad9e-f59e-4934-977f-e3f432176cb7">
</div>

   - 이 태그에서 name과 content의 갑은 대소문자를 구분하지 않음
   - 다음처럼 지시들이 서로 충돌하거나 중복되게 해서는 안 됨
<div align="center">
<img src="https://github.com/user-attachments/assets/84a3b922-62a9-4dec-b2b4-1c88690dbf8c">
</div>

   - 이에 대한 동작은 정의되지 있지 않으므로, 틀림없이 로봇 구현에 따라 제각각일 것

6. 검색엔진 META 태그
   - 모든 로봇 META 태그는 name="robots" 속성을 포함
   - 추가 META 태그 지시자 (DESCRIPTION과 KEYWORDS META 태그는 콘텐츠의 색인을 만드는 검색 엔진 로봇들에 유용)
<div align="center">
<img src="https://github.com/user-attachments/assets/90309157-08f8-44c0-b4e3-224fc747bc56">
</div>
