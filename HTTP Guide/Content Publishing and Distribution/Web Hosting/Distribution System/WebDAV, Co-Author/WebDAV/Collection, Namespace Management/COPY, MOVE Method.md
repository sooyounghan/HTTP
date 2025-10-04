-----
### COPY와 MOVE 메서드
-----
1. COPY 메서드의 대안 : 리소스에 GET 요청을 보내고, 리소스를 다운받은 다음, PUT 요청과 함께 서버에 리소스를 다시 올리는 것
2. MOVE도 이와 유사한 방식의 대안이 존재
3. 하지만 이런 방식은 다단계 콜렉션에 대한 COPY, MOVE 작업에서는 확장이 쉽지 않음
4. COPY와 MOVE 메서드는 요청 URL을 원본의 위치 정보로 사용하고 목적지인 Destination HTTP 헤더의 값을 목적지 정보로 사용
   - MOVE 메서드는 COPY 메서드에 이어 몇 가지 추가 작업 수행
   - 그 작업은 원본지 URL을 목적지에 복사하고, 새로 생성된 URI의 무결성을 검사하고, 원본을 지움
   - 요청과 응답의 예
<div align="center">
<img src="https://github.com/user-attachments/assets/5021584f-7f8b-4d20-8514-f9be0d9c8690">
</div>

<div align="center">
<img src="https://github.com/user-attachments/assets/aa105488-0a22-4a1b-a421-48eb356a899e">
</div>

5. COPY나 MOVE가 컬렉션을 처리할 때는 Depth 헤더의 영향을 받음
   - Depth 헤더가 없으면 무한대 깊이로 가정하고 수행(예) 기본적으로 원본 디렉토리 전체 복사 또는 이동)
   - 만약 Depth가 0으로 설정되면, 이 메서드는 단순히 해당 리소스에만 적용이 될 것
   - 콜렉션을 복사하거나 이동할 경우, 원본 속성과 같은 속성을 가지고 있는 콜렉션들만 목적지에 생성될 것이며, 내부 구성 요소는 복사나 이동되지 않음
   - Depth에 무한대(Infinity) 값을 기술하는 것은 MOVE 메서드에서만 할 수 있음

6. Overwrite 헤더의 영향
   - COPY나 MOVE 메서드도 Overwrite 헤더 사용 가능하며, 이 헤더는 T나 F로 설정 가능
   - T로 설정하였고 목적지가 존재 : COPY나 MOVE 작업을 수행하기 전 무한대 값을 가진 Depth와 함께 DELETE가 목적지 리소스에 수행될 것
   - 만약 F로 설정하였고, 목적지 리소스가 존재하면, 작업은 실패

7. COPY, MOVE의 속성
   - 콜렉션이나 요소를 복사하면, 기본적으로 그것들의 모든 속성도 복사
   - 하지만, 요청은 작업에 대한 추가 정보를 기술한 XML 본문을 포함할 수 있음
   - 여기에는 반드시 모든 속성이 성공적으로 복사되어야 한다고 기술하거나, 어떤 속성만 복사하려고 하는지 기술할 수 있음
   - 고려해야 할 두 가지 단적인 예
     + COPY나 MOVE를 CGI 프로그램이나 콘텐츠를 만들어내는 다른 스크립트로부터 생성된 페이지에 적용한다고 가정 : CGI에 의해 생성된 파일을 복사하고 이동하려면, 그 의미를 보존하기 위해 WebDAV는 해당 페이지를 생성했던 프로그램의 위치를 가리키는 src와 link XML 요소를 제공
     + COPY나 MOVE 메서드가 live 속성을 모두 복제할 수 없음 (예) CGI 프로그램) : 만약 cgi-bin 디렉토리로부터 복사되었다면, 더는 실행되지 않을 수 있음
       * COPY와 MOVE는 현재 WebDAV 명세에서는 최선의 노력 방식으로 처리하여, 모든 정적 속성들과 적절한 live 속성을 모두 복사

8. 잠긴 리소스와 COPY / MOVE
   - 리소스가 현재 잠겨있으면, COPY와 MOVE 모두 목적지로 잠겨있는 리소스를 이동 및 복사는 금지
   - 이 두 가지 모두, 현재 잠겨 있는 콜렉션 아래를 목적지로 하는 COPY나 MOVE가 수행될 경우, 복사 혹은 이동된 리소스도 잠기게 됨
   - 예시
<div align="center">
<img src="https://github.com/user-attachments/assets/78acbf26-f128-442a-baa8-753f80257f1d">
</div>

   - /publishing과 /archived가 이미 lock1과 lock2라는 서로 다른 잠금 상태에 있다고 가정
   - COPY 작업이 완료되면, /publishing은 lock1로 잠긴 상태를 그대로 유지, publishing-old는 lock2로 이미 잠겨져 있던 콜렉션 밑으로 옮겨진 덕에 lock2 잠금이 추가될 것
   - MOVE가 수행될 경우 publishing-old는 lock2 잠금에 추가될 것

9. MKCOL, DELTE, COPY, MOVE 메서드 요청에 대한 응답으로 올 수 있는 상태 코드
<div align="center">
<img src="https://github.com/user-attachments/assets/24858da3-0fa3-4c5c-b1ea-b0152ac2693a">
</div>
