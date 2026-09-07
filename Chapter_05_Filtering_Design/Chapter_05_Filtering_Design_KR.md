**Volume 05. Grounding and EMC**

# Chapter 05. Filtering Design

## 05.01. EMI Filter Design

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

아래와 같이 원문의 문단 구조와 순서를 그대로 유지하여 번역했습니다.

전자기 간섭 필터 설계(EMI Filter Design)는 원하지 않는 전도성 전자기 에너지(Conducted Electromagnetic Energy)가 전자 서브시스템(Electronic Subsystem), 케이블(Cable), 전력 네트워크(Power Network), 민감 회로(Sensitive Circuit) 사이로 전파되기 전에 이를 제어하는 체계적인 과정이다. 이 볼륨(Volume)의 필터링 설계(Filtering Design) 구조에서 이는 이후 다루게 될 페라이트 비드(Ferrite Bead), LC 필터(LC Filter), 공통 모드 초크(Common-Mode Choke), 필터 배치 규칙(Filter Placement Rules)의 일반적인 기반을 제공한다.

전자기 간섭 필터(EMI Filter)는 단순히 공칭 주파수 범위(Nominal Frequency Range)에 따라 선택하는 것이 아니라 실제 노이즈 메커니즘(Noise Mechanism)을 기반으로 설계해야 한다. 엔지니어는 먼저 노이즈 소스(Noise Source), 전파 경로(Propagation Path), 영향을 받는 회로(Affected Circuit), 주파수 스펙트럼(Frequency Spectrum), 지배적인 결합 모드(Coupling Mode)를 식별한다. 따라서 전도성 방출 측정(Conducted-Emission Measurement)과 근접장 EMI 매핑(Near-Field EMI Mapping)에서 얻은 정보는 필터 설계 과정의 직접적인 입력이 될 수 있다.

차동 모드 노이즈(Differential-Mode Noise)는 두 도체(Conductor) 사이에서 원하지 않는 전압 또는 전류 형태로 나타나는 반면, 공통 모드 노이즈(Common-Mode Noise)는 여러 도체에서 섀시(Chassis), 접지(Earth) 또는 다른 기준 구조(Reference Structure)를 기준으로 동일한 방향으로 흐른다. 이 두 메커니즘에는 서로 다른 필터링 전략(Filtering Strategy)이 필요하다. 차동 모드 스위칭 리플(Differential-Mode Switching Ripple)에 효과적인 필터가 공통 모드 케이블 전류(Common-Mode Cable Current)에 대해서는 거의 감쇠 효과를 제공하지 못할 수도 있다.

전자기 간섭 필터(EMI Filter)의 기본 기능은 주파수 의존적인 임피던스 불연속(Frequency-Dependent Impedance Discontinuity)을 형성하여 의도된 전력 또는 신호 에너지(Signal Energy)는 통과시키면서 원하지 않는 고주파 에너지(High-Frequency Energy)를 억제하는 것이다. 직렬 소자(Series Element)는 일반적으로 노이즈 전류에 대한 임피던스를 증가시키고, 병렬 소자(Shunt Element)는 원하지 않는 에너지가 흐를 수 있는 낮은 임피던스의 귀환 경로(Return Path)를 제공한다. 이러한 소자들의 조합에 따라 전체 감쇠 특성(Attenuation Characteristic)이 결정된다.

커패시터(Capacitor)는 이상적인 관계식 Z = 1/(jωC)에 따라 주파수가 증가할수록 임피던스가 감소하기 때문에 널리 사용된다. 전원 도체(Power Conductor) 사이에 배치된 커패시터는 차동 모드 노이즈(Differential-Mode Noise)를 우회시킬 수 있으며, 섀시(Chassis) 방향으로 연결된 커패시터는 공통 모드 전류(Common-Mode Current)의 경로를 제공할 수 있다. 그러나 실제 커패시터에는 등가 직렬 저항(Equivalent Series Resistance)과 등가 직렬 인덕턴스(Equivalent Series Inductance)가 존재하므로 고주파 성능(High-Frequency Performance)이 제한된다.

인덕터(Inductor)는 이상적인 관계식 Z = jωL에 따라 주파수가 증가할수록 임피던스가 증가하기 때문에 직렬 필터링 소자(Series Filtering Element)로 유용하다. 실제 주파수 영역에서는 권선 저항(Winding Resistance), 기생 커패시턴스(Parasitic Capacitance), 자기 코어 손실(Magnetic-Core Loss), 포화(Saturation), 자기 공진(Self-Resonance)이 이러한 특성을 변화시킨다. 따라서 인덕터는 공칭 인덕턴스(Nominal Inductance)뿐만 아니라 주파수에 따른 임피던스 특성(Impedance-versus-Frequency Characteristic)을 함께 고려하여 선정해야 한다.

간단한 1차 RC 또는 RL 네트워크(First-Order RC or RL Network)는 중간 수준의 고주파 교란(High-Frequency Disturbance)을 억제할 수 있지만, 전력 전자 시스템(Power Electronic System)에서는 일반적으로 더 강한 감쇠를 얻기 위해 LC, π 또는 T형 네트워크(Network)를 사용한다. LC 구간의 이상적인 차단 주파수(Cutoff Frequency)는 대략 f_c = 1/(2π√LC)로 표현된다. 이 식은 초기 설계값을 제공하지만 실제 감쇠 성능은 소스 임피던스(Source Impedance), 부하 임피던스(Load Impedance), 기생 성분(Parasitic Component)을 함께 고려해야 한다.

필터 삽입 손실(Filter Insertion Loss)은 단순한 부품값보다 더 의미 있는 공학적 지표이다. 이는 필터가 소스(Source)와 부하(Load) 사이에 삽입된 이후 원하지 않는 에너지가 얼마나 감소하는지를 나타낸다. 이론적으로 높은 차수의 필터(High-Order Filter)도 예상하지 못한 임피던스에 연결되면 성능이 저하될 수 있는데, 이는 소스-필터-부하(Source-Filter-Load)의 조합이 극점(Pole), 공진(Resonance), 댐핑(Damping), 실질적인 전달 특성(Transfer Characteristic)을 변화시키기 때문이다.

따라서 임피던스 부정합(Impedance Mismatch)은 실제 전자기 간섭 필터링(EMI Filtering)의 핵심 요소이다. 직렬 임피던스(Series Impedance)는 일반적으로 주변 회로의 임피던스보다 충분히 클 때 가장 효과적이며, 병렬 경로(Shunt Path)는 원하지 않는 주파수 성분에 대해 충분히 낮은 임피던스를 제공해야 한다. 이러한 관점에서 설계하면 전자기 간섭 필터를 독립적인 2포트 소자(Two-Port Component)로만 취급하는 일반적인 오류를 방지할 수 있다.

LC 기반 필터(LC-Based Filter)에서는 공진(Resonance)에 특별한 주의가 필요하다. 손실이 작은 인덕터와 커패시터는 높은 품질 계수(High-Q)를 갖는 네트워크를 형성하여 균일한 억제 대신 공진 주파수 부근에서 신호를 증폭시킬 수 있다. 감쇠(Damping)는 부품의 등가 직렬 저항(ESR), 의도적으로 추가한 저항(Resistance), RC 댐핑 분기(RC Damping Branch), 손실성 자성 재료(Lossy Magnetic Material) 또는 기타 제어된 방법을 통해 도입할 수 있으며, 이를 통해 실제 운전 조건에서 안정적인 감쇠 특성을 유지할 수 있다.

공통 모드 필터링(Common-Mode Filtering)은 전기 시스템과 섀시(Chassis) 또는 주변 구조 사이를 흐르는 전류를 제어해야 한다. 공통 모드 초크(Common-Mode Choke)는 동일한 방향으로 흐르는 전류에는 높은 임피던스를 제공하면서 차동 동작 전류(Differential Operating Current)는 상대적으로 낮은 임피던스로 통과시킬 수 있다. 이후 섀시 기준 커패시터(Chassis-Referenced Capacitor)를 이용하여 짧은 고주파 귀환 경로(High-Frequency Return Path)를 제공함으로써 노이즈가 외부 케이블로 전달되는 것을 방지할 수 있다.

차동 모드 필터링(Differential-Mode Filtering)은 주로 전원선과 리턴 도체(Return Conductor) 사이를 순환하는 스위칭 리플(Switching Ripple)과 노이즈를 대상으로 한다. 직렬 인덕턴스(Series Inductance)와 도체 사이에 연결된 커패시터를 결합하면 기본적인 저역 통과 필터(Low-Pass Filter) 구조가 형성된다. 선정된 부품은 예상 주파수 범위 전체에서 충분한 필터링 성능을 유지하면서 동작 전류, 과도 전압(Transient Voltage), 리플 전류(Ripple Current), 온도 및 고장 조건(Fault Condition)을 견딜 수 있어야 한다.

필터 설계에서는 노이즈 소스(Noise Source) 자체도 고려해야 한다. 스위칭 컨버터(Switching Converter), 모터 인버터(Motor Inverter), PWM 모터 드라이버(PWM Motor Driver), 디지털 프로세서(Digital Processor), 고속 인터페이스(High-Speed Interface)는 서로 다른 스펙트럼 특성(Spectral Signature)을 발생시킨다. 빠른 스위칭 에지(Fast Switching Edge)는 상당한 고주파 고조파(High-Frequency Harmonic)를 포함하므로 기본 스위칭 주파수 성분만 감소시키는 것으로는 훨씬 높은 주파수 영역의 전도성 및 방사성 EMI(Conducted and Radiated EMI)가 상당량 남을 수 있다.

기생 커패시턴스(Parasitic Capacitance)는 로봇 전력 시스템(Robotic Power System)의 공통 모드 노이즈(Common-Mode Noise)에 큰 영향을 미친다. 높은 dV/dt를 갖는 스위칭 노드(Switching Node)는 전류를 섀시, 모터 하우징(Motor Housing), 방열판(Heat Sink), 케이블 실드(Cable Shield), 기계 구조물(Mechanical Structure)에 용량성 결합(Capacitive Coupling)시킬 수 있다. 이 전류가 긴 케이블에 도달하면 해당 케이블이 효율적인 안테나(Antenna)로 동작할 수 있다. 따라서 필터링은 전도 경로(Conducted Path)와 의도하지 않은 고주파 귀환 경로를 모두 제어해야 한다.

