-----
### Content-Language 헤더
-----
1. Content-Language 엔티티 헤더 필드는 엔티티가 어떤 언어 사용자를 대상으로 하고 있는지 서술
   - 만약 주로 프랑스어를 사용자로 대상으로 한다면, 다음을 포함
```
Content-Language: fr
```

2. Content-Language 헤더는 텍스트 문서만을 위한 것이 아닌, 오디오 클립, 동영상 그리고 애플리케이션도 특정 언어 사용자를 대상으로 할 수 있음
3. 특정 언어 사용자를 대상으로 하는 어떤 종류의 미디어라도 Content-Language 헤더를 가질 수 있음
4. 예시) 나바호(Navajo) 언어 사용자를 위한 태깅된 오디오 파일
<div align="center">
<img src="https://github.com/user-attachments/assets/2ca13b1a-b15d-4044-840e-6ed0836c366a">
</div>

5. 만약 콘텐츠가 여러 언어 사용자를 대상으로 하고 있다면, 여러 언어를 나열할 수 있음
```
Content-Language: mi, en
```

6. 그러나 단지 여러 언어가 하나의 엔티티에 동시에 사용됐다고 해서 반드시 여러 언어 사용자들을 대상으로 하고 있음을 의미하는 것이 아님
