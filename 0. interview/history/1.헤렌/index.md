## 쿠키와 세션 설명 및 차이점

쿠키와 세션은 웹 개발에서 사용자의 상태를 유지하기 위해 사용되는 기술입니다. 사용자가 웹 사이트를 방문할 때, 서버와 클라이언트 간의 상태를 유지하지 않는 HTTP 프로토콜의 무상태성을 보완하기 위해 이들이 사용됩니다. 쿠키와 세션은 비슷한 목적을 가지고 있지만, 구현 방식과 사용하는 리소스, 보안성 등에서 차이가 있습니다.

### 쿠키 (Cookies)
***정의:*** 쿠키는 클라이언트 측에 저장되는 작은 데이터 조각입니다. 웹 서버가 HTTP 응답 헤더를 통해 클라이언트에게 쿠키를 전송하고, 이후 클라이언트는 동일한 서버에 요청할 때마다 쿠키 정보를 HTTP 요청 헤더에 포함시켜 보냅니다.

***특징:*** 클라이언트(브라우저)에 저장되며, 각 쿠키는 도메인별로 구분됩니다. 사용자 식별, 세션 관리, 사용자 선호도 기억 등에 사용됩니다. 쿠키는 만료 기간을 가지고 있으며, 지정된 기간 동안 데이터를 유지할 수 있습니다.

***보안:*** 쿠키 데이터는 클라이언트에 저장되기 때문에 변조 가능성이 있고, 네트워크를 통해 전송될 때도 도청될 수 있습니다. 따라서 중요한 정보는 쿠키에 저장하지 않아야 하며, 보안을 위해 HTTPS와 함께 Secure 속성, HttpOnly 속성 등을 사용하는 것이 좋습니다.

### 세션 (Sessions)
***정의:*** 세션은 서버 측에서 사용자 정보를 유지하는 방법입니다. 사용자가 웹 사이트에 접속하면, 서버는 고유한 세션 ID를 생성하여 클라이언트에게 전달합니다. 이 세션 ID를 통해 클라이언트는 서버에 접속할 때마다 자신을 식별할 수 있고, 서버는 이 ID를 통해 사용자의 상태 정보를 세션에 저장하고 관리합니다.

***특징:*** 사용자 정보를 서버에 저장합니다. 세션 ID는 클라이언트에 저장될 수 있으며(쿠키, URL 등을 통해), 이 ID로 서버에서 사용자 정보에 접근합니다. 서버의 메모리를 사용하므로, 대규모 트래픽이 발생하는 웹 사이트에서는 세션 관리가 서버에 부담을 줄 수 있습니다.

***보안:*** 세션은 사용자 정보를 서버에 저장하기 때문에 쿠키보다 보안성이 높습니다. 사용자는 세션 ID만을 가지고 있으며, 이 ID를 통해 서버에서 관련 정보를 조회합니다.

### 쿠키와 세션의 주요 차이점
***저장 위치:*** 쿠키는 클라이언트에, 세션은 서버에 저장됩니다.

***보안:*** 세션은 쿠키보다 상대적으로 보안성이 높습니다.

***생명 주기:*** 쿠키는 개발자가 지정한 만료 시간까지 클라이언트에 저장되며, 세션은 사용자가 브라우저를 닫거나 서버에서 세션을 명시적으로 만료시킬 때까지 유지됩니다.

***자원 사용:*** 세션은 서버의 자원을 사용하므로 많은 양의 세션 정보 관리는 서버에 부담을 줄 수 있습니다. 쿠키는 클라이언트의 저장 공간을 사용합니다.

## 트랜잭션에 대한 설명
트랜잭션은 데이터베이스 관리 시스템(DBMS)에서 안정성을 보장하기 위해 사용되는 중요한 개념입니다. 트랜잭션은 하나의 논리적 작업 단위로, 여러 개의 연산을 포함할 수 있으며, 이들 연산은 모두 성공하거나 모두 실패해야 합니다. 이러한 특성으로 인해, 트랜잭션은 데이터의 일관성과 안정성을 유지하는 데 필수적입니다.

### 트랜잭션의 ACID 속성
트랜잭션의 특성은 ACID 속성으로 요약됩니다:

***원자성(Atomicity):*** 트랜잭션 내의 모든 연산은 하나의 단위로 취급되어, 모두 성공하거나 모두 실패해야 합니다. 중간 상태에서 실패하면, 트랜잭션 전체가 롤백되어야 합니다.

***일관성(Consistency):*** 트랜잭션 실행 전후에 데이터베이스의 일관성이 유지되어야 합니다. 즉, 트랜잭션이 데이터베이스의 일관된 상태를 다른 일관된 상태로 변화시켜야 합니다.

***독립성(Isolation):*** 동시에 실행되는 여러 트랜잭션이 서로에게 영향을 주지 않도록 격리되어야 합니다. 이는 동시성 제어를 통해 관리됩니다.

***지속성(Durability):*** 트랜잭션이 성공적으로 완료되면, 그 결과는 영구적으로 데이터베이스에 반영되어야 합니다. 시스템에 장애가 발생해도, 이러한 변경 사항은 보존되어야 합니다.

### 트랜잭션의 중요성
트랜잭션은 데이터의 무결성과 일관성을 보장합니다. 예를 들어, 은행 시스템에서 A 계좌에서 B 계좌로 돈을 이체하는 경우, 해당 작업은 두 개의 연산으로 구성됩니다: A 계좌에서 돈을 차감하고, B 계좌에 돈을 추가합니다. 이 두 연산은 트랜잭션의 일부로 묶여 있으며, 두 연산이 모두 성공하거나, 하나라도 실패할 경우 전체 트랜잭션이 취소(롤백)되어야 합니다. 이를 통해, 데이터의 일관성이 유지됩니다.

### 트랜잭션의 관리
DBMS는 트랜잭션의 ACID 속성을 보장하기 위해 여러 기술을 사용합니다. 예를 들어, 롤백 로그를 사용하여 원자성과 지속성을 구현하고, 잠금(Locking)과 타임스탬프를 사용하여 독립성을 보장합니다. 또한, 일관성은 트랜잭션이 데이터베이스의 무결성 제약 조건을 준수하도록 함으로써 유지됩니다

## 스택과 큐에 대한 설명 및 사용처

### 스택(Stack)
***정의:*** 스택은 LIFO(Last In, First Out) 방식으로, 마지막에 들어온 데이터가 가장 먼저 나가는 구조를 가집니다. 이는 쌓여 있는 접시를 생각하면 이해하기 쉽습니다; 가장 위에 놓인 접시를 가장 먼저 사용합니다.

***기본 연산:*** 주로 push(데이터 추가), pop(데이터 제거 및 반환), peek(맨 위 데이터 조회) 등의 연산을 지원합니다.

***사용 예시:***
1. 함수 호출 관리: 컴퓨터의 함수 호출 시스템은 스택을 사용하여 각 함수의 반환 주소와 지역 변수를 저장합니다. 이를 통해 함수 호출이 끝나면 이전 함수로 제어를 올바르게 반환합니다.
2. 문자열 역순 출력: 문자열의 각 문자를 스택에 push한 후, pop을 사용하여 역순으로 출력할 수 있습니다.
괄호 검사: 프로그래밍 코드에서 괄호의 짝이 맞는지 검사할 때 스택을 사용할 수 있습니다. 여는 괄호를 만날 때마다 스택에 push하고, 닫는 괄호를 만날 때마다 pop하여 짝을 확인합니다.

### 큐(Queue)
***정의:*** 큐는 FIFO(First In, First Out) 방식으로, 처음에 들어온 데이터가 가장 먼저 나가는 구조를 가집니다. 마치 사람들이 줄을 서서 기다리는 것과 유사합니다.

***기본 연산:*** 주로 enqueue(데이터 추가), dequeue(데이터 제거 및 반환), front(첫 번째 데이터 조회) 등의 연산을 지원합니다.

***사용 예시:***
1. 프린터의 인쇄 대기열: 여러 문서가 프린터로 보내질 때, 큐를 사용하여 인쇄 작업을 순차적으로 관리할 수 있습니다. 먼저 요청된 문서가 먼저 인쇄됩니다.
2. 네트워크 요청 처리: 웹 서버가 동시에 들어오는 수많은 요청을 처리할 때, 큐를 사용하여 요청을 순차적으로 처리할 수 있습니다.
3. 키보드 버퍼: 사용자가 키보드를 통해 입력하는 키들은 큐에 저장되어 순차적으로 처리됩니다.