부품의 자기 공진(Component Self-Resonance)은 또 다른 실질적인 제한 요소이다. 자기 공진 주파수(Self-Resonant Frequency)를 넘으면 커패시터는 주로 유도성(Inductive)으로 동작할 수 있고, 인덕터는 점차 용량성(Capacitive) 특성을 나타낼 수 있다. 따라서 효과적인 광대역 필터링(Broadband Filtering)을 위해서는 하나의 매우 큰 커패시터나 인덕터에 의존하기보다 서로 보완적인 주파수 특성을 갖는 부품을 조합해야 한다. 필요한 경우 작은 고주파 커패시터(High-Frequency Capacitor)를 큰 벌크 커패시터(Bulk Capacitor)와 함께 사용할 수 있다.

인쇄회로기판 레이아웃(PCB Layout)은 계산상 정확하게 설계된 전자기 간섭 필터의 성공 여부를 결정할 수 있다. 입력 도체(Input Conductor)와 출력 도체(Output Conductor)는 전기장 또는 자기장 결합(Electric or Magnetic Coupling)을 통해 노이즈가 필터를 우회하지 못하도록 물리적으로 분리해야 한다. 병렬 커패시터로 연결되는 경로는 짧고 낮은 임피던스를 가져야 하며, 루프 면적(Loop Area)을 최소화하고 노이즈가 많은 배선과 필터링된 배선이 필터 경계(Filter Boundary)를 가로질러 평행하게 배치되지 않도록 해야 한다.

필터 경계(Filter Boundary)의 개념은 특히 중요하다. 필터링되지 않은 측(Unfiltered Side)과 필터링된 측(Filtered Side)은 전자기적으로 서로 다른 영역으로 취급해야 하며, 두 영역 사이의 전류 경로를 통제해야 한다. 배선, 전원면(Plane), 케이블 또는 섀시 연결이 이 경계를 우발적으로 결합하면 고주파 에너지가 필터 부품 자체를 완전히 우회할 수 있다. 따라서 기계적 패키징(Mechanical Packaging)과 커넥터 배치(Connector Placement) 역시 전자기 간섭 필터 설계의 일부이다.

전원 필터(Power Filter)는 실제 전기 부하 조건(Electrical Loading Condition)에서 평가해야 한다. 인덕터는 피크 전류(Peak Current)에서 포화될 수 있고, 커패시터는 직류 바이어스(DC Bias)에 의해 유효 정전용량(Effective Capacitance)이 감소할 수 있으며, 페라이트 재료(Ferrite Material)는 전류와 온도에 따라 임피던스가 변화할 수 있다. 따라서 전압 정격(Voltage Rating), 전류 정격(Current Rating), 리플 허용 능력(Ripple Capability), 온도 상승(Thermal Rise), 과도 상태 내성(Transient Tolerance), 절연 요구사항(Insulation Requirement), 신뢰성 마진(Reliability Margin)을 감쇠 성능과 함께 고려해야 한다.

로봇 시스템(Robotic System)은 대전류 모터 전자장치(High-Current Motor Electronics)가 민감한 인지 및 컴퓨팅 하드웨어(Perception and Computing Hardware)와 가까운 위치에서 동작하기 때문에 이러한 설계 문제가 특히 까다롭다. 모터 드라이버, DC/DC 컨버터(DC/DC Converter), GPU, 이더넷 인터페이스(Ethernet Interface), 라이다(LiDAR), 카메라(Camera), GNSS 수신기(GNSS Receiver), 관성 측정 장치(IMU), 안전 제어기(Safety Controller)가 동일한 배터리 및 섀시 환경을 공유할 수 있다. 필터링은 한 서브시스템의 스위칭 에너지가 다른 서브시스템을 오염시키는 것을 방지해야 한다.

예를 들어 자율이동로봇 전력 아키텍처(AMR Power Architecture)에서는 배터리에 하나의 대형 필터만 설치하기보다 여러 계층적 경계(Hierarchical Boundary)에 필터링이 필요할 수 있다. 중앙 전원 필터(Central Power Filter)는 전력 분배 네트워크(Power Distribution Network)를 통한 노이즈 전파를 제한하고, 모터 제어기, 컴퓨팅 모듈(Compute Module), 센서 및 통신 장비 주변의 로컬 필터(Local Filter)는 서브시스템별 교란을 억제한다. 이러한 분산형 접근(Distributed Approach)은 제어되지 않는 고주파 전류 경로의 길이를 줄여 준다.

필터 검증(Filter Verification)은 회로 측정과 시스템 수준 전자파 적합성 평가(System-Level EMC Evaluation)를 결합하여 수행해야 한다. 전도성 방출 측정은 전원선과 신호선에 남아 있는 노이즈를 보여주며, 근접장 프로브(Near-Field Probe)는 부품, PCB 영역, 커넥터 및 케이블 주변에서 발생하는 누설을 식별하는 데 도움을 준다. 필터 설치 전후의 스펙트럼(Spectrum)을 비교하면 의도한 주파수에서 감쇠가 발생하는지, 그리고 새로운 공진이 발생했는지를 확인할 수 있다.

따라서 견고한 전자기 간섭 필터(Robust EMI Filter)는 단순히 커패시터와 인덕터를 조합한 회로가 아니다. 이는 노이즈 소스, 전파 네트워크(Propagation Network), 부하, 접지 시스템(Grounding System), 섀시, 실드 구조(Shielding Structure), 물리적 레이아웃(Physical Layout) 사이에 형성되는 공학적 인터페이스(Engineered Interface)이다. 성공적인 설계를 위해서는 공통 모드 및 차동 모드 동작, 임피던스, 공진, 기생 성분, 배치, 전류 용량(Current Capability), 환경 조건(Environmental Condition)을 동시에 고려해야 한다.

이 필터링 설계 장(Filtering Design Chapter)은 페라이트 비드 선정(Ferrite Bead Selection), LC 필터 설계(LC Filter Design), 공통 모드 초크(Common-Mode Choke), 필터 배치 규칙(Filter Placement Rules)을 개별적으로 다루기 전에 이러한 일반적인 전자기 간섭 필터 설계 방법론(EMI Filter Methodology)을 먼저 제시한다. 이러한 구성 순서는 간섭 메커니즘(Interference Mechanism)을 식별하고, 필요한 감쇠량과 임피던스 전략(Impedance Strategy)을 설정하며, 적절한 필터링 기술을 선정한 후, 마지막으로 노이즈 전파를 가장 효과적으로 차단할 수 있는 물리적 위치에 이를 구현하는 실제 엔지니어링 작업 흐름(Engineering Workflow)을 반영한다.

## 05.02. Ferrite Bead Selection

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

페라이트 비드 선정(Ferrite Bead Selection)은 의도된 직류(DC) 또는 저주파 전류(Low-Frequency Current)는 최소한의 방해로 통과시키면서 원하지 않는 고주파 전류(High-Frequency Current)를 억제하기 위한 주파수 영역 임피던스 엔지니어링(Frequency-Domain Impedance Engineering) 작업이다. 전자기 간섭 필터링 아키텍처(EMI Filtering Architecture)에서 비드는 일반적으로 소형 직렬 소자(Series Element)로 동작하며, 손실성 자기 특성(Lossy Magnetic Behavior)을 이용하여 고주파 간섭 에너지 일부를 단순히 저장하고 되돌려 보내는 대신 열로 변환한다.

이상적인 인덕터(Ideal Inductor)와 달리 페라이트 비드(Ferrite Bead)는 주파수에 따라 크게 변화하는 임피던스를 나타낸다. 그 임피던스는 대략 Z(f) = R(f) + jX(f)로 표현할 수 있으며, 여기서 저항 성분(Resistive Component)과 리액턴스 성분(Reactive Component)은 페라이트 재료(Ferrite Material), 형상(Geometry), 권선 또는 도체 구조(Conductor Structure), 동작 조건에 따라 달라진다. 따라서 효과적인 선정을 위해서는 공칭 임피던스(Nominal Impedance)만이 아니라 전체 주파수-임피던스 특성(Impedance-versus-Frequency Characteristic)을 검토해야 한다.

상대적으로 낮은 주파수에서 비드는 주로 작은 유도성 임피던스(Inductive Impedance)로 동작하여 의도된 전원 전류에 거의 전압 강하를 발생시키지 않을 수 있다. 주파수가 증가하면 자기 손실(Magnetic Loss)이 증가하면서 저항 성분이 지배적으로 나타날 수 있다. 이러한 손실 영역(Lossy Region)은 고주파 노이즈 에너지가 강하게 소스 네트워크(Source Network)로 반사되는 대신 소산되기 때문에 전자기 간섭 억제(EMI Suppression)에 특히 유용하다.

제조업체는 일반적으로 100 MHz와 같은 기준 주파수(Reference Frequency)에서 측정한 임피던스값을 이용하여 페라이트 비드의 특성을 표시한다. 예를 들어 100 MHz에서 600 Ω이라는 정격은 부품을 비교하는 데 유용하지만, 전체 EMI 스펙트럼에서 항상 600 Ω을 제공한다는 의미는 아니다. 동일한 공칭 정격(Nominal Rating)을 가진 두 부품도 상당히 다른 임피던스 곡선(Impedance Curve)을 가질 수 있으며, 따라서 실제 회로에서의 억제 성능도 크게 달라질 수 있다.

따라서 첫 번째 선정 단계는 원하지 않는 간섭의 주파수 범위(Frequency Range)를 식별하는 것이다. 전도성 방출 측정(Conducted-Emission Measurement), 오실로스코프 관측(Oscilloscope Observation), 스펙트럼 분석(Spectrum Analysis), 근접장 EMI 매핑(Near-Field EMI Mapping)을 통해 스위칭 기본 주파수(Switching Fundamental), 고조파(Harmonic), 링잉 주파수(Ringing Frequency), 광대역 성분(Broadband Component)을 확인할 수 있다. 선정된 페라이트 비드는 실제 노이즈 에너지를 감소시켜야 하는 주파수 영역에서 충분한 손실성 임피던스를 제공해야 한다.

전류 용량(Current Capability)도 마찬가지로 중요하다. 전원 레일(Power Rail)에 사용되는 페라이트 비드는 원하지 않는 고주파 성분뿐만 아니라 정상 부하 전류(Normal Load Current)도 전달한다. 정격 전류(Rated Current)는 적절한 설계 마진(Design Margin)을 포함하여 예상되는 최대 동작 전류보다 높아야 한다. 과도한 전류는 열적 스트레스(Thermal Stress), 직류 전압 강하(DC Voltage Drop), 자기 바이어스 효과(Magnetic Bias Effect)를 발생시켜 EMI 억제에 사용할 수 있는 유효 임피던스를 감소시킬 수 있다.

