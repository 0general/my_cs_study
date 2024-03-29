# ⏳ 예상 질문과 답변
---

1.  시스템 콜이 무엇인가요?
    > 운영체제는 커널 모드(Kernel Mode)와 사용자 모드(User Mode)로 나뉘어 구동되는데, 시스템 콜은 커널 영역의 기능을 사용자 모드가 사용 가능하게, 즉 프로세스가 하드웨어에 직접 접근해서 필요한 기능을 사용할 수 있게 해줍니다.
    > 시스템 콜의 종류에는 프로세스 제어, 파일 조작, 장치 조작, 정보 유지보수, 통신과 보호가 있습니다.
2.  인터럽트는 무엇인가요?
    > CPU의 정상적인 프로그램 실행 을 방해하는 것으로 
    > 내부 인터럽트  
    > - 하드웨어 고장(Hardware Interrupt)
    > - 데이터 전달 과정에서의 비트 오류
    > - 전원이 나간 경우
    > 실행할 수 없는 명령어 : 기억장치에서 인출한 명령어의 비트 패턴이 정의되어 있지 않은 경우
    > 명령어 실행 오류 : 나누기 0을 하는 경우
    > 사용 권한 위배 : 사용자가 운영체제만 사용할 수 있는 자원에 액세스하는 경우
    > --- 
    > 외부 인터럽트 : 외부 인터럽트는 주로 입출력장치 에 의해 발생된다.
    > 타이머 인터럽트 : 타이머가 일정한 시간 간격으로 중앙처리장치에게 인터럽트를 요청
    > 입출력 인터럽트
1.  메모리의 연속할당 방식 세 가지를 설명해주세요.
    > 최초 적합, 최적 적합, 최악 적합이 있습니다.  
    > 최초 적합은 첫 번째 사용 가능한 가용 공간을 할당하는 방식입니다. 검색은 집합의 시작에서부터 하거나 지난번 검색이 끝났던 곳에서 시작될 수 있으며, 충분히 큰 가용 공간을 찾았을 때 검색을 끝낼 수 있습니다.
    > 최적 적합은 사용 가능한 공간 중에서 가장 작은 것을 택하는 방식입니다. 리스트가 크기 순으로 되어있지 않다면 전체 리스트를 검색해야 합니다. 이 방법은 아주 작은 가용 공간을 만들어냅니다.
    > 최악 적합은 가장 큰 가용 공간을 택합니다. 이 방식에서 할당해주고 남게 되는 가용 공간은 충분히 커서 다른 프로세스들을 위하여 유용하게 사용될 수 있습니다. 최적 적합과 마찬가지로 리스트가 크기 순으로 되어있지 않다면 전체 리스트를 검색해야 합니다.
2.  세그멘테이션과 페이징의 차이점은 무엇인가요?
    > 페이징은 하나의 프로세스가 사용하는 메모리 공간이 연속적이어야 한다는 제약을 없애는 메모리 관리 방법이다.외부 단편화와 압축 작업을 해소하기 위해 생긴 방법론으로, 물리 메모리는 Frame 이라는 고정 크기로 분리되어 있고, 논리 메모리(프로세스가 점유하는)는 페이지라 불리는 고정 크기의 블록으로 분리된다.(페이지 교체 알고리즘에 들어가는 페이지) 내부 단편화 문제가 발생할 수 있습니다.
    > 세그멘테이션은 페이징에서처럼 논리 메모리와 물리 메모리를 같은 크기의 블록이 아닌, 서로 다른 크기의 논리적 단위인 세그먼트(Segment)로 분할합니다. 외부 단편화 문제가 발생할 수 있습니다.
3.  가상 메모리란 무엇인가요?
    > 프로세스 전체가 메모리 내에 올라오지 않더라도 실행이 가능하도록 하는 기법으로, 실제의 물리 메모리 개념과 사용자의 논리 메모리 개념을 분리한 것이다.
