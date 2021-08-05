# Computer Architecture
컴퓨터 구조를 배우고 정리한 내용

---

컴퓨터 내부는 단순하게 CPU, 메모리, 디스크, IO 4가지로 구성된다고 할 수 있습니다.

## CPU

CPU(Central Processing Unit, 중앙 처리 장치)는 연산 장치입니다. 

CPU의 명령(연산의 연속)을 수행합니다. CPU는 트랜지스터라고 하는 반도체로 만들어졌습니다. 

반도체는 실리콘으로 만들어져 있는데 실리콘은 최외각 전자 수가 4개이므로 서로 단단하게 결합합니다. 

반도체는 실리콘에 최외각 전자수가 한 개 많거나(N형 반도체) 적은(P형 반도체) 원자를 넣어 전류를 흐르게 합니다. 

트랜지스터는 NPN 또는 PNP 반도체로 구성됩니다. 

트랜지스터를 이용하여 논리게이트를 만들 수 있으며 논리게이트를 통해 논리 회로를 구성하고 이를 통해 CPU는 연산을 수행할 수 있습니다. 

CPU 하나에는 수십 억 개의 작은 트랜지스터가 들어 있습니다.  

모든 컴퓨터의 부품은 일정한 간격으로 발생되는 전기 신호에 맞추어 동작하는데 이 전기 신호를 클럭이라고 합니다. 

CPU의 성능이 좋다는 것은 1초에 더 많은 클럭이 발생했는지를 의미하며 Hz 단위로 표현합니다. 

보통 안정성을 위해 제조사에서는 CPU를 출시할 떄 클럭의 수를 제한하여 출시하는데 이 제한을 푸는 것을 오버 클럭이라고 합니다.

#### CPU의 구성 요소

CPU의 내부 구성은 산술/논리 연산 장치(ALU), 제어 장치, 레지스터로 구성되어 있습니다.

**ALU** : 산술, 논리적인 연산을 담당합니다. 가산기, 보수기, 누산기, 보수기, 데이터 레지스터, 오버플로 검출기, 시프트 레지스터 등으로 구성됩니다.

**제어 장치** : 컴퓨터에 있는 모든 장치들의 동작을 지시하고 제어하는 장치입니다 . 

수행 중인 명령어의 내용을 임시적으로 기억하는 명령 레지스터, 

명령 레지스터의 명령을 해독하는 명령 해독기, 

해독된 명령에 따라 장치로 보낼 신호를 생성하는 제어 신호 발생기, 

명령어를 실행할 주소를 저장하는 레지스터인 제어 주소 레지스터, 

제어 주소로 부터 얻어온 값을 저장하는 레지스터인 제어 버퍼 기억장치, 

명령어를 저장하는 레지스터인 제어 기억장치 등으로 이루어져 있습니다.

**레지스터** : 레지스터는 가장 빠른 메모리로 CPU에서 처리할 명령어나 연산의 중간 값 등을 일시적으로 기억하는 임시 기억장소입니다.

#### CPU의 명령어 수행 과정

CPU가 하나의 명령을 처리하는 과정은 네가지로 이루어집니다.

1) **읽기(Fetch)** : 실행할 명령어를 가져옵니다.
2) **해석(Decode)** : 명령어를 해석하여 종류를 구분합니다.
3) **실행(Execute)** : 명령어를 실행합니다.
4) **기록(Write)** : 처리 완료된 데이터를 메모리에 기록합니다.

CPU는 이 단계를 각각의 프로세스(쓰레드)로 세분화하여 사용합니다.

## 주기억장치

#### RAM

RAM(Random Access Memory)는 CPU에서 처리해야 할, 처리한 정보들을 임시적으로 기억합니다. Random이

하드 디스크보다 속도가 훨씬 빠르기 때문에 CPU에 필요한 정보들을 하드 디스크에서 불러와 저장하고 있다가 CPU에게 전달하는 역할을 합니다. 

RAM은 휘발성 메모리이기에 전원 공급이 중단되면 저장된 정보가 사라집니다.

RAM은 Capacitor(축전기)에 전하를 저장함으로써 정보를 기록합니다. 하지만 Capacitor는 전자가 조금씩 누설되기에 시간이 지나면 정보가 사라질 수 있습니다.

이를 방지하기 위해 Capacitor에 전하를 주기적으로 채워주는(refresh) DRAM(Dynamic RAM)과 전원이 공급되면 정보를 잃어버리지 않는 SRAM(Static RAM)의 방식으로 사용됩니다.

(SRAM이 속도가 훨씬 빠르고 refresh 과정이 없지만, 싼 가격과 단순한 구조 덕에 DRAM이 많이 사용됩니다.)

#### RAM의 읽기와 쓰기

메모리를 읽고 쓰기 위해서 행(raw)과 열(column)로 구성된 행렬구조(matrix)의 주소를 가집니다.

이를 CAS(Column Adress Strobe)와 RAS(Raw Adress Strobe)라고 부릅니다.

RAM의 동작 과정은 다음과 같습니다

1) CPU가 데이터를 요청하면 메인보드 칩셋은 그 데이터의 행 주소를 메모리로 보냅니다.
2) 행 주소가 들어오면 그 행의 모든 셀을 읽어냅니다.
3) 행 주소로 정확한 위치를 알 수 없으므로 열 주소를 받아 정확한 열을 찾아 정보를 찾습니다.
4) 정보를 출력 버퍼로 옮기고 메인보드 칩셋이 이를 CPU로 전달합니다.

