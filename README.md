### 취업 면접 질문 사안들에 대해 공부 및 작성한 답변

</br>

질문 리스트 출처 : https://github.com/Lob-dev/Junior-Back-end-Developer-Concepts/blob/main/Job%20interview.md

</br>

## JAVA

<details>
<summary>Managed - Unmanaged 언어의 차이는 무엇이고 어떤 장, 단점이 있나요?</summary>

</br>

- 메모리 영역 중 프로그래머가 관리하는 영역이 Heap 영역의 관리여부에 따른 언어가 Managed 와 Umanaged로 나뉘게 된다.

- 대표적인 Managed 언어에는 JAVA, C# 등이 있고, 할당과 해제를 통한 메모리의 관리없이 언어자체적으로 메모리를 관리한다. 따라서 개발자의 역량에 의존하는 부분이 상대적으로 작아져 어느 정도 일정한 생산성을 확보할 수 있다는 장점이 있다.

- 대표적인 Unmanaged 언어에는  C, C++ 등이 있고, 메모리의 할당과 해제(malloc(), free()등)를 통해 메모리를 관리하여, 메모리의 누수가 없게 신경을 써줘야 하지만 Managed 언어에 비해 속도가 빠르다.
</details>

<details>
<summary>Java 접근 제어자에는 무엇이 있는지 설명해주시고 Protect와 Private는 어느 시점에 어떻게 사용될 수 있는지 이야기 해주세요.</summary>

</br>

- 자바의 접근 제어자에는 public, private, default, protected 가 있다.

  - public : 클래스의 외부에서 접근이 가능

  - private : 클래스 내부에서만 접근 가능

  - default : 동일 패키지에 있는 다른 클래스에서 접근 가능

  - protected : 동일 패키지의 다른 클래스와 다른 패키지의 하위클래스에서 접근 가능

- Private 접근 제어자의 경우, 외부에 공개해야 할 일이 없고, 내부에서 주로 사용할 경우 은닉화를 위해 사용한다. 

- Protected 접근 제어자의 경우, 클래스 설계 시, 추후 상속을 대비하기 위해 확장성을 고려해서 만들어 주기 위해 사용한다.

</details>

<details>
<summary>JVM의 메모리 구조에 대해서 설명해 주세요.</summary>

</br>

- JVM(Java Virtual Machine) 이란? : 자바 가상 머신으로, 자바와 운영체제 사이에서 중개자 역할을 수행하며, 자바가 운영체제에 구애 받지 않고 프로그램을 실행할 수 있도록 도와준다.

- JVM의 구조는 Garbage Collector, Execution Engine, Class Loader, Runtime Data Area로 나눌 수 있다.

  - Class Loader : JVM 내로 클래스 파일을 로드하고, 링크를 통해 배치하는 작업을 수행하는 모듈, 런타임 시에 동적으로 클래스를 로드한다.
  - Execution Engine : 클래스 로더를 통해 JVM 내의 Runtime Data Area에 배치된 바이트 코드들을 명렁어 단위로 읽어서 실행한다.
  - Garbage Collector : 힙 메모리 영역에 생성된 객체들 중에서 참조되지 않은 객체들을 탐색 후 제거하는 역할을 한다.
  - Runtime Data Area : JVM의 메모리 영역으로 자바 애플리케이션을 실행할 때 사용되는 데이터들을 적재하는 영역이다. 이 영역은 크게 4가지로 나뉜다.
    - Method area : 모든 쓰레드가 공유하는 메모리 영역
    - Heap area : 모든 쓰레드가 공유하며, new 키워드로 생성된 객체와 배열이 생성되는 영역
    - Stack area : 메서드 호출 시마다 각각의 스택 프레임(그 메서드만을 위한 공간)을 생성한다.
    - PC Register : 쓰레드가 시작될 때 생성되며, 생성될 때마다 생성되는 공간으로 쓰레드마다 하나씩 존재한다.
</details>

<details>
<summary>JVM은 어떤 방식으로 코드를 해석하고 실행시키는지 흐름에 맞게 설명해 주세요. (Java 실행 흐름)</summary>

</br>

- 자바 소스파일(.java)이 실행되는 과정
  1. 자바 컴파일러에 의해 소스파일(.java)이 바이트 코드 파일(.class)로 변환
  2. JVM은 .class 파일을 Class Loader를 이용해 로드하고, 링크를 통해 배치하는 작업 수행
  3. Class Loader에 의해 .class 파일이 JVM 메모리 영역에 적재됨
  4. Execution Engine은 JVM 메모리 영역에 적재된 .class 파일을 기계어로 변경하여 명령어 단위로 실행
</details>


<details>
<summary>Garbage Collector은 무엇이고, Parallel GC와 CMS GC, G1 GC의 큰 차이는 무엇인지 설명해주세요. (mark-sweep-compact, concurrency-sweep, garbage-first)</summary>

</br>

- 시스템에서 더이상 사용하지 않는 동적 할당된 메모리(힙 메모리)를 찾아 자동으로 자원을 회수함으로써, 시스템에서 가비지 컬렉션을 수행하는 부분을 가비지 컬렉터라고 한다.
- 힙 영역에 존재하는 객체들에 접근이 가능한지 확인한 후, Mark 과정을 진행하며, Mark되지 않은 객체는 제거한다.
- Serial GC : 싱글 스레드로 동작하여 느리고, 그만큼 Stop The World 시간이 다른 GC에 비해 길다. 실무에서는 사용 X
- Parallel GC : Java 8의 Default GC로써, 멀티 스레드 방식을 사용하기 때문에, Serial GC에 비해 상대적으로 Stop The World 가 짧다.
- CMS GC : Stop The World로 Java Application이 멈추는 현상을 줄이고자 만든 GC, Reacable 한 객체를 한번에 찾지 않고 나눠서 찾는 방식을 사용 (4 STEP으로 나눠짐)
- G1 GC : Java 9+ 의 default GC로써, Heap을 Region이라는 일정한 부분으로 나눠서 메모리를 관리한다.
</details>


<details>
<summary>Java 8 버전에 추가된 중요 기능들에 대해서 설명해주세요.</summary>

</br>

- Lambda 표현식, Default Method, 함수형 인터페이스, Optional, 날짜 관련 클래스등이 추가되었다.
</details>

<details>
<summary>Java는 Call By Value일까요, Call By Reference 일까요?</summary>

</br>

- Java 는 기본적으로 Call by Value 로만 동작한다.
- 매개변수로 원시타입을 넘길 경우, 메서드 호출 시 stack 영역에 새로 생성, 즉 복사가 이루어진다.
- 참조타입(클래스, 배열 등)의 경우, 변수 자체는 stack 영역에 생성되지만, 실제 객체는 Heap 영역에 위치하므로, 다른 영역에서 객체를 서로 공유하게 된다. 따라서 메서드에서 수정이 일어날 경우, 기존에 참조하고 있던 타입에도 변경이 일어난다.
</details>

<details>
<summary>Shallow Copy와 Deep Copy의 차이는 무엇인가요? 자바에서 Deep Copy를 하기 위해서는 무엇을 사용하여야 하나요?</summary>

