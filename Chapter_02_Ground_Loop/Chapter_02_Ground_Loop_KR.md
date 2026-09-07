**Volume 05. Grounding and EMC**

# Chapter 02. Ground Loop

## 02.01. Ground Loop Mechanism

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

접지 루프(Ground Loop)는 동일한 접지 기준(Ground Reference)을 가져야 하는 두 개 이상의 전기적 지점이 여러 개의 도전 경로(Conductive Path)를 통해 연결될 때 발생한다. 모든 전선, 섀시 연결(Chassis Connection), 실드(Shield), 커넥터(Connector), 인쇄회로기판 배선(PCB Trace)은 유한한 임피던스(Impedance)를 가지므로 각 지점의 접지 전위(Ground Potential)는 완전히 동일할 수 없다. 이들 사이에 폐쇄된 도전 경로가 형성되면 작은 전압 차이만으로도 의도하지 않은 순환 전류(Circulating Current)가 루프를 따라 흐를 수 있다.

접지 루프의 기본적인 발생 메커니즘(Mechanism)은 접지 임피던스(Ground Impedance)에서 시작한다. 도체(Conductor)는 직류(DC) 조건에서 거의 이상적으로 보일 수 있지만, 실제로는 저항(Resistance), 인덕턴스(Inductance), 커넥터 접촉 저항(Contact Resistance), 기생 결합(Parasitic Coupling)으로 인해 측정 가능한 임피던스를 갖는다. 이 임피던스를 통해 전류가 흐르면 V = I × Z에 따라 전압이 발생한다. 따라서 전원 리턴(Power Return)이나 섀시(Chassis)의 서로 다른 위치에 연결된 두 모듈(Module)은 모두 GND로 표시되어 있어도 서로 다른 국부 접지 전위(Local Ground Potential)를 가질 수 있다.

이러한 모듈들이 추가적인 신호 케이블(Signal Cable), 실드(Shield), 통신 인터페이스(Communication Interface), 기계적 섀시 경로(Mechanical Chassis Path)를 통해 연결되면 접지 전위차(Ground-Potential Difference)에 의해 해당 연결을 따라 전류가 흐를 수 있다. 이 전류는 기존 전원 리턴 네트워크(Power-Return Network)를 통해 폐회로를 형성한다. 이러한 루프 전류(Loop Current)는 의도된 신호 경로의 일부가 아니지만 추가적인 전압 강하(Voltage Drop)를 발생시켜 센서 신호, 통신 기준, 아날로그 측정값 또는 제어 인터페이스(Control Interface)에 중첩될 수 있다.

접지 루프는 대전류 부하(High-Current Load)가 민감한 전자회로와 접지 구조의 일부를 공유할 때 특히 심각해진다. 모터(Motor), 서보 드라이브(Servo Drive), 히터(Heater), 펌프(Pump), DC/DC 컨버터(DC/DC Converter), 컴퓨팅 시스템(Computing System)은 빠르게 변화하는 전류를 소비할 수 있다. 이러한 리턴 전류(Return Current)는 케이블과 섀시 구조를 따라 동적인 전압 강하를 발생시킨다. 센서나 통신 장치가 이 구조의 한쪽 끝을 기준으로 하고 제어기가 다른 쪽 끝을 기준으로 하면 변화하는 접지 전압이 직접적인 전기적 노이즈(Electrical Noise)로 나타날 수 있다.

접지 루프의 심각성은 저항뿐만 아니라 주파수(Frequency)에 의해서도 결정된다. 저주파에서는 도체 저항과 천천히 변화하는 접지 전위차가 지배적인 영향을 미칠 수 있다. 고주파에서는 주파수가 증가함에 따라 유도성 임피던스(Inductive Impedance)가 증가하기 때문에 기생 인덕턴스(Parasitic Inductance)의 영향이 더욱 중요해진다. 따라서 직류 접지에서는 충분히 양호한 전선도 빠른 스위칭 전류(Switching Current), 과도 에지(Transient Edge), 현대 전력전자 시스템에서 발생하는 고주파 공통 모드 노이즈(Common-Mode Noise)에 대해서는 상당한 임피던스로 동작할 수 있다.

루프의 기하학적 구조(Loop Geometry) 역시 전자기적 거동(Electromagnetic Behavior)에 영향을 준다. 도전성 루프(Conductive Loop)는 일정한 물리적 면적을 둘러싸며, 이 면적을 통과하는 자기 선속(Magnetic Flux)이 변화하면 전자기 유도(Electromagnetic Induction) 원리에 따라 전압이 유도될 수 있다. 따라서 전원 케이블과 신호 케이블이 서로 멀리 떨어져 형성하는 큰 루프는 자기장 결합(Magnetic-Field Coupling)에 더욱 취약하다. 모터 상 케이블(Motor Phase Cable), 접촉기(Contactor), 변압기(Transformer), 인덕터(Inductor), 대전류 버스 구조(High-Current Bus Structure)는 인접한 접지 루프에 에너지를 결합시킬 수 있는 자기장을 생성한다.

접지 루프 간섭(Ground-Loop Interference)은 전도성 메커니즘(Conducted Mechanism)과 유도성 메커니즘(Induced Mechanism)을 통해 동시에 시스템으로 유입될 수 있다. 전도성 간섭(Conducted Interference)은 공유 접지 임피던스(Shared Ground Impedance)를 통해 흐르는 전류에서 발생하며, 자기 유도성 간섭(Magnetically Induced Interference)은 변화하는 자기장이 루프 면적을 통과하면서 발생한다. 높은 dV/dt 노드(Node)에서 발생하는 용량성 결합(Capacitive Coupling) 역시 공통 모드 전류(Common-Mode Current)를 섀시나 케이블 실드로 주입할 수 있다. 이러한 메커니즘은 동시에 존재하는 경우가 많기 때문에 실제 접지 루프 문제는 단순한 직류 저항 모델보다 훨씬 복잡하다.

케이블 실드(Cable Shield)는 의도하지 않은 접지 루프 경로를 형성하는 대표적인 원인이다. 양쪽 끝에서 섀시에 연결된 실드는 많은 응용 분야에서 우수한 고주파 차폐(High-Frequency Shielding)를 제공하지만, 동시에 두 섀시 지점 사이에 도전성 연결을 형성한다. 두 지점의 저주파 전위가 서로 다르면 실드를 통해 전류가 흐를 수 있다. 따라서 엔지니어는 모든 실드 연결이 이상적인 접지로 동작한다고 가정해서는 안 되며, 실드의 전자기적 기능(Electromagnetic Function)과 신호 기준 기능(Signal-Reference Function)을 구분해야 한다.

단일 종단 아날로그 신호(Single-Ended Analog Signal)는 수신기가 자신의 국부 접지(Local Ground)를 기준으로 신호 전압을 해석하기 때문에 특히 취약하다. 송신기 접지(Transmitter Ground)와 수신기 접지(Receiver Ground) 사이에 Vg의 전압 차이가 존재하면 수신기는 원하는 신호에 Vg의 일부 또는 전부가 결합된 전압을 관측할 수 있다. 밀리볼트(mV) 수준의 출력을 생성하는 저레벨 센서(Low-Level Sensor)의 경우 작은 접지 오프셋(Ground Offset)도 유효 신호와 비슷한 크기가 되어 측정 오차, 겉보기 드리프트(Apparent Drift), 발진(Oscillation), 불안정한 제어 동작을 유발할 수 있다.

디지털 인터페이스(Digital Interface)는 일반적으로 더 큰 전압 마진(Voltage Margin)을 갖지만 접지 루프의 영향을 받을 수 있다. 접지 전위차와 고주파 루프 전류는 신호 레벨을 이동시키고 공통 모드 전압(Common-Mode Voltage)을 증가시키며 신호 에지(Edge)를 왜곡하거나 잘못된 시점에서 임계값(Threshold)을 통과하게 만들 수 있다. 이에 따라 모터 가속, 회생 제동(Regenerative Braking), 스위칭 컨버터(Switching Converter) 동작, 충전 또는 시스템 전류 분포가 변화하는 운전 상태에서 간헐적인 통신 오류(Communication Error)가 발생할 수 있다.