일반적으로 DCR로 표시되는 직류 저항(DC Resistance)은 정상 부하 전류에 의해 발생하는 전도 손실(Conduction Loss)을 결정한다. 이 저항과 관련된 대략적인 전력 손실은 P = I²R로 표현할 수 있다. 따라서 고주파 임피던스 특성이 뛰어나더라도 DCR이 지나치게 큰 비드는 고전류 회로에서 허용하기 어려운 전압 강하와 발열을 발생시킬 수 있다. 전력 분배 응용(Power Distribution Application)에서는 EMI 감쇠와 저주파 효율(Low-Frequency Efficiency) 사이의 균형을 의도적으로 고려해야 한다.

직류 바이어스(DC Bias)는 페라이트 비드 성능을 크게 변화시킬 수 있다. 동작 전류가 증가하면 자기 재료(Magnetic Material)가 바이어스된 동작 상태로 이동하고 유효 투자율(Effective Permeability)이 감소할 수 있다. 결과적으로 소신호 실험실 측정(Small-Signal Laboratory Measurement)에서 높은 임피던스를 나타내는 비드도 상당한 직류 전류를 전달할 때는 훨씬 낮은 임피던스를 제공할 수 있다. 따라서 가능한 경우 바이어스에 따른 임피던스 데이터(Bias-Dependent Impedance Data)를 검토해야 한다.

온도(Temperature)는 또 다른 실질적인 선정 변수이다. 페라이트 재료의 특성과 도체 저항(Conductor Resistance)은 온도에 따라 변화하며, 부하 전류에 의한 자기 발열(Self-Heating)은 부품 온도를 더욱 상승시킬 수 있다. 엔지니어는 실온에서의 카탈로그 특성이 실제 동작을 대표한다고 가정하지 말고 예상 주변 온도(Ambient Temperature), 인클로저 조건(Enclosure Condition), 공기 흐름(Airflow), PCB 열 환경(Thermal Environment), 연속 전류(Continuous Current)를 고려하여 비드를 평가해야 한다.

페라이트 재료 조성(Ferrite Material Composition)은 유효 주파수 범위(Useful Frequency Range)를 크게 결정한다. 서로 다른 재료 조성은 서로 다른 투자율과 손실 특성(Loss Characteristic)을 제공하므로 일부 비드는 상대적으로 낮은 주파수의 EMI 영역에서 효과적이고, 다른 비드는 더 높은 주파수 간섭을 대상으로 한다. 따라서 단순히 가장 큰 임피던스 정격을 선택하기보다 재료의 임피던스 피크(Impedance Peak)와 저항성 손실 영역(Resistive-Loss Region)을 실제 측정된 노이즈 스펙트럼과 일치시켜야 한다.

임피던스 곡선(Impedance Curve)을 해석할 때는 저항(Resistance)과 리액턴스(Reactance)의 관계가 중요하다. 주로 유도성 특성을 나타내는 영역에서 비드는 회로의 커패시턴스(Capacitance)와 상호작용하여 공진 네트워크(Resonant Network)를 형성할 가능성이 있다. 반면 저항 성분이 지배적인 영역에서는 주파수 선택적인 손실 소자(Frequency-Selective Loss Element)에 가까운 특성을 보이며 유용한 댐핑(Damping)을 제공할 수 있다. EMI 억제에서는 이러한 저항성 특성이 페라이트 부품의 주요 장점 중 하나이다.

페라이트 비드는 바이패스 또는 디커플링 커패시터(Bypass or Decoupling Capacitor)와 결합하여 저역 통과 필터(Low-Pass Filter) 구조를 형성하는 경우가 많다. 비드는 고주파 전류에 대한 직렬 임피던스를 증가시키고, 커패시터는 해당 전류에 낮은 임피던스의 국부 경로(Local Path)를 제공한다. 이러한 조합은 노이즈가 많은 전원 영역(Noisy Supply Domain)과 민감한 영역(Sensitive Domain)을 분리할 수 있지만, 비드, 커패시터, PCB 인덕턴스(PCB Inductance), 소스 임피던스(Source Impedance)가 동적으로 상호작용하기 때문에 형성된 네트워크의 공진 여부를 확인해야 한다.

따라서 커패시터 선정(Capacitor Selection)은 비드 성능에도 영향을 미친다. 큰 벌크 커패시턴스(Bulk Capacitance)는 낮은 주파수에서 에너지 저장을 지원하며, 작은 세라믹 커패시터(Ceramic Capacitor)는 높은 주파수에서 더 낮은 임피던스를 제공할 수 있다. 유효 정전용량(Effective Capacitance), 등가 직렬 저항(ESR), 등가 직렬 인덕턴스(ESL), 패키지 크기(Package Size), 실장 형상(Mounting Geometry)은 최종 필터 응답(Filter Response)에 영향을 미친다. 따라서 비드와 커패시터는 독립적인 부품이 아니라 하나의 네트워크로 취급해야 한다.

배치(Placement)는 매우 중요하다. 페라이트 비드는 다른 전도성 또는 전자기적 경로(Conductive or Electromagnetic Path)를 통해 우회하는 노이즈를 억제할 수 없기 때문이다. 민감한 회로를 격리할 경우 비드는 일반적으로 노이즈 영역(Noisy Domain)과 보호된 전원 영역(Protected Power Domain)의 경계에 배치해야 한다. 관련 디커플링 커패시터는 고주파 전류가 긴 PCB 배선을 통과하지 않고 보호된 측에서 국부적으로 순환하도록 배치해야 한다.

비드 주변의 PCB 레이아웃(PCB Layout)은 입력 노드와 출력 노드 사이의 의도하지 않은 결합을 최소화해야 한다. 노이즈가 많은 배선과 필터링된 배선이 서로 가깝게 평행하게 배치되면 전기장 또는 자기장 결합(Electric or Magnetic Coupling)을 통해 고주파 에너지가 비드를 우회하여 전달되고 유효 삽입 손실(Insertion Loss)이 감소할 수 있다. 짧은 연결, 제어된 귀환 경로(Controlled Return Path), 작은 루프 면적(Compact Loop Area), 필터링 전후 영역의 명확한 분리가 의도된 필터 경계를 유지한다.

패키지 크기(Package Size)는 전기적, 열적, 기계적 성능에 영향을 미친다. 작은 표면 실장형 비드(Surface-Mount Bead)는 작은 기생 성분과 우수한 고주파 특성을 제공할 수 있지만 전류 용량이 제한되고 직류 저항이 더 높을 수 있다. 큰 패키지는 더 높은 전류와 낮은 전도 손실을 지원할 수 있지만 서로 다른 기생 특성을 나타낼 수 있다. 따라서 패키지 선정에서는 필요한 주파수 응답과 전력 분배 요구사항을 모두 고려해야 한다.

페라이트 비드를 모든 전원 또는 신호 경로에 자동적으로 삽입해서는 안 된다. 잘못 선정된 비드는 전원 임피던스 문제(Supply Impedance Problem)를 발생시키고 과도 전압 변동(Transient Voltage Variation)을 증가시키며 레귤레이터 제어 루프(Regulator Control Loop)와 상호작용하거나 로컬 커패시터(Local Capacitor)와 공진을 형성할 수 있다. 또한 신호 대역폭(Signal Bandwidth), 특성 임피던스(Characteristic Impedance), 귀환 전류 연속성(Return-Current Continuity)을 고려하지 않고 비드를 신호 경로에 직접 배치하면 민감한 고속 인터페이스(High-Speed Interface)의 성능이 저하될 수 있다.

로봇 시스템(Robotic System)에서 페라이트 비드는 전기적으로 노이즈가 많은 서브시스템과 민감한 서브시스템 사이의 국부 격리(Local Isolation)에 특히 유용하다. 모터 드라이버(Motor Driver), 스위칭 레귤레이터(Switching Regulator), 서보 전자장치(Servo Electronics), 고전류 디지털 모듈(High-Current Digital Module)은 공유 전원 네트워크에 광대역 노이즈를 주입할 수 있는 반면, 카메라, 라이다(LiDAR), 관성 측정 장치(IMU), 위성항법시스템 수신기(GNSS Receiver), 통신 트랜시버(Communication Transceiver), 아날로그 센싱 회로(Analog Sensing Circuit)는 더욱 깨끗한 로컬 전원을 필요로 할 수 있다. 적절한 비드 선정은 이러한 노이즈의 전파를 제한하는 데 도움을 준다.

따라서 자율이동로봇(AMR)은 하나의 범용 부품을 모든 곳에 사용하는 대신 서로 다른 전기적 영역에 서로 다른 특성의 페라이트 비드를 사용할 수 있다. 저전류 센서 레일(Low-Current Sensor Rail)을 보호하는 비드는 높은 임피던스와 광대역 손실(Broadband Loss)을 우선할 수 있는 반면, 컴퓨팅 모듈 보조 전원(Compute-Module Auxiliary Supply)에 사용되는 비드는 훨씬 낮은 DCR과 상당히 높은 전류 용량이 필요할 수 있다. 모터 관련 회로는 스위칭 스펙트럼과 전류 수준이 더욱 가혹하기 때문에 또 다른 필터링 특성이 요구될 수 있다.

검증(Verification)은 비드를 설치한 후 대표적인 실제 동작 조건에서 수행해야 한다. 설치 전후의 전도성 노이즈 스펙트럼(Conducted-Noise Spectrum)을 비교할 수 있으며, 오실로스코프 측정을 통해 전원 리플(Supply Ripple)과 과도 응답(Transient Behavior)의 변화를 확인할 수 있다. 근접장 프로빙(Near-Field Probing)을 이용하면 노이즈가 실제로 국부적으로 감소했는지 또는 다른 경로로 단순히 이동했는지를 확인할 수 있다. 또한 열 측정(Thermal Measurement)을 통해 전류 부하가 허용 가능한 수준인지 검증할 수 있다.

억제 성능이 충분하지 않은 경우 단순히 더 큰 공칭 임피던스를 가진 비드를 선택하는 것이 항상 올바른 해결책은 아니다. 엔지니어는 비드의 저항성 임피던스(Resistive Impedance)가 실제 문제가 발생하는 주파수 영역과 겹치는지, 직류 바이어스로 인해 효과가 감소했는지, 노이즈가 차동 모드가 아니라 공통 모드(Common-Mode)인지, PCB 결합이나 접지(Grounding)가 대체 전파 경로를 제공하는지를 확인해야 한다. 수정 방법은 근본적인 노이즈 메커니즘을 기반으로 결정해야 한다.

