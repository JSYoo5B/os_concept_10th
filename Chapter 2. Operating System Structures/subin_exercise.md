#### 2.9 운영체제가 제공하는 서비스와 기능은 크게 두 범주로 나눌 수 있다. 두 범주에 대해 간략히 설명하고 차이점을 논의하시오. (p62~64)
->
운영체제가 제공하는 사용자 인터페이스, 프로그램 수행, 입출력 연산, 파일 시스템 조작, 통신, 오류 탐지 서비스는 사용자에게 편리함을 제공하는 기능인 반면에 자원 할당, 기록 작성, 보호와 보안 기능은 시스템의 효율적인 작동을 위한 기능이다.

#### 2.10 운영체제에게 매개변수를 전달하는 보편적인 방법 3가지를 설명하시오. (p73)
->
1. 매개변수를 레지스터에 전달하는 방법. 단, 매개변수가 레지스터보다 많은 경우 이용이 불가능하다.

2. 매개변수를 메모리 내의 블록이나 테이블에 저장하고, 블록의 주소를 레지스터 내에 매개변수로 전달하는 방법.

3. 스택에 push 또는 pop 연산을 수행하여 매개변수를 저장, 읽어오는 방법.

#### 2.11 프로그램 코드의 각 영역을 실행하는 데 걸린 시간에 대한 통계 프로파일을 얻는 방법에 관해 설명하시오. 이러한 통계 프로파일을 확보하는 것이 중요한 이유에 대해 논의하시오.
->
 운영체제가 제공하는 서비스 중 회계 기능을 통해 프로파일을 얻을 수 있다. 이를 통해 어떤 프로세스가 자원을 얼마나 사용하는지 추적할 수 있어서 자원 할당 등 운영체제가 더욱 개선되고 효율적인 서비스를 제공하기 위해서는 이러한 통계 프로파일을 확보하는 것이 중요하다. 

#### 2.12 파일과 장치를 조작할 때 같은 시스템 콜 인터페이스를 사용하는 것의 장단점은 무엇인가? (단점 좀 더 생각해보기)
-> 
 같은 시스템 콜 인터페이스를 사용하게 되면 시스템 호출부터 서비스 제공까지의 시간이 빨라진다. 하지만 구현이 어렵다는 단점이 있다.

#### 2.13 사용자가 운영체제에서 제공하는 시스템 호출 인터페이스를 사용하여 새로운 명령 인터프리터를 개발할 수 있는가?
->
 개발할 수 있다. 운영체제가 제공하는 시스템 호출 인터페이스를 사용하여 새로운 명령 인터프리터를 개발한 대표적인 예시가 바로 컴파일러이다. 컴파일러는 사용자가 입력한 고수준 언어를 시스템 호출 인터페이스의 조합으로 해석해준다.

#### 2.14 안드로이드가 just-in-time(JIT)이 아닌 ahead-of-time(AOT)을 사용하는 이유를 설명하시오.
->
AOT : 소스 코드를 미리 컴파일하는 방식, 속도가 상대적으로 빠르며 CPU 사용량이 상대적으로 낮다.

JIT : 브라우저에서 파일들을 다운로드 한 뒤에 한 번 컴파일해서 브라우저 엔진이 실행할 수 있는 저수준 언어로 바꿔준 후, 화면을 렌더링하는 방식, 실행 속도가 상대적으로 느리며, CPU 사용량이 AOT에 비해 높다.

따라서 실행 속도가 상대적으로 빠르며 CPU 사용량이 적은 AOT를 사용하는 것이 효율적이다.

#### 2.15 프로세스 간 통신의 두 가지 모델은 무엇인가? 각 모델의 장단점은 무엇인가? (p81)
->
 프로세스 간 통신의 두 가지 모델에는 공유 메모리와 메시지 전달 모델이 있다. 메시지 전달 모델은 공유 메모리 모델보다 구현이 쉬우며 데이터 교환 시 충돌이 일어나지 않는다는 점이 장점이다. 하지만 통신 속도가 공유 메모리 모델보다 느리며 매번 시스템 콜이 호출되어 이로 인한 오버헤드가 자주 발생한다는 점이 단점이다.

#### 2.16 API와 ABI를 대비하고 비교해보아라.
-> 
 API는 소프트웨어의 소스 코드 레벨에서 서로 인터페이스 하는 방식을 정의한다. 일반적으로 API 표준 인터페이스는 함수이며 상위 레벨의 소프트웨어에서 하위 레벨의 소프트웨어를 호출할 수 있다. API가 소스 코드 수준의 인터페이스를 정의한다면, ABI는 특정 아키텍처 간에서 동작하는 소프트웨어 간의 바이너리 인터페이스를 정의한다. 
 또한, API가 소스 코드 수준의 호환성을 보장한다면, ABI는 바이너리의 호환성을 보장하여 오브젝트 코드를 다시 컴파일하는 수고 없이 같은 ABI를 지원하는 시스템이라면 동일한 기능을 수행하도록 보장한다.