로봇 플랫폼(Robotic Platform)에서는 매우 다양한 경로를 통해 접지 루프가 형성될 수 있다. 센서는 전원 케이블을 통해 접지되는 동시에 이더넷(Ethernet)이나 직렬 인터페이스(Serial Interface)를 통해 다시 연결되고, 전도성 프레임(Conductive Frame)에 기계적으로 결합되며, 실드를 통해 간접적으로 추가 연결될 수도 있다. 따라서 엣지 컴퓨터(Edge Computer), 모터 컨트롤러(Motor Controller), 라이다(LiDAR), 카메라(Camera), 배터리 전력 분배 시스템(Battery Distribution System)은 각 서브시스템(Subsystem)을 개별적으로 검사했을 때 정상적으로 접지되어 보이더라도 여러 개의 중첩된 접지 루프를 형성할 수 있다.

모터 드라이브 시스템(Motor-Drive System)은 펄스 폭 변조(PWM) 스위칭이 크고 빠른 전압 변화를 발생시키기 때문에 특히 중요한 접지 루프 발생원이 된다. 모터 권선, 케이블, 방열판(Heatsink), 섀시, 프레임 구조 사이의 기생 커패시턴스(Parasitic Capacitance)는 회로도에서 명확하게 보이지 않는 경로를 통해 공통 모드 전류가 흐르게 한다. 이러한 전류는 보호 접지(Protective Earth), 섀시 본딩(Chassis Bond), 케이블 실드, 베어링(Bearing), 통신 케이블 또는 센서 접지를 통해 귀환하면서 원래의 인버터(Inverter)에서 멀리 떨어진 위치에서도 간섭을 발생시킬 수 있다.

따라서 물리적인 회로도(Schematic)만으로는 접지 루프를 충분히 분석할 수 없다. 엔지니어는 와이어링 하니스(Wiring Harness), 커넥터, PCB 접지(PCB Ground), 인클로저(Enclosure), 장착 브래킷(Mounting Bracket), 실드, 보호 도체(Protective Conductor), 섀시 구조를 통과하는 실제 전류 경로를 식별해야 한다. 회로도에서 하나의 GND 심벌(Symbol)로 표현된 연결도 실제 시스템에서는 수 미터의 배선과 여러 접촉 인터페이스로 구성될 수 있으며, 그 임피던스는 주파수, 온도, 조립 상태 및 기계적 노화(Mechanical Aging)에 따라 변화한다.

접지 루프를 이해하기 위해서는 의도된 리턴 전류(Intended Return Current)와 의도하지 않은 순환 전류(Unintended Circulating Current)를 구분하는 것이 유용하다. 의도된 전류는 설계자가 제어한 저임피던스 경로(Low-Impedance Path)를 통해 전원으로 귀환해야 한다. 반면 접지 루프 전류는 시스템 상호 연결에 의해 생성된 병렬 경로(Parallel Path)를 이용한다. 두 전류가 도체의 일부를 공유하면 한 서브시스템의 전류가 생성한 전압이 다른 서브시스템의 기준 전압을 변조할 수 있다. 이러한 공유 임피던스 결합(Shared-Impedance Coupling)은 원인을 찾기 어려운 전자파 적합성(EMC) 문제에서 가장 일반적인 메커니즘 중 하나이다.

접지 루프의 동작은 시스템의 운용 구성(Operating Configuration)에 따라서도 달라질 수 있다. 프로그래밍 노트북(Programming Laptop), 오실로스코프(Oscilloscope), 충전기(Charger), 외부 전원 공급 장치(External Power Supply), 시험 장비(Test Equipment), 접지된 이더넷 인프라(Ethernet Infrastructure)를 연결하면 추가적인 대지 접지(Earth Connection)가 형성되어 독립 운전 시에는 존재하지 않았던 루프가 완성될 수 있다. 반대로 실험실 장비를 분리하면 문제가 사라질 수도 있다. 따라서 접지 진단(Grounding Diagnosis)에서는 제품 자체의 아키텍처뿐만 아니라 시험 과정에서 사용되는 모든 임시 외부 연결도 함께 고려해야 한다.

효과적인 접지 엔지니어링(Grounding Engineering)은 접지를 동일 전위를 갖는 추상적인 기준점으로 보는 것이 아니라, 넓은 주파수 범위에서 다양한 전류가 흐르는 분산 임피던스 네트워크(Distributed Impedance Network)로 이해하는 것에서 시작한다. 따라서 접지 루프 방지(Ground-Loop Prevention)를 위해서는 리턴 경로(Return Path), 루프 면적(Loop Area), 본딩 임피던스(Bonding Impedance), 신호 기준 전략(Signal-Reference Strategy), 차폐(Shielding), 서브시스템 인터페이스를 체계적으로 제어해야 한다. 이후 다루는 차동 신호(Differential Signaling), 갈바닉 절연(Galvanic Isolation), 변압기 결합(Transformer Coupling), 체계적 진단(Systematic Diagnosis)은 모두 명목상 동일한 접지가 실제로는 전기적으로 서로 다르기 때문에 발생하는 의도하지 않은 전류라는 동일한 근본 메커니즘을 해결하기 위한 방법이다.

## 02.02. Differential Signal Solution

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

차동 신호(Differential Signaling)는 접지 루프(Ground Loop)가 통신 및 측정 인터페이스(Interface)에 미치는 영향을 줄이는 가장 효과적인 기법 중 하나이다. 하나의 신호 도체와 공유 접지(Shared Ground) 사이의 전압으로 정보를 표현하는 대신, 차동 인터페이스는 두 개의 도체를 통해 신호를 전송한다. 수신기는 각 도체와 접지 사이의 전압이 아니라 주로 두 도체 사이의 전압 차이를 이용하여 정보를 판별한다.

이상적인 차동 시스템(Differential System)에서 송신기는 양극 및 음극 신호선에 상보적(Complementary)이거나 제어된 전압을 생성한다. 두 도체의 전압을 V+와 V−로 나타내면 유효한 차동 전압(Differential Voltage)은 Vdiff = V+ − V−가 된다. 수신기는 이 차이에 반응하기 때문에 두 도체에 거의 동일하게 나타나는 전압 외란(Voltage Disturbance)은 감산 과정에서 대부분 상쇄될 수 있다.

이러한 상쇄 메커니즘(Cancellation Mechanism)은 두 전자 모듈(Electronic Module)의 국부 접지 전위(Local Ground Potential)가 서로 다를 때 특히 유용하다. 단일 종단 인터페이스(Single-Ended Interface)에서는 송신기와 수신기가 각각의 접지를 전압 기준으로 사용하기 때문에 접지 전위차(Ground-Potential Difference)가 수신 신호의 일부가 될 수 있다. 반면 차동 수신기(Differential Receiver)는 한 쌍의 신호 도체 사이의 전압 차이를 관측하므로 두 국부 접지 사이의 전압 차이에 대한 직접적인 의존성을 크게 줄일 수 있다.

두 도체에 거의 동일하게 결합되는 노이즈는 공통 모드 노이즈(Common-Mode Noise)라고 한다. 이상적인 차동 수신기는 원하는 정보를 포함하는 차동 성분(Differential Component)은 유지하면서 이러한 공통 모드 성분(Common-Mode Component)을 제거한다. 공통 모드 신호를 제거하는 수신기의 능력은 일반적으로 공통 모드 제거비(Common-Mode Rejection Ratio, CMRR)로 나타낸다. CMRR이 높을수록 두 입력 도체에 동시에 존재하는 외란을 더욱 효과적으로 억제할 수 있다.

차동 신호를 사용한다고 해서 접지 전위가 중요하지 않게 되는 것은 아니다. 모든 차동 수신기에는 허용 가능한 공통 모드 입력 전압 범위(Common-Mode Input-Voltage Range)가 존재한다. 연결된 장치 사이의 접지 전위차가 너무 커져 신호 쌍이 이 범위를 벗어나면 수신기가 포화(Saturation)되거나 파형이 왜곡되고 통신 오류가 발생하며, 심한 경우 전기적 과부하(Electrical Overstress)가 발생할 수 있다. 따라서 차동 신호는 규정된 한계 내에서 접지 오프셋(Ground Offset)을 허용하는 것이며 완전한 갈바닉 절연(Galvanic Isolation)을 제공하는 것은 아니다.