따라서 페라이트 비드 선정은 주파수에 따른 임피던스 특성, 저항 및 리액턴스 성분, 전류 정격, 직류 저항(DCR), 직류 바이어스, 온도, 재료 조성, 패키지 크기, 주변 커패시턴스, PCB 레이아웃, 실제 노이즈 스펙트럼을 동시에 고려해야 하는 다차원적인 엔지니어링 의사결정(Multidimensional Engineering Decision)이다. 성공적인 부품은 카탈로그에서 가장 높은 임피던스를 갖는 비드가 아니라 실제 동작 조건에서 필요한 손실성 임피던스를 제공하는 비드이다.

전체 필터링 설계 과정(Filtering Design Sequence)에서 페라이트 비드는 보다 구조적인 LC 필터링(LC Filtering), 공통 모드 필터링(Common-Mode Filtering), 물리적 필터 배치(Physical Filter Placement)를 고려하기 전에 고주파 간섭을 제어할 수 있는 소형의 효과적인 방법을 제공한다. 그 효과를 정확하게 확보하려면 페라이트 비드를 전체 소스-필터-부하 네트워크(Source-Filter-Load Network)에 포함된 주파수 의존적 자기 손실 소자(Frequency-Dependent Magnetic Loss Element)로 이해해야 하며, 이러한 접근은 이후의 LC 필터 설계(LC Filter Design)와 공통 모드 초크 분석(Common-Mode Choke Analysis)을 위한 공학적 기반을 형성한다.

## 05.03. LC Filter Design

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

LC 필터 설계(LC Filter Design)는 필요한 직류(DC) 또는 저주파 전력(Low-Frequency Power)을 최소한의 손실로 전달하면서 원하지 않는 주파수 성분을 감쇠하기 위해 인덕턴스(Inductance)와 커패시턴스(Capacitance)를 결합하는 공학적 설계 과정이다. 전자기 간섭 필터링(EMI Filtering)에서 LC 네트워크(LC Network)는 단일 수동 소자(Passive Component)보다 강한 주파수 선택적 감쇠(Frequency-Selective Attenuation)를 제공하며, 스위칭 컨버터(Switching Converter), 모터 드라이버(Motor Driver), 전력 분배 네트워크(Power Distribution Network)에서 상당한 전도성 노이즈(Conducted Noise)가 발생하는 경우 특히 유용하다.

기본적인 LC 저역 통과 필터(LC Low-Pass Filter)는 일반적으로 전력 경로에 인덕터(Inductor)를 직렬로 배치하고 전원 도체와 리턴 도체(Return Conductor) 사이에 커패시터(Capacitor)를 배치한다. 인덕터는 급격한 전류 변화에 저항하고, 커패시터는 고주파 전압 성분에 낮은 임피던스 경로(Low-Impedance Path)를 제공한다. 이 두 소자가 결합되면 2차 필터링 응답(Second-Order Filtering Response)을 형성하여 단순한 1차 네트워크(First-Order Network)보다 차단 영역 이후에서 훨씬 큰 감쇠를 제공할 수 있다.

이상적인 LC 저역 통과 네트워크(LC Low-Pass Network)의 특성 공진 주파수 또는 차단 관련 주파수는 일반적으로 f₀ = 1/(2π√LC)로 추정한다. 이 관계식은 인덕턴스와 커패시턴스 값을 선정하기 위한 초기 기준을 제공한다. 그러나 실제 EMI 설계에서는 필요한 필터 코너 주파수(Filter Corner Frequency)를 원하지 않는 노이즈 스펙트럼(Noise Spectrum)에 맞추어 선정하면서 의도된 동작 대역폭(Operating Bandwidth) 및 정상적인 전력 시스템 동특성(Power-System Dynamics)과는 충분히 분리해야 한다.

인덕턴스나 커패시턴스 중 어느 하나를 증가시키면 특성 주파수(Characteristic Frequency)는 낮아지지만, 더 큰 부품값이 항상 더 좋은 것은 아니다. 높은 인덕턴스는 직류 저항(DC Resistance), 물리적 크기, 비용, 자기 포화(Magnetic Saturation) 위험을 증가시킬 수 있으며, 큰 커패시턴스는 돌입 전류(Inrush Current), 저장 에너지(Stored Energy), 누설(Leakage), 전력 컨버터와의 상호작용을 증가시킬 수 있다. 따라서 부품값은 감쇠 요구사항과 전기적, 열적, 기계적, 동적 제약조건 사이에서 균형을 이루어야 한다.

이상적인 2차 LC 저역 통과 필터의 감쇠 기울기(Attenuation Slope)는 코너 영역 이후에서 대략 데케이드당 40 dB(40 dB per Decade)에 접근할 수 있다. 실제 필터는 부품의 기생 성분(Parasitic Component), 소스 및 부하 임피던스(Source and Load Impedance), PCB 형상(PCB Geometry), 전자기 결합(Electromagnetic Coupling)에 의해 응답이 변화하기 때문에 전체 주파수 범위에서 이러한 이상적인 특성을 거의 달성하지 못한다. 따라서 계산된 부품값은 EMC 성능을 보장하는 값이 아니라 설계를 시작하기 위한 기준으로 보아야 한다.

인덕터 선정(Inductor Selection)은 단순히 공칭 인덕턴스(Nominal Inductance)를 지정하는 것 이상을 요구한다. 부품은 허용할 수 없는 포화나 온도 상승 없이 최대 동작 전류와 과도 전류(Transient Current)를 전달할 수 있어야 한다. 직류 저항은 전도 손실(Conduction Loss)과 전압 강하를 제한할 수 있도록 충분히 낮아야 한다. 코어 재료(Core Material), 전류 정격(Current Rating), 포화 전류(Saturation Current), 열 특성(Thermal Characteristic), 자기 공진 주파수(Self-Resonant Frequency), 목표 EMI 스펙트럼에서의 임피던스 특성을 모두 평가해야 한다.

커패시터 선정(Capacitor Selection) 역시 공칭 커패시턴스만으로 결정해서는 안 된다. 전압 정격(Voltage Rating), 리플 전류 허용 능력(Ripple-Current Capability), 유전체 종류(Dielectric Type), 직류 바이어스 의존성(DC-Bias Dependence), 등가 직렬 저항(ESR), 등가 직렬 인덕턴스(ESL), 온도 특성, 수명은 모두 필터 성능에 영향을 미칠 수 있다. 세라믹 커패시터(Ceramic Capacitor)는 특히 고주파에서 효과적이지만, 유전체 재료와 패키지 구조에 따라 직류 바이어스가 인가될 때 유효 커패시턴스(Effective Capacitance)가 크게 감소할 수 있다.

실제 인덕터와 커패시터에는 사용 가능한 주파수 범위를 제한하는 기생 성분이 존재한다. 인덕터에는 권선 저항(Winding Resistance)과 기생 커패시턴스(Parasitic Capacitance)가 포함되고, 커패시터에는 ESR과 ESL이 존재한다. 자기 공진(Self-Resonance) 부근과 그 이상의 주파수에서는 실제 동작이 이상적인 회로 모델과 크게 달라질 수 있다. 따라서 광대역 EMI 억제(Broadband EMI Suppression)를 위해 서로 다른 간섭 스펙트럼 영역에 최적화된 여러 커패시터 값 또는 필터링 소자가 필요할 수 있다.

공진(Resonance)은 LC 필터 설계에서 가장 중요한 문제 중 하나이다. 이상적인 인덕터와 커패시터는 에너지를 소산하는 대신 저장하기 때문에 댐핑이 작은 LC 네트워크(Lightly Damped LC Network)는 높은 품질 계수 공진(High-Q Resonance)을 형성할 수 있다. 이 경우 필터가 간섭을 균일하게 감소시키는 대신 공진 주파수 주변의 교란을 증폭하거나 전원 링잉(Supply Ringing), 과도 오버슈트(Transient Overshoot)를 증가시키며 소스 컨버터(Source Converter) 및 하류 전자 부하(Downstream Electronic Load)와 바람직하지 않은 상호작용을 일으킬 수 있다.

따라서 안정적인 실제 응답을 얻기 위해서는 댐핑(Damping)이 자주 필요하다. 자연적으로 존재하는 ESR과 권선 저항이 어느 정도 댐핑을 제공하지만 충분하지 않을 수 있다. 추가 저항, RC 댐핑 분기(RC Damping Branch), 의도적인 손실 소자(Lossy Element), 적절하게 선정된 커패시터 ESR을 이용하여 공진 피크(Resonance Peak)를 낮출 수 있다. 목표는 단순히 최대의 이론적 감쇠를 얻는 것이 아니라 유해한 임피던스 피크(Impedance Peak)를 발생시키지 않으면서 예측 가능한 억제 성능을 확보하는 것이다.

소스 및 부하 임피던스는 LC 필터의 실제 전달 함수(Transfer Function)에 큰 영향을 미친다. 일정한 저항성 종단(Resistive Termination)을 가정하여 설계된 필터도 스위칭 레귤레이터(Switching Regulator)와 동적인 전자 부하(Dynamic Electronic Load) 사이에 연결되면 다르게 동작할 수 있다. 컨버터 출력 임피던스(Converter Output Impedance), 케이블 임피던스(Cable Impedance), 로컬 디커플링 네트워크(Local Decoupling Network), 부하 입력 임피던스(Load Input Impedance)가 함께 댐핑과 공진을 결정한다. 따라서 전체 소스-필터-부하 시스템(Source-Filter-Load System)을 평가해야 한다.

스위칭 컨버터에 연결되는 입력 필터(Input Filter)는 컨버터 제어 동특성(Converter Control Dynamics)과 상호작용할 수 있기 때문에 특별한 주의가 필요하다. 정밀하게 조절되는 컨버터(Tightly Regulated Converter)는 특정 동작 범위에서 유효 음의 증분 입력 임피던스(Negative Incremental Input Impedance)를 나타낼 수 있다. LC 입력 필터가 이 영역에서 강한 임피던스 피크를 가지면 발진(Oscillation)이나 과도 응답 저하가 발생할 수 있다. 따라서 필터 설계에서는 EMC 감쇠와 전력 컨버터 안정성(Power-Converter Stability)을 동시에 고려해야 한다.

LC 필터는 직렬 인덕터 양쪽에 커패시터를 추가하여 C-L-C 구조를 형성하는 파이 필터(π Filter)로 확장할 수 있다. 이 토폴로지(Topology)는 주변 임피던스 조건이 적절한 경우 더욱 강한 고주파 감쇠를 제공할 수 있다. T형 구성(T-Type Arrangement)이나 다단 필터(Cascaded Section)도 사용할 수 있다. 필터 차수(Filter Order)를 높이면 잠재적인 감쇠 성능은 증가하지만 동시에 부품 수, 공진 복잡성, 공간 요구사항, 레이아웃 민감도도 증가한다.

