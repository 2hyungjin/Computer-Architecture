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

1) **읽기(Fetch)** :
2) **해석(Decode)**
3) **실행(Execute)**
4) **기록(Write)**

---

#### 출처

IT 기술 노트  https://wikidocs.net/book/2184

cpu는 어떻게 작동할까 https://www.youtube.com/watch?v=Fg00LN30Ezg

중앙처리장치란 무엇인가(코딩 팩토리) https://coding-factory.tistory.com/351