#### 캐시 메모리

캐시 메모리는 RAM과 CPU간의 데이터 속도 향상을 위해 중간 버퍼 역할을 하는 메모리입니다. 

CPU에서 메모리에 읽기 요청을 하게 되면 먼저 캐시에 접근하여 해당 정보가 있는지 확인하는데 그 때 그 정보가 있다면 캐시에서 불러오게 됩니다.(이를 Hit했다고 합니다.) 

캐시 메모리는 지역성을 활용하여 적재할 정보를 예측하고 저장하여 Hit율을 높입니다.

#### 캐시 메모리의 지역성

프로세스들이 메모리의 정보를 균일하게 접근하는 것이 아니라 어느 순간 특정 부분을 집중적으로 접근하는 것을 말합니다.

메모리의 위치와 접근 시간에 따라 공간적, 시간적인 특성을 보입니다.

공간적 지역성 : 한 번 참조한 메모리 옆에 있는 메모리를 다시 참조하게 되는 성질을 말합니다.

시간적 지역성 : 한 번 참조된 주소의 내용은 곧 다음에 다시 참조된다는 성질을 말합니다.

#### Write Through와 Write Back

Write Through : 메모리에 쓰기 요청을 할 때마다 캐시의 내용과 메모리의 내용을 같이 바꾸는 방식입니다.

구조가 단순하지만 매 요청마다 바꿔야 하므로 속도가 느린 메모리에 기록할 때 CPU가 대기하는 시간이 생깁니다.

Write Back : 메모리에 쓰기 요청 시 캐시에만 쓰기 작업을 하고 해당 캐시가 제거될 때 메모리에 쓰기 작업을 하는 방식입니다. 

#### 캐시 메모리의 주소 매핑

캐시 메모리는 크기가 매우 작아서 1:1로 매칭되는 동일한 주소 체계를 가질 수 없습니다.

 그래서 메인 메모리와 다른 형태의 주소 매핑 방식을 사용하는데 direct mapping, associative mapping, set associative mapping 방식들을 대체로 사용합니다.

#### 캐시 메모리의 교체 알고리즘

캐시에 빈 공간이 없는 상태에서 새로운 내용이 복사 되어야 하는 상황에서 어떤 내용을 내릴지 정하는 알고리즘입니다.

교체 알고리즘엔 FIFO(선입선출), LRU(오랫동안 사용되지 않은 것을 교체), LFU(사용 횟수가 적은 것 교체) 등이 있으며 LRU를 기본적으로 많이 사용합니다.

#### 가상 메모리

가상 메모리를 사용하여 보조 기억 장치의 공간을 사용하여 RAM의 크기보다 더 큰 공간을 사용할 수 있습니다.

가상 메모리 기법으로는 페이징(paging)과 세그멘테이션(segmentation)이 있는데 현대 운영체제에서는 두 가지 방식을 혼용하여 사용합니다.

## 보조 기억 장치

#### 하드 디스크

하드 디스크는 정보를 저장하는 역할을 합니다.

하드 디스크는 파일을 저장하며 사용자가 삭제하지 않는 한 파일이 유지되는 반영구적 저장 장소입니다

하드 디스크 내부에는 회전하는 원판이 층을 이루고 있으며 각 원판은 자성을 띄는 금속 알갱이로 덮여있습니다.

이 금속 알갱이를 전자석으로 이루어진 기록 헤드가 자기장을 발생시켜  두 가지 상태로 기록합니다. 이 알갱이 하나는 1비트를 의미하며 상태는 0과 1을 의미합니다.

하드 디스크의 회전 속도 단위는 RPM이라고 하며 1분동안 몇 번의 회전을 하는지 나타냅니다.

#### SSD

SSD(Solid State Driver)는 NAND 플래시 메모리로 만든 저장 매체로 HDD를 대체하는 저장 매체입니다.

HDD가 원판을 회전하면서 정보를 찾아야 하는 반면 SSD는 전기신호로 정보를 찾는 방식이어서 HDD와 비교할 수 없을 정도로 빠릅니다.

---

#### 출처

IT 기술 노트  https://wikidocs.net/book/2184

cpu는 어떻게 작동할까 https://www.youtube.com/watch?v=Fg00LN30Ezg

중앙처리장치란 무엇인가(코딩 팩토리) https://coding-factory.tistory.com/351

ram의 이중성 https://www.youtube.com/watch?v=Vj2rNQFvdDw

위키백과 랜덤 액세스 메모리 https://ko.wikipedia.org/wiki/랜덤_액세스_메모리

레지스터와 RAM : 컴퓨터 과학 특강 # 6 https://www.youtube.com/watch?v=fpnE6UAfbtU&t=6s

DRAM구조, 동작원리, 특징 - 메모리반도체 https://goroom.tistory.com/3

[Cache] Write Through와 Write Back의 차이 http://melonicedlatte.com/computerarchitecture/2019/02/12/203749.html

가상 메모리(virtual memory) https://gamedevlog.tistory.com/85

운영체제 가상메모리(VIrtual Memory)란? https://vmilsh.tistory.com/384

How do hard drives work? - Kanawat Senanan https://www.youtube.com/watch?v=wteUW2sL7bc&t=10s