커패시터 귀환 경로(Capacitor Return Path)는 직렬 인덕터만큼 중요하다. 커패시터를 통해 우회된 고주파 전류는 짧고 낮은 인덕턴스를 갖는 경로를 통해 되돌아가야 한다. 긴 배선이나 불명확하게 정의된 귀환 구조(Return Structure)는 기생 인덕턴스를 증가시켜 필터링 효과를 감소시킨다. 커패시터가 노이즈를 섀시(Chassis) 방향으로 우회시키도록 설계되었다면 섀시 연결 역시 상당한 인덕턴스를 가진 긴 연결이 아니라 제어된 고주파 경로(Controlled High-Frequency Path)를 제공해야 한다.

물리적 배치(Physical Placement)는 계산된 LC 네트워크가 실제로 효과적인 EMI 필터가 될 수 있는지를 결정한다. 필터는 일반적으로 원하지 않는 전도성 에너지가 전파되는 경계(Boundary) 부근에 배치해야 한다. 입력 배선과 출력 배선은 서로 분리해야 하며 노이즈가 많은 도체가 필터링된 도체와 전자기적으로 결합하지 않도록 해야 한다. 그렇지 않으면 고주파 에너지가 LC 부품을 우회하여 의도된 감쇠 효과를 무력화할 수 있다.

PCB 레이아웃(PCB Layout)은 노이즈 전류 경로와 필터링 경로 모두에서 루프 면적(Loop Area)을 최소화해야 한다. 직렬 인덕터는 의도된 전파 경로를 직접 차단하도록 배치하고, 커패시터는 짧고 넓은 도체를 통해 해당 귀환 기준(Return Reference)에 연결해야 한다. 접지면(Ground Plane)과 전원면(Power Plane)은 고주파 전류가 의도하지 않은 영역을 통과하거나 인지, 통신, 제어 전자장치의 민감한 귀환 경로를 공유하지 않도록 구성해야 한다.

차동 모드 LC 필터(Differential-Mode LC Filter)는 전원 도체와 리턴 도체 사이를 순환하는 스위칭 노이즈를 억제하는 데 특히 효과적이다. 그러나 이것이 자동으로 공통 모드 간섭(Common-Mode Interference)을 해결한다고 가정해서는 안 된다. 두 도체에서 섀시를 기준으로 동시에 흐르는 공통 모드 전류(Common-Mode Current)는 차동 LC 필터를 제한적인 감쇠만 받고 통과할 수 있다. 이러한 경우 공통 모드 초크(Common-Mode Choke), 섀시 기준 커패시터(Chassis-Referenced Capacitor), 실딩(Shielding), 개선된 접지 아키텍처(Grounding Architecture)가 필요할 수 있다.

로봇 플랫폼(Robotic Platform)은 고전력 스위칭 전자장치(High-Power Switching Electronics)와 민감한 디지털 시스템(Sensitive Digital System)이 좁은 전기 아키텍처 내에서 함께 동작하기 때문에 LC 필터 적용 조건이 까다롭다. 모터 인버터(Motor Inverter), 서보 드라이브(Servo Drive), DC/DC 컨버터, 배터리 분배 네트워크(Battery Distribution Network)는 전도성 교란을 발생시킬 수 있으며, GPU, 카메라, 라이다(LiDAR), 관성 측정 장치(IMU), 위성항법시스템 수신기(GNSS Receiver), 이더넷 인터페이스(Ethernet Interface), 안전 제어기(Safety Controller)는 안정적이고 비교적 깨끗한 전원 레일을 필요로 할 수 있다.

따라서 자율이동로봇(AMR)은 여러 전기적 경계에 LC 필터를 사용할 수 있다. DC/DC 컨버터 근처의 필터는 스위칭 노이즈가 주 전력 분배 네트워크(Main Power Distribution Network)로 유입되는 것을 방지할 수 있으며, 다른 필터는 민감한 센서 또는 컴퓨팅 분기(Computing Branch)를 격리할 수 있다. 모터 제어 전자장치 근처의 필터는 차동 스위칭 전류를 국부적으로 제한할 수 있다. 이러한 분산형 필터링 전략(Distributed Filtering Strategy)은 고주파 에너지가 긴 와이어 하니스(Wire Harness)를 따라 이동하여 방사 구조(Radiating Structure)로 동작하는 것을 방지한다.

필터링은 소스와 부하 사이의 임피던스를 변화시키기 때문에 부하 과도 현상(Load Transient)도 설계에 포함해야 한다. 큰 인덕터는 갑작스러운 전력 요구 변화에 소스 전류가 반응하는 속도를 제한할 수 있으므로 하류 커패시턴스(Downstream Capacitance)가 일시적으로 필요한 에너지를 공급해야 한다. 이 관계가 적절하게 설계되지 않으면 필터가 뛰어난 고주파 EMI 감쇠를 제공하더라도 컴퓨팅 모듈이나 센서 클러스터(Sensor Cluster)에 과도한 전압 강하(Voltage Droop)가 발생할 수 있다.

검증(Verification)은 임피던스 및 주파수 응답 분석(Frequency-Response Analysis)에서 시작하여 대표적인 하드웨어에 대한 측정으로 이어져야 한다. 필터 적용 전후의 전도성 방출 스펙트럼(Conducted-Emission Spectrum)을 통해 억제량을 정량화할 수 있으며, 오실로스코프 측정을 통해 리플(Ripple), 링잉(Ringing), 기동 동작(Startup Behavior), 부하 과도 응답(Load-Transient Response)을 확인할 수 있다. 근접장 프로빙(Near-Field Probing)은 전자기적 우회 경로를 식별할 수 있고, 열 측정(Thermal Measurement)은 인덕터와 커패시터가 허용 가능한 동작 범위 내에 있는지를 검증할 수 있다.

부품 공차(Component Tolerance)와 환경 조건(Environmental Condition)도 검증 과정에 포함해야 한다. 인덕턴스는 전류와 온도에 따라 변할 수 있고, 커패시턴스는 전압 및 유전체 특성에 따라 변화할 수 있으며, ESR 역시 주파수와 온도에 따라 달라진다. 공칭 실온 부품값에서만 정상적으로 동작하는 필터는 실제 운전 한계 조건에서 효과가 감소하거나 불안정해질 수 있다. 따라서 견고한 설계(Robust Design)는 일반적인 값만이 아니라 최악 조건 조합(Worst-Case Combination)을 평가해야 한다.

측정된 성능이 시뮬레이션과 다를 경우 단순히 L 또는 C 값을 증가시키기 전에 실제 물리적 네트워크를 조사해야 한다. 기생 결합(Parasitic Coupling), 커넥터 인덕턴스(Connector Inductance), 케이블 특성(Cable Behavior), 접지, 커패시터 실장, 인덕터 포화, 부품 자기 공진, 공통 모드 전파(Common-Mode Propagation)가 결과를 지배할 수 있다. EMI 문제 해결(EMI Troubleshooting)은 어떤 전류 경로가 여전히 제어되지 않고 있는지를 식별한 다음 해당 필터 또는 물리적 아키텍처를 수정하는 방식으로 진행해야 한다.

따라서 LC 필터 설계는 단순히 L과 C를 계산하는 문제가 아니라 임피던스(Impedance), 공진, 에너지 저장(Energy Storage), 레이아웃, 전자파 적합성(EMC)을 통합적으로 고려하는 문제이다. 성공적인 필터는 실제 동작 조건에서 필요한 주파수 감쇠와 함께 충분한 전류 용량, 낮은 전도 손실, 제어된 댐핑, 컨버터 안정성, 과도 응답 성능, 열적 마진(Thermal Margin), 효과적인 물리적 배치를 동시에 만족해야 한다.

전체 필터링 설계 구조(Filtering Design Structure)에서 LC 필터 설계는 일반적인 EMI 필터 설계 방법론(EMI Filter Methodology)과 페라이트 비드 선정(Ferrite Bead Selection)의 다음 단계에 위치하며, 이후 공통 모드 초크(Common-Mode Choke)와 필터 배치 규칙(Filter Placement Rules)을 구체적으로 다루게 된다. 이러한 진행 과정은 기본적인 노이즈 억제 소자에서 시작하여 차동 모드 및 공통 모드 전파(Differential and Common-Mode Propagation)를 더욱 체계적으로 제어하는 방향으로 발전하며, 최종적으로 전기적 필터 특성을 로봇 시스템의 물리적 EMC 아키텍처(Physical EMC Architecture)와 통합한다.

## 05.04. Common Mode Choke

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

공통 모드 초크(Common-Mode Choke)는 두 개 이상의 도체에서 동일한 방향으로 흐르는 원하지 않는 전류를 억제하면서, 의도된 차동 전류(Differential Current)는 상대적으로 낮은 임피던스로 통과시키도록 설계된 결합형 자기 필터링 부품(Coupled Magnetic Filtering Component)이다. 전체 필터링 설계 과정에서 공통 모드 초크는 기존의 차동 모드 필터링(Differential-Mode Filtering)만으로 충분히 제어하기 어려운 공통 모드 간섭(Common-Mode Interference)을 직접 억제함으로써 페라이트 비드(Ferrite Bead)와 LC 필터(LC Filter)를 보완한다.

동작 원리는 공유 자기 코어(Shared Magnetic Core) 내부에서 발생하는 자속 상쇄(Magnetic Flux Cancellation)와 자속 강화(Magnetic Flux Reinforcement)에 기반한다. 정상적인 차동 전류가 한 도체를 통해 나가고 다른 도체를 통해 되돌아오면 두 권선에서 생성되는 자속이 대부분 서로 상쇄된다. 따라서 초크는 상대적으로 낮은 차동 모드 인덕턴스(Differential-Mode Inductance)를 나타내며, 필요한 전력 또는 평형 신호 전류(Balanced Signal Current)를 과도한 전압 강하 없이 통과시킨다.

공통 모드 전류(Common-Mode Current)는 다르게 동작한다. 노이즈 전류가 섀시(Chassis), 접지(Earth) 또는 다른 외부 기준(External Reference)을 기준으로 두 도체에서 동일한 방향으로 흐르기 때문이다. 이 조건에서는 두 권선에서 발생하는 자속이 서로 상쇄되지 않고 강화된다. 이에 따라 큰 공통 모드 인덕턴스(Common-Mode Inductance)가 형성되어 원하지 않는 고주파 전류에 상당한 임피던스를 제공하고, 케이블과 외부 인터페이스를 통한 노이즈 전파를 감소시킨다.