</br>

- 얕은 복사의 경우, 객체의 참조값을 복사함으로써, 해당 객체를 수정할 때 기존에 참조하고 있던 데이터 또한 변경이 된다.
- 깊은 복사의 경우, 직접 객체를 복사함으로써, 객체를 수정해도 각각 다른 객체 2개를 참조한다.
- 깊은 복사를 위해서 직접 객체를 생성후 복사하거나, 복사 생성자 및 복사 팩토리, Clonable 인터페이스를 구현하는 방법이 있다.
</details>

<details>
<summary>Java Reflection이란 무엇이고, 어떨 때 사용되는 것인가요?</summary>

</br>

- 리플렉션은 힙 영역에 로드된 Class 타입의 객체를 통해, 원하는 클래스의 인스턴스를 생성할 수 있도록 지원하고, 인스턴스의 필드와 메소드를 접근 제어자와 상관 없이 사용할 수 있도록 지원하는 API이다.
- 리플렉션을 사용하면 동적으로 클래스를 만들어서 의존 관계를 맺어줄 수 있다.
- Spring의 Bean Factory는 런타임에 해당 어노테이션이 붙은 클래스를 탐색하고 발견한다면, 리플렉션을 통해 해당 클래스의 인스턴스를 생성하고 필요한 필드를 주입하여 Bean Factory에 저장하는 식으로 사용이 된다.
</details>

<details>
<summary>Java Instrumentation이란 무엇이고 사용했을 때 어떤 장점이 있을까요?</summary>

</br>

- 
</details>


<details>
<summary>Java Lambda는 왜 만들어졌고, 어느 때 주로 사용할까요?</summary>

</br>

- 람다식이란 함수를 하나의 식으로 표현한 것이다.
- 람다식이 등장하게 된 이유는 불필요한 코드를 줄이고, 가독성을 높이기 위함이다.
- 불필요한 코드를 줄이고, 가독성을 높이기 위해 사용한다.
</details>


<details>
<summary>Java Stream API의 특징은 무엇이 있나요?</summary>

</br>

- 원본의 데이터를 변경하지 않는다.
- 일회용이기 때문에 Stream은 닫히면 재생성 해주어야 한다.
- 내부 반복으로 작업을 처리하므로 간결한 코드 작성이 용이하다.
</details>


<details>
<summary>Java의 Functional interface는 무엇인가요?</summary>

</br>

- 추상 메서드가 오직 하나인 인터페이스를 의미한다.
- 여러 개의 디폴트 메서드가 있더라도 추상 메서드가 오직 하나면 함수형 인터페이스이다.
</details>


<details>
<summary>foreach를 사용할 수 있는 자료구조는 어떤 인터페이스를 상속 받고 있나요?</summary>

</br>

- Iterable 인터페이스를 상속 받는다.
</details>


<details>
<summary>iterator와 iterable 차이는 무엇인가요?</summary>

</br>

- Iterator 인터페이스는 Collection과는 별개로 존재하는 인터페이스이다. (hasNext(), next(), remove() 등이 메소드 이용)
- Iterable은 컬렉션의 상위 인터페이스이다.
- Iterable 인터페이스 안에는 iterator 메소드가 추상메소드로 선언되어있다.
</details>


<details>
<summary>Fast-fail iterator는 무엇이고 어떤 것을 위해 사용되는 건가요?</summary>

</br>

- Fail-Fast 방식은 동작중 오류가 발생하면 바로 오류를 알리고, 작업을 중단한다.
- 
</details>


<details>
<summary>자바의 synchronized 키워드에 대해 설명해주시고 Reentrant Lock와의 차이는 무엇인지 말씀해주세요.</summary>

</br>

- synchronized는 멀티쓰레드 환경에서 현재 데이터를 사용하고 있는 해당 스레드를 제외하고 나머지 스레드들은 데이터에 접근 할 수 없도록 막는 기능이다.
- synchronized는 메서드 단위로 lock을 거는 반면, Reentrant Lock의 경우 코드 블럭을 설정할 수 있어, synchronized 영역을 해당 코드블럭 내로 한정한다.
</details>


<details>
<summary>Java의 synchronized Lock 범위에 대해서 알려주세요. (Class Lock, Instance Lock)</summary>

</br>

- synchronized method는 인스턴스에 대하여 lock을 건다. 또한 synchronized가 적용된 모든 object에 대해서 lock을 공유한다.
- static이 포함된 synchronized method방식은 인스턴스가 아닌 클래스 단위로 lock이 발생한다. 인스턴스 단위의 synchronized method와 lock을 공유하지 않는다.
</details>

</br>

## SPRING

<details>
<summary>Spring이란 무엇인가요? Spring이 이야기하는 장점에는 무엇들이 있을까요? (EJB와 비교해서 설명하면 좋을듯)</summary>

</br>

- 기존 EJB의 단점들을 해결하기 위해 등장한 객체 지향 애플리케이션 개발 프레임워크이다.
  - EJB의 기존 문제점
    - 자동화된 테스트가 매우 어렵거나 불가능
    - 특정 환경, 기술에 종속적인 코드
    - 컨테이너에 안에서만 동작할 수 있는 객체구조
    - 객체지향적이지 않음
    - 복잡한 프로그래밍 모델
    
- Spring의 대표적인 장점
  - 특정 라이브러리나 컨테이너의 기술에 종속적이지 않기 때문에 높은 생산성과 유연한 테스트 가능
  - DI(의존성 주입)을 통한 객체 관계 구성
  - AOP(관점지향 프로그래밍) 지원
  - 편리한 MVC 구조
  - Springboot를 통한 내장 서버 -> WAS에 독립적인 개발 환경

</details>

<details>
<summary>IoC, DI는 무엇이고 어떠한 장점이 있을까요?</summary>

</br>

- IOC(Inversion of Control) 이란 개발자가 아닌 스프링 컨테이너에서 직접 객체간에 관계를 제어하는 것을 의미한다.
  - 개발자가 직접 객체간의 관계를 설정하지 않음으로 인한 생산성 향상
- DI(Dependency Injection) 이란 외부에서 두 객체간의 관계를 결정해주는 디자인 패턴
  - 두 객체 간의 결합도를 낮춤
  - 객체의 유연성을 높임
  - 테스트 작성이 용이

</details>

<details>
<summary>Spring IoC Container란 무엇인가요?</summary>

</br>

- 객체를 생성하고 관리하고 책임지며 의존성을 관리해주는 컨테이너이며, DI 컨테이너, 애플리케이션 컨텍스트라고 불림
- 인스턴스 생성부터 소멸까지의 인스턴스 생명주기를 관리한다.

</details>

<details>
<summary>Spring, Spring Boot의 차이점에 대해 각각 설명해 주세요.</summary>

</br>

- Spring boot는 Spring Framework 설정의 많은 부분을 자동화 하였다.
- Embed Tomcat을 사용하여 따로 Tomcat 설치 및 버전 관리가 필요없다.
- starter를 통해 dependency를 자동화
- XML 설정 불필요
- dependency를 통한 API 