## REST API 설명
REST API는 네트워크 상의 두 시스템 간의 통신을 위한 규칙, 규약, 또는 인터페이스를 의미합니다. REST는 분산 시스템 설계를 위한 아키텍처 스타일 중 하나로, 웹 기술과 HTTP 프로토콜을 사용하여 애플리케이션 간의 상호 운용성을 제공합니다. REST API를 사용하여, 클라이언트는 서버로부터 자원(Resource)을 요청하거나 자원에 대한 조작을 수행할 수 있습니다.

### REST의 주요 원칙
REST 아키텍처 스타일은 다음과 같은 여러 가지 핵심 원칙을 기반으로 합니다:

***클라이언트-서버 분리:*** 클라이언트와 서버는 서로 독립적으로 동작해야 하며, 각각의 진화가 다른 쪽에 영향을 주지 않아야 합니다. 이를 통해 각 시스템의 확장성과 유지보수성이 향상됩니다.

***무상태성(Stateless):*** 각 요청은 독립적이며, 서버가 클라이언트의 상태 정보를 저장하지 않아야 합니다. 이는 서버의 처리를 단순화하고 확장성을 높입니다.

***캐시 가능성(Cacheable):*** 클라이언트는 서버로부터 받은 응답을 캐시할 수 있어야 합니다. 캐싱을 통해 클라이언트의 요청을 줄이고, 서버의 부담을 경감시킬 수 있습니다.

***계층화된 시스템(Layered System):*** 클라이언트는 최종 서버와 직접 통신하는지, 중간에 다른 계층이 있는지 알 수 없어야 합니다. 이를 통해 네트워크의 구조를 유연하게 관리할 수 있습니다.

***코드 온 디맨드(Code on Demand, 선택적):*** 서버는 실행 가능한 코드를 클라이언트에 전송할 수 있습니다(예: 자바스크립트). 이는 클라이언트의 기능을 임시적으로 확장할 수 있게 해줍니다.

일관된 인터페이스(Uniform Interface): 일관된 인터페이스를 통해 시스템 간의 상호 작용이 단순화됩니다. 이 원칙에는 리소스 식별, 자기-기술적 메시지(self-descriptive messages), 하이퍼미디어를 통한 애플리케이션 상태의 엔진으로서의 사용(HATEOAS) 등의 개념이 포함됩니다.

### REST API 디자인 규칙
***리소스 기반 URL 사용:*** 리소스를 식별하는 데 사용되며, 일반적으로 명사를 사용합니다. 예: /users, /orders

***HTTP 메소드 활용:*** 리소스에 대한 CRUD(Create, Read, Update, Delete) 작업을 정의하는 데 사용됩니다. 예: GET(조회), POST(생성), PUT(전체 업데이트 또는 생성), PATCH(부분 업데이트), DELETE(삭제)

***상태 코드 사용:*** 응답 메시지에 HTTP 상태 코드를 포함하여 요청의 성공 또는 실패 여부를 나타냅니다. 예: 200(성공), 404(찾을 수 없음), 500(서버 에러)


## spring framework 의 3대 컨셉 및 설명
***DI, IOC, AOP***

### DI (Dependency Injection, 의존성 주입)
***정의:*** 객체가 필요로 하는 의존성(다른 객체)을 외부에서 주입하는 디자인 패턴입니다. 이를 통해 객체 간의 결합도를 낮출 수 있습니다.

***중요성:*** 객체가 직접 의존성을 생성하지 않고 외부에서 주입받음으로써, 코드의 재사용성과 테스트 용이성이 향상됩니다. 변경에 더 유연하게 대응할 수 있으며, 의존성 관리가 용이해집니다.

***사용 예:*** Spring에서는 @Autowired 어노테이션을 통해 DI를 구현합니다. 이는 생성자, 필드, 세터 메소드에 적용할 수 있으며, Spring 컨테이너가 자동으로 의존성을 주입합니다.

