# 3장 서비스 모델링하기
> 요약
극대화하고잠재적인 단점을 회피할 수 있는 마이크로서비스의 경계에 대해 생각해보자.<br/><br/>
-책 전반에 걸쳐 가상 도메인에 대해 다루고 마이크로서비스의 개념이 어떻게 현실세계에 작용하는지 알아본다.<br/><br/>
>> __뮤직코퍼레이션 소개__ <br/>
오프라인 소매점에서 축음기 음반 사업이 바닥을 친 후 온라인 사업에 집중하게 된 뮤직코퍼레이션은 세계를 석권할 최고의 기회가 가능한  한 쉽게 변화하는 것에 달려 있다고 판단했다. 그 성공의 열쇠가 바로 "마이크로서비스" 다. <br/>
뮤직코퍼레이션에서 도메인은 운영 중인 전체 사업에 해당한다. (창고, 접수처, 재무, 주문 등등) 콘텍스트로 보이는 도메인은 창고, 재무부서 등이 있다.<br/>
창고와 재무부서를 서로 분리하는 경계가 있는 콘테스트로 생각할 수 있다. 재고 수준은 각 콘텍스트가 서로 공유하지만 주문 내역 등은 창고만 알 수 있고 외부에 공개하지 않는다.<br/>
만약 주문조달/재고관리/제품 인수가 각기 다른 팀에 의해 관리된다면 그들은 최상위 계층의 마이크로서비스가 될 자격이 있다. 반면 한 팀에 의해 관리된다면 내포 모델이 합리적일 것이다.<br/><br/>
>> __무엇이 좋은 서비스를 만드는가__ <br/>
느슨한 결합(loose coupling)과 강한 응집력(high cohesion), 두 가지 주요 개념에 집중할 필요가 있다.<br/>
그 외 다른 실천사항에 대해서도 나와있지만 이 두 개념이 잘못되면 나머지도 의미가 없다.<br/>
>>1. 느슨한 결합 : 마이크로서비스의 요점은 시스템의 그 어떤 부분도 추가 변경할 필요 없이 특정 서비스를 변경, 배포할 수 있다는 것!(매우 중요!!) 즉, 서비스가 느슨하게 결합되어 있다면 하나의 서비스 변경이 다른 서비스의 변경을 초래하지 않는다.<br/>
과도한 커뮤니케이션은 잠재적인 성능 문제를 넘어 강한 결합을 초래할 수 있기 때문에 느슨하게 결합된 서비스는 그와 협업하는 서비스에 관해 알 필요가 없다.
>>1. 강한 응집력 : 여러 곳에서 변경하는 것은 느릴 분만 아니라 한번에 많은 서비스를 배포하는 것은 위험하다. 따라서 서로 연관된 행위가 한 곳에 모이고, 다른 경계와는 가능한 한 느슨하게 소통할 수 있도록 우리 문제 영역 내에서 경계를 찾고자 한다.