4.  TLB는 무엇인가요?
    > TLB(translation look-aside buffer)는 페이지 테이블의 하드웨어 캐시로 가상 메모리 주소를 물리적인 주소로 변환하는 속도를 높이기 위해 사용되는 캐시입니다. 각 TLB항목에는 페이지 번호와 상응하는 프레임을 저장합니다. 
    > 페이징 시스템의 주소 변환에 TLB를 사용하려면 논리 주소에서 페이지 번호를 가져와서 해당 페이지의 프레임이 TLB에 있는지 확인합니다. 만약 그렇다면, 프레임은 TLB로부터 얻어지고 TLB에 프레임이 없으면 페이지 테이블에서 찾아야 합니다.
5.  쓰레싱이란 무엇인가요?
    > 메모리 영역에 접근하게 될 때, 메모리에 페이지 부재(=페이지 폴트(Page fault)율이 높은 것을 의미하며, 심각한 성능 저하를 초래
    > 방지를 위해 각 프로세스가 필요로 하는 최소한의 프레임 갯수를 보장해주어야 합니다.
6.  페이지 교체 알고리즘엔 어떤 것들이 있나요?
    > FIFO(가장 먼저 들어온 페이지를 내보냄), OPT(가장 오랫동안 사용하지 않을 페이지 교체), LRU(참조 시간 기준, 가장 오래된 페이지 교체), LFU(참조 횟수가 가장 적은 페이지 교체)
7.  페이지 크기에 대한 trade-off를 설명해주세요.
    > 
8.  프로세스 메모리 구조에 대해 설명해주세요.
    > 
9.  프로세스 상태에는 어떤 것들이 있나요?
    > 생성, 준비, 실행, 대기, 종료 등이 있습니다.
10. 컨텍스트 스위칭 시에는 어떤 일들이 일어나나요?
    > 컨텍스트 스위칭이란 여러개의 프로세스가 실행되고 있을 때 기존에 실행되던 프로세스를 중단하고 다른 프로세스를 실행하는 것. 즉, CPU에 실행할 프로세스를 교체하는 기술이다.
11. IPC가 무엇이고, 어떤 종류가 있는지 설명해 주세요.
    > 프로세스 간 통신(Inter-Process Communication, IPC)이란 프로세스들 사이에 서로 데이터를 주고받는 행위 또는 그에 대한 방법이나 경로를 뜻한다.
    > PIPE, 파이프는 두 개의 프로세스를 연결하게 되고, 하나의 프로세스는 데이터를 쓰기만, 다른 하나는 데이터를 읽기만 할 수 있습니다. 한쪽 방향으로만 통신이 가능한 파이프의 특징 때문에 Half-Duplex(반이중) 통신이라고 부르기도 합니다.   
    > Message Queue, 메시지 큐의 장점은 컨테이너 벨트가 가지는 장점을 그대로 가지게 됩니다. 컨테이너 벨트에 올라올 물건에 라벨을 붙이면 동시에 다양한 물건을 다룰 수 있는 것과 같이, 메시지 큐에 쓸 데이터에 번호를 붙임으로써 여러 개의 프로세스가 동시에 데이터를 쉽게 다룰 수 있습니다.
    > Shared Memory(공유 메모리), PIPE, NamedPIPE, Message Queue가 통신을 이용한 설비라면, Shared Memory는 공유메모리가 데이터 자체를 공유하도록 지원하는 설비입니다. Shared Memory(공유 메모리)는 프로세스간 메모리 영역을 공유해서 사용할 수 있도록 허용합니다. 프로세스가 공유 메모리 할당을 커널에 요청하면 커널은 해당 프로세스에 메모리 공간을 할당해줍니다. 이후 어떤 프로세스건 해당 메모리영역에 접근할 수 있습니다.공유메모리는 중개자가 없이 곧바로 메모리에 접근할 수 있기 때문에 다른 모든 IPC들 중에서 가장 빠르게 작동할 수 있습니다.
    > Memory Map, Memory Map도 Shared Memory(공유메모리)공간과 마찬가지로 메모리를 공유한다는 측면에 있어서는 서로 비슷한 측면이 있습니다. 차이점은 Memory Map의 경우 열린파일을 메모리에 맵핑시켜서, 공유한다는 점일 것입니다. 파일은 시스템의 전역적인(모두 공유할 수 있는) 자원이므로 서로 다른 프로세스들끼리 데이터를 공유하는데 문제가 없을 것임을 예상할 수 있습니다.
    > Socket, Socket은 프로세스와 시스템의 기초적인 부분이며, 프로세스들 사이의 통신을 가능하게 합니다.
    > Semaphore, Semaphore는 Named PIPE, PIPE, Message Queue와 같은 다른 IPC설비들이 대부분 프로세스간 메시지 전송을 목적으로 하는데 반해, Semaphore는 프로세스 간 데이터를 동기화 하고 보호하는데 그 목적을 두게 됩니다. 
12. 프로세스와 쓰레드의 차이점은 무엇인가요?
    > 프로세스들은 각각 독립된 메모리 영역을 할당받으며 한 프로세스가 다른 프로세스의 자원에 접근하려면 프로세스 간의 통신(IPC)을 사용해야 합니다.
    > 스레드는 레지스터와 스택 영역만을 할당받고 스레드는 프로세스 내에서 각각 Stack만 할당받고, 주소 공간이나 Code/Data/Heap 자원들은 같은 프로세스 내의 스레드들끼리 공유하며 실행됩니다.
13. 쓰레드 풀이란 무엇인가요?
    > 프로세스 중 병렬 작업처리가 많아지면 스레드 개수가 증가되고 그에 따른 스레드 생성과 스케줄링으로 인해 CPU가 바빠져 메모리 사용량이 늘어난다. 따라서 시스템성능이 저하되고, 갑작스러운 병렬작업의 폭증에 따른 스레드 폭증을 막으려면 스레드 풀 Thread Pool을 사용해야 한다.
    > 스레드 풀은 작업처리에 사용되는 스레드를 제한된 개수만큼 정해놓고 작업큐 (Queue)에 들어오는 작업들을 하나씩 스레드가 맡아 처리한다. 그렇게 하면 작업처리 요청이 폭증되어도 스레드의 전체개수가 늘어나지 않으므로(제한해서 하나씩 처리하기 때문)  시스템 성능이 급격히 저하되지 않는다.
    > 즉, 스레드 풀은 매번 생성 및 수거 요청이 올 때 스레드를 생성하고 수거하는 것이 아닌, 스레드 사용자가 설정해둔 개수만큼 미리 생성해두는 것이다.
14. 프로세스 스케줄링 알고리즘에는 어떤 것들이 있나요?
    > 장기 스케줄러, 중기 스케줄러, 단기 스케줄러
    > FCFS, SJF, ROUND-ROBIN(각 프로세스는 동일한 크기의 할당 시간(time quantum)을 갖게 된다)
15. Deadlock 에 대해 설명해 주세요.
    > 상호배타(하나의 자원에는 한번에 하나의 프로세스만이 접근)
    > 점유 대기(한 프로세스는 자원을 점유한 상태로 다른 자원을 점유하기 위해 대기)
    > 비선점(자원을 할당받은 프로세스의 작업이 완료되기 전까지 시스템에서는 프로세스의 제어권을 뺏을 수 없음)
    > 환형 대기(위의 조건과 맞물려 사이클이 발생) 4가지 조건이 모두 충족되었을 때 발생한다. 
16. 뮤텍스와 세마포어의 차이점은 무엇인가요?
    >  관리하는 동기화 대상의 개수에서 가장 큰 차이점이 있습니다. Semaphore는 동기화 대상이 하나 이상일 때 사용하고, Mutex는 동기화 대상이 하나일 때 사용합니다. 따라서 Semaphore는 Mutex가 될 수 있지만 Mutex는 Semaphore가 될 수 없습니다. 굳이 표현하자면 Mutex는 상태가 0, 1 두 개뿐인 binary Semaphore입니다. Semaphore는 소유할 수 없지만 Mutex는 소유가 가능하며 소유주가 이에 대한 책임을 집니다. Mutex를 소유한 스레드는 이 Mutex를 해제할 수 있지만, Semaphore는 소유하지 않는 스레드도 Semaphore를 해제할 수 있습니다. 또한 Semaphore는 시스템 범위에 걸쳐있어 파일 시스템 상의 파일 형태로 존재합니다. 반면에 Mutextsms 프로세스 범위를 가지며 프로세스가 종료될 때 자동으로 Clean up됩니다.
17. 캐시 메모리 및 메모리 계층성에 대해 설명해 주세요.
    > 
18. 프로그램이 컴파일 되어, 실행되는 과정을 간략하게 설명해 주세요.
    > 프로그래머는 먼저 고급 언어와 같은 프로그래밍 언어를 이용해 원시 코드를 작성합니다.  
    > ​그 다음으로는 번역기(컴파일러)가 원시 코드를 목적 코드로 변환합니다. 여기서 목적 코드는 기계어로 된 프로그램으로 컴퓨터가 바로 실행할 수 있는 상태의 프로그램 코드를 의미합니다. 목적 코드는 메모리로 옮겨져 실행되고 결과물을 계산해 냅니다.
    > 프로그램 전체를 한 번에 기계어로 번역하는 방식으로 컴파일러를 이용하거나, 프로그램을 한 행씩 읽어 번역과 실행을 동시에 하는 인터프리터를 이용한 방식이 있습니다.
19. Thread Safe 하다는 것은 어떤 의미인가요?
    > Thread safety는 하나의 함수가 한 스레드로부터 호출되어 실행 중일 때, 다른 스레드가 그 함수를 호출하여 동시에 함께 실행되더라도 각 스레드에서의 함수 수행 결과가 올바르게 나오는 것으로 정의됩니다.  
    > 즉 멀티 스레드 프로그래밍에서 일반적으로 어떤 함수나 변수, 혹은 객체가 여러 스레드로부터 동시에 접근이 이루어져도 프로그램의 실행에 문제가 없음을 뜻합니다.  
    > Threads-safe하게 만들기 위해서는 Re-entrancy(어떤 함수가 한 스레드에 의해 호출되어 실행 중일 때 다른 스레드가 그 함수를 호출하더라도 그 결과가 각각에게 올바르게 주어짐을 의미), Thread-local storage(공유 자원의 사용을 최대한 줄여 각각의 스레드에서만 접근 가능한 저장소들을 사용함으로써 동시 접근을 막는 방식. 동기화 방법과 관련되어 있고, 또한 공유상태를 피할 수 없을 때 사용.), Mutual exclusion(공유 자원을 꼭 사용해야 할 경우 해당 자원의 접근을 세마포어 등의 락으로 통제), Atomic operations(공유 자원에 접근할 때 원자 연산을 이용하거나 '원자적'으로 정의된 접근 방법을 사용함으로써 상호 배제를 구현) 등의 방법을 사용할 수 있습니다.  
    > 통상적으로 Mutual Exclusion(상호배제) 방식을 이용한 Critical Section 처리가 자주 사용되는 편입니다.
20. File Descriptor 에 대해 설명해 주세요.
    > 파일 디스크립터(File Descriptor)란 리눅스 혹은 유닉스 계열의 시스템에서 프로세스(process)가 파일(file)을 다룰 때 사용하는 개념으로, 프로세스에서 특정 파일에 접근할 때 사용하는 추상적인 값입니다. 파일 디스크럽터는 일반적으로 0이 아닌 정수값을 가지며,  
    > 프로세스가 실행 중에 파일을 Open하면 커널은 해당 프로세스의 파일 디스크립터 숫자 중 사용하지 않는 가장 작은 값을 할당해줍니다. 그 다음 프로세스가 열려있는 파일에 시스템 콜을 이용해서 접근할 때, 파일 디스크립터(FD)값을 이용해서 파일을 지칭할 수 있습니다.