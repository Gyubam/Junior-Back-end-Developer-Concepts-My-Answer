### 취업 면접 질문 사안들에 대해 공부 및 작성한 답변

</br>

질문 리스트 출처 : https://github.com/Lob-dev/Junior-Back-end-Developer-Concepts/blob/main/Job%20interview.md

</br>

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



