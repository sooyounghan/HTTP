-----
### 네트워크 구성 요소 제어 프로토콜 (Network Element Control Protocol, NECP)
-----
1. 아이피 패킷을 전달하는 라우터나 스위치 같은 네트워크 구성요소들(NE)이 웹 서버나 프록시 캐시와 같이 애플리케이션 계층 요청을 처리하는 서버 구성요소들(SE)과 대화할 수 있게 해줌
2. NECP는 부하 균형을 명시적으로 지원하지 않음
3. 다만, SE는 NE에게 부하 균형 정보를 제공할 수 있는 방법을 제공하여 SE가 적합하다고 판단한 대로 NE가 부하 균형을 유지할 수 있도록 함
4. NECP는 MAC 포워딩(MAC Forwarding), GRE 캡슐화(GRE Encapsulation), NAT와 같은 패킷을 전달하는 여러 방법 제공
5. NECP는 예외에 대한 개념을 지원
   - SE는 특정 출발지 아이피 주소가 서비스 할 수 없다고 판단할 수 있으며, 그런 경우 그 수조들을 NE로 보낼 수 있음
   - 그러면 NE는 그 아이피 주소로부터 요청을 원 서버로 전달 가능
  
6. NECP 메세지
<div align="center">
<img src="https://github.com/user-attachments/assets/4b5a14aa-daff-45d5-9b65-c52f04be823b">
</div>
