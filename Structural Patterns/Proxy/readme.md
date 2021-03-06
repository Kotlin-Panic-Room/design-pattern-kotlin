## 의도

GoF 책에서는 다음과 같이 옵저버 패턴의 의도를 밝힌다.

> 다른 객체에 대한 접근을 제어하기 위한 대리자 또는 자리채움자 역할을 하는 객체를 둡니다


![](https://johngrib.github.io/wiki/pattern/proxy/proxy.svg)

Subject 구현체(Proxy)로 Request() 함수를 호출할 때 RealSubject를 참조하고 있는 Proxy가 RealSubject를 대리하는 구조.


## 프록시 패턴의 다양한 변형들

### Remote Proxy

* 리모트 프록시는 원본 소스를 캡슐화하며, 원본과 통신하는 방식으로 작동한다.
* 리모트 프록시는 다음 질문과 같이 클라이언트와 원본의 위치에 따라 세부적으로 나뉘어질 수 있다.
  * 클라이언트와 원본이 같은 머신에서 실행되는가?
  * 클라이언트와 원본이 다른 프로세스에서 실행되는가?

### Protection Proxy

보호 프록시(protection proxy)는 자신과 같은 인터페이스를 구현하는 실객체의 특정 메소드로의 접근을 제어한다. 이 경우 프록시 메소드는 인증 토큰을 전달받고, 이 토큰이 요청한 연산을 인증하지 못하면 예외를 던질 수 있다.

Collections.unmodifiableCollection(...)을 통해 받 은 Collection 구현체는 보호 프록시의 예이다


### Cache Proxy

* 캐시 프록시는 캐시를 보관하는 프록시이므로, 캐시 프록시를 구현할 때에는 다음 사항에 대해서도 고민해 보아야 한다.
  * 캐시를 어떻게 저장할 것인가?
  * 캐시를 어떻게 갱신할 것인가?
  * 캐시 유효성을 어떻게 검사할 것인가?
* 구글 크롬이나 파이어폭스 같은 웹 브라우저가 캐시 프록시의 구현을 사용한다고 볼 수 있다.

### Synchronization Proxy

하나의 컴포넌트에 대해 다수의 유사한 액세스들을 동기화해야 한다.

### Counting Proxy

우발적으로 컴포넌트가 삭제되지 않도록 해야하거나 사용량 통계(usage statistics)를 계산해야 한다.

### Virtual Proxy

가상 프록시 (virtual proxy)는 값비싼 객체를 필요할 때 생성하도록 해준다. 예를 들어 데이터베이스 접근은 데이터가 실제로 사용되기 전까지 프록시가 대신한다. 용량이 큰 이미지를 백그라운드 프로세스에서 네트워크를 통해 가져오는 동안 사용자는 이미지가 이미 그곳에 있다고 생각한다. 이러한 과정을 후기 초기화(lazy instantiation)라 부른다. 가상 프록시는 복사 수정 전략을 구현하는 데에도 유용하다. 객체의 복사 본을 요청받으면 프록시는 단순히 원본 객체에 대한 레퍼런스만을 갖는다그리고 복사본에 대한 수정 요 청이 들어오면 이때 비로소 프록시가 원본 객체를 실 제로 복사하게 된다


### Decorator와의 비교

>Decorator: 보호 프록시는 특히 Decorator로 보기 쉽다. 구조상 차이는 없으며 의도가 다를 뿐이다. Decorator는 데코레이팅되지 않은 객체를 직접 접근하는 것을 허용한다.


Decorator 디자인 패턴은 Proxy 패턴의 구조와 매우 유사하다. (Proxy 패턴에서 원본에 해당하는) ConcreteComponent는 (Proxy 패턴에서 프록시에 해당하는) 데코레이터를 통해 호출되는 몇 가지 동작을 구현한다. 두 클래스는 공통 기본 클래스(common base class)로부터 상속받는다. Decorator 패턴과 Proxy 패턴 간의 주요한 차이점은 그 의도에 있다. 데코레이터는 기능을 추가하거나, (좀 더 일반적으로는) ConcreteComponent의 핵심 기능에 추가 기능을 동적으로 선택할 수 있는 옵션을 제공한다. 프록시는 세부적으로 정의된 하우스키핑 코드(housekeeping code)를 원본으로부터 분리하는 역할을 한다.


### Proxy 패턴의 장점과 단점

#### 장점

기존 코드를 건드리 않고서 구현 가능하다. (SRP,OCP 원칙 준수 가능)

##### 단점

호출해야 하는 객체가 클래스 기반이라면 구현하기 어려울 수 있음

직관적이지 않음
