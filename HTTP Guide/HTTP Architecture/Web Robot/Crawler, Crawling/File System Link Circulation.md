-----
### 파일 시스템 링크 순환
-----
1. 파일 시스템의 심볼릭 링크는 사실상 아무것도 존재하지 않으면서도 끝없이 깊어지는 디렉토리 계층을 만들 수 있으므로, 매우 교묘한 종류의 순환을 유발할 수 있음
2. 심볼릭 링크 순환은 서버 관리자가 실수로 만들게 되는 것이 보통이지만, 때때로 웹 로봇을 함정에 빠뜨리기 위해 악의적으로 만들어짐
3. 예시) 두 파일 시스템
<div align="center">
<img src="https://github.com/user-attachments/assets/a241d183-894a-46d8-813f-dd318c4327b5">
</div>

   - 9-3a : subdir은 보통 디렉토리
   - 9-3b : subdir은 /을 가리키는 심볼릭 링크
   - 두 그림 모두 파일 /index.html은 파일 subdir/index.html을 가리키는 하이퍼링크를 담고 있음

4. 9-3a의 파일 시스템을 사용해, 웹 크롤러는 다음 동작 수행
   - GET ```http://www.foo.com/index.html``` : /index.html을 가져와서, subdir/index.html로 이어지는 링크 발견
   - GET ```http://wwww.foo.com/subdir/index.html``` : subdir/index.html을 가져와서, subdir/logo.gif로 이어지는 링크 발견
   - GET ```http://www.foo.com/subdir/logo.gif``` : subdir/logo.gif를 가져오고, 더 이상 링크가 없으므로 여기서 완료

5. 9-3b의 파일 시스템에서의 동작
   - GET ```http://www.foo.com/index.html``` : /index.html을 가져와서, subdir/index.html로 이어지는 링크 발견
   - GET ```http://wwww.foo.com/subdir/index.html``` : subdir/index.html을 가져오지만, index.html로 되돌아감
   - GET ```http://wwww.foo.com/subdir/subdir/index.html``` : subdir/subdir/index.html을 가져옴
   - GET ```http://wwww.foo.com/subdir/subdir/subdir/index.html``` : subdir/subdir/subdir/index.html을 가져옴

6. 9-3b의 문제는 subdir/이 /로 링크되어있으므로 순환되는 것이지만, URL이 달라보이므로 로봇은 URL만으로 문서가 같다는 것을 모름
7. 어떤 식으로든 루프 발견을 하지 못하면, URL 길이가 로봇이나 서버의 한계를 넘을 때까지 순환은 계속 반복