공통 모드 임피던스(Common-Mode Impedance)는 개념적으로 Z_CM = R(f) + jωL_CM으로 근사할 수 있지만, 실제 동작은 주파수에 크게 의존한다. 코어 손실(Core Loss), 권선 저항(Winding Resistance), 누설 인덕턴스(Leakage Inductance), 권선 간 커패시턴스(Interwinding Capacitance), 기생 결합(Parasitic Coupling)이 이상적인 응답을 변화시킨다. 따라서 초크는 부품 사양에 표시된 공칭 인덕턴스만으로 선정하지 말고 주파수에 따른 실제 임피던스 데이터(Impedance-versus-Frequency Data)를 기반으로 선정해야 한다.

효과적인 초크는 실제 간섭이 존재하는 주파수 범위에서 높은 공통 모드 임피던스를 제공해야 한다. 스위칭 컨버터(Switching Converter), 모터 인버터(Motor Inverter), PWM 드라이버(PWM Driver), 디지털 프로세서(Digital Processor), 고속 통신 회로(High-Speed Communication Circuit)는 서로 매우 다른 주파수 영역의 노이즈를 발생시킬 수 있다. 따라서 자기 재료와 초크 구조를 선정하기 전에 전도성 방출 측정(Conducted-Emission Measurement)과 근접장 EMI 매핑(Near-Field EMI Mapping)을 통해 지배적인 주파수를 식별해야 한다.

자기 코어 재료(Magnetic Core Material)는 사용할 수 있는 노이즈 억제 주파수 범위를 크게 결정한다. 서로 다른 페라이트 조성(Ferrite Composition)은 서로 다른 투자율(Permeability)과 손실 특성(Loss Characteristic)을 제공하므로 임피던스 피크(Impedance Peak)와 저항성 손실 영역(Resistive-Loss Region)이 서로 다른 주파수에서 나타난다. 상대적으로 낮은 주파수의 스위칭 노이즈에 최적화된 부품이 수백 MHz 영역의 간섭에는 효과적이지 않을 수 있으며, 반대로 고주파용 초크는 낮은 주파수에서 충분한 임피던스를 제공하지 못할 수 있다.

공통 모드 임피던스의 저항 성분(Resistive Component)은 고주파 간섭 에너지를 단순히 자기적으로 저장하는 대신 소산하기 때문에 특히 중요하다. 높은 리액턴스(Reactive Impedance)를 갖는 초크는 케이블 및 커패시터의 기생 성분과 상호작용하여 공진(Resonance)을 형성할 수 있다. 반면 손실성 주파수 영역(Lossy Frequency Region)에서는 자기 코어 손실이 자연적인 댐핑(Natural Damping)을 제공하여 지나치게 날카로운 공진 응답을 발생시키지 않으면서 공통 모드 전류의 크기를 감소시킬 수 있다.

누설 인덕턴스(Leakage Inductance)는 권선 사이의 불완전한 자기 결합(Imperfect Magnetic Coupling)으로 인해 불가피하게 발생한다. 일반적으로 공통 모드 인덕턴스보다 훨씬 작지만 차동 전류에는 직렬 인덕턴스로 나타나므로 일정 수준의 차동 모드 필터링 효과를 제공할 수 있다. 그러나 과도한 누설 인덕턴스는 고속 신호를 왜곡하거나 커패시터와 상호작용하거나 원하지 않는 과도 전압(Voltage Transient)을 발생시킬 수 있으므로 항상 유리한 요소라고 가정해서는 안 된다.

전력 응용에서는 정상적인 차동 부하 전류가 공통 모드 초크의 권선을 통과하기 때문에 전류 정격(Current Rating)이 매우 중요하다. 차동 전류가 생성하는 자속은 대부분 상쇄되지만 도체 저항으로 인한 I²R 손실과 온도 상승은 여전히 발생한다. 따라서 권선은 허용할 수 없는 발열, 도체 손상 또는 과도한 전압 강하 없이 연속 전류(Continuous Current)와 과도 전류(Transient Current)를 전달하면서 필요한 공통 모드 억제 성능을 유지해야 한다.

코어 포화(Core Saturation)도 고려해야 한다. 이상적으로 평형된 차동 전류는 서로 상쇄되는 자속을 생성하지만 실제 시스템에는 전류 불균형(Current Imbalance), 비대칭적인 권선 특성(Asymmetric Winding Behavior), 직류 오프셋(DC Offset), 누설 전류(Leakage Current), 과도 상태가 존재할 수 있다. 이러한 현상은 코어에 잔류 자속(Residual Magnetic Flux)을 형성할 수 있으므로 특히 모터 드라이브, 전력 컨버터 및 기타 고전류 로봇 서브시스템에서는 충분한 자기적 마진(Magnetic Margin)을 확보해야 한다.

권선 간 및 권선 대 권선 기생 커패시턴스(Interwinding and Winding-to-Winding Parasitic Capacitance)는 주파수가 증가할수록 더욱 중요해진다. 이 커패시턴스는 공통 모드 노이즈가 초크의 자기 임피던스를 우회할 수 있는 의도하지 않은 경로를 제공할 수 있다. 따라서 특정 주파수 이상에서는 부품의 효과가 감소하거나 공진 특성이 나타날 수 있다. 그러므로 물리적 구조(Physical Construction)와 권선 형상(Winding Geometry)은 고주파 초크 선정에서 중요한 요소이다.

공통 모드 초크는 보다 완전한 EMI 필터를 구성하기 위해 커패시터와 함께 사용되는 경우가 많다. 섀시 기준 커패시터(Chassis-Referenced Capacitor)는 초크가 높은 직렬 임피던스를 제공한 이후 공통 모드 전류에 제어된 낮은 임피던스 경로를 제공할 수 있다. 이렇게 구성된 네트워크는 고주파 노이즈가 외부 케이블을 따라 이동하는 대신 국부적으로 우회되도록 한다. 커패시터값과 섀시 연결은 전기 안전(Electrical Safety) 및 누설 전류 요구사항(Leakage-Current Requirement)을 고려하여 선정해야 한다.

전력 시스템에서 도체와 섀시 사이에 연결되는 커패시터는 기능적으로 공통 모드 억제(Common-Mode Suppression)와 관련되는 경우가 많으며, 전원과 리턴 사이에 직접 연결되는 커패시터는 주로 차동 모드 노이즈(Differential-Mode Noise)를 대상으로 한다. 실제 필터는 이 두 기능을 동시에 포함할 수 있다. 공통 모드 초크는 두 도체에 공통으로 존재하는 전류를 억제하고, 차동 커패시터(Differential Capacitor)와 누설 인덕턴스는 두 도체 사이를 순환하는 노이즈 감쇠에 기여한다.

배치(Placement)는 매우 중요하다. 초크가 실제 공통 모드 전류 경로(Common-Mode Current Path)를 차단해야 하기 때문이다. 일반적으로 간섭이 전파되는 커넥터(Connector), 케이블 인터페이스(Cable Interface), 서브시스템 경계(Subsystem Boundary) 가까이에 배치할 때 가장 효과적이다. 노이즈 소스의 경계와 초크 사이에 긴 케이블이나 PCB 배선이 존재하면 필터링 소자가 효과를 발휘하기 전에 해당 도체가 이미 섀시 또는 주변 구조로 에너지를 결합시킬 수 있다.

초크의 입력 측과 출력 측은 전자기적으로 분리되어야 한다. 필터링된 도체와 필터링되지 않은 도체를 서로 가깝게 배선하면 용량성 또는 유도성 결합(Capacitive or Inductive Coupling)이 발생하여 노이즈가 초크를 우회할 수 있다. 따라서 PCB 레이아웃(PCB Layout)은 명확한 필터링 경계(Filtering Boundary)를 유지하고, 루프 면적(Loop Area)을 최소화하며, 연결 경로를 짧게 하고, 제어되지 않은 접지, 전원면(Plane), 섀시 경로를 통해 고주파 전류가 노이즈 영역과 보호 영역 사이를 이동하지 못하도록 해야 한다.

케이블 인터페이스는 긴 케이블에 존재하는 공통 모드 전류가 상당한 방사성 방출(Radiated Emission)을 발생시킬 수 있기 때문에 특히 중요하다. 케이블 길이와 주파수 조건이 효율적인 안테나 동작을 형성하면 비교적 작은 공통 모드 전류도 문제가 될 수 있다. 따라서 케이블이 전자 장치의 인클로저(Enclosure)를 벗어나는 지점 가까이에서 전류를 억제하면 전체 시스템의 전도성 간섭과 방사성 전자기 방출을 동시에 감소시킬 수 있다.

공통 모드 초크는 통신 인터페이스(Communication Interface)에서도 널리 사용되지만 신호 무결성(Signal Integrity)을 신중하게 고려해야 한다. 차동 통신 링크(Differential Communication Link)의 경우 초크는 높은 공통 모드 임피던스를 제공하면서 신호 대역폭 내에서 차동 임피던스, 삽입 손실(Insertion Loss), 불균형(Imbalance), 모드 변환(Mode Conversion)을 최소화해야 한다. 데이터 속도와 스펙트럼 대역폭이 증가할수록 기생 커패시턴스와 누설 인덕턴스의 영향은 더욱 중요해진다.

자동차 이더넷(Automotive Ethernet), 산업용 이더넷(Industrial Ethernet), CAN 기반 네트워크(CAN-Based Network) 및 기타 차동 통신 시스템은 EMC 요구조건에 따라 적절하게 설계된 공통 모드 필터링의 효과를 얻을 수 있다. 그러나 초크는 잘못된 차동 배선, 불연속적인 귀환 경로(Return Path), 부적절한 커넥터 설계 또는 잘못된 실드 종단(Shield Termination)을 보완할 수 없다. 따라서 초크는 독립적인 해결책이 아니라 전체 물리 계층 EMC 아키텍처(Physical-Layer EMC Architecture)를 구성하는 하나의 요소로 취급해야 한다.

로봇 플랫폼(Robotic Platform)에서는 모터 드라이브, DC/DC 컨버터, 배터리, 섀시 구조(Chassis Structure), 케이블 실드(Cable Shield), 센서, 컴퓨팅 모듈이 좁은 기계 시스템 내부에서 서로 연결되어 있기 때문에 다양한 공통 모드 노이즈 경로가 형성된다. 높은 dV/dt를 갖는 스위칭 노드(Switching Node)는 모터 하우징(Motor Housing), 방열판(Heat Sink), 프레임(Frame), 케이블 실드에 전류를 용량성으로 주입할 수 있으며, 이렇게 생성된 공통 모드 전류가 센서 또는 통신 하니스를 통해 전파될 수 있다.

