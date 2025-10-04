-----
### DELETE 메서드
-----
1. 디렉토리를 지우려고 한다면, Depth 헤더가 필요할 것
2. Depth 헤더가 기술되어 있지 않다면, DELETE 메서드는 Depth 헤더가 무한으로 설정되어 있다고 가정하여, 디렉토리와 그 하위에 있는 모든 디렉토리가 지워짐
3. 응답 역시 지워진 콜렉션을 가리키는 Content-Location 헤더를 포함
4. 요청과 응답의 예
<div align="center">
<img src="https://github.com/user-attachments/assets/d2ffcaaf-a1e2-4f5c-8bbf-95f0ae1b6fc8">
</div>

<div align="center">
<img src="https://github.com/user-attachments/assets/c81cfe3f-1215-421a-abc1-498740e31b2b">
</div>


   - 이 트랜잭션에서 ```<status>``` XML 요소에는 다른 사용자에 ch-publish.fm을 잠갔음을 가리키는 423 Locked 상태 코드 기술
