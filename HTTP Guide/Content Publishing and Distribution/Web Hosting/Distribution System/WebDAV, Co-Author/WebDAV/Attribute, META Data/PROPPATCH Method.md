-----
### PROPPATCH 메서드
-----
1. 특정 리소스의 여러 속성을 설정하거나 제거하는 원자적 메커니즘 제공
   - 원자성 : 모든 요청이 성공하거나 모든 요청이 무효가 되거나, 둘 중 하나만 수행하는 것을 보장

2. PROPPATCH 메서드의 기본 XML 요소 : ```<propertyupdate>```
   - 업데이트가 필요한 모든 속성을 담는 컨테이너 역할을 함
   - ```<set>```과 ```<remove>``` XML 요소는 수행할 동작을 가리킴

3. ```<set>``` : 설정할 속성 기술
   - 리소스에 적용할 이름 / 값 쌍의 속성을 기술하는 한 개 이상의 ```<prop>``` 하위 요소를 포함
   - 만약 해당 속성이 존재하면, 그 값은 현재 보내는 값으로 교체

4. ```<remove>``` : 제거할 속성 기술로, ```<set>```과 달리 ```<prop>``` 컨테이너에는 속성의 이름만 나열

5. 예시 (owenr 속성을 설정하고 제거)
<div align="center">
<img src="https://github.com/user-attachments/assets/f07c4129-77f6-40ea-965c-8a3242603643">
</div>

6. PROPPATCH 요청에 대한 응답은 PROPFIND 요청에 대한 응답과 매우 유사
7. PROPFIND 메서드와 PROPPATCH 메서드에 대한 응답 상태 코드
<div align="center">
<img src="https://github.com/user-attachments/assets/154cbf1e-9cb0-442d-895c-e7b4ff3b9914">
</div>