</details>

<details>
<summary>Spring Boot가 해결하려고 했던 문제는 무엇이고 어떻게 해결하였나요?</summary>

</br>

- 초기 프로젝트 세팅 시, 외장 톰캣에 war 파일을 배포하는 등, 개발자가 겪는 번거로움을 해소하고자 하였다.
-> 라이브러리들의 버전 관리 자동화, 내장 웹서버, AutoConfig를 통한 설정 자동화 등을 통해 해결하였다.

</details>

<details>
<summary>Bean이란 무엇인가요?</summary>

</br>

- Spring IoC 컨테이너가 관리하는 자바 객체를 의미한다.
- 직접 Class를 생성하는게 아닌, Spring에 의하여 생성되고 관리되는 자바 객체이다.

</details>

<details>
<summary>Bean Scope와 종류에 대해 아는 만큼 설명해주세요.</summary>

</br>

- 기본적으로 모든 bean을 singleton으로 생성하여 관리
- 싱글톤
  - Spring 프레임워크에서 기본이 되는 스코프
  - 스프링 컨테이너의 시작과 종료까지 1개의 객체로 유지됨
- 프로토타입
  - 프로토타입 빈의 생성과 의존관계 주입까지만 관여하고 더는 관리하지 않는 스코프
  - 요청이 오면 항상 새로운 인스턴스를 생성하여 반환하고 이후에 관리하지 않음
  - 프로토타입을 받은 클라이언트가 객체를 관리해야 함
- 웹
  - request: 각각의 요청이 들어오고 나갈때가지 유지되는 스코프
  - session: 세션이 생성되고 종료될 때 까지 유지되는 스코프
  - pplication: 웹의 서블릿 컨텍스트와 같은 범위로 유지되는 스코프

</details>

<details>
<summary>Configuration은 어떻게 Bean을 등록하고 관리할까요? (Singleton을 지키는 매커니즘은?)</summary>

</br>

- Configuration을 통해 Bean을 수동으로 등록한다. 
- 1개 이상의 @Bean을 제공하는 클래스의 경우 반드시 @Configuration을 명시해 주어야 싱글톤이 보장됨
-> CGLib으로 프록시 패턴을 적용해 수동으로 등록하는 스프링 빈이 반드시 싱글톤으로 생성됨을 보장한다.

</details>

<details>
<summary>Bean Lite Mode는 무엇인가요?</summary>

</br>

- CGLIB를 이용하여 바이트 코드 조작을 하지 않는 방식을 의미한다. 즉, 스프링 빈의 싱글톤을 보장하지 않는다.

</details>

</details>

<details>
<summary>Spring Bean Life-cycle에 대해서 말해주세요.</summary>

</br>

- 스프링 빈은 초기화 작업과 종료 작업이 나눠서 진행된다.
- 객체 생성 → 의존관계 주입이라는 라이프사이클을 가진다.
- 스프링 IoC 컨테이너 생성 →  스프링 빈 생성 → 의존관계 주입 → 초기화 콜백 메소드 호출 → 사용 → 소멸 전 콜백 메소드 호출 → 스프링 종료
-  @PostConstruct, @PreDestory을 통해 빈 생명주기 콜백을 관리할 수 있다.
</details>


<details>
<summary>@Bean과 @Component은 각각 언제 사용되고 어떤 차이점을 가지나요?</summary>

</br>

- @Bean은 메소드 레벨에서 선언하며, 반환되는 객체(인스턴스)를 개발자가 수동으로 빈으로 등록하는 애노테이션이다.
- @Bean은 개발자가 컨트롤이 불가능한 외부 라이브러리 사용시에 사용한다.
- @Component는 클래스 레벨에서 선언함으로써 스프링이 런타임시에 컴포넌트스캔을 하여 자동으로 빈을 찾고(detect) 등록하는 애노테이션이다.
- @Component는 개발자가 직접 컨트롤이 가능한 내부 클래스에 사용한다.
</details>


<details>
<summary>순환 참조는 무엇이고 어떤 상황에서 발생할까요?</summary>

</br>

- 예를 들어, A 클래스가 B 클래스의 Bean 을 주입받고, B 클래스가 A 클래스의 Bean 을 주입받는 상황처럼 서로 순환되어 참조할 경우 발생하는 문제를 의미한다.
</details>


<details>
<summary>Spring으로 개발하실 때 어떠한 DI 방식을 사용하시나요? 사용하는 이유는 무엇이 있는 것일까요?</summary>

</br>

- 생성자 주입 방식 사용
  - 필드 주입이나 수정자 주입은 런타임 시에 의존성을 주입하기때문에 의존성을 주입하지 않아도 객체가 생성된다. -> NPE 발생
  - 생성자 주입은 객체가 생성되는 시점에 빈을 주입하여, 런타임 전에 의존성이 주입되지 않아 발생할 수 있는 NPE를 방지 가능
  - 컴파일 단계에서 순환 참조를 잡아내어, 미리 방지 할 수 있음
</details>

<details>
<summary>Field Injection를 왜 사용하면 안된다고 하는 것인가요? 사용할 때 어떠한 단점이 있을까요?</summary>

</br>

- 필드 인젝션으로 주입받는 클래스는 final로 선언 할 수 없기 때문에 state safe 하지 않다.
- 스프링을 통해서만 의존성 주입이 가능하기 때문에 해당 Bean들이 스프링의 DI 컨테이너와의 강한 결합 생성
- 필드 인젝션으로 주입한 객체를 테스트 하려면 무거운 스프링 컨테이너를 띄워야 함
</details>

<details>
<summary>(Field 주입과 대비하여) 생성자 주입은 빈 생성 때 사용되는 리플랙션 외에 추가적인 리플랙션을 진행하나요?</summary>

</br>

- 리플렉션이란: 힙 영역에 로드된 Class 타입의 객체를 통해, 원하는 클래스의 인스턴스를 생성할 수 있도록 지원하고, 인스턴스의 필드와 메소드를 접근 제어자와 상관 없이 사용할 수 있도록 지원하는 API
- 생성자 주입은 필드, 메서드 방식보다 적게 리플렉션을 사용
- bean을 생성할 때, 다른 bean 정보를 가져오는 Dependency Lookup까지만 사용
</details>

<details>
<summary>Interceptor와 Filter의 차이점을 말해주세요</summary>

</br>

- 필터는 디스패처 서블릿에 요청이 전달되기 전/후에 url 패턴에 맞는 모든 요청에 대해 부가작업을 처리할 수 있는 기능을 제공
- 인터셉터는 Spring이 제공하는 기술로써, 디스패처 서블릿이 컨트롤러를 호출하기 전과 후에 요청과 응답을 참조하거나 가공할 수 있는 기능을 제공
- 필터는 Request와 Response를 조작할 수 있지만 인터셉터는 조작할 수 없다.
- 필터에서는 기본적으로 스프링과 무관하게 전역적으로 처리해야 하는 작업들을 처리할 수 있다.
- 인터셉터에서는 API 호출, Controller로 넘겨주는 정보(데이터)의 가공 등, 클라이언트의 요청과 관련되어 전역적으로 처리해야 하는 작업들을 처리할 수 있다.
</details>