>***참고사항:*** @Autowired 어노테이션은 Spring에서 의존성 주입(Dependency Injection)을 위해 널리 사용됩니다. 이 어노테이션을 통해 개발자는 명시적으로 생성자, 필드, 또는 세터 메소드에 의존성을 주입할 수 있으며, Spring IoC(Inversion of Control) 컨테이너가 자동으로 필요한 빈(Bean)을 찾아 주입합니다. 그러나 @Autowired의 과도한 사용은 몇 가지 문제를 일으킬 수 있으며, 다음과 같은 이유로 사용을 줄이는 것이 권장됩니다.

>1. 코드의 명시성 감소  
>@Autowired를 필드 주입에 사용할 경우, 의존성이 클래스 내부에 숨겨져 코드를 분석하기 어렵게 만듭니다. 특히, 대규모 프로젝트나 여러 개발자가 협업하는 환경에서는 코드의 명시성이 중요합니다.
>2. 변경 불가능한(Immutable) 객체 사용의 제한  
필드 주입을 사용하면, 생성 후에는 의존성을 변경할 수 없으므로 객체의 불변성을 보장하기 어렵습니다. 생성자 주입을 사용하면 객체를 불변으로 유지할 수 있으며, 모든 의존성이 생성 시점에 주입되어야 함을 명시적으로 보장합니다.
>3. 테스트의 어려움  
필드 주입을 사용하면, 단위 테스트를 작성할 때 의존성을 명시적으로 주입하기 어렵습니다. 테스트 코드에서 객체를 생성할 때 생성자나 세터를 통해 테스트 대상의 의존성을 쉽게 주입할 수 있습니다. 그러나 @Autowired를 사용한 필드 주입은 리플렉션을 통해야만 의존성을 주입할 수 있어, 테스트 코드 작성을 복잡하게 만듭니다.
>4. 순환 참조 문제  
@Autowired 필드 주입을 사용하면, 런타임 시에 순환 참조가 발생할 위험이 있으며, 이는 애플리케이션의 시작 실패로 이어질 수 있습니다. 생성자 주입을 사용하면, 컴파일 시점에 순환 참조 문제를 감지할 수 있어 더 안전합니다.

>***권장 사항***
따라서, @Autowired의 사용을 줄이고, 대신 생성자 주입을 사용하는 것이 권장됩니다. 생성자 주입은 의존성 주입의 명시성을 높이고, 객체의 불변성을 유지하며, 단위 테스트의 작성을 용이하게 하고, 순환 참조 문제를 컴파일 시점에 발견할 수 있도록 해줍니다. Spring Framework 4.3 이후부터는 단일 생성자를 가진 클래스에서는 @Autowired 어노테이션을 생략할 수 있으므로, 더욱 깔끔한 코드를 작성할 수 있습니다.

### IoC (Inversion of Control, 제어의 역전)
***정의:*** 프로그램의 제어 흐름을 사용자가 아닌 프레임워크에게 맡기는 것을 의미합니다. 객체의 인스턴스화와 생명 주기 관리를 컨테이너가 담당합니다.

***중요성:*** 개발자는 비즈니스 로직에만 집중할 수 있게 되며, 프레임워크가 애플리케이션의 흐름을 제어합니다. 이를 통해 코드의 모듈성과 유연성이 증가합니다.

***사용 예:*** Spring 프레임워크는 IoC 컨테이너를 제공하여 객체의 생성과 생명 주기를 관리합니다. 개발자는 Spring의 Bean 정의를 통해 객체 관리를 Spring 컨테이너에 위임합니다.

### AOP (Aspect-Oriented Programming, 관점 지향 프로그래밍)
***정의:*** 애플리케이션의 핵심적인 관심사와 이를 가로질러 있는 관심사(횡단 관심사)를 분리하는 프로그래밍 패러다임입니다. 로깅, 트랜잭션 관리 등 여러 모듈에서 공통적으로 사용되는 기능을 Aspect로 모듈화하여 관리합니다.

***중요성:*** 코드 중복을 줄이고, 모듈 간의 결합도를 낮춰 애플리케이션의 유지보수성을 향상시킵니다. 공통 기능의 변경이 필요할 때 Aspect만 수정하면 되므로, 변경 관리가 용이해집니다.

***사용 예:*** Spring AOP에서는 @Aspect 어노테이션을 사용하여 Aspect를 정의합니다. @Before, @After, @Around 등의 어노테이션을 통해 어떤 메소드의 실행 전후에 특정 로직을 실행할지 정의할 수 있습니다.