차동 신호의 장점을 충분히 확보하려면 균형 잡힌 물리적 구조(Balanced Physical Construction)가 필수적이다. 두 도체는 유사한 임피던스(Impedance), 기하학적 구조(Geometry), 기생 커패시턴스(Parasitic Capacitance), 외부 전자기장에 대한 노출 조건을 가져야 한다. 외부 간섭이 두 도체에 유사하게 결합되면 대부분 공통 모드 노이즈가 되어 수신기에서 제거될 수 있다. 그러나 불균형(Imbalance)이 크면 외부 간섭의 일부가 차동 모드 전압(Differential-Mode Voltage)으로 변환되며, 이는 공통 모드 제거 기능으로 제거할 수 없다.

연선 배선(Twisted-Pair Wiring)은 케이블을 따라 두 도체의 물리적 위치가 지속적으로 서로 교환되기 때문에 널리 사용된다. 따라서 외부 자기장이나 전기장은 연속되는 꼬임 구간에서 두 전선에 비슷한 크기의 외란을 결합시키는 경향이 있다. 이는 유효 루프 면적(Effective Loop Area)을 감소시키고 전자기장 상쇄(Field Cancellation)를 향상시킨다. 꼬임률(Twist Rate), 페어 형상(Pair Geometry), 케이블 구조 및 배선 환경은 모두 전자기 간섭(Electromagnetic Interference)에 대한 최종적인 내성에 영향을 미친다.

차동 신호는 센서(Sensor), 모터 컨트롤러(Motor Controller), 엣지 컴퓨터(Edge Computer), 분산 입출력 모듈(Distributed I/O Module), 통신 노드(Communication Node)가 상당한 길이의 케이블로 분리될 수 있는 로봇 플랫폼(Robotic Platform)에서 특히 유용하다. 배터리 전류, 모터 전류, DC/DC 컨버터(DC/DC Converter), 섀시 본딩(Chassis Bonding), 과도 현상(Transient Event)으로 인해 각 장치의 국부 접지에는 서로 다른 전압 강하가 발생할 수 있다. 적절하게 설계된 차동 인터페이스는 섀시나 전원 리턴(Power Return)을 주요 신호 도체로 직접 사용하지 않고 이러한 영역 사이에서 정보를 전달할 수 있게 한다.

산업 및 로봇 통신 표준은 이러한 원리를 광범위하게 활용한다. CAN과 CAN FD는 CAN_H와 CAN_L 사이의 차동 관계를 이용하여 통신하며, RS-422와 RS-485는 전기적 노이즈가 많은 환경에서 견고한 통신을 위해 평형 차동 페어(Balanced Differential Pair)를 사용한다. 이더넷(Ethernet)의 물리 계층(Physical Layer) 역시 차동 전송 기법을 사용하므로 스위칭 컨버터, 모터, 프로세서 및 기타 주요 전자기 노이즈원이 존재하는 시스템에서도 고속 데이터 통신을 구현할 수 있다.

신호 리턴 경로(Signal Return Path) 역시 신중하게 고려해야 한다. 두 차동 트랜시버(Differential Transceiver) 사이에 접지 도체(Ground Conductor)를 추가하면 공통 모드 전압을 제어하는 데 도움이 될 수 있지만, 두 서브시스템(Subsystem)의 접지 전위가 크게 다르면 접지 루프 전류가 흐르는 또 다른 경로가 될 수도 있다. 이러한 기준 도체가 필요한지는 인터페이스 아키텍처, 트랜시버 사양, 케이블 길이, 예상 접지 오프셋, 차폐 구성 및 시스템 수준의 접지 전략에 따라 결정해야 한다.

종단 처리(Termination)는 차동 인터페이스 설계에서 또 하나의 중요한 요소이다. 케이블 길이가 신호 상승 시간(Signal Rise Time)에 비해 전기적으로 무시할 수 없을 정도가 되면 신호 페어는 이상적인 전선이 아니라 전송선(Transmission Line)으로 동작한다. 차동 특성 임피던스(Differential Characteristic Impedance)에 정합된 종단 저항(Termination Resistor)은 반사(Reflection)를 감소시키고 파형 무결성(Waveform Integrity)을 유지한다. 잘못된 종단 처리는 링잉(Ringing), 오버슈트(Overshoot), 임계값 불확실성(Threshold Uncertainty), 통신 오류를 발생시킬 수 있으며, 이러한 문제는 접지나 전자기 간섭 문제로 잘못 판단될 수 있다.

케이블 차폐(Cable Shielding)와 차동 신호는 서로 관련되어 있지만 서로 다른 기능을 수행한다. 차동 신호는 두 도체에 유사하게 나타나는 외란을 제거하는 반면, 차폐는 케이블 내부 또는 외부로의 전자기 결합(Electromagnetic Coupling)을 감소시킨다. 따라서 실드(Shield)를 차동 신호의 리턴 도체로 자동적으로 간주해서는 안 된다. 실드의 종단 전략(Termination Strategy)은 주파수, 섀시 아키텍처, 전자파 적합성(EMC) 요구사항, 커넥터 구조 및 접지 전위차로 인해 발생할 수 있는 실드 전류를 고려하여 설계해야 한다.

인쇄회로기판 배치(PCB Layout)는 케이블에서 확보된 전기적 대칭성(Electrical Symmetry)을 유지해야 한다. 차동 배선(Differential Trace)은 제어된 기하학적 구조, 적절한 간격, 일관된 기준 구조(Reference Structure)를 유지하고 불필요한 불연속(Discontinuity)을 최소화하여 배치해야 한다. 스텁(Stub), 비대칭 비아(Asymmetric Via), 정합되지 않은 필터 부품, 커넥터 전이부(Connector Transition), 불균등한 기생 커패시턴스는 불균형을 발생시킬 수 있다. 이러한 불균형은 공통 모드 외란을 차동 노이즈로 변환하여 차동 아키텍처에서 기대되는 실제 노이즈 내성을 감소시킨다.

고주파 공통 모드 전류가 중요한 경우 공통 모드 초크(Common-Mode Choke)와 적절하게 선정된 필터 부품을 사용하여 차동 신호를 보완할 수 있다. 공통 모드 초크는 두 도체에서 같은 방향으로 흐르는 전류에는 높은 임피던스를 제공하면서 의도된 차동 전류는 상대적으로 작은 방해만으로 통과시킨다. 부품 선정에서는 신호 대역폭(Signal Bandwidth), 차동 임피던스, 기생 커패시턴스, 포화 특성(Saturation Behavior), 제어하려는 EMC 주파수 스펙트럼을 함께 고려해야 한다.

차동 신호는 낮은 레벨의 정보를 물리적으로 떨어진 모듈 사이에서 전달해야 하는 아날로그 센서(Analog Sensor)에 특히 유용하다. 계측 증폭기(Instrumentation Amplifier)와 차동 ADC 입력(Differential ADC Input)은 센서 출력 사이의 전압 차이를 측정하면서 공통으로 존재하는 외란의 상당 부분을 제거할 수 있다. 그러나 센서 접지, 바이어스 전류 경로(Bias-Current Path), 소스 임피던스 정합(Source Impedance Matching), 케이블 균형, 입력 보호(Input Protection), 수신기의 공통 모드 범위는 여전히 전체 설계에서 중요한 요소이다.

디지털 통신(Digital Communication)에서도 동일한 원리를 적용하여 모터 스위칭, 릴레이 동작, 컨버터 과도 현상 및 섀시 전위 변화에 대한 내성을 향상시킬 수 있다. 수신기는 원격 접지를 기준으로 개별 신호를 판단하는 대신 차동 전압을 이용하여 논리 상태를 결정한다. 차동 진폭(Differential Amplitude), 공통 모드 범위, 타이밍 마진(Timing Margin), 종단 조건, 트랜시버의 허용 한계가 유지되는 한 상당한 수준의 환경적 외란이 존재해도 전송되는 정보를 손상시키지 않고 통신할 수 있다.

따라서 차동 인터페이스는 접지 사이의 전압 차이에 대한 민감도를 감소시키는 방법으로 이해해야 하며, 접지 사이의 전기적 연결 자체를 제거하는 방법으로 이해해서는 안 된다. 접지 전위차가 지나치게 크거나 안전을 위해 분리가 필요하거나 순환 전류(Circulating Current)를 물리적으로 차단해야 하는 경우에는 갈바닉 절연이 필요하다. 광 절연(Optical Isolation)과 변압기 절연(Transformer Isolation)은 공통 모드 외란을 단순히 제거하는 것이 아니라 직접적인 도전 경로(Conductive Path)를 차단하기 때문에 근본적으로 다른 해결 방법을 제공한다.