<details>
<summary>스프링에서 Bean으로 Filter를 구현할 수 있을까요? 혹시나 가능하다면 어떻게 할 수 있을까요?</summary>

</br>

- servlet의 Filter 인터페이스를 구현하여 만들 수 있다.
- init(), dofilter(), destroy() 메서드를 오버라이딩하여 구현한다.
- 해당 필터를 @Configuration, @Bean을 통해 Spring Bean으로 등록한다.
</details>


<details>
<summary>Message Converter는 어느 시점에 사용되고 어떤 기능을 제공하나요?</summary>

</br>

- 요청 본문에서 메시지를 읽어들이거나(@RequestBody), 응답 본문에 메시지를 작성할 때(@ResponseBody) 사용
- RequestMappingHandlerAdapter 에서 ArgumentResolver 호출할 때
- ArgumentResolver에 요청하는 파라미터가 @RequestBody 또는 HttpEntity인 경우 HTTP 메시지 컨버터를 사용해 'read'
- 응답의 경우에도 @ResponseBody 또는 HttpEntity를 처리하는 ReturnValueHandler에서 HTTP 메시지 컨버터를 호출해 응답 결과를 'write' 
</details>


<details>
<summary>Value Object, Data Transfer Object, Data Access Object 대해서 각각 설명해 주세요.</summary>

</br>

- DAO : 데이터베이스의 data에 접근하기 위한 객체, DataBase에 접근 하기 위한 로직 & 비지니스 로직을 분리하기 위해 사용
- DTO : 계층 간 데이터 교환을 하기 위해 사용하는 객체, 로직을 가지지 않는 순수한 데이터 객체(getter & setter 만 가진 클래스)
- VO : 값 오브젝트로써 값을 위해 쓰임, read-Only 특징(사용하는 도중에 변경 불가능하며 오직 읽기만 가능)
</details>