따라서 자율이동로봇(AMR)은 여러 기능적 경계(Functional Boundary)에 공통 모드 초크를 필요로 할 수 있다. 모터 드라이브 전원 연결에는 스위칭 전류가 차량 하니스(Vehicle Harness)로 확산되는 것을 방지하기 위한 억제 기능이 필요할 수 있으며, 센서 전원 분기에는 노이즈가 많은 전력 분배 네트워크로부터의 격리가 필요할 수 있다. 이더넷 또는 기타 통신 인터페이스는 해당 신호 대역폭에 맞게 설계된 전용 초크를 사용할 수 있으며, 외부 충전 또는 보조 인터페이스에도 별도의 필터링 전략이 필요할 수 있다.

공통 모드 초크는 단순히 사용 가능한 부품 중 가장 높은 임피던스를 선택하는 방식으로 선정해서는 안 된다. 엔지니어는 목표 노이즈 스펙트럼(Target Noise Spectrum), 임피던스 곡선(Impedance Curve), 전류 정격, 직류 저항(DC Resistance), 누설 인덕턴스, 기생 커패시턴스, 코어 재료, 온도 상승(Temperature Rise), 절연 요구사항(Insulation Requirement), 패키지 크기(Package Size), 기계적 견고성(Mechanical Robustness)을 함께 고려해야 한다. 올바른 부품은 정상적인 전력 전달 또는 신호 무결성을 유지하면서 충분한 공통 모드 감쇠를 제공하는 부품이다.

검증(Verification)은 공통 모드 특성이 전체 물리적 시스템에 크게 의존하기 때문에 대표적인 실제 하드웨어에 초크를 설치한 상태에서 수행해야 한다. 전도성 방출 측정은 외부 인터페이스에서의 전류 또는 전압 감소량을 정량화할 수 있으며, 전류 프로브(Current Probe)를 사용하면 공통 모드 케이블 전류를 직접 확인할 수 있다. 근접장 측정(Near-Field Measurement)은 남아 있는 결합 경로를 식별할 수 있고, 방사성 방출 시험(Radiated-Emission Testing)은 케이블 전류 감소가 예상한 시스템 수준의 개선으로 이어졌는지를 확인할 수 있다.

측정된 억제 성능이 충분하지 않은 경우 단순히 초크 임피던스를 증가시키는 것만으로 문제를 해결하지 못할 수 있다. 노이즈가 기생 커패시턴스, 섀시 연결, 케이블 실드, 장착 구조(Mounting Structure), 의도하지 않은 접지 경로를 통해 부품을 우회할 수 있기 때문이다. 또한 간섭에 상당한 차동 모드 성분이 포함되어 있을 수도 있다. 따라서 효과적인 문제 해결은 필터를 수정하기 전에 공통 모드와 차동 모드 메커니즘을 분리하고 실제 물리적 귀환 경로를 식별하는 방식으로 수행해야 한다.

공통 모드 초크 설계는 궁극적으로 결합 자기 임피던스(Coupled Magnetic Impedance)를 이용하여 고주파 전류 경로를 제어하는 문제이다. 그 효과는 자기 재료, 권선 결합(Winding Coupling), 주파수 의존적 손실(Frequency-Dependent Loss), 기생 커패시턴스, 누설 인덕턴스, 전류 용량, 배치, 섀시 전략(Chassis Strategy), 주변 회로에 의해 결정된다. 이러한 요소들이 적절하게 조정되면 공통 모드 초크는 전도성 간섭과 케이블에 의해 발생하는 방사성 간섭을 모두 크게 감소시킬 수 있다.

전체 필터링 설계 구조(Filtering Design Structure)에서 공통 모드 초크 분석(Common-Mode Choke Analysis)은 EMI 필터 설계(EMI Filter Design), 페라이트 비드 선정(Ferrite Bead Selection), LC 필터 설계(LC Filter Design)의 다음 단계에 위치하며, 이후 필터 배치 규칙(Filter Placement Rules)으로 직접 이어진다. 이러한 진행 과정은 단순한 부품 선정만으로는 충분하지 않다는 점을 강조한다. 효과적인 전자파 적합성(EMC)을 확보하려면 원하지 않는 전류 경로가 실제로 차단될 수 있도록 적절한 필터링 메커니즘을 정확한 전기적·물리적 경계(Electrical and Physical Boundary)에 배치해야 한다.

## 05.05. Filter Placement Rules

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

필터 배치(Filter Placement)는 필터가 실제 노이즈 전파 경로(Noise Propagation Path) 내에 위치할 때만 간섭을 억제할 수 있기 때문에 전자파 적합성(Electromagnetic Compatibility)의 핵심 요소이다. 정확하게 계산된 EMI 필터(EMI Filter), 페라이트 비드(Ferrite Bead), LC 네트워크(LC Network), 공통 모드 초크(Common-Mode Choke)라도 고주파 전류가 필터링 소자를 만나기 전에 케이블, 커넥터, 섀시 구조(Chassis Structure), 민감한 서브시스템에 도달하면 시스템 수준에서 거의 개선 효과를 제공하지 못할 수 있다.

가장 기본적인 배치 규칙은 원하지 않는 에너지가 서브시스템으로 들어오거나 빠져나가는 전기적 경계(Electrical Boundary)에 필터를 배치하는 것이다. 내부에서 발생한 노이즈의 경우 일반적으로 노이즈 소스(Noise Source) 또는 노이즈가 외부로 빠져나가는 인터페이스 가까이에서 필터링해야 한다. 민감한 전자장치의 경우 잠재적으로 오염된 전원이나 신호가 보호 영역(Protected Domain)으로 들어오는 지점 가까이에 필터를 배치해야 한다.

이러한 경계 개념(Boundary Concept)은 시스템을 노이즈 영역(Noisy Region)과 클린 영역(Clean Region)으로 구분한다. 필터링되지 않은 측의 도체는 필터링된 측의 도체와 물리적·전기적으로 분리되어야 한다. 배선, 와이어, 전원면(Plane), 부품이 필터 주변에서 교차 결합(Cross-Coupling)되면 고주파 에너지가 의도된 임피던스를 우회하여 두 영역을 실질적으로 다시 연결할 수 있으며, 이에 따라 필터 네트워크가 제공하는 삽입 손실(Insertion Loss)이 감소한다.

따라서 필터를 긴 PCB 배선이나 케이블 구간의 중간에 임의로 배치해서는 안 된다. 노이즈 소스와 필터 사이에 긴 도체가 존재하면 해당 도체가 결합 구조(Coupling Structure) 또는 안테나(Antenna)처럼 동작하여 노이즈가 억제되기 전에 간섭을 전파할 수 있다. 마찬가지로 외부 커넥터와 인터페이스 필터 사이의 연결이 길면 공통 모드 전류(Common-Mode Current)가 인클로저(Enclosure), 섀시 또는 인접 회로에 결합될 수 있다.

외부 케이블 인터페이스(External Cable Interface)에서는 일반적으로 커넥터 또는 인클로저 관통부(Enclosure Penetration)에 가깝게 필터를 배치할 때 가장 효과적이다. 이러한 배치는 원하지 않는 전류가 내부 배선을 따라 흐르는 것을 방지하고 방사성 방출(Radiated Emission)에 참여할 수 있는 도체의 길이를 제한한다. 공통 모드 초크, 피드스루 구조(Feedthrough Structure), 섀시 기준 커패시터(Chassis-Referenced Capacitor) 및 기타 인터페이스 필터는 특히 전자기적 경계(Electromagnetic Boundary)에 직접 배치할 때 효과적이다.

소스 측 필터링(Source-Side Filtering)은 스위칭 전력 전자장치(Switching Power Electronics)에서 특히 중요하다. DC/DC 컨버터, PWM 모터 드라이버(PWM Motor Driver), 인버터(Inverter), 서보 드라이브(Servo Drive) 및 기타 고속 스위칭 회로는 가능한 한 고주파 전류 루프(High-Frequency Current Loop)를 국부적으로 유지해야 한다. 이러한 회로 가까이에 필터를 배치하면 스위칭 고조파(Switching Harmonic)와 링잉 전류(Ringing Current)가 전체 전력 분배 네트워크로 유입되어 케이블과 전원면을 통해 시스템 전체로 확산되는 것을 방지할 수 있다.

부하 측 필터링(Load-Side Filtering)은 공유 네트워크에 이미 존재하는 노이즈로부터 민감한 서브시스템을 보호하는 것이 주요 목적일 때 적합하다. 카메라(Camera), 라이다(LiDAR), 관성 측정 장치(IMU), 위성항법시스템 수신기(GNSS Receiver), 아날로그 센서(Analog Sensor), 통신 트랜시버(Communication Transceiver), 컴퓨팅 모듈(Computing Module)은 전원 입력 지점 가까이에 로컬 필터링(Local Filtering)을 사용할 수 있다. 이후 필터링된 출력은 다시 전기적으로 노이즈가 많은 영역을 지나지 않고 보호 회로에 직접 공급되어야 한다.

필터 부품과 관련 바이패스 커패시터(Bypass Capacitor) 사이의 물리적 거리는 성능에 큰 영향을 미칠 수 있다. 고주파 전류는 회로도상의 연결 형태가 아니라 실제 임피던스에 의해 결정되는 경로를 따라 흐르며, 짧은 PCB 배선에도 인덕턴스(Inductance)가 존재한다. 따라서 병렬 커패시터(Shunt Capacitor)는 원하지 않는 전류가 커패시터에 도달하기 전에 큰 루프를 통과하지 않고 국부적으로 귀환할 수 있도록 짧고 넓은 경로를 통해 연결해야 한다.

귀환 경로 배치(Return-Path Placement)는 순방향 도체의 필터 배치만큼 중요하다. 노이즈 전류가 필터링 경계를 우회하는 제어되지 않은 귀환 경로(Uncontrolled Return Path)를 가지고 있다면 필터는 의도한 대로 동작할 수 없다. 전원 리턴(Power Return), 신호 리턴(Signal Return), 섀시, 케이블 실드(Cable Shield), 장착 구조(Mounting Structure), 기생 커패시턴스(Parasitic Capacitance)가 모두 고주파 전류 루프에 참여할 수 있다. 따라서 배치를 결정할 때 양의 전원 도체만이 아니라 전체 전류 경로를 고려해야 한다.

필터 양쪽에서 루프 면적(Loop Area)을 최소화해야 한다. 노이즈 루프는 자기장이 인접 회로에 약하게 결합되도록 작게 유지해야 하며, 필터링된 루프는 고전류 스위칭 회로와 경로를 공유하지 않아야 한다. 순방향 도체와 귀환 도체를 서로 가깝게 유지하면 루프 인덕턴스(Loop Inductance)도 감소하고 자기장 방사(Magnetic-Field Radiation)를 제한할 수 있으므로 전도성 및 방사성 EMC 특성을 모두 개선할 수 있다.

