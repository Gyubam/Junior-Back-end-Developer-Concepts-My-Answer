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