#### 2.17 기법과 정책을 분리하는 것이 바람직한 이유는 무엇인가? (p88~89)
->
 기법이란 어떤 일을 어떻게 할 것인가를 결정하는 것, 정책은 무엇을 할 것인가를 결정하는 것이다. 정책은 장소가 바뀌거나 시간의 흐름에 따라 변경될 수 있다. 이때, 기법과 정책이 분리되어 있다면 정책의 수정만으로도 해당 환경에 반영할 수 있다. 

#### 2.18 운영체제의 두 구성요소가 서로에게 종속적이면 계층구조로 시스템을 구성하는 것이 어려울 때가 있다. 서로의 기능이 밀접하게 연결되어 있어서 계층구조로 나누는 방법이 불분명한 경우를 제시하시오.
->
  
#### 2.19 시스템을 설계할 때 마이크로커널 방식을 사용하는 장점은 무엇인가? 마이크로커널 구조에서 사용자 프로그램과 시스템 서비스가 상호작용하는 방식에 대해 설명하시오, 마이크로커널 방식을 사용할 때의 단점은 무엇인가? (p94)
->
 마이크로커널은 중요치 않은 구성요소를 커널로부터 제거하고, 그들을 별도의 주소 공간에 존재하는 사용자 수준 프로그램으로 구현하여 운영체제를 구성하는 방법이다. 마이크로커널은 확장성이 뛰어나고 새로운 시스템에 이식하기 쉬우며, 더욱 높은 보안성과 신뢰성을 제공한다는 장점이 있다. 하지만 가중된 시스템 기능 오버헤드 때문에 성능이 나빠진다는 단점이 있다. 

 마이크로커널에서 사용자 프로그램과 시스템 서비스가 상호작용하는 방법은 주로 메시지 전달 기법을 사용한다. 사용자 프로그램이 운영체제에 메시지를 전달하면 마이크로커널은 인터럽트를 처리하는 프로세스에게 사용자 프로그램의 메시지를 전달한다. 이후 인터럽트 처리기는 메시지를 스케줄링하여 처리한다.

#### 2.20 적재 가능 커널 모듈을 사용하는 장점은 무엇인가? (p95~96)
->
 적재 가능 커널 모듈은 전체적으로 커널의 각 부분이 정의되고 보호된 인터페이스를 가진다는 점에서 계층구조를 닮았지만, 다른 모듈을 호출할 수 있다는 점에서 계층구조보다 유연하다. 중심 모듈은 핵심 서비스만을 제공하고 다른 모듈의 적재 방법과 통신 방법을 안다는 점에서는 마이크로커널과 유사하다. 하지만 통신을 위해 메시지 전달을 호출할 필요가 없어 더 효율적이다. 
 즉, 적재 가능 커널 모듈은 계층구조와 마이크로커널의 장점은 부각하고 단점은 보완한 커널이다.

#### 2.21 iOS와 Android의 유사점을 설명하시오. 둘의 차이점은 무엇인가? (p96~100)
->
 iOS와 Android의 공통점은 모두 모바일 운영체제이며 다양한 기능을 지원하는 프레임워크를 제공하는 소프트웨어 스택이라는 점이다. 
 iOS는 아이폰과 아이패드를 위해 설계된 운영체제이며 Android는 Android 스마트 폰과 태블릿을 위해 개발되었다는 점에서 차이점을 보인다. 또한 iOS는 소스가 공개되지 않았지만, Android는 오픈소스이다.

#### 2.22 Android 시스템에서 실행되는 Java 프로그램이 표준 Java API와 가상머신을 사용하지 않는 이유에 관해 설명하시오. (p99~100)
->
 Android는 Dalvik 가상머신을 사용하는데 이 가상머신은 JVM보다 메모리를 적게 사용하고, 빠른 CPU 처리 능력을 갖췄다. 즉, Dalvik을 사용하는 것이 모바일에 최적화되어있기 때문이다.

#### 2.23 실험적인 Synthesis 운영체제는 커널 안에 어셈블러가 포함되어 있다. 시스템 호출의 성능을 최적화하기 위해, 커널은 커널 공간 내의 루틴을 어셈블 하여 반드시 지나가야 할 커널 경로를 최소화한다. 이러한 접근 방법은 계층적 접근 방법과는 반대되는 것으로 계층적 접근 방법에서는 운영체제 구현을 쉽게 하도록 커널 경로를 연장한다. 커널 설계 측면과 시스템 성능 최적화 측면에서 Synthesis 방식의 장단점을 논의하시오.
-> 