가능한 경우 필터의 입력 배선(Input Trace)과 출력 배선(Output Trace)을 서로 가깝게 평행하게 배치해서는 안 된다. 이러한 배선은 용량성 및 유도성 결합(Capacitive and Inductive Coupling)을 형성하여 고주파 에너지를 필터링되지 않은 측에서 필터링된 측으로 직접 전달한다. 이러한 전자기적 우회(Electromagnetic Bypass)는 주파수가 증가할수록 중요해지며 이론적으로 우수한 필터도 효과를 잃게 만들 수 있다. 따라서 물리적 분리(Physical Separation) 자체가 필터 전달 특성(Filter Transfer Function)의 일부이다.

접지면(Ground Plane)과 전원면(Power Plane) 역시 동일한 주의가 필요하다. 두 영역 사이에 배치된 필터도 그 아래에 연속적인 전원면이 존재하여 제어되지 않은 고주파 전류가 경계를 넘어 결합될 수 있다면 우회될 수 있다. 반대로 불필요하게 전원면을 분할하면 귀환 전류 연속성(Return-Current Continuity)이 손상되고 방사가 증가할 수 있다. 따라서 전원면 전략(Plane Strategy)은 단순한 기하학적 분리가 아니라 실제 공통 모드 및 차동 모드 전류 경로(Common-Mode and Differential-Mode Current Path)를 기반으로 결정해야 한다.

섀시 기준 필터링(Chassis-Referenced Filtering)에서는 특히 낮은 인덕턴스를 갖는 섀시 연결(Low-Inductance Chassis Connection)이 필요하다. 공통 모드 노이즈를 섀시 방향으로 우회시키기 위한 커패시터도 길고 좁은 배선, 와이어 또는 멀리 떨어진 접지 지점을 통해 연결되면 효과가 감소한다. 고주파에서는 이러한 연결부의 인덕턴스가 커패시터 임피던스보다 지배적일 수 있다. 따라서 섀시 연결은 짧고 넓으며 필터링 대상 인터페이스와 물리적으로 가까워야 한다.

케이블 실드(Cable Shield)와 필터 배치는 서로 연계하여 설계해야 한다. 실드 케이블(Shielded Cable)이 인클로저로 들어오는 경우 실드 종단(Shield Termination)은 일반적으로 진입 지점에서 의도된 고주파 경계를 형성해야 한다. 실드 전류가 섀시에 연결되기 전에 전자장치 내부 깊숙이 이동하면 공통 모드 에너지가 내부 회로에 결합될 수 있다. 따라서 필터 부품과 실드 종단은 하나의 일관된 인터페이스 EMC 구조(Interface EMC Structure)를 형성해야 한다.

페라이트 비드(Ferrite Bead)는 격리하려는 전원 영역의 경계에 배치할 때 가장 효과적이다. 센서 전원 레일(Sensor Rail)을 보호하는 비드는 노이즈가 많은 상류 전원(Upstream Supply)과 로컬 클린 전원(Local Clean Supply)을 분리해야 하며, 디커플링 커패시턴스(Decoupling Capacitance)는 보호된 측에 배치해야 한다. 동일한 비드를 부하에서 멀리 배치하면 필터링된 측의 긴 배선이 주변 스위칭 노드나 모터 전류 도체로부터의 결합에 노출될 수 있다.

LC 필터(LC Filter)는 인덕터와 커패시터가 에너지 저장 네트워크(Energy-Storage Network)를 형성하기 때문에 추가적인 배치 주의가 필요하다. 직렬 인덕터(Series Inductor)는 노이즈 전파 경로를 직접 차단해야 하며, 병렬 커패시터는 작은 귀환 경로(Compact Return Path)를 가져야 한다. 두 부품 사이의 거리가 지나치게 멀면 기생 인덕턴스와 결합이 증가하여 계산된 응답을 변화시키고 이상적인 회로 모델에는 존재하지 않았던 공진(Resonance)을 발생시킬 수 있다.

공통 모드 초크(Common-Mode Choke)는 일반적으로 공통 모드 전류가 긴 케이블로 유입되거나 서브시스템 경계를 통과하기 직전의 위치에 배치해야 한다. 두 도체는 의도된 방식으로 초크를 통과해야 하며, 신호 무결성(Signal Integrity)이 중요한 경우 배선의 대칭성(Symmetry)을 유지해야 한다. 필터링된 도체 쌍과 필터링되지 않은 도체 쌍은 기생 결합이 자기 부품을 우회하는 대체 고주파 경로를 만들지 않도록 서로 분리해야 한다.

필터 배치에서는 열과 전류 용량(Current Capability)도 고려해야 한다. 모터 드라이버, 프로세서(Processor), 컨버터 또는 기타 열원 가까이에 위치한 부품은 부품 선정 과정에서 가정한 것보다 훨씬 높은 온도에서 동작할 수 있다. 온도가 증가하면 저항, 자기 특성(Magnetic Property), 커패시턴스, 수명이 변화할 수 있다. 따라서 전자기적으로 이상적인 위치라 하더라도 열적, 기계적, 신뢰성(Reliability), 정비성(Serviceability) 요구사항을 동시에 만족해야 한다.

로봇 시스템(Robotic System)에서는 전력, 통신, 센서, 모터 하니스(Harness)가 제한된 패키징 공간을 공유하는 경우가 많기 때문에 케이블 라우팅(Cable Routing)과 필터 배치가 특히 중요하다. 필터만으로는 노이즈가 많은 모터 케이블과 민감한 센서 배선이 긴 구간 동안 평행하게 배치되는 문제를 보상할 수 없다. 상당한 결합이 발생하기 전에 노이즈가 억제될 수 있도록 물리적 분리, 제어된 교차(Controlled Crossing), 실딩(Shielding), 접지(Grounding), 필터링을 함께 조정해야 한다.

자율이동로봇 전력 분배 아키텍처(AMR Power Distribution Architecture)는 계층적 필터 배치(Hierarchical Filter Placement)를 통해 효과를 얻을 수 있다. 먼저 모터 드라이버와 스위칭 컨버터에서 노이즈를 국부적으로 억제하고, 이후 전력 분배 경계에서 추가 필터링을 수행하며, 민감한 부하 가까이에서 다시 로컬 필터링을 적용할 수 있다. 이러한 방식은 하나의 대형 중앙 필터에 의존하는 것보다 고주파 전류가 분산된 전자 모듈 사이의 긴 하니스 구간을 따라 전파되는 것을 방지하는 데 일반적으로 더 효과적이다.

통신 인터페이스(Communication Interface)는 EMC와 신호 무결성을 동시에 유지할 수 있는 위치에 필터를 배치해야 한다. 이더넷(Ethernet) 또는 기타 고속 차동 링크(High-Speed Differential Link)의 공통 모드 필터링은 의도된 물리 계층(PHY), 커넥터, 트랜스포머(Transformer), 실드, 귀환 경로 아키텍처에 따라 배치해야 한다. 이러한 요소 사이의 배선이 지나치게 길면 불균형(Imbalance)과 모드 변환(Mode Conversion)이 증가하여 차동 신호 에너지가 공통 모드 방사로 변환되거나 외부 간섭이 수신기로 유입될 수 있다.

필터링은 인클로저 경계(Enclosure Boundary)와의 관계도 고려하여 배치해야 한다. 도전성 인클로저(Conductive Enclosure)는 케이블 진입, 실드 종단, 필터링, 섀시 본딩(Chassis Bonding)이 표면에서 적절하게 조정될 때 효과적인 전자기 기준(Electromagnetic Reference)을 제공할 수 있다. 필터링되지 않은 도체가 필터링되기 전에 인클로저 내부 깊숙이 들어가도록 허용하면 이러한 경계가 약해지고 외부와 내부의 전자기 환경이 서로 결합될 수 있다.

배치 검증(Placement Verification)은 회로도 분석만으로는 기생 결합을 완전히 표현할 수 없기 때문에 실제 하드웨어에서 수행해야 한다. 근접장 프로브(Near-Field Probe)를 이용하여 필터 입력 측과 출력 측의 노이즈 수준을 비교할 수 있으며, 전류 프로브(Current Probe)를 사용하여 케이블의 공통 모드 전류를 식별할 수 있다. 전도성 및 방사성 방출 측정(Conducted and Radiated Emission Measurement)을 통해 필터 위치 변경이 시스템 동작에 미치는 영향을 확인할 수 있으며, 이를 통해 부품값만큼 배치가 중요하다는 사실을 확인할 수 있다.

필터가 예상보다 낮은 감쇠 성능을 제공하는 경우 부품을 교체하기 전에 먼저 우회 경로(Bypass Path)를 조사해야 한다. 입력과 출력 사이의 결합, 긴 커패시터 귀환 경로, 공유 접지 임피던스(Shared Ground Impedance), 케이블 실드, 섀시 연결, 커넥터 형상(Connector Geometry), 주변의 노이즈 배선이 모두 필터를 우회할 수 있다. 기존 부품을 비교적 짧은 물리적 거리만 이동시키는 것만으로도 공칭 임피던스를 크게 증가시키는 것보다 더 큰 개선 효과를 얻을 수 있는 경우가 있다.

따라서 효과적인 필터 배치는 회로도의 논리적 구성(Logical Organization)이 아니라 실제 고주파 전류의 물리적 흐름(Physical Flow)을 따라야 한다. 엔지니어는 노이즈 소스, 결합 경로(Coupling Path), 피해 회로(Victim), 순방향 경로(Forward Path), 귀환 경로를 식별하고 전자기적 경계를 설정한 다음 적절한 필터링 메커니즘을 해당 경계에 직접 배치해야 한다. 이후 레이아웃, 접지, 실딩, 커넥터 설계, 케이블 라우팅을 통해 필터가 형성한 분리 상태를 유지해야 한다.

전체 필터링 설계 구조(Filtering Design Structure)에서 필터 배치 규칙(Filter Placement Rules)은 EMI 필터 설계(EMI Filter Design), 페라이트 비드 선정(Ferrite Bead Selection), LC 필터 설계(LC Filter Design), 공통 모드 초크 분석(Common-Mode Choke Analysis)에 이어 필터링 설계 과정을 완성한다. 핵심 원칙은 올바른 부품, 노이즈 메커니즘(Noise Mechanism), 전류 경로(Current Path), 물리적 위치(Physical Location)를 서로 독립적인 전기적 설계 요소가 아니라 하나의 통합된 설계 문제(Integrated Design Problem)로 다룰 때만 EMC 필터링이 효과적으로 작동한다는 것이다.