실제 로봇 전자파 적합성 엔지니어링(Robotics EMC Engineering)에서 가장 효과적인 접근 방법은 차동 전송(Differential Transmission)을 제어된 접지, 평형 케이블(Balanced Cabling), 적절한 종단, 차폐, 신중한 배선 및 공통 모드 전류 관리와 결합하는 것이다. 차동 신호는 많은 접지 루프 외란이 유효 신호 오류로 변환되는 것을 방지하고, 주변 전기 아키텍처는 인터페이스가 허용 가능한 전기적 한계 내에서 동작하도록 유지한다. 이러한 특성으로 인해 차동 통신은 단순한 공유 접지 배선(Shared-Ground Wiring)과 완전한 갈바닉 절연 사이에서 사용할 수 있는 핵심적인 설계 수단이 된다.

## 02.03. Optical Isolation Solution

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

광 절연(Optical Isolation)은 전기 서브시스템(Electrical Subsystem) 사이에서 접지 루프 전류(Ground-Loop Current)가 순환할 수 있도록 만드는 도전 경로(Conductive Path)를 직접 차단하는 방법을 제공한다. 공통 모드 제거(Common-Mode Rejection)에만 의존하는 대신 광 절연기(Optical Isolator)는 빛을 이용하여 전기적 절연 장벽(Electrical Isolation Barrier)을 넘어 정보를 전달한다. 금속 신호 도체가 장벽을 통과하지 않기 때문에 송신 회로와 수신 회로는 서로 독립적인 국부 접지 기준(Local Ground Reference)을 유지할 수 있다.

일반적인 옵토커플러(Optocoupler)는 입력 측의 발광 다이오드(Light-Emitting Diode, LED)와 출력 측의 광감지 소자(Photosensitive Device)로 구성된다. 전기적 입력이 LED를 구동하면 신호가 광 에너지(Optical Energy)로 변환된다. 검출기는 이 빛을 수신하고 수신 측 접지를 기준으로 전기적 출력을 재구성한다. 따라서 신호 정보는 절연 장벽을 통과하지만 접지 전위차(Ground-Potential Difference)에 의해 발생하는 직류 전류는 동일한 경로를 따라 흐를 수 없다.

이러한 메커니즘은 접지 루프의 토폴로지(Ground-Loop Topology)를 근본적으로 변화시킨다. 기존의 도전성 인터페이스(Conductive Interface)에서는 신호 케이블이 두 서브시스템 접지 사이에 추가적인 연결을 제공하여 전원 리턴(Power Return), 섀시 본딩(Chassis Bonding), 보호 접지(Protective Earth)를 통해 폐쇄 루프를 완성할 수 있다. 광 절연은 이러한 도전성 신호 경로를 제거한다. 다른 의도하지 않은 연결이 존재하지 않는다면 루프는 전기적으로 개방되고 인터페이스를 통한 순환 접지 전류가 제거된다.

차동 신호(Differential Signaling)와 광 절연의 차이를 이해하는 것은 중요하다. 차동 신호는 공통 모드 전압(Common-Mode Voltage)을 제거함으로써 일정 범위의 접지 전위차를 허용하지만 일반적으로 두 시스템은 여전히 전기적으로 연결되어 있다. 반면 광 절연은 두 측 사이에 갈바닉 절연(Galvanic Isolation)을 제공한다. 따라서 예상되는 접지 오프셋(Ground Offset)이 인터페이스 허용 한계를 초과하거나 의도하지 않은 전류 경로를 물리적으로 차단해야 하는 설계에 적합하다.

절연 장벽이 존재한다고 해서 두 회로 사이의 모든 결합이 완전히 사라지는 것은 아니다. 실제 옵토커플러와 디지털 절연기(Digital Isolator)는 절연 장벽을 가로지르는 기생 커패시턴스(Parasitic Capacitance)를 갖는다. 빠른 공통 모드 전압 변화는 I = C × dV/dt 관계에 따라 이 커패시턴스를 통해 변위 전류(Displacement Current)를 발생시킬 수 있다. 전류 자체는 작을 수 있지만 높은 dV/dt 스위칭 환경에서는 이러한 결합이 민감한 전자회로와 고주파 EMC 성능에 중요한 영향을 미칠 수 있다.

따라서 로봇 전력전자(Robotic Power Electronics)에 사용할 절연 소자를 선정할 때 공통 모드 과도 내성(Common-Mode Transient Immunity)은 중요한 파라미터이다. 모터 인버터(Motor Inverter), 서보 드라이브(Servo Drive), 스위칭 컨버터(Switching Converter), 고전압 배터리 시스템(High-Voltage Battery System)은 서로 다른 전기적 도메인(Electrical Domain) 사이에서 빠른 전압 변화를 발생시킬 수 있다. 절연기는 양쪽 사이에 이러한 과도 현상이 발생하는 동안에도 정상적으로 정보를 전달해야 하며, 과도 내성이 부족하면 오동작, 데이터 손상 또는 일시적인 통신 손실이 발생할 수 있다.

절연 전압 정격(Isolation Voltage Rating) 역시 전기 아키텍처(Electrical Architecture)에 적합해야 한다. 절연 부품은 동작 전압(Working Voltage), 과도 전압 내성(Transient Withstand Capability), 절연 내력(Dielectric Strength), 절연 협조(Insulation Coordination) 등의 파라미터로 규정된다. 절연기 주변 PCB의 연면 거리(Creepage)와 공간 거리(Clearance)는 의도한 절연 장벽을 유지해야 한다. 높은 절연 정격을 가진 부품을 사용하더라도 구리 배선, 장착 하드웨어, 오염 또는 커넥터 구조가 필요한 절연 거리를 우회하면 시스템 수준의 절연을 확보할 수 없다.

신호 경로만 절연하는 것으로 실제 접지 루프가 제거되지 않을 수 있으므로 전력 분배(Power Distribution) 역시 동일하게 중요하다. 광 인터페이스의 양쪽 회로가 공통 리턴 도체(Shared Return Conductor)를 갖는 비절연 전원(Common Non-Isolated Supply)에서 전력을 공급받으면 전원 네트워크를 통해 도전성 연결이 계속 유지된다. 완전한 접지 분리가 필요한 경우 진정한 갈바닉 분리를 위해 일반적으로 절연 측 회로에 절연형 DC/DC 컨버터(Isolated DC/DC Converter)와 같은 절연 전원 공급 장치(Isolated Power Supply)가 필요하다.

옵토커플러에는 신호 정확도와 타이밍에 영향을 주는 여러 특성이 존재한다. 전파 지연(Propagation Delay), 펄스 폭 왜곡(Pulse-Width Distortion), 스위칭 속도(Switching Speed), 출력 구성(Output Configuration), 온도 의존성(Temperature Dependence), 소자 노화(Device Aging)를 고려해야 한다. 기존의 포토트랜지스터 옵토커플러(Phototransistor Optocoupler)는 비교적 느린 제어 및 상태 신호에 적합할 수 있지만 통신이나 정밀한 타이밍에는 더 빠른 광 소자가 필요하다. 선택한 기술은 인터페이스의 대역폭(Bandwidth)과 지연 시간(Latency) 요구사항에 적합해야 한다.

전류 전달비(Current Transfer Ratio, CTR)는 기존 옵토커플러의 또 다른 중요한 특성이다. 이는 입력 LED 전류와 출력 검출기 전류 사이의 관계를 나타내며 온도, 동작 전류, 제조 공차(Manufacturing Tolerance), 노화에 따라 달라질 수 있다. 따라서 설계에서는 하나의 공칭값(Nominal Value)만을 가정해서는 안 된다. 입력 구동 전류(Input Drive Current), 출력 풀업 저항(Output Pull-Up Resistance), 스위칭 임계값(Switching Threshold), 최악 조건 마진(Worst-Case Margin)을 고려하여 목표 수명 전체에서 신뢰성 있는 동작을 유지하도록 설계해야 한다.

