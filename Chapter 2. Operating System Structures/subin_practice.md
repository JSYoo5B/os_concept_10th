## [공룡책 2장 Practice Problems]

#### 2.1 시스템 콜의 목적은 무엇인가? (p68~69)
-> 시스템 콜을 호출하여 운영체제에 의해 사용 가능한 서비스를 사용하기 위함이다.

#### 2.2 명령 인터프리터의 목적은 무엇인가? 통상 커널에 포함되지 않는 이유는 무엇인가? (p64~66)
-> 
목적 : 명령 인터프리터는 사용자가 직접 운영체제가 수행할 명령어를 입력할 수 있도록 한다. 또한, 명령어들은 적합한 프로그램 로직을 가진 새로운 파일을 생성함으로써 쉽게 추가할 수 있다. 통상 커널에 포함되지 않는 이유는 명령 인터프리터가 바뀔 수 있기 때문이다.
(통상 커널에 포함되지 않는 이유는 답지 참고, 왜 명령 인터프리터가 바뀔 수 있는지 이유를 모르겠음)

#### 2.3 UNIX 시스템에서 새 프로세스를 시작하기 위해 명령 인터프리터나 셸에서 어떤 시스템 콜이 호출되어야 하는가? (p78)
->
 새 프로세서를 시작하기 위해서는 fork() 시스템 콜을 실행한다, 그 후, 선택된 프로그램이 exec() 시스템 콜을 호출하여 메모리에 적재된다. 

#### 2.4 시스템 프로그램의 목적은 무엇인가?
->
 시스템 프로그램은 사용자가 컴퓨터 하드웨어 및 각종 정보를 효율적으로 사용할 수 있도록 하기 위한 프로그램의 집합체로 사용자의 편리한 서비스의 제공을 목적으로 한다. 

#### 2.5 시스템 설계 시 계층화된 접근 방식의 주요 장점은 무엇인가? 계층화된 접근 방식의 단점은 무엇인가? (p92~93)
->
 계층적 접근의 주된 장점은 구현과 디버깅의 간단함에 있다. 각 층은 오직 자신의 하위층들 서비스와 기능/연산들만을 사용하도록 선택되기 때문에 시스템의 검증과 디버깅 작업을 단순화한다. 또한, 시스템을 계층적으로 나누면 시스템의 설계나 구현이 간단해진다.

 계층적 접근의 단점은 각 계층의 기능을 적절히 정의해야 하는 문제와, 이러한 시스템의 전반적인 성능은 운영체제 서비스를 얻기 위해 사용자 프로그램이 여러 계층을 통과해야 하므로 오버헤드가 발생할 수 있다는 점이다. 

#### 2.6 운영체제에서 제공하는 5가지 서비스를 나열하고 각 서비스가 사용자에게 편의를 제공하는 방법을 설명하라. 사용자 수준 프로그램이 이러한 서비스를 제공할 수 없는 경우는 언제인가? 여러분의 답을 설명하라. (p62~64)
-> 
1. 프로그램 실행 : 시스템은 프로그램을 메모리에 적재해 실행할 수 있어야 한다. 프로그램의 정상, 비정상 여부를 떠나 실행을 끝낼 수 있어야 한다. 
 CPU를 제대로 할당하기 위해 사용자 수준 프로그램을 신뢰할 수 없다.

2. 입출력 연산 : 수행 중인 프로그램은 파일 또는 입출력 장치와 연관된 입출력을 요구할 수 있다. 이때 효율과 보호를 위해 사용자들은 입출력 장치를 직접 제어할 수 없다.
　
3. 파일 시스템 조작 : 프로그램은 파일 읽기, 쓰기, 생성, 삭제, 찾기, 열거할 수 있어야 한다. 또한, 파일 소유권에 따른 권한 관리를 이용하여 파일/디렉터리의 접근을 허가하거나 거부할 수 있어야 한다. 
 사용자 프로그램은 보호 방법을 준수할 수 없으므로 사용 가능한 블록 할당하고, 블록 할당을 해제할 수 없다.

4. 통신 : 같은 컴퓨터에서 수행되고 있는 프로그램들은 공유 메모리를 통해, 같은 컴퓨터는 아니지만, 네트워크에 의해 함께 묶여 있는 서로 다른 컴퓨터 시스템상에서 수행되는 프로그램들은 메시지 전달 기법을 사용하여 정보를 교환할 수 있어야 한다. 
 사용자 프로그램은 네트워크 장치에 대한 액세스를 조정하지 않거나 다른 패킷을 수신할 수 있다.

5. 오류 탐지 : CPU, 메모리 하드웨어, 입출력 장치 또는 사용자 프로그램에서 일어날 수 있는 모든 오류를 항상 의식하고 있어야 한다. 또한, 올바르고 일관성 있는 계산을 보장하기 위해 각 유형의 오류에 대해 적당한 조치를 해야 한다. 

#### 2.7 일부 시스템은 운영체제를 펌웨어에 저장하고 다른 시스템은 디스크에 저장하는 이유는 무엇인가? (답지 참고)
-> 
 임베디드 시스템과 같은 특정 장치의 경우 파일 시스템이 있는 디스크를 해당 장치에 사용하지 못할 수 있다. 이 경우 운영체제를 펌웨어에 저장해야 한다.

#### 2.8 부팅할 운영체제를 선택할 수 있도록 시스템을 설계하는 방법은 무엇인가? 부트스트랩 프로그램이 해야 할 일은 무엇인가? 
->
 운영체제는 디스크에 저장되고, 시스템 부팅 중 부팅 관리자에 의해 결정되게 한다. 즉, 컴퓨터 전원을 누른 후 바로 운영체제를 부팅하지 않고 부팅 관리자가 먼저 실행된 후 이 부팅 관리자가 사용자가 선택한 운영체제를 선택하도록 한다. 사용자가 부팅 할 운영체제를 선택하지 않을 경우도 고려해 이 경우에는 기본 운영체제로 전환하도록 한다.