<details>
<summary>Spring AOP는 어떻게 동작할까요? (프록시는 언제 생성되고 요청은 어떻게 잡아내나요?</summary>

</br>

- 타겟이 호출되는 시점에 호출을 가로채 프록시를 생성하며, 실제 작업을 행하는 오브젝트를 감싼 후에 실제 오브젝트의 요청하기 전, 후의 작업을 실행한다.
- 프록시 방식을 사용하는 스프링 AOP는 메서드 실행 지점에만 AOP를 적용할 수 있다.
- 스프링 AOP에서는 런타임시에 Weaving을 통해서 프록시 객체를 생성하게 된다.
</details>


<details>
<summary>Spring AOP는 CTW, PCW, LTW, RTW 중에 무엇일까요?</summary>

</br>

- 스프링 aop는 런타임 시에 적용되는 RTW 방식을 사용한다.
  - CTW : .java 소스 코드를 컴파일러를 사용해서 .class 를 만드는 시점에 부가 기능 로직을 추가
  - PCW : 외부 라이브러리를 Weaving 할 때 사용, compile-Time 위빙과 거의 동일한 동작
  - LTW : 중간에서 .class 파일을 조작한 다음 JVM에 올림
</details>

<details>
<summary>Dynamic Proxy의 CTW, BTW, LTW, RTW은 각각 어떤 시점에 개입하는 것일까요?</summary>

</br>

- 
</details>


<details>
<summary>(Spring AOP와 비교하여) AspectJ의 도입 시점은 어느 시점이 될까요? 본인 만의 생각을 알려주세요.</summary>

</br>

- 
</details>


<details>
<summary>@Transactional를 스프링 Bean 메서드 A에 적용하였고, 해당 Bean의 메서드 B가 호출되었을 때 메서드 내부에서 메서드 A를 호출하면 어떤 요청 흐름이 발생하게 되나요?</summary>

</br>

- @Transactional는 프록시 기반이므로, 메서드가 실행되기 전 트랜잭션을 묶는다. 이때 인스턴스에서 처음 호출하는 메서드의 속성을 따라가게 되는데, 하위 메서드인 B의 속성이 상위 메서드인 A에 전이되지 않으므로 트랜잭션 처리가 되지 않는다.
</details>

<details>
<summary>MVC 1, 2 개념에 대해서 설명해 주세요.</summary>

</br>

- MVC 1
  - View와 Controller 모두 jsp가 담당하는 형태이다.
  - 따라서 jsp 내에 자바 코드와 html, css 코드가 섞여 유지보수 차원에서 좋지 않다.
- MVC 2
  - jsp는 뷰의 역할만 하며, Controller의 역할을 Servelt이 수행한다.
  - 사용자의 요청을 servlet이 받아, 웹 브라우저의 요청을 처리한 후 jsp 페이지로 포워딩한다.
</details>

<details>
<summary>Front Controller Pattern은 무엇인가요?</summary>

</br>

- 공통된 로직을 하나의 서블릿만을 앞단에 두어 모든 클라이언트의 요청을 처리하는 방식이다.
- 스프링은 프론트 컨트롤러 패턴을 따르고 이를 DispatcherServlet이 담당한다.
</details>

<details>
<summary>Dispatcher Servlet이란 무엇인가요?</summary>

</br>

- HTTP 프로토콜로 들어오는 모든 요청을 가장 먼저 받아 적합한 컨트롤러에 위임해주는 프론트 컨트롤러(Front Controller)이다.
- 클라이언트로부터 어떠한 요청이 오면 Tomcat(톰캣)과 같은 서블릿 컨테이너가 요청을 받게 되는데, 이 모든 요청을 프론트 컨트롤러인 디스패처 서블릿이 가장 먼저 받게 된다. 그러면 디스패처 서블릿은 공통적인 작업을 먼저 처리한 후에 해당 요청을 처리해야 하는 컨트롤러를 찾아서 작업을 위임한다.
</details>


<details>
<summary>Spring MVC에서 HTTP 요청이 들어왔을 때의 흐름을 설명해 주세요.</summary>

</br>

1. 클라이언트의 요청을 디스패처 서블릿이 받음
2. 요청 정보를 통해 요청을 위임할 컨트롤러를 찾음
3. 요청을 컨트롤러로 위임할 핸들러 어댑터를 찾아서 전달함
4. 핸들러 어댑터가 컨트롤러로 요청을 위임함
5. 비지니스 로직을 처리함
6. 컨트롤러가 반환값을 반환함
7. HandlerAdapter가 반환값을 처리함
8. 서버의 응답을 클라이언트로 반환함

</details>


<details>
<summary>A 라는 Service 객체의 메서드가 존재하고 내부에서 로컬 트랜잭션이 3개가 존재한다고 할 때, @Transactional을 A 메서드에 적용하였을 때 어떠한 일이 벌어지고, 어떤 요청 흐름이 발생하게 되나요?</summary>

</br>

- 트랜잭션 전파 수준에 따라 달라진다.
- 만약 기본 옵션인 REQUIRED를 가져간다면 로컬 트랜잭션 3개가 모두 부모 트랜잭션인 A에 합류하여 수행된다.
- 따라서 부모 트랜잭션이나 로컬 트랜잭션 3개나 모두 같은 트랜잭션이므로 어느 하나의 로직에서든 문제가 발생하면 전부 롤백이 된다.

</details>


<details>
<summary>Reflection API는 Runtime에서 코드를 생성하는데 많이 사용됩니다. 이는 Spring에서도 자주 활용되는데요. 스프링 컨테이너는 이런 Reflection으로 생성된 Bean의 정보를 실행 이후에 알고 있네요? 어떻게 알 수 있을까요?</summary>

</br>

- 

</details>

</br>
</br>


## ORM - JPA

<details>
<summary>ORM Framework가 무엇인지 설명해주세요.</summary>

</br>

- ORM은 데이터베이스와 객체지향 프로그래밍 언어간의 호환되지 않는 데이터를 변환하는 프로그래밍 기법이다.
- 따라서 ORM Framework는 직접 쿼리를 날리는 등의 작업을 하지않고, 객체와 데이터베이스를 매핑하며 객체 지향 어플리케이션 개발에 집중이 가능하다.

</details>

<details>
<summary>ORM Framework와 Query Mapping Framework의 차이에 대해서 설명해주세요. (JPA vs Mybatis)</summary>

</br>

- Query Mapping의 경우, SQL문을 직접 작성하고 쿼리 수행 결과를 어떠한 객체에 매핑할지 바인딩 하기 때문에, DB에 종속적이다.
- ORM의 경우, 쿼리문을 작성하지 않으므로 DB에 종속적이지 않아, 객체 중심의 개발이 가능하며 1차 캐싱, 쓰기지연, 변경감지, 지연로딩 등을 제공한다.

</details>

<details>
<summary>ORM Framework가 해결하는 Object–relational impedance mismatch 이 무엇인지 아는 만큼 설명해주세요.</summary>

</br>

- 

</details>

<details>
<summary>Hibernate가 제공하는 Cache 방식들에 대해서 아는 만큼 설명해주세요.</summary>

</br>

- 1차 캐시(영속성 컨텍스트 내부에 엔티티를 보관)
  - 동작 방식
  - 1. 최초 조회할 때는 1차 캐시에 엔티티가 없기 때문에 DB에서 조회
  - 2. 엔티티를 1차 캐시에 보관
  - 3. 1차 캐시에 보관된 결과를 반환
  - 4. 이후 같은 엔티티를 조회하면 1차 캐시에 같은 엔티티가 있으므로 데이터베이스를 조회하지 않고 1차 캐시의 엔티티를 그대로 반환
  - 5. 1차 캐시는 객체의 동일성을 (a == b)를 보장
  
- 2차 캐시(애플리케이션 범위의 캐시)
  - 동작 방식
  - 1. 영속성 컨텍스트는 엔티티가 필요하면 2차 캐시를 조회
  - 2. 2차 캐시에 엔티티가 없으면 데이터베이스를 조회
  - 3. 결과를 2차 캐시에 보관
  - 4. 2차 캐시는 자신이 보관하고 있는 엔티티를 복사해서 반환
  - 5. 2차 캐시에 저장되어 있는 엔티티를 조회하면 복사본을 만들어 반환합니다.
  - 6. 2차 캐시는 데이터베이스 기본 키를 기준으로 캐시하지만 영속성 컨텍스트가 다르면 객체 동일성 (a == b)을 보장하지 않음.

</details>

<details>
<summary>JPA의 준 영속 상태와 영속 상태에 대해서 설명해주세요.</summary>

</br>

- 준 영속 상태란 영속상태의 엔티티가 영속성 컨텍스트에서 분리된 상태를 의미
- 영속 상태란 엔티티 매니저에 의해, 영속성 컨텍스트에서 관리되는 상태를 의미
- 영속 상태일 때, 1차 캐시, 변경 감지, 지연 로딩등의 기능을 사용할 수 있다.

</details>



<details>
<summary>JPA Persistence Context이 무엇인지 설명해주시고 제공하는 기능에 대해서 설명해주세요.</summary>

</br>

- 엔티티를 영구 저장하는 환경으로, 애플리케이션과 데이터베이스 사이에서 객체를 보관하는 논리적인 개념이다.
- 영속성 컨텍스트를 사용함으로써, 엔티티를 캐시에 저장하는 1차캐시 기능을 사용할 수 있다.
- 엔티티를 반복 호출할 경우에 1차 캐시에 있는 같은 인스턴스를 반환하므로 동일성을 보장한다.
- 쓰기 지연을 통해 SQL을 한번에 데이터베이스에 보낸다.
- 영속 상태인 엔티티는 값이 수정될 경우, 변경 감지를 통해 데이터베이스에 반영된다.
- 지연로딩을 통해 객체가 필요할 경우에만 추가 쿼리를 실행하므로 성능 향상에 도움이 된다.

</details>


<details>
<summary>JPA MappedSuperclass와 Embeddable Annotation의 차이는 무엇이고 각각 언제 사용해야 되는지 설명해주세요.</summary>

</br>

- MappedSuperclass의 경우, 부모 클래스를 상속 받는 자식 클래스에 매핑 정보만 제공한다. 단순히 엔티티가 공통으로 사용하는 매핑정보를 모으는 역할이다.
- Embeddable type은 엔티티가 아니며, 단순히 값들을 하나로 묶어놓은 것이다.
- 일반적으로 MappedSuperclass를 통해 구현할 경우, 부모 타입과 자식 타입이 강한 결합성을 가짐으로써 캡슐화가 깨지므로 객체지향의 일반적인 법칙을 따라 상속보단 위임을 사용한다.
- 하지만 엔티티 내에 등록일, 수정일과 같은 운영상의 이유를 포함하는 컬럼을 공통으로 사용할 때는 상속을 사용하는게 더욱 편리하다.

</details>


<details>
<summary>JPA의 Fetch 전략 대해서 설명해주세요.</summary>

</br>

- Fetch 전략에는 즉시 로딩, 지연 로딩이 존재한다.
- FetchType이 EAGER일 경우, 엔티티를 조회한 직후 바로, 연관된 엔티티까지 조회하는 방식이다.
- FetchType이 LAZY일 경우, 엔티티를 조회한 후, 추후에 연관된 엔티티를 참조하는 시점에서 해당 엔티티를 조회하는 방식이다.

</details>

<details>
<summary>JPA의 Bulk Data Operations에 대해서 설명해주세요.</summary>

</br>
- 벌크 연산이란 한 번의 쿼리로 대량의 데이터들을 수정하는 것을 말한다.
- 스프링에서 벌크 연산은 UPDATE, DELETE 문을 지원하며, Hibernate는 INSERT 문도 지원한다.
- 벌크 연산은 영속성 컨텍스트를 무시하고 데이터베이스에 직접 쿼리를 날린다.
</details>


<details>
<summary>JPA의 Bulk Data Operations을 이용하였을 경우 발생하는 문제에 대해서 아는만큼 설명해주세요.</summary>

</br>

- 벌크 연산은 영속성 컨텍스트를 무시하므로, 벌크 연산을 실행할 경우 영속성 컨텍스트를 비우는 등의 작업을 통해 데이터베이스와의 동기화가 필요하다.

</details>


<details>
<summary>JPA N+1 문제가 언제 발생하는지 아는 만큼 설명해주세요.</summary>

</br>

- n+1 문제는 JPA Repository를 활용해 인터페이스 메소드를 호출할 때, 1:N 또는 N:1 관계를 가진 엔티티를 조회할 때 발생한다.
- Fetch 전략이 EAGER일 경우, LAZY일 경우, 정도의 차이만 있을 뿐 모두 발생한다.
- JPA Repository로 find 시 실행하는 첫 쿼리에서 하위 엔티티까지 한 번에 가져오지 않고, 하위 엔티티를 사용할 때 추가로 조회하기 때문에 발생한다.

</details>

<details>
<summary>JPA N+1 문제를 해결하는 방법들을 아는 만큼 설명해주세요.</summary>

</br>

- 패치 조인을 통해 엔티티를 조회하는 시점에서 연관된 엔티티까지 한번에 조회한다.
- 일반적으로 Fetch 전략을 모두 LAZY로 설정하고, 성능 최적화가 필요한 곳에 JPQL 페치 조인을 사용하는 것이 추천되는 전략이다.
- BatchSize 설정을 통해 쿼리문이 데이터베이스의 row 수만큼 나가는게 아닌, 설정한 Size만큼 미리 로하도록 한다.

</details>

<details>
<summary>Entity와 Value Object를 구분 지을만한 요소가 무엇이 있을지 말씀해주세요. (무엇이 엔티티로 선언되고, 무엇이 벨류 오브젝트로 선언되는지? 그 구분점은?)</summary>

</br>

- Entity는 식별성과 연속성을 가진 객체이다. DB의 Primary Key등이 식별자 역할을 하며, 엔티티는 자신의 생명주기 동안에 형태와 내용이 변경될 수 있다.
- Entity의 예로는 회원, 상품과 같이 식별이 가능하고 고유성을 지니며, 연속성을 지닌 객체이다.
- 반면 Value Object의 경우, 개념적인 식별성 없이 도메인의 서술적 특면만을 나타내는 객체이다. Value Object는 속성의 값이 중요하기 때문에, 대부분 식별자를 필요로 하지 않는다.
- Value Object은 예를 들어, 가격이라는 테이블이 금액, 통화, 과세정보 등의 컬럼을 지닐 때, 상품이라는 Entity에 포함된 하나의 Value Object라고 표현할 수 있다.

</details>


<details>
<summary>QueryDSL 같은 JPQL Builder를 사용하는 이유를 설명해주세요.</summary>

</br>

- 기존 JPQL은 쿼리문을 String 형식으로 작성하기 때문에 개발자 의존적이다.
- 또한 컴파일 단계에서 Type-Check가 불가해, 런타임시에 오류를 발견하는 치명적인 문제를 야기한다.
- 따라서 QueryDsl과 같이 문자가아닌, 코드를 통한 쿼리문 작성과 컴파일 시점에 오류를 발견할 수 있다는 장점을 지니기 때문에 위와같은 JPQL Builder를 사용한다.
</details>

</br>
</br>

## Network, Web


<details>
<summary>TCP와 UDP의 차이는 무엇인가요?</summary>

</br>

- TCP는 연결 지향적 프로토콜이며, 3-way handshaking 과정을 통해 연결을 설정하고, 4-way handshaking 과정을 통해 연결을 해제한다.
- TCP는 흐름제어, 혼잡제어 및 신뢰성을 보장하기 때문에 파일 전송과 같이 연속성보단 신뢰성이 우선시 되는 경우에 사용한다.
- UDP는 비연결형 프로토콜이며, 데이터의 전송 순서가 바뀔 수 있다.
- UDP는 데이터 수신 여부를 확인하지 않아 신뢰성이 낮으며, 실시간 서비스와 같이 신뢰성보단 연속성이 우선시 되는 경우에 사용한다.
</details>

<details>
<summary>어느 서비스에서 UDP 기반의 프로토콜을 사용하는 것이 좋을까요?</summary>

</br>

- 실시간 스트리밍 동영상과 같이, 중간에 데이터가 손실되는 측면에서의 위험성은 낮고, 속도가 우선시되는 상황에 사용하는 것이 좋다.
</details>


<details>
<summary>3 Way Handshake와 4 Way Handshake는 무엇인가요?</summary>

</br>

- 3 Way Handshake는 정확한 전송을 보장하기 위해 상대방 컴퓨터와 사전에 세션을 수립하는 과정을 의미한다.
  - 1. Client가 Server에게 접속을 요청하는 SYN 플래그를 보낸다.
  - 2. Server는 SYN이 들어온 것을 확인하고 SYN + ACK 플래그를 Client에게 전송한다.
  - 3. SYN + ACK 상태를 확인한 Client는 서버에게 ACK를 보내고 연결 성립(Established)이 된다.
- 4 way handshake는 세션을 종료하기 위해 수행되는 절차를 말한다.
  - 1. Client가 연결을 종료하겠다는 FIN 플래그를 전송한다.
  - 2. FIN 플래그를 받은 Server는 확인메세지인 ACK를 Client에게 보내준다.
  - 3. Close 준비가 다 된 후 Server는 Client에게 FIN 플래그를 전송한다.
  - 4. Client는 해지 준비가 되었다는 정상응답인 ACK를 Server에게 보내준다.
</details>


<details>
<summary>3 Way Handshake는 왜 3번 요청을 주고 받는 것인가요?</summary>

</br>

- 양쪽 모두 데이터를 전송할 준비가 되어있다는 것을 보장하고, 실제로 데이터 전달이 시작하기 전에 다른 한쪽이 준비되었다는 것을 알 수 있도록 하기 위함이다.
</details>


<details>
<summary>TCP Flow Control은 무엇을 해결하기 위한 기능의 집합인가요?</summary>

</br>

- 수신측이 송신측보다 데이터 처리 속도가 빠르면 문제없지만, 송신측의 속도가 더 빠를 경우 생기는 문제인 데이터 손실의 위험을 방지하기 위함이다.
</details>


<details>
<summary>Sliding Window 라는 개념에 대해서 알고 계시나요?</summary>

</br>

- 수신측에서 설정한 윈도우 크기만큼 송신측에서 확인응답없이 세그먼트를 전송할 수 있게 하여 데이터 흐름을 동적으로 조절하는 제어기법이다.
</details>


<details>
<summary>TCP Congestion Control은 무엇을 해결하기 위한 기능의 집합인가요?</summary>

</br>

- 만약 한 라우터에 데이터가 몰릴 경우, 자신에게 온 데이터를 모두 처리할 수 없게 되는 문제를 방지하기 위함이다.
</details>


<details>
<summary>Buffer와 Stream 방식은 각각 무엇인가요? 실시간으로 처리할 필요가 없는 대량의 데이터에 대해서 어떤 방식을 사용하는 것이 효율적일까요?</summary>

</br>

- Buffer 방식은 데이터 전송 시 특정 단위만큼 묶어서 전송하여, 전송 속도 차이에 대한 성능을 보완하기 위해 사용한다.
- Stream 방식은 버퍼의 크기를 작게 만들어, 주기적으로 데이터를 전달한다.
- 실시간으로 처리할 필요가 없는 데이터의 경우에는 Buffer 방식을 사용하여, 잦은 api 호출이 일어나지 않도록 성능을 향상시킨다.
</details>


<details>
<summary>HTTP 멱등성에 대해 설명해주세요.</summary>

</br>

- 동일한 요청을 한 번 보내는 것과 여러 번 연속으로 보내는 것이 같은 효과를 지니고, 서버의 상태도 동일하게 남을 때 HTTP Method 가 멱등성을 갖는다.
</details>


<details>
<summary>HTTP는 무엇인가요?</summary>

</br>

- Hyper Text Transfer Protocol의 두문자어로, 인터넷에서 데이터를 주고받을 수 있는 프로토콜이다.
- 전통적인 클라이언트-서버 모델을 따르며 무상태 프로토콜이다.
- 요청시에 HTTP 메서드, HTTP 메시지, 헤더 등이 존재한다.
- 일반적으로 안정적인 TCP/IP 레이어를 기반으로 사용하는 응용 프로토콜이다.
</details>


<details>
<summary>HTTP의 버전별 차이를 알려주세요. (0.9 1.0 1.1 2.0)</summary>

</br>

- 0.9 : 요청은 단일 라인으로 구성, 메서드는 GET만 존재, 헤더 없음
- 1.0 : HTTP 헤더 도입, 버전 정보와 요청 메서드가 함께 전송, Content-Type을 통한 문서 전송 기능
- 1.1 : Persistent Connection(지정한 타임아웃 동안 커넥션을 닫지 않는 방법)추가, Pipelining(앞 요청의 응답을 기다리지 않고 순차적인 요청 연속적 전송)추가
- 2.0 : 기존 HTTP 1.X 버전의 성능 향상에 초점
</details>


<details>
<summary>Time wait Socket은 무엇일까요?</summary>

</br>

- 마지막 패킷이 제대로 전송 되었는지를 확인하기 위해(패킷 손실이 일어날 수도 있으므로), ACK 전송 이후에 일정 시간동안, 커넥션 상태를 유지하는 것이다.
</details>


<details>
<summary>Keep Alive는 무엇일까요?</summary>

</br>

- 요청마다 커넥션을 생성하는게 아닌, 커넥션을 유지하여 불필요한 연결의 맺고 끊음을 최소하하여, 네트워크의 부하를 줄이는 방법이다.
</details>


<details>
<summary>SYN Flooding 공격에 대해서 아시나요?</summary>

</br>

- TCP의 3 Way Handshake의 취약점을 이용한 공격 방식이다.
- 서버에 과도한 SYN 요청을 보낸 후, 서버의 응답 이후에 ACK를 보내지 않아, 서버 Backlog Queue에 공간을 가득 채워 다른 연결 요청을 불가능하게 만든다.
- Queue Size를 늘리거나, SYN 임게치 설정, TCP연결 대기시간을 줄임으로써 방지할 수 있다.
</details>

<details>
<summary>Polling, Long Polling, Pulling 기법은 각각 무엇이고 어떠한 Trade Off를 가지고 있나요?</summary>

</br>

- Polling : Polling 은 client 가 일정시간 내에 데이터를 얻기 위해 request 를 server 에 보내는 기술을 말한다.
- Short Polling : client 가 데이터를 얻기위해 request를 서버에 보낸 후, 정해진 지연(정해진 시간) 후에 respose 를 얻을 수 있는 기술이다.
  - 간단하며 약간의 지연 발생, 주기가 짧을 경우 서버에 무리를 줄 수 있다.
- Long Polling : client 가 데이터를 위해 request 를 server 에 요청할때, 데이터를 가져오는 것이 불가능할경우, server 가 즉각적으로 반응하지 않고 특정 시간을 기다리는 기술이다.
  - 더 복잡하고 server 자원을 많이 소비한다. 그러나 client 가 지연없이 real-time 경험을 할 수 있도록 한다.
- Pulling : 서버의 데이터를 클라이언트가 직접, 쿼리등을 통해서 주기적으로 가져가는 기술이다.
</details>

<details>
<summary>Server Sent Events와 Web Socket 기법은 무엇이고 어떠한 장, 단점을 가지고 있나요?</summary>

</br>

- Web Socket : HTML5 표준 기술로, 사용자의 브라우저와 서버 사이의 동적인 양방향 연결 채널을 구성한다. Websocket API를 통해 서버로 메세지를 보내고, 요청 없이 응답을 받아오는 것이 가능하다.
- Server Sent Events : 서버의 데이터를 실시간, 지속적으로 클라이언트에 보내는 기술이다.
- SSE는 서버에서 클라이언트로의 단방향 전송이 일어나므로, 프로토콜이나 서버 구현이 필요하지 않다. 또한 클라이언트-서버간에 연결을 유지하지 않아도 되기 때문에 오버헤드가 적다.
- Web Socket은 SSE와 달리 클라이언트 또한 서버에 데이터를 보낼 수 있다.
- 
</details>


<details>
<summary>HTTPS는 무엇인가요?</summary>

</br>

- 기존 HTTP에 보안 요소가 추가된 프로토콜이다.
- 서버와 클라이언트 사이의 모든 통신 내용을 암호화하는 방식이다.
- 기본 TCP/IP 포트는 443이고, SSL 프로토콜 위에서 HTTPS 프로토콜이 동작한다.
</details>

<details>
<summary>구현된 HTTP API는 어떠한 요소들을 만족해야 RESTful한 API 라고 부를 수 있나요?</summary>

</br>

- 클라이언트와 서버간에 의존성이 없어야 한다.(Client-Server)
- 클라이언트에서 서버로의 각 요청에는 그 요청을 이해하는 데 필요한 모든 정보가 포함되어야 한다.(Stateless)
- 요청에 대한 응답 내의 데이터에 해당 요청은 캐시가 가능한지 불가능 한지 명시해야 한다.(Cacheable)
- URI로 지정된 리소스에 균일하고 통일된 인터페이스를 제공해야 한다.(Uniform Interface)
- 서버는 중개 서버(게이트웨이, 프록시)나 로드 밸런싱, 공유 캐시 등의 기능을 사용하여 확장성 있는 시스템을 구성할 수 있다.(Layered System)
- 클라이언트는 서버에서 자바 애플릿, 자바스크립트 실행 코드를 전송받아 기능을 일시적으로 확장할 수 있다.(Code-On-Demand)
</details>



<details>
<summary>get은 무엇이고 어느 상황에 주로 사용하나요?</summary>

</br>

- GET 메소드는 주로 데이터를 읽거나(Read) 검색(Retrieve)할 때에 사용되는 메소드이다.
- HTTP 명세에 의하면 GET 요청은 오로지 데이터를 읽을 때만 사용되고 수정할 때는 사용하지 않는다.
- 멱등성이 보장되어야 한다.
</details>

<details>
<summary>put과 patch는 무엇이고 각각 언제 사용되나요?</summary>

</br>

- put의 경우 리소스의 모든 부분을 업데이트 하기 위한 메서드이다.
- patch의 경우 요청된 리소스에 한해 일부만 변경하기 위한 메서드이다.
- put은 비어져있는 값에 대해 null로 업데이트한다.
</details>

<details>
<summary>User라는 리소스가 하위로 item이라는 리소스를 가지고 있습니다. 이를 조회해야할 때 RESTful하게 URL을 설계한다면 어떤 형태의 URL에 GET을 요청하게 되나요?</summary>

</br>
- http://restapi.example.com/user/1/item/1
</details>

<details>
<summary>통신시 사용되는 대표적인 Format으로는 무엇이 있나요?</summary>

</br>
- 일반 Text 데이터, CSV, XML, JSON 등이 있다.
</details>

<details>
<summary>JSON은 무엇인가요?</summary>

</br>
- JavaScript Object Notation라는 의미의 축약어로 데이터를 저장하거나 전송할 때 많이 사용되는 경량의 DATA 교환 형식이다.
</details>

<details>
<summary>Cookie와 Session 방식은 어떠한 차이점을 가지나요?</summary>

</br>
- 쿠키는 클라이언트 측에 저장이 되어, Request 시에 자동으로 헤더에 포함되어 서버에 전송된다. (속도가 빠르나 로컬에 저장되기 때문에 변질 및 snipping의 우려)
- 사용자의 정보를 세션id 를 통해 서버측에 저장하고 관리한다. (보안면에서 우수하나 서버의 부담이 증가한다.)
- 추가) 캐시와는 엄연히 다름 - 캐시는 브라우저나 서버 앞단에 css, js 등 파일을 저장해놓고 사용하는것, 라이프사이클 자체가 다름.
</details>