광 절연은 활성화 명령(Enable Command), 고장 표시(Fault Indication), 비상 상태 인터페이스(Emergency Status Interface), 릴레이 명령(Relay Command), 특정 디지털 입출력(Digital I/O)과 같은 개별 제어 신호에 유용하다. 적절한 절연 트랜시버(Isolated Transceiver)나 광통신 장치를 사용하면 직렬 통신(Serial Communication)에도 적용할 수 있다. 각 경우에 절연은 통신 도체 자체가 서로 분리된 전기적 도메인 사이의 접지 전위를 평형화하는 저주파 전류 경로가 되는 것을 방지한다.

아날로그 신호(Analog Signal)는 기본적인 디지털 옵토커플러가 임의의 아날로그 진폭을 높은 정밀도로 재현하지 못하기 때문에 보다 전문적인 접근 방법이 필요하다. 선형 옵토커플러(Linear Optocoupler), 절연 증폭기(Isolated Amplifier), 절연 ADC 아키텍처(Isolated ADC Architecture)를 사용하거나 측정값을 디지털 표현(Digital Representation)으로 변환한 후 절연 장벽을 통과시키는 방법을 사용할 수 있다. 정확도, 선형성(Linearity), 대역폭, 오프셋(Offset), 온도 드리프트(Temperature Drift), 절연 요구사항에 따라 특정 센서 인터페이스에 적합한 방식을 결정해야 한다.

자율이동로봇(AMR) 또는 모바일 로봇(Mobile Robot)에서는 광 절연을 이용하여 노이즈가 많은 모터 제어 도메인(Motor-Control Domain)과 민감한 제어 및 인지 전자장치(Control and Perception Electronics)를 분리할 수 있다. 모터 드라이브는 PWM과 관련된 큰 공통 모드 전류를 발생시킬 수 있는 반면 카메라, 라이다(LiDAR), 내비게이션 프로세서(Navigation Processor), 측정 회로는 안정적인 기준 전위를 필요로 한다. 선택된 인터페이스에 전략적으로 절연을 적용하면 모터 도메인의 접지 외란이 제어 배선을 통해 컴퓨팅 및 센서 접지 네트워크로 전파되는 것을 방지할 수 있다.

외부 인터페이스(External Interface)에서도 절연은 유용하다. 서비스 컴퓨터(Service Computer), 실험실 계측기(Laboratory Instrument), 충전 장비(Charging Equipment), 산업용 장비(Industrial Machine), PLC, 외부 전원 센서(Externally Powered Sensor)는 정상적인 자율 운전 중에는 존재하지 않는 대지 기준 연결(Earth-Referenced Connection)을 추가할 수 있다. 절연 인터페이스는 이러한 외부 접지 기준이 로봇의 내부 접지 네트워크에 자동으로 포함되는 것을 방지하여 운전 및 시험 과정에서 구성에 따라 달라지는 접지 루프 문제를 줄일 수 있다.

그러나 모든 위치에 절연을 삽입하는 것이 반드시 바람직한 것은 아니다. 각각의 절연 장벽은 추가 부품, 비용, PCB 면적, 전파 지연, 전원 공급 요구사항 및 잠재적인 신뢰성 문제를 증가시킨다. 지나치게 많은 절연은 문제 해결(Troubleshooting)과 기준 전위 관리(Reference Management)를 더욱 복잡하게 만들 수도 있다. 따라서 엔지니어링의 목표는 절연을 통해 순환 전류, 공통 모드 스트레스(Common-Mode Stress), 안전 위험을 실질적으로 감소시킬 수 있는 전기적 도메인 경계를 식별하는 것이다.

절연 장벽의 위치는 단순한 회로도상의 편의성이 아니라 실제 전류 경로 분석(Current-Path Analysis)을 기준으로 결정해야 한다. 설계자는 의도하지 않은 전류가 인터페이스의 어느 위치로 유입되는지, 어디를 통해 전원으로 귀환하는지, 어떤 도전성 연결이 루프를 완성하는지를 식별해야 한다. 이후 문제가 되는 경로를 물리적으로 차단하면서 필요한 신호 기능, 전력 공급, 차폐, 진단(Diagnostics), 안전 동작을 유지할 수 있는 위치에 절연기를 배치해야 한다.

차폐(Shielding)는 신호 절연과 별개의 기능으로 다루어야 한다. 신호가 광 절연 장벽을 통과하더라도 케이블 실드(Cable Shield)나 섀시 연결이 두 전기적 도메인을 계속 연결할 수 있다. EMC 아키텍처에 따라 이러한 실드 연결은 고주파 전류 제어를 위해 의도적으로 사용될 수 있지만 원래의 접지 루프 경로 일부를 유지할 수도 있다. 따라서 절연 설계에서는 신호 도체, 전원 리턴, 실드, 섀시 본딩, 보호 접지를 함께 고려해야 한다.

견고한 로봇 접지 아키텍처(Robotic Grounding Architecture)는 광 절연 하나에만 의존하기보다 여러 기법을 결합하는 경우가 많다. 차동 신호는 중간 수준의 공통 모드 외란을 효과적으로 처리하고, 차폐는 전자기 결합을 제어하며, 필터링(Filtering)은 원하지 않는 주파수 성분을 억제하고, 제어된 본딩(Controlled Bonding)은 예측 가능한 리턴 경로를 제공한다. 광 절연은 도전성 인터페이스로 인해 허용할 수 없는 접지 루프 전류가 발생하거나 전기적 도메인 분리가 명확하게 필요한 위치에 적용한다.

따라서 광 절연은 접지 루프 문제에 대한 토폴로지 수준의 해결책(Topology-Level Solution)으로 이해해야 한다. 핵심적인 장점은 단순한 노이즈 제거 성능 향상이 아니라 서로 다른 접지 도메인 사이의 직접적인 도전성 신호 경로를 제거한다는 점이다. 절연 전원, 적절한 절연 장벽 정격, 제어된 기생 결합, 신중한 PCB 절연 거리, 의도적으로 설계된 실드 종단(Shield Termination)과 결합하면 접지 전위차가 순환 전류와 시스템 수준의 간섭으로 변환되는 것을 방지하는 강력한 방법을 제공한다.

## 02.04. Transformer Isolation

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

변압기 절연(Transformer Isolation)은 직접적인 도전성 연결(Conductive Connection) 대신 자기 결합(Magnetic Coupling)을 통해 에너지나 정보를 전달함으로써 전기 회로 사이에 갈바닉 분리(Galvanic Separation)를 제공한다. 1차 권선(Primary Winding)과 2차 권선(Secondary Winding)은 전기적으로 분리되어 있지만 변압기 코어(Transformer Core)를 통해 자기 선속(Magnetic Flux)을 공유한다. 권선 사이에 의도적인 금속 도전 경로가 없으므로 저주파 접지 루프 전류(Ground-Loop Current)는 한 전기적 접지 도메인에서 다른 도메인으로 직접 흐를 수 없다.

