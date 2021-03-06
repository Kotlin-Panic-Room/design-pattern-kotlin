팩토리 패턴은 클래스 생성자를 대체하기 위해 사용되며, 인스턴스화된 객체의 타입을 런타임 때 결정할 수 있도록 객체 생성 과정을 추상화합니다.

팩토리 패턴(Factory Pattern) 또는 팩토리 메서드 패턴(Factory Method Pattern)은 객체를 만들기 위한 인터페이스 또는 추상 클래스를 정의하지만 하위 클래스가 인스턴스화할 클래스를 결정하도록 합니다.

즉, 하위 클래스는 클래스의 인스턴스를 만드는 역할을 합니다. 공장 메서드 패턴은 가상 생성자라고도 합니다.

### 팩토리 패턴으로 해결된 문제:
* 특히 클래스 계층의 여러 계층 내에서 복잡한 객체 생성
* 애플리케이션 코드에서 복잡성, 중복 및 유연성 문제를 야기하는 new() 연산자 사용
* 클라이언트가 세부 클래스 구현에 액세스할 수 있는 권한이 없는 경우

### 팩토리 디자인 패턴 을 사용하는 경우:
* 팩토리 메서드 패턴은 제품이 생성되는 방법을 알 필요가 없는 경우에 사용됩니다.
* 제공된 데이터에 따라 하위 클래스 중 하나의 개체를 생성해야 하는 팩토리 패턴을 사용할 수 있습니다.
* 일부 또는 모든 콘크리트 제품은 여러 가지 방법으로 생성될 수 있습니다. 또는 미래에 콘크리트 제품을 만들 수 있는 새로운 방법이 있을 수 있다는 옵션을 열어두고 싶습니다.