<details>
<summary>Local, Global, Distributed Session에 대해서 아는 만큼 설명해주세요.</summary>

</br>
- 
</details>

<details>
<summary>JWT란 무엇인가요? 왜 사용하게 되는 것인가요?</summary>

</br>
- Json 포맷을 이용하여 사용자에 대한 속성을 저장하는 Claim 기반의 Web Token이다.
- 일반적으로 클라이언트 측의 인가 및 권한을 위해서 JWT를 통해 검증한다.
- 세션을 통한 인증 방식과 비교하여, 서버측의 부하를 줄일 수 있다는 장점이 있다.
</details>

<details>
<summary>Servlet Spec은 무엇이고 CGI와 어떠한 차이점을 가지고 있나요?</summary>

</br>
- 서블릿은 클라이언트 요청에 따라 동적으로 컨텐츠를 만들 수 있는 java 기술이다. 서블릿 자체는 java로 만들어진 하나의 클래스이므로 jvm이 필수이다.
- CGI는 웹서버와 동적 컨텐츠를 만들어내는 프로그램간의 방법을 정의한 규격이다.
- 서블릿은 쓰레드를 실행시켜, CGI보다 서버 자원성 측면에서 유용하다.
</details>


<details>
<summary>WAS는 무엇인가요?</summary>

