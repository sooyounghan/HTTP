-----
### WCCP 리다이렉션
-----
1. 시스코 시스템즈는 웹 라우터들이 웹 트래픽을 프록시 캐시로 리다이렉트 할 수 있도록 하기 위해 캐시 조직 프로토콜(WCCP)을 개발
2. WCCP는 라우터들과 캐시들 사이의 대화를 관리하여 라우터가 캐시를 검사하고(실행되어 있고 동작중임을), 특정 종류의 트래픽을 특정 캐시로 보낼 수 있게 해줌
3. WCCP 버전 2(WCCP2)는 개방된 프로토콜

4. WCCP 리다이렉션 동작
   - 네트워크가 필요 : 이 네트워크에는 WCCP를 사용할 수 있는 라우터와, 다른 캐시와 의사소통할 수 있는 캐시가 포함되어야 함
   - 라우터들의 집합과 그들의 대상이 되는 캐시들이 WCCP 서비스 그룹을 구성 : 서비스 그룹의 설정은 어떤 트래픽이 어디로 어떻게 보내지는지, 그리고 서비스 그룹에서 부하가 캐시들 사이에서 어떻게 분산되어야 하는지 명시
   - 만약 서비스 그룹이 HTTP 트래픽을 리다이렉션하도록 설정되어 있다면, 서비스 그룹의 라우터는 HTTP 요청을 서비스 그룹 캐시로 보냄
   - HTTP 요청이 서비스 그룹 라우터에 도착했을 때, 라우터는 그 요청을 처리하기 위해 서비스 그룹의 캐시 중 하나를 선택 (요청 아이피 주소의 해시 값이나 마스크 / 값 집합 짝짓기(Pairing) 스킴 중 하나에 근거)
   - 라우터는 요청 패킷을, 캐시의 아이피 주소와 함께 캡슐화하거나 아이피 맥 포워딩을 하여 캐시로 보냄
   - 만약 캐시가 요청을 처리할 수 없다면, 패킷은 평범하게 포워딩되기 위해 라우터로 돌아옴
   - 서비스 그룹의 구성원들은 지속적으로 다른 구성원들의 가용성을 확인하기 위해 하트비트 메세지(자신이 정상 동작하고 있음을 알려주는 메세지)를 교환

5. WCPP2 메세지들 : 네 가지가 존재
<div align="center">
<img src="https://github.com/user-attachments/assets/cae15f3a-0485-4d4e-af73-8c6dbe0fc5be">
</div>

   - WCCP2_HERE_I_AM 메세지 포맷
<div align="center">
<img src="https://github.com/user-attachments/assets/7541038a-f76c-4d7f-978b-b1b9eb7df83c">
</div>

   - WCCP2_I_SEE_YOU 메세지 포맷
<div align="center">
<img src="https://github.com/user-attachments/assets/846867d4-3245-4ee6-a847-96cba6652303">
</div>

   - WCCP2_REDIRECT_ASSGIN 메세지 포맷
<div align="center">
<img src="https://github.com/user-attachments/assets/d352ec3d-639e-4a6b-a5f2-2610139ae6fd">
</div>

   - WCCP2_REMOVAL_QUERY 메세지 포맷
<div align="center">
<img src="https://github.com/user-attachments/assets/7c14f1ac-7297-4902-b794-c267731082db">
</div>

6. 메세지 구성 요소
   - 각 WCCP2 메세지는 헤더와 구성요소로 구성
   - WCCP 헤더 정보는 메세지 정보(Here I Am, I See You, Assgienment, Removal Query), WCCP 버전, 메세지 길이(헤더 길이는 포함되지 않음) 포함
   - 각 구성 요소는 그 구성요소의 종류와 길이를 서술하는 4바이트 헤더로 시작
   - 구성요소 길이는 구성요소 헤더 길이를 포함하지 않음
   - 메세지 구성요소
<div align="center">
<img src="https://github.com/user-attachments/assets/7e6c4740-1e85-4aa9-a218-e00454eaf960">
</div>

7. 서비스 그룹
   - 서비스 그룹은 WCCP를 지원하는, 그래서 WCCP 메세지를 교환할 수 있는 라우터와 캐시들의 집합으로 구성
   - 이 라우터들은 웹 트래픽을 서비스 그룹의 캐시로 보냄
   - 서비스 그룹의 설정은 어떻게 트래픽이 서비스 그룹의 캐시들로 분산되는지 결정
   - 라우터와 캐시는 Here I Am과 I See You 메세지를 이용해 서비스 그룹 설정 정보를 교환

8. GRE 패킷 캡슐화
   - WCCP를 지원하는 라우터들은 HTTP 패킷을 특정 서버의 IP 주소와 함께 캡슐화함으로써 그 서버로 리다이렉트
   - 이 패킷 캡슐화는 일반 라우터 캡슐화(Generic Router Encapsulation, GRE)임을 나타내는 IP 헤더 proto 필드도 포함하고 있음
   - proto 필드의 존재는 수신 측 프록시에게 그 패킷이 캡슐화된 패킷을 갖고 있음을 말해줌
   - 패킷이 캡슐화 되어있으므로, 클라이언트 아이피 주소를 잃어버리지 않음
   - GRE 패킷 캡슐화
<div align="center">
<img src="https://github.com/user-attachments/assets/7e2b6dbc-94f0-4e0b-be8e-85348ece2eec">
</div>

9. WCCP 부하 균형
   - WCCP 라우터는 라우팅 뿐만 아니라 여러 수신 서버 간 부하 균형을 유지할 수 있음
   - WCCP 라우터와 그들의 수신 서버들은 그들이 살아 있고 동작 중임을 다른 장비들이 알 수 있도록 하트비트 메세지를 서로 교환
   - 만약 특정 수신 서버가, 하트비트 메세지를 보내지 않게 되었다면, WCCP 라우터는 트래픽 요청을 그 노드로 리다이렉트하는 대신 인터넷으로 바로 보냄
   - 노드가 다시 정상화되면, WCCP 라우터는 다시 하트비트 메세지를 받고, 그 노드로 요청 트래픽을 보내기 시작
