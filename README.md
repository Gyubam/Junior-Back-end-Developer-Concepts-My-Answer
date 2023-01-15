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

</br>
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