</br>
- 인터넷 상에서 HTTP를 통해 사용자 컴퓨터나 장치에 애플리케이션을 수행해주는 미들웨어이다.
- 웹 서버와 달리, WAS는 동적 서버 컨텐츠를 수행한다.
- 웹서버 + 웹 컨테이너(JSP나 Servlet을 실행시킬 수 있는 SW-서블릿 컨테이너)라고 볼 수 있다.
</details>


<details>
<summary>gRPC에 대해서 아시나요?</summary>

</br>
- 구글에서 개발한 어느 환경에서 실행할 수 있는 최신 오픈 소스 고성능 RPC 프레임워크이다.
</details>

</br>

## Etc.

<details>
<summary>프레임워크와 라이브러리 차이는 무엇인가요?</summary>

</br>
- 프레임워크 : 기능 구현에 집중하여 개발할 수 있도록 일정한 형태와 기능을 갖추고 있는 골격, 뼈대를 의미
- 라이브러리 : 개발 시에 특전 기능을 모아둔 코드, 함수들의 집합
- 가장 큰 차이는 라이브러리의 경우, 애플리케이션의 코드의 흐름은 사용자의 의해 제어된다. 반면 프레임워크는 애플리케이션의 코드가 프레임워크에 의해 제어된다.
</details>