>> __경계가 있는 콘텍스트__ <br/>
경계가 있는 모든 콘텍스트에는 명백한 인터페이스가 존재하며, 그 것은 어떤 모델이 다른 콘텍스트와 공유될지 결정된다.<br/>
경계가 있는 콘텍스트와 관련한 또 다른 정의로는 '명로한 경계에 의해 강제된 구체적인 책임'이다. (http://googl/KRIcUx)<br/>
>>1. 감춰진 공유 모델 : 특정 모델은 각각의 경계가 있는 콘텍스트 내의 다른 프로세스 및 지원 개체들과 연계될 수 있지만, 또 다른 모델은 콘텍스트 자체의 아주 내부적인 관심사 일 뿐! 우리가 어떤 모델을 공유해야 하는지, 그리고 어떤 내부 표현을 공유하면 안되는지 명확히 고려함으로써 강한 결합을 초래하는 잠재적 함정 중 하나를 회피 한다.
>>2. 모듈과 서비스 : 일반적으로 마이크서비스는 경계가 있는 콘텍스트와 완전히 정렬되어야 한다. 그러나 서비스 경계를 잘못 정하면 큰 비용이 들게 되므로 새로운 도메인 영역에 익숙해져서 안정화될 떄까지 기다리는 것이 현명하다. 만약 서비스 경계가 도메인 경계가 있는 콘텍스트와 정렬되고, 마이크로서비스가 경계가 잇는 콘텍스트를 잘 대표한다면, 우리의 마이크로서비스가 느슨히 결합되고 강하게 응집되도록 보장한다는 점에서 아주 좋은 출발을 하고 있는 것이다.
>>3. 성급한 분해 : 시스템을 마이크로서비스로 성급하게 분해하면 막대한 비용이 소요될 수 있다.(특히 도메인의 경험이 없다면 더더욱!!!) 따라서 기존 코드베이스를 마이크로서비스로 분해하는 것이 처음부터 마이크로서비스로 가는 것보다 훨씬 쉽다.

>> __비즈니스 능력__ <br/>
조직 내 존재하는 경계가 있는 콘텍스트에 관해 고민할 때는 공유 데이터 관점이 아닌 나머지 도메인을 제공하는 콘텍스트의 능력 과점에서 봐야 한다.<br/>
'이 콘텍스트는 무엇을 하는가?' / '그 일을 하기 위해 어떤 데이터가 필요한가?' 질문이 선행되어야 한다.<br/><br/>
>> __거북이 밑에 거북이__ <br/>
경계가 있는 콘텍스트는 더 많은 '경계가 있는 콘텍스트'들을 내포할 수 있다. 마이크로서비스의 경계를 고려할 때는 우선 더 넓고 큰 단위의 콘텍스트 관점에서 생각한 뒤 접합부의 분리를 통한 혜택을 발견했을 때 내포된(nested) 콘텍스트에 따라 세분화하라.<br/>
내포 방식을 선호하는 또 다른 이유는 테스팅의 단순화르 ㄹ위해 아키텍처를 큰 덩어리로 묶을 수 있다는 점이다.<br/><br/>
>> __비즈니스 콘셉트 관점에서의 커뮤니케이션__ <br/>
도메인을 대표하는 경계가 있는 콘텍스트에 따라 우리 시스템이 분해된다면 그 변경 사항은 단일 마이크로서비스 경계로 격리되기 쉽다. 이렇게 되면 변경 대상을 줄이고 신속한 배포가 가능하다.<br/><br/>
>> __기술적 경계__ <br/>
서비스가 부정확하게 모델링 되었을 때 어떻게 잘못되는지 지켜보는 것은 유용하다.<br/>
기술 접합부에 따라 서비스 경계를 모델링하는 결정이 항상 잘못된 것은 아니다. 저자는 조직이 특정 성능 목표를 달성하려 할 때 수평으로 나누는 방식이 더 적절하다는 것을 분명히 모격ㄱ한 바 있다. 하지만 이는 기술 접합부를 찾는 첫 번쨰 목표가 아닌 두 번쨰 목표가 되어야 한다.<br/><br/>
>> __마치며__ <br/>
경계가 있는 콘텍스트는 이들 접합부를 찾는 데 중요한 도구고, 마이크로서비스를 이 경계에 정렬하여 우리의 최종 시스템이 온전한 장점들을 유지하도록 만들어야 한다.<br/><br/>

> 느낀점
>> 각각의 작은 서비스가 서로 상호작용하면서 이루어지는 것이 마이크로서비스라고 생각하는데 서비스 모델링 역시 해당 개념과 유사하다. 모든 개발이 그렇듯 마이크로서비스도 모델링, 서비스를 콘텍스트로 나누는 작업이 가장 중요하거 어려운 작업인 것 같다.<br/> 

---
### 책 속 용어
- RPC 일괄 처리 메커니즘(RPC-batching mechanism) : 일괄처리를 수행하면 클라이언트가 임의로 많은 수의 호출 메시지를 보낼 수 있으며, 클라이언트는 일련의 호출에 대한 응답을 기다리지 않고 서버도 모든 호출에 대한 응답을 보내지 않아 통신 부하를 줄일 수 있지만 파이프라인 버퍼 제어 등 보다 정교한 처리가 요구된다.