교류 전압(Alternating Voltage)이 1차 권선에 인가되면 변압기 코어 내부에 변화하는 자기 선속이 생성된다. 이 자기 선속은 패러데이 법칙(Faraday\'s Law)에 따라 2차 권선에 전압을 유도한다. 2차 회로는 자신의 국부 접지(Local Ground)를 기준으로 전달된 파형을 재구성한다. 따라서 1차 측과 2차 측은 서로 다른 접지 전위(Ground Potential)에서 동작하면서도 절연 장벽(Isolation Barrier)을 통해 교류 에너지 또는 부호화된 정보(Encoded Information)를 교환할 수 있다.

이러한 동작은 많은 접지 루프를 발생시키는 도전성 메커니즘(Conductive Mechanism)을 직접적으로 해결한다. 접지된 두 서브시스템(Subsystem)이 일반적인 신호 도체로 연결되면 해당 연결이 섀시(Chassis), 전원 리턴(Power Return), 케이블 실드(Cable Shield), 보호 접지(Protective Earth)를 통해 루프를 완성할 수 있다. 도전성 신호 경로를 변압기 결합(Transformer Coupling)으로 대체하면 신호 도메인 사이의 직류 연결이 개방되어 지속적인 접지 전위차가 인터페이스를 통해 전류를 흐르게 하는 것을 방지할 수 있다.

변압기 절연은 차동 신호(Differential Signaling)와 근본적으로 다르다. 차동 수신기(Differential Receiver)는 공통 모드 외란(Common-Mode Disturbance)을 제거하지만 연결된 시스템은 여전히 전기적으로 연결되어 있을 수 있다. 반면 변압기는 갈바닉 경로(Galvanic Path) 자체를 차단한다. 따라서 다른 도체, 실드, 전원 리턴 또는 섀시 연결이 절연 장벽을 우회하는 대체 경로를 형성하지 않는다면 저주파 접지 오프셋(Ground Offset)과 순환 전류(Circulating Current)에 대해 강력한 보호 기능을 제공한다.

광 절연(Optical Isolation)과 달리 변압기 절연은 빛이 아니라 자기장(Magnetic Field)을 통해 정보를 전달한다. 이러한 특성으로 인해 변압기 결합은 교류 신호(AC Signal), 펄스 신호(Pulse Signal), 통신 파형(Communication Waveform), 절연 전력 변환(Isolated Power Conversion)에 특히 적합하다. 전자기 유도(Electromagnetic Induction)에는 변화하는 자기 선속이 필요하므로 일정한 직류 레벨은 직접 전달할 수 없다. 따라서 직류 정보는 변압기를 통과하기 전에 전이(Transition), 펄스, 변조(Modulation) 또는 다른 시간 변화 파형으로 부호화되어야 한다.

주파수 응답(Frequency Response)은 변압기 절연 인터페이스에서 핵심적인 고려사항이다. 저주파에서는 자화 인덕턴스(Magnetizing Inductance)가 충분한 임피던스를 제공하지 못하여 파형 드룹(Waveform Droop), 왜곡 또는 과도한 자화 전류(Magnetizing Current)가 발생할 수 있다. 고주파에서는 누설 인덕턴스(Leakage Inductance), 권선 커패시턴스(Winding Capacitance), 코어 손실(Core Loss), 기생 효과(Parasitic Effect)가 성능을 제한한다. 따라서 변압기 설계는 신호 스펙트럼, 데이터 전송률, 펄스 폭 및 필요한 대역폭(Bandwidth)에 맞추어 신중하게 설계해야 한다.

코어 포화(Core Saturation) 역시 방지해야 한다. 1차 권선에 과도한 볼트-초(Volt-Seconds)가 인가되면 자기 코어가 사용 가능한 자속 범위를 벗어날 수 있다. 포화가 발생하면 자화 전류가 급격하게 증가하고 전달되는 파형이 왜곡될 수 있다. 따라서 변압기 결합 회로에서는 제어된 듀티 사이클(Duty Cycle), 균형 잡힌 여자(Balanced Excitation), 적절한 코어 재료(Core Material), 적절한 권선 수(Turns Count), 비정상적인 직류 바이어스(DC Bias) 또는 장시간의 비대칭 펄스에 대한 보호가 필요하다.

변압기는 절연을 제공하지만 실제 소자에서는 1차 권선과 2차 권선 사이에 기생 커패시턴스(Parasitic Capacitance)가 존재한다. 고주파 공통 모드 전압의 변화는 직류 도전 경로가 개방되어 있더라도 이 커패시턴스를 통해 변위 전류(Displacement Current)를 발생시킬 수 있다. 그 크기는 대략 I = C × dV/dt 관계와 연관되므로 권선 간 커패시턴스(Interwinding Capacitance)는 모터 인버터(Motor Inverter), 스위칭 컨버터(Switching Converter), 기타 높은 dV/dt를 발생시키는 전력전자 회로 주변에서 특히 중요하다.

권선 구조(Winding Construction)는 이러한 공통 모드 결합(Common-Mode Coupling)에 큰 영향을 미친다. 1차 권선과 2차 권선 사이의 물리적 거리를 증가시키면 커패시턴스를 감소시킬 수 있지만 누설 인덕턴스가 증가할 수 있다. 인터리브 권선(Interleaved Winding)은 자기 결합과 대역폭을 향상시킬 수 있지만 절연 장벽을 가로지르는 용량성 결합(Capacitive Coupling)을 증가시키는 경우가 많다. 따라서 변압기 엔지니어링에서는 절연 성능, 결합 효율, 누설 인덕턴스, 기생 커패시턴스, 대역폭, 크기 및 EMC 성능 사이의 절충이 필요하다.

통신 네트워크(Communication Network)는 변압기 절연의 대표적인 적용 사례를 제공한다. 일반적인 이더넷(Ethernet) 인터페이스는 PHY와 케이블 사이에 마그네틱스(Magnetics)를 사용하여 갈바닉 분리와 공통 모드 관리를 제공하면서 차동 데이터를 전달한다. 변압기는 임피던스 정합(Impedance Matching)과 공통 모드 동작에도 관여한다. 의도한 EMC 성능을 확보하려면 정확한 센터 탭 연결(Center-Tap Connection), 종단 네트워크(Termination Network), PCB 배선, 커넥터 구조 및 섀시 전략이 필수적이다.

변압기 결합은 절연 전원 공급 장치(Isolated Power Supply)에도 널리 사용된다. 절연형 DC/DC 컨버터(Isolated DC/DC Converter)는 먼저 직류 에너지를 스위칭 파형(Switching Waveform)으로 변환하고, 변압기를 통해 에너지를 전달한 다음 2차 측에서 정류(Rectification)하고 조정(Regulation)한다. 이렇게 생성된 2차 전원은 1차 측 접지에 대해 부동(Floating) 상태를 유지할 수 있다. 이는 절연된 통신 또는 측정 인터페이스의 절연 측에도 독립적인 전원이 필요한 경우 특히 유용하다.

로봇 시스템(Robotic System)에서는 변압기 절연을 사용하여 서로 다른 노이즈 환경에 노출되는 통신, 제어 또는 전력 도메인(Power Domain)을 분리할 수 있다. 모터 드라이브와 대전류 전력전자 장치는 상당한 공통 모드 외란을 발생시킬 수 있는 반면, 엣지 컴퓨터(Edge Computer), 이더넷 네트워크, 센서 및 제어 전자장치는 안정적인 신호 기준을 필요로 한다. 적절한 변압기 절연은 저주파 접지 평형 전류(Ground Equalization Current)가 통신 배선이나 보조 전원 배선을 의도하지 않은 리턴 경로로 사용하는 것을 방지할 수 있다.

이 기법은 케이블이 로봇 외부로 연결되거나 접지 기준이 불확실한 장비와 연결되는 경우 특히 유용하다. 외부 산업용 네트워크(Industrial Network), 서비스 장비(Service Equipment), 충전 인프라(Charging Infrastructure), 원격 제어기(Remote Controller), 별도 전원을 사용하는 서브시스템은 새로운 섀시 또는 대지 접지(Earth Connection)를 추가할 수 있다. 변압기 절연 인터페이스는 이러한 외부 연결이 로봇 내부 전자장치를 통해 자동으로 도전성 접지 루프를 형성할 가능성을 줄여준다.

절연 전압(Isolation Voltage)과 절연 구조(Insulation Construction)는 예상되는 전기적 환경에 맞게 선정해야 한다. 권선 절연(Winding Insulation), 보빈 구조(Bobbin Structure), 연면 거리(Creepage Distance), 공간 거리(Clearance Distance), 절연 내력(Dielectric Withstand Capability), 동작 전압 정격(Working-Voltage Rating)이 함께 절연 장벽의 건전성을 결정한다. PCB 배치는 이러한 거리를 유지해야 하며 도전성 오염, 구리 패턴, 장착 하드웨어 또는 커넥터 구조가 변압기 절연을 우회하지 않도록 해야 한다.

변압기 주변의 차폐(Shielding) 역시 신중하게 다루어야 한다. 권선 사이에 배치되는 정전 차폐(Electrostatic Shield)는 적절하게 연결하면 용량성 결합을 감소시킬 수 있지만 실드 자체가 커패시턴스를 추가하며 제어된 리턴 경로(Controlled Return Path)를 필요로 한다. 변압기 외부의 케이블 실드와 섀시 본딩도 고주파 또는 저주파에서 전기적 도메인을 다시 연결할 수 있다. 따라서 변압기 절연은 전체 차폐 및 접지 아키텍처(Grounding Architecture)와 함께 분석해야 한다.

갈바닉 절연이 확보된 경우에도 신호 무결성(Signal Integrity)은 중요하다. 임피던스 부정합(Impedance Mismatch), 과도한 누설 인덕턴스, 기생 커패시턴스, 부족한 자화 인덕턴스, 부적절한 종단(Termination), PCB 불연속(PCB Discontinuity)은 전달되는 파형을 왜곡할 수 있다. 고속 통신에서는 변압기를 단순한 절연 부품이 아니라 전송 채널(Transmission Channel)의 일부로 고려해야 한다. 변압기의 전기적 특성은 송신기, 수신기, 케이블 및 종단 네트워크와 함께 조정되어야 한다.

따라서 변압기 절연과 광 절연은 서로 관련되어 있지만 서로 다른 역할을 담당한다. 광 소자는 개별 논리 신호(Discrete Logic Signal)와 다양한 제어 신호에 편리한 반면, 변압기는 교류 결합 통신(AC-Coupled Communication)과 절연 전력 전달에 자연스럽게 적합하다. 적절한 방식은 대역폭, 지연 시간(Latency), 전력 요구사항, 전압 정격, 공통 모드 과도 환경(Common-Mode Transient Environment), 수명 요구사항, 물리적 크기, 비용 및 절연 경계를 통과해야 하는 정보의 종류에 따라 결정된다.

접지 루프 완화(Ground-Loop Mitigation)에서 핵심적인 설계 질문은 변압기가 실제로 문제가 되는 전류 경로를 차단하는가에 있다. 변압기로 절연된 신호가 존재하더라도 공유 전원 리턴, 섀시 본딩, 실드 종단(Shield Termination), 외부 대지 연결이 또 다른 루프를 유지할 수 있다. 따라서 엔지니어는 도메인 사이의 모든 도전 경로를 추적하고 직류, 전원 주파수, 스위칭 주파수 및 통신 주파수에서 어떤 전류가 흐르는지를 파악한 후 인터페이스의 절연 여부를 판단해야 한다.

따라서 변압기 절연은 갈바닉 절연 기법(Galvanic-Isolation Technique)이면서 동시에 주파수 의존적인 EMC 부품(Frequency-Dependent EMC Component)으로 이해해야 한다. 변압기는 직접적인 직류 접지 루프 전류를 차단하면서 원하는 시간 변화 에너지를 자기적으로 전달하지만, 기생 커패시턴스를 통해 일부 고주파 공통 모드 전류는 여전히 흐를 수 있다. 변압기 특성, 절연, 종단, 차폐, 절연 전원, PCB 배치 및 접지를 체계적으로 조정하면 로봇 시스템에서 노이즈가 많은 전기적 도메인을 분리하기 위한 견고한 해결책을 구현할 수 있다.

## 02.05. Ground Loop Diagnosis

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

접지 루프 진단(Ground-Loop Diagnosis)은 GND로 표시된 모든 지점이 동일한 전위를 갖는다고 가정하는 대신, 접지를 분산된 전기 네트워크(Distributed Electrical Network)로 취급하는 것에서 시작한다. 진단의 목적은 의도하지 않은 도전 경로(Conductive Path)를 식별하고 순환 전류(Circulating Current)가 어디로 흐르는지 파악하며, 해당 전류가 민감한 신호에 어떠한 영향을 미치는지 확인하는 것이다. 따라서 효과적인 진단은 회로도 검토, 물리적 검사, 전압 측정, 전류 관찰 및 제어된 구성 변경을 결합하여 수행한다.

첫 번째 단계는 명확하게 정의된 운전 조건(Operating Condition)에서 증상을 재현하는 것이다. 접지 루프 문제는 모터 토크, 인버터 스위칭(Inverter Switching), 배터리 충전, 회생 제동(Regenerative Braking), 통신 동작 또는 외부 장비 연결에 따라 전류 분포가 변하기 때문에 간헐적으로 발생하는 경우가 많다. 각 고장과 연관된 운전 상태를 기록하면 접지 관련 간섭을 소프트웨어 오류, 센서 결함 또는 일반적인 통신 문제와 구분하는 데 도움이 된다.

그다음 단순한 GND 심벌(Symbol)이 아니라 실제 하드웨어를 기준으로 시스템 수준의 접지 맵(Grounding Map)을 작성해야 한다. 이 맵에는 배터리 리턴(Battery Return), 전력 분배 장치(Power Distribution Unit), DC/DC 컨버터(DC/DC Converter), 모터 드라이브(Motor Drive), 컨트롤러(Controller), 센서, 엣지 컴퓨터(Edge Computer), 케이블 실드(Cable Shield), 섀시 본딩(Chassis Bonding), 보호 접지(Protective Earth), 외부 인터페이스가 포함되어야 한다. 명목상 분리된 접지 영역 사이의 모든 연결이 중요하며, 개별적으로는 적절한 두 연결이 결합되어 의도하지 않은 폐쇄 루프를 형성할 수 있다.

물리적 검사(Physical Inspection)를 수행하면 전기 회로도에는 나타나지 않는 경로를 발견하는 경우가 많다. 도전성 장착 브래킷(Conductive Mounting Bracket), 금속 인클로저(Metal Enclosure), 실드 커넥터(Shielded Connector), 케이블 브레이드(Cable Braid), 장비 랙(Equipment Rack), 방열판(Heatsink), USB 케이블, 이더넷 실드(Ethernet Shield), 프로그래밍 인터페이스(Programming Interface), 시험 계측기(Test Instrument)가 접지 도메인을 의도하지 않게 연결할 수 있다. 전원을 차단한 상태에서 저항을 측정하면 예상하지 못한 도통(Continuity)을 찾는 데 도움이 되지만, 낮은 저항값만으로 해당 연결의 전체 고주파 특성을 설명할 수는 없다.

접지 전위차(Ground-Potential Difference)는 가장 유용한 측정 항목 중 하나이다. 시스템이 동작하는 동안 적절한 차동 측정 기법(Differential Measurement Technique)을 사용하여 의심되는 두 접지 지점 사이의 전압을 관찰할 수 있다. 직류 오프셋(DC Offset)과 교류 성분(AC Component)을 모두 고려해야 한다. 천천히 변화하는 전압은 공유 리턴 저항(Shared Return Resistance)을 나타낼 수 있으며, 반복적인 고주파 외란은 스위칭 전류, 유도성 임피던스(Inductive Impedance), 전력전자 장치의 공통 모드 결합(Common-Mode Coupling)을 나타낼 수 있다.

오실로스코프(Oscilloscope)가 조사 대상의 접지 토폴로지(Grounding Topology)를 변화시킬 수 있기 때문에 측정 기법은 매우 중요하다. 일반적인 대지 기준 오실로스코프 프로브(Earth-Referenced Oscilloscope Probe)는 접지 클립을 보호 접지에 연결하므로 의도하지 않은 새로운 전류 경로를 만들 수 있다. 이로 인해 증상이 변하거나 장비가 손상될 수 있으며 안전 위험까지 발생할 수 있다. 분리된 접지 도메인 사이의 전압을 측정할 때는 차동 프로브(Differential Probe), 절연 측정 장비(Isolated Measurement Instrument), 적절하게 절연된 데이터 수집 시스템(Isolated Acquisition System)을 사용하는 것이 바람직하다.

파형 상관관계(Waveform Correlation)는 노이즈 발생원을 확인하는 강력한 근거를 제공할 수 있다. 센서 신호의 외란이 모터 드라이브의 PWM 스위칭 주파수, 접촉기 전환(Contactor Transition), DC/DC 컨버터 동작과 동기화되어 발생한다면 이러한 관계는 가능한 결합 메커니즘(Coupling Mechanism)을 나타낸다. 시간 영역 측정(Time-Domain Measurement)은 과도 현상을 보여줄 수 있으며, 주파수 영역 분석(Frequency-Domain Analysis)은 스위칭 기본 주파수, 고조파(Harmonic), 통신 클록(Communication Clock), 기계적 운전 상태에 대응하는 스펙트럼 성분을 식별할 수 있다.

전류 측정(Current Measurement)을 통해 의도하지 않은 루프가 실제로 상당한 전류를 전달하는지 확인할 수 있다. 케이블, 실드, 접지 스트랩(Ground Strap) 또는 도체 묶음 주변에 전류 프로브(Current Probe)를 설치하면 회로를 개방하지 않고도 저주파 순환 전류와 고주파 공통 모드 전류(Common-Mode Current)를 확인할 수 있다. 신호 케이블 실드나 통신 케이블에서 전류가 측정되고 그 크기가 모터 또는 컨버터 동작에 따라 변화한다면 해당 인터페이스가 리턴 전류 네트워크(Return-Current Network)에 참여하고 있다는 중요한 증거가 된다.

공통 모드 전류 측정(Common-Mode Current Measurement)은 EMC 진단에서 특히 유용하다. 하나의 케이블을 구성하는 모든 도체를 함께 전류 프로브 내부로 통과시키면 의도된 차동 전류(Differential Current)의 자기장이 대부분 서로 상쇄된다. 이후 측정되는 잔여 전류는 케이블에서 다른 경로로 빠져나가 다른 위치를 통해 귀환하는 전류를 나타낸다. 이러한 기법을 사용하면 섀시 결합, 기생 커패시턴스(Parasitic Capacitance), 실드 및 스위칭 전력전자 장치와 관련된 공통 모드 전류를 찾아낼 수 있다.

제어된 분리(Controlled Disconnection)는 또 하나의 강력한 진단 방법이다. 의심되는 2차 접지 경로(Secondary Ground Path)를 한 번에 하나씩 일시적으로 제거하면서 증상의 변화를 관찰할 수 있다. 적절한 시험 지점에서 실드를 분리하거나 외부 통신 케이블을 제거하고, 시험 장비를 분리하거나 절연 인터페이스(Isolated Interface)로 대체하면 어떤 연결이 루프를 완성하는지 확인할 수 있다. 이러한 시험에서는 전기 안전, 보호 접지 요구사항 및 장비의 허용 한계를 반드시 준수해야 한다.

유용한 진단 원칙은 한 번에 하나의 경로만 변경하는 것이다. 여러 접지, 실드, 필터, 케이블을 동시에 변경하면 문제가 개선되더라도 어떤 변경이 실제 원인을 제거했는지 확인하기 어렵다. 제어된 시험 매트릭스(Test Matrix)를 사용하면 진단을 반복 가능하게 만들 수 있다. 각 구성에 대해 연결 상태, 운전 조건, 측정된 접지 전압, 관측된 전류, 신호 품질(Signal Quality), 통신 오류율(Communication Error Rate), 최종적인 시스템 동작을 기록해야 한다.

외부 장비(External Equipment)는 일시적인 접지 루프를 형성하는 경우가 많으므로 특별히 주의해야 한다. 배터리만으로 정상 동작하던 로봇이 프로그래밍 노트북, 충전기, 오실로스코프, 이더넷 스위치(Ethernet Switch), PLC 또는 실험실 전원 공급 장치(Laboratory Power Supply)에 연결되면 노이즈 문제가 발생할 수 있다. 외부 장치가 보호 접지나 다른 접지 네트워크 경로를 추가할 수 있기 때문이다. 독립 운전 구성과 외부 장비 연결 구성을 비교하면 이러한 구성 의존적 문제를 신속하게 식별할 수 있다.

신호에서 나타나는 증상은 영향을 받는 경로를 찾는 데 도움이 될 수 있다. 아날로그 접지 루프 간섭(Analog Ground-Loop Interference)은 오프셋, 리플(Ripple), 드리프트(Drift), 주기적 변조(Periodic Modulation), 불안정한 측정값으로 나타날 수 있다. 디지털 인터페이스에서는 손상된 프레임(Corrupted Frame), 오류 카운터 증가, 예상하지 못한 리셋 또는 대전류 이벤트와 동기화된 고장이 나타날 수 있다. 서로 다른 접지 도메인을 기준으로 하는 여러 신호를 비교하면 외란이 국부적으로 발생하는지 또는 공유 접지 구조를 통해 전파되는지를 파악할 수 있다.

케이블 배선 경로(Cable Routing)는 전기적 도통과 함께 조사해야 한다. 큰 물리적 면적을 갖는 접지 루프는 모터 상 케이블(Motor Phase Cable), 접촉기(Contactor), 변압기(Transformer), 대전류 도체에서 발생하는 자기 결합(Magnetic Coupling)에 더욱 취약하다. 신호 페어(Signal Pair)의 배선 경로를 일시적으로 변경하거나 루프 면적을 감소시키고, 노이즈가 많은 케이블과의 거리를 증가시키거나 촘촘하게 꼬인 차동 페어(Twisted Differential Pair)를 사용하면 자기 유도(Magnetic Induction)와 공유 도전 임피던스(Shared Conductive Impedance)에 의한 간섭을 구분하는 데 도움이 된다.

주파수 의존성(Frequency Dependence)은 또 다른 중요한 단서를 제공한다. 멀티미터(Multimeter)로 측정했을 때 정상적으로 보이는 연결도 전선과 본딩의 인덕턴스 때문에 스위칭 주파수에서는 상당한 임피던스를 나타낼 수 있다. 반대로 직류 전류가 거의 흐르지 않는 섀시 연결도 기생 커패시턴스를 통해 주요 고주파 리턴 경로가 될 수 있다. 따라서 진단에서는 직류 도통 측정에만 의존하지 않고 저항, 인덕턴스, 커패시턴스 및 물리적 기하학적 구조(Physical Geometry)를 함께 고려해야 한다.

대체 시험(Substitution Test)은 인터페이스의 민감성과 노이즈 발생을 구분하는 데 도움이 된다. 단일 종단 연결(Single-Ended Connection)을 일시적으로 차동 인터페이스(Differential Interface)로 교체하거나 도전성 인터페이스를 광 절연(Optical Isolation) 또는 변압기 절연(Transformer Isolation)으로 대체할 수 있다. 갈바닉 절연(Galvanic Isolation) 이후 문제가 사라진다면 도전성 접지 경로가 중요한 원인이었음을 강하게 시사한다. 간섭이 계속된다면 방사 결합(Radiated Coupling), 용량성 결합(Capacitive Coupling), 전원 노이즈 또는 다른 리턴 경로를 조사해야 한다.

진단에서는 최종적으로 노이즈 발생원(Noise Source)과 전체 결합 경로를 모두 식별해야 한다. 단순히 노이즈가 많은 모터 드라이브를 발견하는 것만으로는 충분하지 않다. 동일한 드라이브라도 다른 접지 아키텍처에서는 정상적으로 동작할 수 있기 때문이다. 엔지니어는 노이즈가 어떻게 생성되는지, 어떤 임피던스가 전류를 원하지 않는 전압으로 변환하는지, 외란이 어떤 경로를 통해 피해 회로(Victim Circuit)에 도달하는지, 그리고 전류가 어떤 경로를 통해 발생원으로 귀환하는지를 확인해야 한다.

수정 조치(Corrective Action)는 고장이 발견된 특정 조건에서만 검증해서는 안 되며 전체 운전 영역(Operating Envelope)에 걸쳐 검증해야 한다. 시험에는 높은 모터 전류, 가속 및 제동, 컨버터 부하 변화, 충전, 통신 트래픽(Communication Traffic), 센서 동작 및 관련 외부 연결을 포함해야 한다. 측정을 통해 접지 전위차 또는 의도하지 않은 전류가 감소했음을 확인하는 동시에 신호 무결성(Signal Integrity), 차폐, 안전 본딩(Safety Bonding), 보호 기능이 정상적으로 유지되는지도 검증해야 한다.

따라서 접지 루프 진단은 관찰 가능한 전기적 증거를 바탕으로 실제 전류 흐름(Current Flow)을 재구성하는 과정이다. 접지 맵, 차동 전압 측정, 전류 프로브, 파형 상관관계, 제어된 분리, 배선 경로 시험 및 절연 시험을 단계적으로 적용하면 가능한 발생 메커니즘의 범위를 점차 좁힐 수 있다. 최종 목표는 단순히 증상을 사라지게 만드는 것이 아니라 의도된 리턴 전류와 원하지 않는 공통 모드 전류 또는 순환 전류를 명확하게 구분할 수 있는 예측 가능한 접지 아키텍처(Predictable Grounding Architecture)를 확립하는 것이다.
