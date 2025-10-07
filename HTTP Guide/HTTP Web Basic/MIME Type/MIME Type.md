-----
### MIME 타입 구조
-----
1. 각 MIME 미디어 타입은 타입, 서브 타입, 선택적인 매개변수들 목록으로 구성
2. 타입과 서브 타입은 빗금(/)으로 구분되고, 선택적인 매개변수가 존재할 경우 세미콜론으로 시작
3. HTTP에서 MIME 미디어타입은 Content-Type과 Accept 헤더에서 널리 사용
<div align="center">
<img src="https://github.com/user-attachments/assets/764273fe-9606-437e-af25-3b68a8783d4e">
</div>

4. 분리형
   - MIME 타입은 객체 타입으로 묘사되거나 다른 객체 타입의 컬렉션이나 패키지로 묘사 가능
   - 만약 MIME 타입이 객체 타입을 직접 묘사했다면, 이는 분리형
   - 이는 텍스트 파일, 비디오, 애플리케이션 전용 파일 포맷

5. 혼합형
   - 다른 콘텐츠의 컬렉션이나 요약본인 MIME 타입을 혼합형
   - 즉, 혼합형은 패키지로 묶여있는 포맷을 가리킴
   - 묶여있는 패키지를 풀어 놓으면, 각 객체는 그 만의 형식을 가짐

6. 멀티파트형
   - 멀티파트 미디어 타입은 혼합형으로, 멀티 파트 객체는 여러 개의 컴포넌트 타입으로 구성
   - 예) 각각 자체 MIME 타입을 가지는 multipart/mixed 콘텐츠의 예
<div align="center">
<img src="https://github.com/user-attachments/assets/65087355-2a7a-4c0d-b261-9d7fba8668af">
</div>

-----
### 문법
-----
1. MIME 타입에는 타입 / 서브 타입 / 선택적으로 명시할 수 있는 매개변수 목록 존재
2. 타입은 이미 정의되어 있는, IETF가 정의된 확장 토큰이나 실험적 토큰(x-로 시작하는)이 될 수 있음
3. 공통 주요 MIME 타입
<div align="center">
<img src="https://github.com/user-attachments/assets/72ec24c2-a699-4c89-948c-eb5c2f0a2026">
</div>

4. 서브 타입은 text/text에서와 같이 주 타입과 같거나 IANA에 등록된 서브 타입이거나 x-로 시작하는 실험적 확장 토큰이 될 수 있음
5. 타입과 서브 타입은 US-ASCII 문자 집합으로 구성
6. - 빈칸과 tspecials라고 부르는 예약되어 있는 그룹과 문장 부호 문자들은 제어 문자이므로, 타입과 서브 타입에서 사용 불가

7. RFC 2046에 있는 MIME 타입 문법
<div align="center">
<img src="https://github.com/user-attachments/assets/256194c2-565d-4ac4-89db-dc3593fcc7fb">
</div>