<details>
<summary>디자인 패턴이란 무엇인가요?</summary>

</br>
- 기존 환경 내에서 반복적으로 일어나는 문제들을 어떻게 풀어나갈 것인가에 대한 일종의 솔루션이다.
</details>

<details>
<summary>Monolitc Architecture, Micro Service Architecture에 대해 각각 설명해 주세요.</summary>

</br>
- Monolitc Architecture : 전통적인 웹 시스템 개발 스타일로, 하나의 애플레케이션 내에 모든 로직이 들어가 있는 구조이다.
- Micro Service Architecture : 작은 서비스 여러개가 모여서 하나의 시스템을 제공하는 아키텍처를 의미한다.
</details>

<details>
<summary>Thread-safe한 프로그래밍이란 어떤 것인가요?</summary>

</br>
- 멀티 스레드 프로그래밍에서 일반적으로 어떤 함수나 변수, 혹은 객체가 여러 스레드로부터 동시에 접근이 이루어져도 프로그램의 실행에 문제가 없도록 하는 것이다.
</details>

<details>
<summary>CAP 이론에 대해서 아시나요?</summary>

</br>
- "적절한 응답 시간 내 세 가지 속성을 모두 만족시키는 분산 시스템을 구성할 수 없다”는 이론이다.
- 세가지 속성은 일관성, 가용성, 분할 허용성이다.
- 분산 데이터베이스 시스템은 분할이 생겼을 때 일관성과 가용성 중 하나를 희생해야 한다는 것을 의미한다.
</details>

<details>
<summary>WEB API의 성능 최적화를 위해서는 어떤 부분들을 고려해야 할까요?</summary>

</br>
- 캐싱 설정을 통해 특정 시간 만큼 api에 대한 재요청을 방지한다.
- 사용자가 요청하는 데이터보다 더 많은 데이터를 보내주는 오버 패칭을 방지한다.
- 조회의 경우 페이징과 같이 필터링을 통해, 소수의 데이터만 반환한다.

</details>

<details>
<summary>Stateless와 Stateful의 차이점은 무엇인가요?</summary>

</br>
- Stateless의 경우 서버측에서 상태를 저장하지 않기 때문에, 요청 시에 상태에 관한 데이터가 포함되어야 한다.
- Stateful의 경우 서버측에 상태 정보가 저장되어있어, 사용자는 서버를 통해 상태를 확인한다.
- Stateless의 경우 클라이언트 측의 정보에 의존하기 때문에, 서버 확장성 측면에서 이점이 있으며, 서버의 자원 또한 덜 사용하게 된다.

</details>
