**Volume 05. Grounding and EMC**

# Chapter 09. Camera EMI

## 09.01. MIPI CSI-2 Noise Countermeasure

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

MIPI CSI-2는 적은 핀 수와 낮은 전력 소비로 높은 데이터 처리량을 제공하기 때문에 이미지 센서(Image Sensor)와 프로세서(Processor)를 연결하는 데 널리 사용된다. 그러나 로봇 시스템에서는 모터(Motor), DC-DC 컨버터(DC-DC Converter), 스위칭 레귤레이터(Switching Regulator), 대전류 배선(High-Current Wiring), 무선 통신 모듈(Wireless Module) 가까이에서 동작하는 경우가 많다. 이러한 잡음원(Noise Source)은 카메라 인터페이스(Camera Interface)에 전자기 잡음(Electromagnetic Noise)을 결합시켜 디지털 링크가 정상적으로 동작하는 것처럼 보여도 영상 신뢰성을 저하시킬 수 있다.

일반적인 MIPI CSI-2 카메라 경로(Camera Path)는 이미지 센서(Image Sensor), D-PHY 또는 C-PHY 물리 인터페이스(Physical Interface), 차동 데이터 레인(Differential Data Lane), D-PHY 시스템의 클록 레인(Clock Lane), 커넥터(Connector) 또는 플렉스 케이블(Flex Cable), 수신 프로세서(Receiving Processor)로 구성된다. 레인 전송률(Lane Rate)은 수 Gbps에 이를 수 있으므로 신호 에지(Signal Edge)는 상당한 고주파 에너지(High-Frequency Energy)를 포함한다. 따라서 이 인터페이스는 일반적인 저전압 디지털 배선이 아니라 제어된 고속 전송 구조(Controlled High-Speed Transmission Structure)로 취급해야 한다.

잡음 문제(Noise Problem)는 방출(Emission)과 내성(Susceptibility) 메커니즘 모두를 통해 발생한다. 빠른 MIPI 신호 천이(Transition)는 주변 회로에 에너지를 방사하거나 결합할 수 있으며, 외부 전자기장(Electromagnetic Field)은 차동 레인(Differential Lane)을 교란할 수 있다. 로봇 플랫폼에서는 모터 인버터 스위칭(Motor Inverter Switching), PWM 에지(PWM Edge), DC-DC 컨버터 스위칭 노드(Switching Node), 대전류 정류(High-Current Commutation)가 특히 중요하다. 이들의 고조파(Harmonic)는 기본 스위칭 주파수를 훨씬 넘어 확장되어 고속 카메라 회로와 상호작용할 수 있다.

차동 신호(Differential Signaling)는 두 도체에 동일하게 결합되는 잡음에 대해 높은 제거 능력을 제공하지만, 이러한 장점은 신호 경로의 대칭성(Symmetry)이 유지될 때에만 충분히 확보된다. 트레이스 형상(Trace Geometry), 커넥터 기생성분(Connector Parasitics), 비아(Via), 기준면(Reference Plane), 케이블 구조의 차이는 차동 신호의 일부를 공통 모드 에너지(Common-Mode Energy)로 변환한다. 이러한 모드 변환(Mode Conversion)은 방사 방출(Radiated Emission)을 증가시키는 동시에 잡음 내성을 감소시키므로 차동쌍 균형(Differential-Pair Balance)은 MIPI CSI-2 EMC 설계의 핵심 요구사항이다.

PCB 배선(PCB Routing)은 전체 채널에서 선택된 MIPI 물리 계층(Physical Layer)이 요구하는 차동 임피던스(Differential Impedance)를 유지해야 한다. 차동쌍 간격(Pair Spacing), 트레이스 폭(Trace Width), 유전체 두께(Dielectric Thickness), 기준면과의 거리는 제어되어야 한다. 급격한 형상 변화, 불필요한 비아, 긴 스텁(Long Stub), 테스트 패드(Test Pad), 불연속부(Discontinuity)는 임피던스 교란을 발생시켜 반사(Reflection), 지터(Jitter), 차동-공통 모드 변환(Differential-to-Common-Mode Conversion)을 유발하므로 최소화해야 한다.

연속적인 귀환 전류 경로(Return-Current Path)도 매우 중요하다. 고주파 귀환 전류(High-Frequency Return Current)는 단순히 접지까지의 가장 짧은 기하학적 경로가 아니라 신호 도체 가까이에 형성되는 최소 임피던스 경로(Path of Minimum Impedance)를 따른다. MIPI 차동쌍을 분할된 기준면(Split Reference Plane), 섀시 간극(Chassis Gap), 연결이 불충분한 접지 영역, 큰 PCB 절개부 위로 배선하면 귀환 전류가 우회하면서 전자기 루프(Electromagnetic Loop)가 커진다. 따라서 차동 레인은 연속적인 접지 구조(Continuous Ground Structure)를 기준으로 배선해야 한다.

레인 간 스큐(Lane-to-Lane Skew)와 차동쌍 내부 스큐(Intra-Pair Skew)는 제어해야 하지만 과도한 서펜타인 보상(Serpentine Compensation)은 피해야 한다. 크거나 조밀하게 배치된 미앤더(Meander)는 명목상의 길이 정합(Length Matching)을 개선하더라도 추가적인 불연속과 원하지 않는 결합을 발생시킬 수 있다. 따라서 불필요한 기하학적 동일성을 추구하기보다 전기적 대칭성(Electrical Symmetry)과 깨끗한 배선 형상을 우선해야 한다. 최종 판단 기준은 실제 동작 데이터 전송률에서 충분한 타이밍 및 신호 무결성 여유(Signal-Integrity Margin)를 확보하는 것이다.

커넥터(Connector)와 연성 인쇄 회로(Flexible Printed Circuit)는 형상이 PCB의 제어된 트레이스보다 불완전하기 때문에 잡음에 민감한 주요 영역이 되는 경우가 많다. 접지 접점(Ground Contact)은 고속 신호 주변에 적절히 분포되어야 하며 PCB, 커넥터, 플렉스 케이블 사이의 전이 구간에서도 귀환 경로가 유지되어야 한다. 패키징이 허용하는 범위에서 긴 비차폐 플렉스 구간(Unshielded Flex Section)은 모터, 인덕터, 스위칭 노드, 안테나 급전부(Antenna Feed), 대전류 하네스(High-Current Harness)에서 떨어뜨려 배치해야 한다.

물리적 분리(Physical Separation)는 EMC 문제가 발생한 이후 필터를 추가하는 것보다 효과적인 경우가 많다. 카메라 케이블(Camera Cable)은 모터 상 배선(Motor Phase Cable), 인버터 출력 배선(Inverter Output Wiring), 대전류 배터리 도체와 긴 구간 동안 평행하게 배선하지 않는 것이 좋다. 교차가 불가피한 경우에는 가능한 한 수직에 가까운 각도로 교차시키는 것이 일반적으로 결합을 줄인다. 스위칭 전력 부품과 충분한 거리를 유지하고 민감한 카메라 전자회로를 전자기적으로 조용한 영역에 배치하면 시스템 견고성(System Robustness)을 크게 향상시킬 수 있다.

카메라 전원 무결성(Power Integrity)은 MIPI 신뢰성과 밀접하게 관련된다. 센서 전원 레일(Power Rail)에 유입된 잡음은 내부 PLL, 클록(Clock), 직렬화기(Serializer), 아날로그 회로(Analog Circuit), 픽셀 판독 회로(Pixel Readout Circuit)를 변조할 수 있기 때문이다. 로컬 디커플링 커패시터(Local Decoupling Capacitor)는 관련 센서 전원 핀 가까이에 짧은 전류 루프를 형성하도록 배치해야 한다. 전원 분배망(Power Distribution Network)은 필요한 주파수 범위에서 낮은 임피던스를 제공해야 하며, 잡음이 많은 시스템 전원에는 페라이트 비드(Ferrite Bead), LC 필터(LC Filter), 전용 레귤레이터(Dedicated Regulator)가 필요할 수 있다.

접지 설계(Ground Design)는 대전류 액추에이터 귀환 전류(Actuator Return Current)가 민감한 카메라 귀환 경로를 공유하지 않도록 해야 한다. 카메라 접지는 프로세서 측 기준점과 낮은 임피던스로 연결되어야 하며 모터, 인버터, 컨버터 전류가 동일한 좁은 PCB 또는 하네스 경로를 통해 흐르는 구조를 피해야 한다. 고주파 영역에서는 멀티미터로 측정되는 직류 저항(DC Resistance)보다 연결부 인덕턴스(Connection Inductance)와 물리적 형상이 더 중요한 경우가 많다.

MIPI 레인에 필터링(Filtering)을 적용할 때에는 일반적인 용량성 EMI 필터(Capacitive EMI Filter)가 수 Gbps급 신호를 심각하게 왜곡할 수 있으므로 주의해야 한다. 고속 레인에 배치하는 공통 모드 필터(Common-Mode Filter) 또는 ESD 보호 소자(ESD Protection Device)는 충분히 낮은 기생 커패시턴스(Parasitic Capacitance)와 적절한 대역폭을 가져야 한다. 부품은 단순한 명목 EMI 감쇠 특성만으로 선정하지 말고 삽입 손실(Insertion Loss), 반사 손실(Return Loss), 모드 변환, 아이 품질(Eye Quality)을 함께 고려해야 한다.

공통 모드 초크(Common-Mode Choke)는 차동 데이터를 통과시키면서 원하지 않는 공통 모드 전류(Common-Mode Current)를 억제할 수 있지만 모든 문제를 해결하는 범용 대책은 아니다. 기생 커패시턴스, 차동 삽입 손실(Differential Insertion Loss), 공진 특성(Resonance Behavior), 임피던스 특성이 MIPI 데이터 전송률과 채널 설계에 적합해야 한다. 잘못 선정된 부품은 특정 주파수의 방출을 줄이면서도 아이 다이어그램(Eye Diagram)을 닫거나 지터를 증가시켜 통신 오류를 발생시킬 수 있다.

ESD 보호(Electrostatic Discharge Protection)에서도 중요한 절충 관계가 존재한다. 외부에 노출되는 커넥터 근처에 보호 소자를 배치하면 과도 전류(Transient Current)가 이미지 센서나 프로세서에 도달하기 전에 우회시킬 수 있지만, 과도한 커패시턴스나 비대칭적인 소자 배치는 차동 균형을 저하시킬 수 있다. 따라서 신호 무결성과 잡음 내성을 동시에 확보하려면 저커패시턴스 보호 소자(Low-Capacitance Protection Device), 짧은 방전 경로, 대칭 배선, 적절한 과도 전류 기준점으로의 효과적인 연결이 필요하다.

카메라 모듈(Camera Module)과 프로세서 사이의 거리가 길어질수록 차폐(Shielding)의 중요성이 증가한다. 도전성 인클로저(Conductive Enclosure), 차폐 플렉스 구조(Shielded Flex Structure), 차폐 케이블(Shielded Cable)은 전기장 결합을 감소시킬 수 있지만 실제 효과는 차폐 종단(Shield Termination)에 크게 좌우된다. 긴 차폐 피그테일(Shield Pigtail)은 인덕턴스를 증가시켜 고주파에서 효과가 감소한다. 기구 구조가 허용한다면 낮은 인덕턴스를 갖는 원주형 또는 넓은 면적의 차폐 종단이 고주파 성능에 유리하다.

로봇 시스템에서는 카메라가 여러 동적 잡음원(Dynamic Noise Source)과 동시에 동작하므로 특별한 주의가 필요하다. 휠 모터(Wheel Motor), 서보 드라이브(Servo Drive), 매니퓰레이터(Manipulator), LiDAR 전자회로, 이더넷 인터페이스(Ethernet Interface), 배터리 컨버터(Battery Converter), 컴퓨팅 플랫폼(Computing Platform)의 동작 상태가 지속적으로 변한다. 따라서 로봇이 정지했을 때 정상인 카메라도 모터 가속, 회생 제동(Regenerative Braking), 매니퓰레이터의 급격한 대전류 동작 중에는 프레임 손상이 발생할 수 있다.

MIPI CSI-2 간섭(Interference)의 증상은 프레임 손상(Corrupted Frame), 수평 또는 수직 영상 아티팩트(Image Artifact), 간헐적인 동기 손실(Synchronization Loss), 프레임 드롭(Dropped Frame), 수신기의 CRC 또는 ECC 오류, 링크 재훈련(Link Retraining), 완전한 카메라 연결 해제 등으로 나타날 수 있다. 이러한 증상은 소프트웨어나 드라이버 오류와 유사할 수 있으므로 문제를 소프트웨어로 판단하기 전에 카메라 오류와 모터 PWM 동작, 컨버터 부하, 프로세서 작업량, 케이블 위치, 로봇 동작 상태 사이의 상관관계를 확인해야 한다.

오실로스코프(Oscilloscope), 근접장 프로브(Near-Field Probe), 스펙트럼 분석기(Spectrum Analyzer), 수신기 오류 카운터(Receiver Error Counter)는 서로 보완적인 진단 정보를 제공한다. 차동 프로빙(Differential Probing)을 통해 아이 품질 저하와 과도한 지터를 확인할 수 있으며, 근접장 스캐닝(Near-Field Scanning)은 커넥터, 플렉스 케이블, 스위칭 레귤레이터, 프로세서 인터페이스 주변의 결합 경로를 식별하는 데 도움이 된다. 시험은 조용한 실험실 벤치에서 외부 전원만 사용하기보다 실제 로봇의 최악 조건(Worst-Case Condition)을 재현해야 한다.

효과적인 잡음 대책(Countermeasure)은 잡음원에서 시작하여 결합 경로(Coupling Path)를 따라 피해 회로(Victim Circuit) 방향으로 분석하는 방식이 유용하다. 인버터 에지 속도(Inverter Edge Rate)를 낮추고, 스위칭 루프(Switching Loop)를 최소화하며, 모터 케이블 차폐를 개선하거나 컨버터 레이아웃을 수정하는 것이 MIPI 인터페이스 자체를 변경하는 것보다 큰 효과를 제공할 수 있다. 잡음원 억제 이후 배선, 접지, 차폐, 전원 필터링, 커넥터 설계, 적절한 고속 보호 소자를 통해 남아 있는 잡음 민감도를 추가로 감소시킬 수 있다.

검증(Validation)은 신호 무결성 시험(Signal-Integrity Testing)과 EMC 시험을 함께 수행해야 한다. 두 분야 중 하나만 통과했다고 해서 견고한 카메라 시스템이 보장되는 것은 아니다. 아이 마진(Eye Margin), 레인 오류 통계(Lane Error Statistics), 프레임 무결성(Frame Integrity), 방사 방출, 전도성 외란(Conducted Disturbance), 전자기 내성(Immunity), ESD 특성, 과도 상태 동작을 함께 평가해야 한다. 시험 조건에는 최대 카메라 해상도와 프레임률, 최대 프로세서 부하, 모터 가속과 제동, 주요 로봇 서브시스템의 동시 동작이 포함되어야 한다.

따라서 가장 신뢰성 높은 MIPI CSI-2 잡음 대책은 하나의 필터 부품에 의존하는 것이 아니라 시스템 수준 설계(System-Level Design)로 접근하는 것이다. 제어된 차동 배선 형상, 연속적인 귀환 경로, 최소화된 모드 변환, 깨끗한 센서 전원, 체계적인 접지, 적절한 케이블 배선, 효과적인 차폐, 모터 및 컨버터 잡음 억제가 함께 작동해야 한다. 이러한 원칙을 설계 초기부터 반영하면 전자기적으로 열악한 로봇 플랫폼에서도 안정적인 카메라 신뢰성을 확보할 수 있다.

## 09.02. GMSL2 EMC Design

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

GMSL2(Gigabit Multimedia Serial Link 2)는 비교적 긴 케이블 거리를 통해 고해상도 영상, 제어 정보 및 관련 데이터를 전송하기 위해 로봇 및 자동차 카메라 시스템(Camera System)에서 널리 사용된다. 전자 장치 내부의 단거리 MIPI CSI-2 연결과 달리 GMSL2는 동축 케이블(Coaxial Cable) 또는 차폐 연선(Shielded Twisted Pair)을 통해 카메라 인터페이스를 확장한다. 따라서 전자기 적합성(Electromagnetic Compatibility)은 직렬화기(Serializer), 케이블(Cable), 커넥터(Connector), 역직렬화기(Deserializer), 전원망(Power Network), 접지 구조(Grounding Architecture)를 포함하는 시스템 수준의 설계 문제가 된다.

일반적인 GMSL2 카메라 링크(Camera Link)는 이미지 센서(Image Sensor) 가까이에 직렬화기(Serializer)를 배치하고 중앙 프로세서(Central Processor) 또는 비전 ECU(Vision ECU) 근처에 역직렬화기(Deserializer)를 배치한다. 직렬화기는 카메라 데이터를 차량이나 로봇 내부에서 전송하기 적합한 고속 직렬 데이터 스트림(High-Speed Serial Stream)으로 변환한다. 수신 측에서는 역직렬화기가 데이터를 복원하고 일반적으로 프로세서 방향으로 MIPI CSI-2 인터페이스를 제공한다. 이를 통해 장거리 고속 신호 도체 수를 줄이면서 원격 카메라(Remote Camera)를 중앙 집중식 인지 구조(Centralized Perception Architecture)에 통합할 수 있다.

GMSL2는 수 Gbps급 데이터 전송률(Multi-Gigabit-per-Second Data Rate)로 동작하기 때문에 전송되는 정보가 디지털 데이터라 하더라도 인터커넥트(Interconnect)에는 상당한 고주파 스펙트럼 에너지(High-Frequency Spectral Energy)가 존재한다. 케이블 불연속(Cable Discontinuity), 커넥터 전이부(Connector Transition), 불량한 PCB 배선, 부적절한 종단(Termination)은 이러한 에너지 일부를 공통 모드 전류(Common-Mode Current)로 변환할 수 있다. 공통 모드 전류가 케이블이나 인클로저 구조에 도달하면 인터커넥트가 효율적인 안테나처럼 동작하여 주요 방사성 전자기 방출(Radiated Electromagnetic Emission) 원인이 될 수 있다.

따라서 주요 EMC 목표는 단순히 정상적인 통신을 유지하는 것에 그치지 않고 전체 채널에서 전송선 균형(Transmission-Line Balance)을 유지하고 고주파 귀환 전류(High-Frequency Return Current)를 제어하는 것이다. 직렬화기 출력, PCB 트레이스, 커넥터, 케이블, 수신 커넥터, 역직렬화기 입력은 하나의 제어된 전송 경로(Controlled Transmission Path)로 동작해야 한다. 임피던스 불연속(Impedance Discontinuity)은 반사를 발생시켜 신호 무결성(Signal Integrity)을 저하시키는 동시에 모드 변환(Mode Conversion)과 전자기 방사를 증가시킬 수 있으므로 최소화해야 한다.

직렬화기와 역직렬화기 주변의 PCB 배선(PCB Routing)은 이들 소자가 로컬 디지털 회로와 외부 고속 케이블 사이의 전기적 전이부를 형성하기 때문에 특별한 주의가 필요하다. 고속 트레이스(High-Speed Trace)는 짧고 형상적으로 일관되게 구성하며 연속적인 접지면(Continuous Ground Plane)을 기준으로 배선해야 한다. 불필요한 비아(Via), 스텁(Stub), 테스트 패드(Test Pad), 급격한 형상 변화, 기준면 간극(Reference-Plane Gap)을 가로지르는 배선은 각각 임피던스를 변화시키고 고주파 귀환 전류 경로를 교란할 수 있으므로 피해야 한다.

커넥터 선정(Connector Selection)과 커넥터-PCB 전이부(Connector-to-PCB Transition) 설계는 EMC 성능에 큰 영향을 준다. 저주파에서는 적절하게 동작하는 커넥터도 GMSL2 주파수 영역에서는 상당한 기생 인덕턴스(Parasitic Inductance), 기생 커패시턴스(Parasitic Capacitance), 불균형(Imbalance)을 발생시킬 수 있다. 접지와 차폐 연결은 신호 전이부 주변에서 낮은 인덕턴스 경로(Low-Inductance Path)를 제공해야 하며, 기계적인 핀 배열은 PCB에서 케이블 어셈블리(Cable Assembly)까지 의도한 전송 구조를 가능한 한 유지해야 한다.

동축 케이블(Coaxial Cable)은 외부 도체(Outer Conductor)가 신호 경로를 둘러싸고 밀접하게 결합된 귀환 경로를 자연스럽게 형성하기 때문에 우수한 전자기 차폐 특성을 제공한다. 그러나 EMC 성능은 커넥터와 모듈 인터페이스를 통한 차폐 연속성(Shield Continuity)을 유지하는 것에 좌우된다. 불량한 차폐 종단(Shield Termination), 긴 피그테일(Pigtail), 불완전한 커넥터 본딩(Connector Bonding), 의도하지 않은 간극은 고주파 임피던스를 증가시키고 공통 모드 전류가 의도된 케이블 경로에 제한되지 않고 섀시 또는 하네스 구조를 통해 흐르게 할 수 있다.

차폐 연선(Shielded Twisted Pair)을 사용하는 구현에서는 도체 대칭성(Conductor Symmetry)과 차폐 구조(Shield Construction)가 EMC 성능에 큰 영향을 준다. 꼬임(Twisting)은 두 도체에 대한 전자기 결합을 균등하게 만드는 데 도움을 주며 주변 차폐는 외부 전자기장과의 상호작용을 감소시킨다. 커넥터 근처에서 연선이 풀리는 구간은 최소화하고 커넥터와 직렬화기 또는 역직렬화기 사이의 비대칭 배선을 피해야 한다. 케이블 굽힘, 기계적 변형, 불균일한 종단 역시 국부 임피던스를 변화시켜 정상적으로 설계된 링크의 EMC 여유(EMC Margin)를 감소시킬 수 있다.

차폐 종단(Shield Termination)은 단순한 직류 접지 문제가 아니라 고주파 연결(High-Frequency Connection)의 관점에서 설계해야 한다. 멀티미터로 측정했을 때 거의 0에 가까운 저항을 갖는 연결도 수백 MHz 또는 수 GHz 영역에서는 상당한 유도성 임피던스(Inductive Impedance)를 나타낼 수 있다. 넓은 면적의 차폐 본딩(Broad-Area Shield Bonding) 또는 원주형 차폐 본딩(Circumferential Shield Bonding)은 루프 면적과 연결 인덕턴스를 최소화하기 때문에 일반적으로 긴 와이어 연결보다 우수한 고주파 성능을 제공한다.

추가적인 잡음 억제가 필요한 경우 공통 모드 필터링(Common-Mode Filtering)을 적용할 수 있지만 GMSL2 채널에 삽입되는 모든 필터는 신호 대역폭(Signal Bandwidth)에 적합해야 한다. 공통 모드 초크(Common-Mode Choke)는 의도된 신호를 통과시키면서 불필요한 공통 모드 전류를 감쇠할 수 있지만 과도한 기생 커패시턴스, 차동 삽입 손실(Differential Insertion Loss), 공진(Resonance)은 링크 품질을 저하시킬 수 있다. 따라서 필터 선정 시 S-파라미터(S-Parameter), 삽입 손실(Insertion Loss), 반사 손실(Return Loss), 모드 변환, 동작 데이터 전송률을 함께 고려해야 한다.

외부에 노출된 커넥터와 긴 외부 하네스를 사용하는 카메라 링크에는 정전기 방전 보호(ESD Protection)도 필요하다. 보호 소자(Protection Device)는 과도 전류(Transient Current)가 민감한 직렬화기 또는 역직렬화기 회로에 유입되기 전에 우회되도록 배치해야 한다. 동시에 선택된 소자는 수 Gbps급 동작에 적합하도록 충분히 낮은 기생 부하(Parasitic Loading)를 가져야 한다. 성공적인 보호를 위해서는 대칭적인 배선, 짧은 방전 경로, 의도된 과도 전류 기준점으로의 낮은 인덕턴스 연결이 중요하다.

많은 원격 GMSL2 카메라 구조(Remote GMSL2 Camera Architecture)는 동축 케이블 전원 공급(Power-over-Coax) 또는 이와 유사한 데이터 선로 전원 공급(Power-over-Data) 방식을 사용하여 동일한 케이블로 전력을 전달한다. 이는 하네스를 단순화하지만 고속 통신과 직류 전력이 동일한 전송 구조를 공유하기 때문에 추가적인 EMC 상호작용을 발생시킨다. 전원 주입 및 추출 회로(Power Injection and Extraction Network)는 스위칭 잡음이 통신 경로로 유입되는 것을 방지하는 동시에 고주파 데이터 에너지가 더 넓은 전원 분배 시스템으로 전파되지 않도록 해야 한다.

따라서 링크 양단의 전원 필터링(Power Filtering)은 전체 주파수 특성을 고려하여 설계해야 한다. 페라이트 비드(Ferrite Bead), 인덕터(Inductor), 커패시터(Capacitor), 바이어스 네트워크 부품(Bias-Network Component)은 유해한 공진을 발생시키지 않으면서 적절한 절연 특성을 제공해야 한다. 이미지 센서와 직렬화기를 위한 로컬 레귤레이터(Local Regulator)는 효과적으로 디커플링해야 하며, 스위칭 레귤레이터(Switching Regulator)는 고속 링크 회로에서 물리적으로 분리해야 한다. 작은 스위칭 전류 루프와 체계적으로 제어된 접지는 전도성 및 방사성 결합을 모두 감소시킨다.

원격 카메라와 중앙 컴퓨팅 장치(Central Computing Unit)가 서로 다른 금속 구조물에 장착되는 경우 접지 구조(Ground Architecture)는 특히 중요해진다. 접지 전위차(Ground Potential Difference)는 케이블 차폐 또는 신호 귀환 구조를 통해 원하지 않는 전류를 흐르게 할 수 있다. 따라서 기계적 장착점과 우연한 연결이 전류 경로를 결정하도록 두기보다는 카메라 접지(Camera Ground), 전자회로 접지(Electronic Ground), 케이블 차폐(Cable Shield), 섀시 접지(Chassis Ground)가 어떻게 상호작용할 것인지를 설계 단계에서 명확하게 정의해야 한다.

케이블 배선(Cable Routing)은 로봇 플랫폼에서 매우 효과적인 EMC 대책이다. GMSL2 케이블은 모터 상 배선(Motor Phase Wiring), 인버터 출력(Inverter Output), 대전류 배터리 도체(High-Current Battery Conductor), DC-DC 스위칭 노드, 기타 강한 전자기 잡음원으로부터 분리해야 한다. 가능한 경우 긴 평행 배선을 피하고 교차가 불가피하다면 약 90도에 가까운 각도로 교차시키는 것이 바람직하다. 물리적 이격 거리(Separation Distance)를 확보하면 추가 필터 부품에서 발생할 수 있는 신호 무결성 저하 없이 광대역 잡음 내성을 개선할 수 있다.

로봇은 동작 상태에 따라 전자기 잡음이 동적으로 변화하기 때문에 특히 까다로운 환경을 형성한다. 휠 모터(Wheel Motor), 조향 액추에이터(Steering Actuator), 매니퓰레이터(Manipulator), 펌프(Pump), 팬(Fan), LiDAR, 이더넷 네트워크(Ethernet Network), 무선 통신 장치(Wireless Radio), 고성능 컴퓨팅 시스템이 동시에 동작할 수 있다. 따라서 정지 상태 시험에서는 정상적으로 동작하는 GMSL2 카메라 링크도 가속, 회생 제동(Regenerative Braking), 빠른 매니퓰레이터 동작, 최대 컴퓨팅 및 통신 부하 상황에서는 간헐적인 오류를 나타낼 수 있다.

대표적인 링크 문제(Link Problem)로는 간헐적인 영상 손상(Video Corruption), 프레임 손실(Frame Loss), 동기화 오류(Synchronization Error), 직렬화기 또는 역직렬화기의 잠금 손실(Lock Loss), CRC 관련 오류, 링크 재훈련(Link Retraining), 완전한 카메라 연결 중단 등이 있다. 이러한 고장을 즉시 소프트웨어 문제로 분류해서는 안 된다. 전자기 결합이나 신호 무결성 저하 여부를 판단하기 위해 오류 발생 시점을 모터 PWM 동작, 컨버터 작동, 하네스 위치, 기계적 움직임, 프로세서 부하 및 기타 시스템 이벤트와 연관하여 분석해야 한다.

EMC 진단(EMC Diagnosis)은 통신 통계(Communication Statistics)와 전기적 및 전자기적 측정을 함께 사용해야 한다. 오실로스코프(Oscilloscope)와 적절한 고대역폭 프로브(High-Bandwidth Probe)를 사용하여 신호 품질과 지터(Jitter)를 확인할 수 있으며, 스펙트럼 분석기(Spectrum Analyzer)와 근접장 프로브(Near-Field Probe)를 통해 직렬화기, 역직렬화기, 커넥터, 전원 회로, 케이블 전이부 주변의 방출을 식별할 수 있다. 오류 카운터(Error Counter)와 링크 잠금 상태(Link-Lock Status)는 측정된 외란 및 특정 로봇 동작 조건과 연계할 수 있는 중요한 디지털 진단 정보를 제공한다.

효과적인 수정 조치(Corrective Action)는 가능하면 잡음원(Noise Source) 자체에서 잡음을 줄이는 것부터 시작해야 한다. 모터 인버터 스위칭 루프(Motor Inverter Switching Loop), 컨버터 핫 루프(Converter Hot Loop), 부적절하게 종단된 차폐, 과도한 스위칭 에지 속도(Switching Edge Rate)는 GMSL2 채널에 추가 부품을 삽입하기 전에 먼저 개선해야 한다. 이후 배선, 차폐, 접지, 커넥터 최적화, 전원 필터링, 적절하게 선정된 공통 모드 및 과도 보호 부품을 통해 결합 경로를 추가로 개선해야 한다.

최종 검증(Final Validation)은 실제 최악 조건(Worst-Case Condition)에서 EMC와 통신 견고성(Communication Robustness)을 함께 평가해야 한다. 시험에는 최대 카메라 대역폭, 여러 카메라의 동시 동작, 최대 프로세서 부하, 모터 가속 및 제동, 대전류 액추에이터 동작, 무선 통신, 전원 시스템 과도 현상(Power-System Transient)을 포함해야 한다. 방사 방출(Radiated Emission), 전도성 외란(Conducted Disturbance), 전자기 내성(Immunity), ESD, 링크 오류 통계, 영상 무결성(Video Integrity), 복구 동작(Recovery Behavior)을 동일한 시스템 문제의 상호 연관된 요소로 평가해야 한다.

견고한 GMSL2 EMC 설계(Robust GMSL2 EMC Design)는 궁극적으로 하나의 잡음 억제 부품에 의존하는 것이 아니라 전체 신호 및 귀환 전류 경로(Signal and Return-Current Path)를 제어함으로써 달성된다. 제어 임피던스(Controlled Impedance), 연속적인 차폐(Continuous Shielding), 낮은 인덕턴스 종단(Low-Inductance Termination), 깨끗한 전원 공급(Clean Power Delivery), 의도적으로 설계된 접지, 적절한 케이블 배선, 최소화된 공통 모드 변환(Common-Mode Conversion), 주요 로봇 잡음원의 억제가 함께 작동해야 한다. 이러한 시스템 수준 접근(System-Level Approach)을 통해 현대 로봇 플랫폼의 전기적으로 열악한 환경에서도 원격 고대역폭 카메라(Remote High-Bandwidth Camera)의 안정적인 동작을 유지할 수 있다.

## 09.03. FPD-Link III EMC

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

FPD-Link III는 원격 카메라(Remote Camera)와 중앙 처리 장치(Centralized Processing Unit) 사이에서 영상, 제어 정보, 클록 관련 정보 및 양방향 통신(Bidirectional Communication)을 전송하도록 설계된 고속 직렬화/역직렬화 통신 기술(High-Speed SerDes Communication Technology)이다. 로봇 시스템에서는 소형 동축 케이블(Coaxial Cable) 또는 차폐 연선(Shielded Twisted Pair)을 사용하면서 고해상도 카메라를 메인 프로세서에서 멀리 배치할 수 있다. 이는 하네스 복잡성을 줄이지만 수 Gbps급 신호, 긴 케이블, 원격 전원 공급(Remote Power Delivery), 전기적으로 잡음이 많은 동작 환경과 관련된 EMC 문제를 발생시킨다.

일반적인 FPD-Link III 카메라 구조(Camera Architecture)는 이미지 센서(Image Sensor)에 연결된 직렬화기(Serializer), 고속 케이블 및 커넥터 시스템, 프로세서 또는 비전 ECU(Vision ECU) 근처에 위치한 역직렬화기(Deserializer)로 구성된다. 직렬화기는 병렬 또는 MIPI 기반 카메라 정보를 장거리 전송에 적합한 직렬 데이터 스트림(Serial Stream)으로 변환한다. 역직렬화기는 정보를 복원하여 일반적으로 MIPI CSI-2를 통해 프로세서로 전달하며, 양방향 채널(Bidirectional Channel)은 카메라 설정, 진단 및 제어를 지원할 수 있다.

FPD-Link III는 매우 빠른 신호 천이(Signal Transition)로 동작하기 때문에 전자기적 특성을 단순히 명목 데이터 전송률(Nominal Data Rate)만으로 평가할 수 없다. 빠른 에지(Fast Edge)는 훨씬 높은 주파수 영역까지 확장되는 고조파(Harmonic)를 포함하며, 이 영역에서는 PCB 트레이스, 커넥터, 케이블 차폐, 인클로저 구조가 효과적인 결합 경로(Coupling Path) 또는 안테나로 동작할 수 있다. 따라서 저주파에서는 중요하지 않아 보이는 작은 불연속도 실제 카메라 시스템에서는 반사, 공통 모드 변환(Common-Mode Conversion), 방출 증가 또는 내성 저하를 발생시킬 수 있다.

가장 중요한 EMC 원칙은 직렬화기에서 역직렬화기까지 제어된 전송 경로(Controlled Transmission Path)를 유지하는 것이다. 특성 임피던스(Characteristic Impedance)는 PCB 배선, 커넥터 전이부, 케이블 어셈블리 및 수신 회로 전체에서 일관되게 유지되어야 한다. 임피던스 불연속(Impedance Discontinuity)은 신호 여유를 감소시키는 반사를 발생시키고 의도된 전송 에너지를 원하지 않는 공통 모드 전류(Common-Mode Current)로 변환할 수 있다. 따라서 전체 링크를 서로 독립적인 PCB, 커넥터 및 케이블 부품이 아니라 하나의 상호 연결된 고주파 구조(High-Frequency Structure)로 설계해야 한다.

직렬화기와 역직렬화기의 PCB 레이아웃(PCB Layout)은 연속적인 기준면(Continuous Reference Plane)을 기반으로 짧고 직접적인 고속 배선을 사용해야 한다. 고주파 귀환 전류(High-Frequency Return Current)는 신호 가까이에 낮은 임피던스 경로가 필요하므로 트레이스가 접지 분할(Ground Split), 큰 보이드(Void), 연결이 불충분한 기준 영역을 가로지르지 않아야 한다. 불필요한 비아(Via), 테스트 패드(Test Pad), 스텁(Stub), 급격한 폭 변화 및 비대칭 전이부는 최소화해야 한다. 예측 가능한 배선 형상을 유지하면 반사를 줄이고 차동 또는 단일 종단 신호 에너지(Single-Ended Signal Energy)가 공통 모드 방사로 변환되는 것을 억제할 수 있다.

동축 케이블(Coaxial Cable)은 외부 도체(Outer Conductor)가 전자기 차폐와 밀접하게 결합된 귀환 전류 경로(Return-Current Path)를 동시에 제공하기 때문에 FPD-Link III에 특히 유용하다. 그러나 이러한 장점은 차폐 연속성(Shield Continuity)에 크게 의존한다. 차폐는 커넥터, 케이블, 카메라 인클로저 및 수신 모듈 전체에서 전기적으로 유효하게 유지되어야 한다. 긴 피그테일(Pigtail)이나 좁은 차폐 연결은 인덕턴스를 증가시켜 고주파 임피던스를 높이고 원하지 않는 전류가 섀시, PCB 접지 또는 주변 하네스 구조로 확산되도록 만들 수 있다.

차폐 연선(Shielded Twisted Pair)을 사용하는 구현에서는 차동쌍 대칭성(Pair Symmetry)과 차폐 종단(Shield Termination)을 신중하게 제어해야 한다. 꼬임(Twisting)은 두 도체가 거의 동일한 전자기장에 노출되도록 하여 잡음 민감도를 줄이고, 차폐는 주변 회로와의 결합을 제한한다. 커넥터 주변에서 지나치게 많이 풀린 연선, 서로 다른 트레이스 길이, 비대칭 비아, 균형이 맞지 않는 커넥터 형상은 모드 변환을 발생시킬 수 있다. 기계적인 케이블 변형과 과도하게 작은 굽힘 반경도 국부적인 임피던스를 변화시키고 링크 성능을 저하시킬 수 있으므로 관리해야 한다.

커넥터 설계(Connector Design)는 FPD-Link III 채널에서 가장 취약한 EMC 지점 중 하나가 되는 경우가 많다. 커넥터는 안정적인 차폐 및 접지 연속성을 제공하면서 의도된 고주파 형상을 유지해야 한다. 핀, 셸(Shell), 장착 구조 및 PCB 전이부에서 발생하는 기생 커패시턴스(Parasitic Capacitance)와 기생 인덕턴스(Parasitic Inductance)를 최소화해야 한다. 특히 케이블이 금속 카메라 하우징이나 중앙 컴퓨팅 인클로저에 진입하는 부분에서는 차폐 본딩(Shield Bonding)에 짧고 넓으며 낮은 인덕턴스의 연결을 사용해야 한다.

원격 카메라 시스템은 종종 동축 케이블 전원 공급(Power-over-Coax) 또는 관련 방식을 통해 데이터 통신과 전원 공급을 동일한 케이블에 결합한다. 이는 로봇 하네스를 크게 단순화하지만 전원망(Power Network)이 잡음이 많은 차량 또는 로봇 전원 레일과 민감한 고속 통신 회로 사이의 결합 경로가 될 수 있다. 전원 주입 및 추출 네트워크(Power Injection and Extraction Network)는 고주파 통신 신호와 직류 전원을 분리하면서 스위칭 레귤레이터 잡음과 시스템 과도 현상(System Transient)이 FPD-Link III 채널로 유입되지 않도록 해야 한다.

전원 필터링(Power Filtering)은 링크의 카메라 측과 프로세서 측 모두에서 고려해야 한다. 로컬 디커플링 커패시터(Local Decoupling Capacitor), 페라이트 부품(Ferrite Component), 인덕터 및 적절한 필터 네트워크를 통해 전도성 외란(Conducted Disturbance)이 직렬화기, 역직렬화기, 이미지 센서 또는 공유 케이블로 전달되는 것을 방지할 수 있다. 이론적으로 적절한 필터도 과도한 기생 인덕턴스를 가진 긴 트레이스를 통해 연결되면 효과가 떨어지므로 부품 배치가 매우 중요하다. 가능하면 스위칭 레귤레이터(Switching Regulator)를 민감한 고속 회로에서 물리적으로 분리해야 한다.

공통 모드 전류가 주요 방출 또는 내성 문제의 원인으로 확인된 경우 공통 모드 초크(Common-Mode Choke)를 통해 추가적인 억제 효과를 얻을 수 있다. 그러나 초크는 과도한 삽입 손실(Insertion Loss), 기생 커패시턴스 또는 바람직하지 않은 공진(Resonance)을 발생시키지 않으면서 필요한 FPD-Link III 대역폭을 지원해야 한다. 따라서 부품 선정은 단일 주파수에서 규정된 임피던스 값만이 아니라 고주파 S-파라미터(S-Parameter)와 실제 링크 성능을 함께 고려해야 한다. 부적절한 초크는 EMC 방출을 줄이면서 동시에 통신 여유를 감소시킬 수 있다.

정전기 방전 및 과도 보호(ESD and Transient Protection)는 원격 카메라가 외부로 배선된 하네스를 통해 연결되어 조립 및 동작 과정에서 정전기 방전이나 전기적 과도 현상에 노출될 수 있기 때문에 중요하다. 보호 소자(Protection Device)는 외란이 모듈로 들어오는 인터페이스 가까이에 배치해야 한다. 정상적인 신호 무결성을 저하시키지 않도록 고속 채널에 충분히 낮은 기생 커패시턴스를 제공하면서 의도된 기준점으로 짧은 방전 경로(Discharge Path)를 형성해야 한다.

접지(Grounding)는 카메라 전자회로 접지(Camera Electronics Ground), 프로세서 접지(Processor Ground), 케이블 차폐(Cable Shield), 섀시(Chassis)의 관계를 의도적으로 정의해야 한다. 원격 카메라 모듈이 서로 다른 접지 전위를 가진 위치의 도전성 로봇 프레임에 장착되면 케이블 차폐 또는 신호망을 통해 의도하지 않은 전류 경로가 형성될 수 있다. 직류에서 양호해 보이는 연결도 고주파에서는 상당한 임피던스를 가질 수 있으므로 접지와 본딩(Bonding)은 인덕턴스, 형상, 장착 구조 및 전류 귀환 경로를 함께 고려하여 결정해야 한다.

케이블 배선(Cable Routing)은 이동 로봇(Mobile Robot)에서 가장 실용적인 FPD-Link III EMC 대책 중 하나이다. 카메라 케이블은 모터 상 배선(Motor Phase Wiring), 인버터 출력(Inverter Output), 대전류 배터리 케이블(High-Current Battery Cable), 스위칭 컨버터(Switching Converter), 액추에이터 하네스(Actuator Harness)에서 분리해야 한다. 긴 평행 배선은 유도성 및 용량성 결합(Inductive and Capacitive Coupling)을 증가시키지만 이격 거리를 늘리면 두 결합 모두 감소한다. 카메라 케이블과 전원 케이블이 교차해야 하는 경우에는 긴 평행 배선보다 약 90도에 가까운 각도로 교차시키는 것이 일반적으로 결합을 줄이는 데 유리하다.

로봇의 동작 환경에서는 운전 조건에 따라 간섭이 변화하므로 EMC 검증(EMC Verification)이 특히 까다롭다. 주행 모터(Traction Motor), 조향 시스템(Steering System), 서보 드라이브(Servo Drive), 매니퓰레이터(Manipulator), DC-DC 컨버터, LiDAR, 이더넷 장비(Ethernet Equipment), 무선 통신 장치(Wireless Radio), GPU 컴퓨터가 동시에 외란을 발생시킬 수 있다. 로봇이 정지한 상태에서는 정상적으로 동작하는 카메라 링크도 모터 가속, 회생 제동(Regenerative Braking), 매니퓰레이터 동작, 최대 컴퓨팅 부하 또는 여러 센서의 동시 동작 중에는 불안정해질 수 있다.

대표적인 간섭 증상(Interference Symptom)으로는 영상 손상(Corrupted Video), 간헐적인 프레임 손실(Frame Loss), 동기화 오류(Synchronization Error), CRC 관련 오류, 직렬화기 또는 역직렬화기의 잠금 손실(Lock Loss), 반복적인 링크 복구(Link Recovery), 완전한 카메라 연결 해제 등이 있다. 이러한 증상은 소프트웨어, 드라이버 또는 카메라 설정 오류와 유사하게 나타날 수 있다. 따라서 고장을 소프트웨어 문제로 분류하기 전에 통신 오류와 로봇 동작 이벤트, 모터 PWM 조건, 컨버터 부하, 하네스 움직임, 온도 및 프로세서 활동 사이의 상관관계를 분석해야 한다.

측정(Measurement)은 신호 무결성(Signal Integrity) 기법과 EMC 기법을 함께 사용해야 한다. 고대역폭 오실로스코프(High-Bandwidth Oscilloscope)는 파형 품질과 지터(Jitter)를 평가할 수 있으며, 스펙트럼 분석기(Spectrum Analyzer)와 근접장 프로브(Near-Field Probe)는 직렬화기, 역직렬화기, 커넥터, 전원 주입 네트워크 및 케이블 전이부 주변의 방출을 찾는 데 사용할 수 있다. 링크 상태(Link Status), 오류 카운터(Error Counter), CRC 통계 및 프레임 드롭 정보는 측정된 전자기 활동과 특정 로봇 동작 조건을 연계할 수 있는 디지털 증거를 제공한다.

수정 대책(Corrective Action)은 가능하면 지배적인 잡음원(Dominant Noise Source)을 억제하는 것부터 시작해야 한다. 모터 인버터 루프 면적을 줄이고, 컨버터 레이아웃을 개선하며, 스위칭 에지 속도(Switching Edge Rate)를 제어하고, 케이블 차폐 종단을 수정하며, 고주파 접지 불연속을 제거하는 것이 FPD-Link III 신호에 직접 필터를 추가하는 것보다 더 큰 개선 효과를 제공할 수 있다. 잡음원을 억제한 이후 배선, 차폐, 본딩, 필터링, 커넥터 최적화 및 전원망 개선을 통해 결합 경로를 추가적으로 개선할 수 있다.

시스템 검증(System Validation)은 카메라 링크를 독립적으로 시험하기보다 실제적인 최악 조건(Worst-Case Combination)을 재현해야 한다. 최대 해상도 및 프레임률, 여러 카메라의 동시 동작, 최대 GPU 처리 부하, 모터 가속 및 제동, 액추에이터 동작, 무선 통신, 배터리 과도 현상(Battery Transient), DC-DC 컨버터 부하를 시험 조건에 포함해야 한다. 방사 방출(Radiated Emission), 전도성 외란, 전자기 내성(Immunity), ESD, 통신 오류, 영상 무결성(Video Integrity), 링크 복구 및 장시간 안정성(Long-Duration Stability)을 함께 평가해야 한다.

신뢰성 높은 FPD-Link III EMC 성능은 궁극적으로 이미지 센서와 직렬화기에서 케이블을 거쳐 역직렬화기와 프로세서까지 이어지는 전체 전자기 경로(Electromagnetic Path)를 제어하는 것에 달려 있다. 제어 임피던스(Controlled Impedance), 연속적인 차폐(Continuous Shielding), 낮은 인덕턴스 본딩(Low-Inductance Bonding), 깨끗한 전원(Clean Power), 의도적으로 설계된 접지, 적절한 필터링, 신중한 케이블 배선, 주요 로봇 잡음원의 억제가 함께 작동해야 한다. 이러한 시스템 수준 접근(System-Level Approach)은 전기적으로 열악한 로봇 환경에서도 안정적인 고대역폭 비전(High-Bandwidth Vision)을 유지하는 데 필요한 충분한 설계 여유를 제공한다.

## 09.04. Shield Cable and Termination

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

차폐 케이블(Shielded Cable)은 고속 영상 인터페이스가 모터, 인버터(Inverter), DC-DC 컨버터(DC-DC Converter), 대전류 배터리 배선(High-Current Battery Wiring), 무선 송신기(Wireless Transmitter) 및 기타 전자기 잡음원(Electromagnetic Noise Source)이 존재하는 환경에서 동작하기 때문에 로봇 카메라 시스템에서 매우 중요하다. 차폐(Shield)는 원하지 않는 고주파 전류(High-Frequency Current)에 대해 제어된 경로를 제공하고 내부 신호 도체와 외부 전자기장 사이의 결합을 감소시키지만, 그 효과는 케이블 구조와 종단 품질(Termination Quality)에 크게 좌우된다.

케이블 차폐(Cable Shield)를 단순한 추가 접지 도체(Ground Conductor)로 간주해서는 안 된다. 고주파 영역에서 차폐의 주요 목적은 전자기장(Electromagnetic Field)을 제어하고 공통 모드 전류(Common-Mode Current)에 낮은 임피던스 경로(Low-Impedance Path)를 제공하는 것이다. 차폐는 신호 도체를 둘러싸 외부 전기장 결합을 감소시키는 동시에 케이블 내부 전류에서 발생하는 방사를 제한한다. 차폐 자체가 우수한 피복률을 가지고 있더라도 종단이 부적절하면 이러한 기능이 크게 저하될 수 있다.

일반적인 차폐 구조(Shielding Structure)에는 포일 차폐(Foil Shield), 편조 차폐(Braided Shield), 그리고 두 방식을 결합한 구조가 있다. 포일은 높은 피복률을 제공하고 높은 주파수에서 전기장 결합 억제에 효과적이며, 편조는 낮은 저항, 기계적 내구성, 넓은 주파수 범위에서 효과적인 성능을 제공한다. 포일과 편조를 결합한 하이브리드 구조(Hybrid Foil-and-Braid Construction)는 높은 피복률과 견고한 저임피던스 차폐 및 향상된 기계적 신뢰성을 동시에 제공하므로 로봇 카메라 케이블에 유리한 경우가 많다.

차폐 효과(Shield Effectiveness)는 전달 임피던스(Transfer Impedance), 피복률(Coverage), 전도도(Conductivity), 형상(Geometry), 주파수에 따른 특성에 의해 결정된다. 비교적 낮은 주파수에서 우수한 차폐도 높은 주파수에서는 인덕턴스, 개구부(Aperture), 커넥터 불연속(Connector Discontinuity), 종단 형상의 영향을 크게 받을 수 있다. GMSL2와 FPD-Link III 같은 카메라 인터페이스는 수 Gbps급 신호로 동작하므로 차폐 성능은 단순한 명목 데이터 전송률보다 훨씬 넓은 주파수 범위에서 평가해야 한다.

차폐 종단(Shield Termination)은 경우에 따라 케이블 차폐 자체보다 더 중요하다. 고품질 차폐도 긴 와이어 또는 피그테일(Pigtail)을 통해 연결되면 종단부에서 인덕턴스가 발생하여 차폐 효과의 상당 부분을 잃을 수 있다. 주파수가 증가하면 짧은 도체조차 상당한 임피던스를 가질 수 있다. 따라서 고주파 카메라 링크에서는 케이블 차폐, 커넥터 셸(Connector Shell), 모듈 인클로저(Module Enclosure), 지정된 섀시 기준점 사이를 넓고 짧으며 낮은 인덕턴스로 연결하는 것이 유리하다.

360도 차폐 종단(360-Degree Shield Termination)은 케이블 원주 전체를 둘러싸는 형태로 차폐를 커넥터 셸 또는 도전성 인클로저(Conductive Enclosure)에 직접 연결한다. 이러한 구조는 루프 면적(Loop Area)과 종단 인덕턴스(Termination Inductance)를 최소화하면서 인터페이스를 통과하는 전자기적 연속성(Electromagnetic Continuity)을 유지한다. 좁은 피그테일 연결과 비교하면 원주형 종단(Circumferential Termination)은 일반적으로 훨씬 우수한 고주파 EMC 성능을 제공하므로 기계적 패키징이 허용하는 경우 고속 카메라 링크에 우선적으로 적용하는 것이 바람직하다.

피그테일 종단(Pigtail Termination)은 저비용 또는 기계적으로 제한된 시스템에서 사용될 수 있지만 그 한계를 이해해야 한다. 노출된 차폐 연장부와 연결 와이어는 유도성 경로(Inductive Path)를 형성하며 주파수가 증가할수록 차폐 효과가 점차 감소한다. 종단부에 발생하는 전압은 공통 모드 전류를 주변 구조물, PCB 접지 또는 내부 배선으로 유도할 수 있으며, 그 결과 케이블의 주요 구간이 완전히 차폐되어 있더라도 케이블 전체가 전자기 에너지를 방사할 수 있다.

커넥터 설계(Connector Design)는 케이블과 전자 모듈 사이의 차폐 연속성(Shield Continuity)을 유지해야 한다. 도전성 커넥터 셸(Conductive Connector Shell), 적절하게 설계된 차폐 클램프(Shield Clamp), 낮은 임피던스의 인클로저 본딩(Enclosure Bonding)은 케이블 진입점에서 전자기 에너지가 누설되는 것을 방지하는 데 도움이 된다. 차폐가 커넥터에 도달하기 전에 끝나거나 좁은 PCB 트레이스를 통해 연결되면 해당 불연속부가 주요 방출 지점이 될 수 있으며 외부 간섭이 민감한 카메라 전자회로로 유입되는 경로를 제공할 수도 있다.

케이블 차폐, 신호 접지(Signal Ground), 섀시 접지(Chassis Ground)의 관계는 의도적으로 정의해야 한다. 이들 도체는 특정 위치에서 서로 연결될 수 있지만 서로 다른 기능을 수행한다. 신호 접지는 회로의 전기적 기준(Electrical Reference)을 제공하는 반면 차폐는 주로 전자기장과 공통 모드 전류를 제어한다. 섀시는 큰 도전성 기준 구조(Conductive Reference Structure)를 제공하며 연결이 짧고 넓으며 적절한 위치에 구성된 경우 고주파 전류의 귀환 경로로 효과적으로 활용할 수 있다.

차폐를 한쪽 끝에서만 종단할지 또는 양쪽 끝에서 종단할지는 주파수, 시스템 구조(System Architecture), 접지 전위 조건(Ground-Potential Condition)에 크게 좌우된다. 단일 종단(Single-End Termination)은 일부 응용에서 저주파 접지 루프 전류(Ground-Loop Current)를 방지할 수 있지만 한쪽 끝이 전기적으로 개방되므로 일반적으로 고주파 차폐 성능은 약해진다. 고속 디지털 카메라 인터페이스는 일반적으로 양단의 신중한 고주파 본딩(High-Frequency Bonding)이 필요하며, 저주파 절연 문제는 하나의 종단 규칙을 모든 시스템에 적용하기보다 전체 접지 구조를 통해 해결해야 한다.

양단 차폐 종단(Both-End Shield Termination)은 효과적인 고주파 귀환 경로를 제공하고 케이블 방사를 감소시킬 수 있지만 섀시 전위차(Chassis Potential Difference)가 존재하면 저주파 전류가 차폐를 통해 흐를 수 있다. 이는 원격 카메라와 프로세서가 대형 로봇의 서로 다른 구조물에 장착되는 경우 특히 중요하다. 따라서 설계에서는 직류 전위차, 저주파 전류, 고주파 EMC 특성, 기계적 본딩(Mechanical Bonding), 의도된 섀시 구조를 동시에 고려해야 한다.

카메라 케이블은 전체 배선 경로를 따라 가능한 한 연속적인 차폐 피복(Shield Coverage)을 유지해야 한다. 길게 노출된 도체 구간, 차폐 단절, 잘못 조립된 커넥터, 손상된 편조, 종단부에서 과도하게 제거된 포일은 전자기 누설 영역(Electromagnetic Leakage Region)을 형성할 수 있다. 제조 편차가 의도된 EMC 설계를 훼손하지 않도록 케이블 조립 절차에는 제거할 수 있는 재킷(Jacket)과 차폐의 길이, 그리고 차폐를 기계적으로 고정하는 방법을 명확하게 규정해야 한다.

케이블 배선(Cable Routing)은 차폐를 대체하는 것이 아니라 차폐와 함께 작용한다. 우수하게 차폐된 카메라 케이블이라도 모터 상 케이블(Motor Phase Cable), 인버터 출력, 대전류 배터리 도체, 스위칭 인덕터(Switching Inductor), 기타 강한 잡음원으로부터 분리해야 한다. 긴 평행 배선은 전자기 결합(Electromagnetic Coupling)을 증가시키는 반면 물리적 이격 거리를 늘리면 결합을 감소시킬 수 있다. 교차가 불가피한 경우 약 90도에 가까운 배선은 강한 전자기장이 카메라 케이블과 상호작용하는 길이를 최소화하는 데 일반적으로 유리하다.

기계적 설치(Mechanical Installation)는 차폐 성능에 상당한 영향을 줄 수 있다. 과도하게 작은 굽힘 반경, 압착, 반복적인 굽힘, 마모, 과도한 인장력은 편조, 포일, 유전체 형상(Dielectric Geometry), 커넥터 종단을 손상시킬 수 있다. 이동 로봇과 매니퓰레이터는 카메라 케이블을 지속적인 진동과 움직임에 노출시킬 수 있으므로 변형 방지(Strain Relief)와 제어된 굽힘 반경(Controlled Bend Radius)은 신뢰성뿐만 아니라 중요한 EMC 고려사항이다. 따라서 로봇의 예상 기계적 수명 동안 차폐 무결성(Shield Integrity)이 유지되어야 한다.

도전성 하우징(Conductive Housing)을 사용하는 경우 카메라 인클로저(Camera Enclosure)는 차폐 시스템의 일부를 구성할 수 있다. 이상적으로 케이블 차폐는 낮은 인덕턴스의 커넥터 또는 클램프를 통해 도전성 인클로저로 직접 전이되어 민감한 전자회로 주변에 전자기적 연속성을 형성해야 한다. 차폐를 인클로저 내부 깊숙한 위치까지 배선한 후 종단하면 원하지 않는 고주파 전류가 의도된 귀환 경로에 도달하기 전에 모듈 내부로 유입되어 이미지 센서, 직렬화기(Serializer), 전원 또는 프로세서 회로에 결합될 수 있다.

플라스틱 카메라 하우징(Plastic Camera Housing)은 도전성 인클로저와 동일한 전자기 경계(Electromagnetic Boundary)를 직접 제공할 수 없으므로 추가적인 고려가 필요하다. 효과적인 고주파 기준 구조를 형성하기 위해 내부 도전성 코팅(Conductive Coating), 국부적인 금속 브래킷(Metal Bracket), 차폐판(Shield Plate), 전용 본딩 구조(Dedicated Bonding Structure)가 필요할 수 있다. 케이블 차폐 종단은 추가적인 인덕턴스를 발생시키는 긴 PCB 트레이스에 의존하지 말고 가능한 한 짧은 경로로 이러한 구조에 연결해야 한다.

동축 케이블 전원 공급(Power-over-Coax)과 유사한 카메라 구조에서는 전원과 고속 통신이 동일한 케이블 구조를 공유하므로 특별한 주의가 필요하다. 차폐 전류(Shield Current), 전원 귀환 전류(Power-Return Current), 고주파 통신 전류(High-Frequency Communication Current)는 스위칭 잡음이 데이터 채널을 오염시키지 않도록 제어된 경로를 따라야 한다. 따라서 적절한 전원 주입 및 추출 필터링(Power Injection and Extraction Filtering), 커넥터 본딩, 로컬 디커플링(Local Decoupling), 차폐 종단을 하나의 통합된 EMC 구조로 설계해야 한다.

차폐 문제는 영구적인 카메라 고장보다는 간헐적인 고장(Intermittent Failure)으로 나타나는 경우가 많다. 대표적인 증상으로 영상 손상(Image Corruption), 프레임 손실(Frame Loss), 동기화 오류(Synchronization Error), CRC 오류, 직렬화기 또는 역직렬화기(Deserializer)의 잠금 손실(Lock Loss), 일시적인 카메라 연결 해제 등이 발생할 수 있다. 이러한 현상이 모터 가속, 회생 제동(Regenerative Braking), 액추에이터 움직임, 컨버터 스위칭 또는 케이블 움직임과 연관된다면 신호 무결성과 전원 품질뿐만 아니라 차폐 경로와 종단 상태를 함께 조사해야 한다.

진단(Diagnosis)에는 근접장 프로브(Near-Field Probe)를 사용하여 커넥터와 케이블 진입부 주변의 누설을 식별하고, 전류 프로브(Current Probe)를 사용하여 공통 모드 케이블 전류를 검출하며, 스펙트럼 분석기(Spectrum Analyzer)를 사용하여 주요 방출 주파수를 확인하는 방법이 활용될 수 있다. 이후 오실로스코프(Oscilloscope)와 통신 오류 카운터(Communication Error Counter)를 사용하여 전자기 활동과 링크 성능 저하 사이의 상관관계를 확인할 수 있다. 제어된 시험 중 차폐 위치를 변경하거나 임시로 본딩하는 방법도 종단 임피던스 또는 케이블 배선이 고장에 영향을 주는지 확인하는 데 도움이 된다.

검증(Validation)은 완성된 로봇에서 예상되는 기계적 및 전기적 조건을 재현해야 한다. 케이블 설치, 진동, 반복 굽힘, 커넥터 체결 반복(Connector Mating Cycle), 대표적인 환경 노출 이후에도 차폐 연속성과 본딩 상태를 확인해야 한다. EMC 시험에는 케이블만 실험실 벤치에서 독립적으로 평가하는 대신 모터 동작, 컨버터 부하, 최대 카메라 대역폭, 여러 센서의 동시 동작, 무선 통신 및 기타 최악 조건 조합(Worst-Case Combination)을 포함해야 한다.

따라서 효과적인 차폐 케이블 및 종단 설계(Shield Cable and Termination Design)는 케이블, 커넥터, 인클로저, 섀시, 접지망(Grounding Network), 배선 경로를 하나의 전자기 구조(Electromagnetic Structure)로 취급함으로써 달성된다. 높은 차폐 피복률만으로 부적절한 종단을 보완할 수 없으며, 우수한 종단 역시 부적절한 배선이나 손상된 케이블 구조를 완전히 극복할 수 없다. 연속적인 차폐, 낮은 인덕턴스 본딩, 제어된 접지, 견고한 기계적 설치, 시스템 수준 EMC 검증이 함께 적용되어야 전기적으로 열악한 로봇 환경에서도 신뢰성 높은 카메라 동작을 확보할 수 있다.

## 09.05. Camera Power Filter Design

카메라 전원 무결성(Camera Power Integrity)은 이미지 센서(Image Sensor), 직렬화기(Serializer), 역직렬화기(Deserializer), 클록 회로(Clock Circuit), 고속 인터페이스(High-Speed Interface)가 전원 레일(Supply Rail)의 외란에 민감할 수 있기 때문에 EMC 설계의 핵심 요소이다. 로봇 시스템의 카메라 전원은 모터, 액추에이터, 컴퓨터, 컨버터와 전원을 공유하는 배터리 또는 공통 DC 버스(Shared DC Bus)에서 공급되는 경우가 많다. 따라서 전도성 잡음(Conducted Noise)과 과도 외란(Transient Disturbance)이 영상 품질이나 통신 신뢰성을 저하시키지 않도록 전용 전원 필터 전략(Power-Filter Strategy)이 필요하다.

카메라 전원 외란(Camera Power Disturbance)은 모터 PWM 스위칭(Motor PWM Switching), 인버터 정류(Inverter Commutation), DC-DC 컨버터, 회생 제동(Regenerative Braking), 릴레이(Relay), 솔레노이드(Solenoid), 대전류 부하 변화(High-Current Load Change)에서 발생할 수 있다. 이러한 외란은 공통 전원 배선과 접지 경로를 통해 전파된 후 카메라 모듈에 도달할 수 있다. 스위칭 에지는 광대역 주파수 성분(Broadband Frequency Component)을 포함하므로 전원 필터링은 기본 스위칭 주파수만을 대상으로 하지 않고 비교적 낮은 주파수의 버스 외란과 고주파 전도성 잡음을 모두 처리해야 한다.

효과적인 카메라 전원 구조(Camera Power Architecture)는 단계별 필터링(Staged Filtering)과 로컬 레귤레이션(Local Regulation)을 통해 잡음이 많은 시스템 전원과 민감한 카메라 전자회로를 분리한다. 시스템 입력은 먼저 과도 보호(Transient Protection)와 대용량 에너지 저장(Bulk Energy Storage)을 거친 후 EMI 필터와 전용 레귤레이터(Dedicated Regulator)를 통과할 수 있다. 이후 추가적인 로컬 필터링을 통해 이미지 센서, 직렬화기, 아날로그 회로 및 클록 관련 부하에 전원을 공급할 수 있다. 이러한 단계적 접근은 하나의 필터 부품이 전체 외란 주파수 범위를 담당해야 하는 부담을 줄인다.

입력 커패시터(Input Capacitor)는 급격한 부하 변화 시 로컬 에너지를 공급하고 적절한 주파수 범위에서 카메라 전원 입력의 임피던스를 낮춘다. 대용량 벌크 커패시터(Bulk Capacitor)는 낮은 주파수에서 효과적이며, 작은 세라믹 커패시터(Ceramic Capacitor)는 높은 주파수에서 더 낮은 임피던스를 제공한다. 실제 효과는 등가 직렬 저항(Equivalent Series Resistance), 등가 직렬 인덕턴스(Equivalent Series Inductance), 패키지 크기, 배치 및 PCB 형상에 좌우되므로 단순히 정전용량 값만으로 견고한 디커플링 네트워크(Decoupling Network)를 선정해서는 안 된다.

세라믹 커패시터는 전원 입력 지점과 민감한 소자의 전원 핀 가까이에 배치하고 전원 및 접지와 짧게 연결해야 한다. 긴 트레이스는 기생 인덕턴스(Parasitic Inductance)를 증가시켜 큰 정전용량의 커패시터도 고주파에서 효과를 잃게 할 수 있다. 넓은 주파수 범위에서 유용한 임피던스 특성을 확보하기 위해 여러 용량의 커패시터를 사용하는 경우가 많지만 과도한 조합은 반공진 피크(Anti-Resonance Peak)를 발생시킬 수 있다. 따라서 단순히 커패시턴스를 많이 추가하면 EMC가 개선된다고 가정하기보다 전원 분배 임피던스(Power-Distribution Impedance)를 고려해야 한다.

페라이트 비드(Ferrite Bead)는 공통 전원 레일의 고주파 잡음으로부터 민감한 카메라 회로를 분리하기 위해 자주 사용된다. 페라이트 비드는 유효한 주파수 영역에서 임피던스가 증가하고 손실성 특성(Dissipative Characteristic)을 이용하여 저항에서 발생하는 큰 직류 전압 강하 없이 고주파 에너지를 억제할 수 있다. 부품 선정 시에는 단일 명목 임피던스 값만이 아니라 주파수에 따른 임피던스 특성, 정격 전류, 직류 저항(DC Resistance), 포화 특성(Saturation Effect), 온도 및 실제 잡음 스펙트럼을 고려해야 한다.

페라이트 비드와 입력 및 출력 커패시터를 결합하면 효과적인 고주파 필터를 구성할 수 있지만 형성된 네트워크는 전기적으로 안정해야 한다. 손실이 작은 세라믹 커패시터와 리액티브 부품(Reactive Component)은 특정 주파수를 감쇠하는 대신 증폭시키는 공진 피크(Resonant Peak)를 발생시킬 수 있다. 따라서 부품 자체의 손실 또는 의도적으로 추가한 저항을 통한 댐핑(Damping)이 필요할 수 있다. 필터 성능은 실제적인 소스 임피던스(Source Impedance)와 부하 임피던스(Load Impedance) 조건에서 측정을 통해 검증해야 한다.

LC 필터(LC Filter)는 카메라 전원이 상당한 전도성 잡음에 노출되는 경우 더욱 강한 감쇠 효과를 제공한다. 인덕터(Inductor)는 급격한 전류 변화를 억제하고 커패시터는 원하지 않는 교류 성분에 낮은 임피던스 경로를 제공한다. 차단 주파수(Cutoff Frequency)는 허용 가능한 과도 응답(Transient Response)을 유지하면서 주요 외란 주파수 영역보다 충분히 낮게 설정해야 한다. 최대 카메라 부하와 최소 입력 전압 조건에서 인덕터 포화 전류, 직류 저항, 커패시터 바이어스 특성 및 공진을 평가해야 한다.

파이 필터(π Filter)는 커패시터-인덕터-커패시터 구조를 사용하여 추가적인 감쇠 효과를 제공할 수 있지만 실제 효과는 물리적 배치에 크게 좌우된다. 첫 번째 커패시터는 잡음이 많은 측에서 짧은 고주파 귀환 경로(High-Frequency Return Path)를 제공하고, 직렬 소자는 민감한 측을 절연하며, 마지막 커패시터는 카메라 부하를 로컬에서 지원해야 한다. 이러한 부품 주변의 PCB 트레이스가 큰 루프를 형성하면 기생 인덕턴스가 의도된 고주파 필터링 동작을 우회할 수 있다.

공통 모드 외란(Common-Mode Disturbance)은 차동 모드 전원 잡음(Differential-Mode Power Noise)과 다른 접근이 필요하다. 차동 잡음은 전원과 귀환 도체 사이에 나타나는 반면 공통 모드 잡음은 두 도체를 섀시 또는 다른 기준 구조에 대해 함께 구동한다. 따라서 공통 모드 전류가 지배적인 경우 차동 LC 필터링만으로는 충분하지 않을 수 있다. 전체 카메라 전원 인터페이스의 일부로 공통 모드 초크(Common-Mode Choke), 제어된 섀시 결합(Controlled Chassis Coupling), 케이블 차폐(Cable Shielding), 적절한 접지(Grounding)가 필요할 수 있다.

모든 카메라 전류에는 귀환 경로가 필요하므로 접지 경로(Ground Path)는 양의 전원 경로와 함께 설계해야 한다. 모터 또는 컨버터 전류가 카메라와 동일한 높은 임피던스의 접지 도체를 통해 흐른다면 양의 전원 레일을 아무리 잘 필터링해도 효과가 제한된다. 카메라 귀환 전류는 의도된 기준점까지 제어된 낮은 임피던스 경로를 가져야 하며, 대전류 액추에이터 귀환 전류는 전압 외란이 민감한 카메라 전자회로를 변조하지 않도록 분리해야 한다.

로컬 레귤레이션(Local Regulation)은 시스템 전원 버스와 카메라 회로 사이에 또 하나의 절연 단계를 제공한다. 스위칭 레귤레이터(Switching Regulator)는 중간 전압을 효율적으로 생성할 수 있으며, 전력 손실이 허용되는 경우 특히 잡음에 민감한 아날로그, PLL 또는 센서 전원에는 저드롭아웃 레귤레이터(Low-Dropout Regulator)를 사용할 수 있다. 레귤레이터의 전원 공급 제거비(Power-Supply Rejection Ratio), 스위칭 주파수, 과도 응답, 출력 잡음, 효율, 열 특성 및 선택된 커패시터와의 안정성을 함께 고려해야 한다.

카메라 근처에서 사용하는 스위칭 레귤레이터는 스위칭 노드(Switching Node)와 높은 di/dt 전류 루프가 로컬 EMI 잡음원이 될 수 있으므로 PCB 레이아웃에 특별한 주의가 필요하다. 입력 커패시터, 스위칭 소자, 인덕터 및 출력 커패시터는 루프 면적을 최소화하도록 배치해야 한다. 스위칭 노드의 구리 면적은 필요한 수준으로 제한하고 민감한 이미지 센서, 클록, 직렬화기 및 고속 신호 트레이스는 레귤레이터의 잡음이 많은 영역에서 물리적으로 분리해야 한다.

긴 하네스를 통해 전원을 공급받는 원격 카메라(Remote Camera)는 케이블 인덕턴스로 인해 중앙 전원이 급격한 부하 변화에 즉시 대응할 수 없으므로 추가적인 고려가 필요하다. 카메라 근처의 로컬 벌크 커패시턴스(Local Bulk Capacitance)는 과도 전류 요구 시 전압을 유지하는 데 도움을 주며 입력 필터링은 케이블을 통해 전달되는 잡음이 모듈로 유입되는 것을 방지한다. 설계에서는 전압 강하, 커넥터 저항, 케이블 온도, 기동 전류(Startup Current), 하네스 임피던스와 로컬 입력 필터 사이의 상호작용도 고려해야 한다.

GMSL2 또는 FPD-Link III와 함께 사용하는 동축 케이블 전원 공급(Power-over-Coax) 시스템에서는 직류 전원과 고주파 통신 신호를 분리하는 필터가 필요하다. 바이어스 네트워크(Bias Network)는 케이블에 전원을 주입하고 원격 카메라에서 이를 추출하면서 통신 주파수 대역이 최소한의 왜곡으로 통과하도록 해야 한다. 따라서 인덕터, 커패시터 및 관련 부품은 전원 전류 요구사항과 고주파 신호 조건을 동시에 만족해야 하며, 이 경우 EMC 검증과 신호 무결성 검증(Signal-Integrity Verification)을 서로 분리하여 생각할 수 없다.

과도 보호(Transient Protection)는 외란이 민감한 전자회로로 전파되기 전에 우회될 수 있도록 카메라 전원 입력 가까이에 배치해야 한다. TVS 소자(TVS Device) 및 기타 보호 부품은 전기적 과도 현상을 클램핑할 수 있지만 전압 정격, 클램핑 특성(Clamping Behavior), 펄스 처리 능력(Pulse Capability), 누설 전류, 커패시턴스 및 연결 인덕턴스가 시스템에 적합해야 한다. 보호 전류는 민감한 카메라 접지 또는 신호 기준 영역을 통과하지 않고 짧고 의도적으로 설계된 경로를 따라야 한다.

필터 배치(Filter Placement)는 필터 선정만큼 중요하다. 잡음이 많은 전원 영역과 민감한 카메라 영역의 경계 가까이에 부품을 배치하여 PCB 트레이스, 접지 구조 또는 주변 배선을 통해 잡음이 필터를 우회하여 결합되지 않도록 해야 한다. 가능한 경우 필터 입력 측과 출력 측을 물리적으로 분리해야 한다. 그렇지 않으면 용량성 또는 자기적 결합(Capacitive or Magnetic Coupling)이 이론적으로 잘 설계된 필터를 우회하여 실제 EMC 성능을 크게 저하시킬 수 있다.

카메라 전원 문제(Camera Power Problem)는 영상 아티팩트(Image Artifact), 프레임 손상(Frame Corruption), 동기화 손실(Synchronization Loss), CRC 오류, 직렬화기 또는 역직렬화기의 잠금 손실(Lock Loss), 예기치 않은 리셋(Unexpected Reset), 완전한 카메라 연결 해제 등으로 나타날 수 있다. 이러한 증상은 모터 가속, 회생 제동, 액추에이터 움직임 또는 높은 컴퓨팅 부하에서만 발생할 수도 있다. 카메라 오류를 전원 전압, 접지 외란, 컨버터 스위칭 및 로봇 동작 상태와 연관하여 분석하면 전원 무결성 고장을 소프트웨어 또는 통신 문제와 구분하는 데 도움이 된다.

진단(Diagnosis)은 시간 영역 측정(Time-Domain Measurement)과 주파수 영역 측정(Frequency-Domain Measurement)을 함께 사용해야 한다. 오실로스코프(Oscilloscope)는 전원 리플(Supply Ripple), 전압 강하(Voltage Droop), 기동 동작, 과도 현상 및 고주파 외란을 포착할 수 있으며, 스펙트럼 분석기(Spectrum Analyzer) 또는 근접장 프로브(Near-Field Probe)는 주요 스위칭 성분과 국부적인 결합 잡음원을 식별할 수 있다. 중앙 전원에서만 측정하면 하네스와 로컬 회로에서 발생하는 외란을 놓칠 수 있으므로 가능한 경우 실제 카메라 전원 핀 또는 필터 출력에서 측정해야 한다.

검증(Validation)은 최대 카메라 해상도와 프레임률, 여러 센서의 동시 동작, 모터 가속 및 제동, 액추에이터 동작, 무선 통신, 최대 컴퓨팅 부하를 포함하여 로봇의 최악 동작 조건(Worst-Case Operation)을 재현해야 한다. 필터 성능은 배터리 전압, 온도, 카메라 부하 및 부품 공차(Component Tolerance) 범위 전체에서 확인해야 한다. 전도성 내성(Conducted Immunity), 과도 현상, ESD, 기동, 종료 및 장시간 동작을 영상 및 통신 오류 통계와 함께 평가해야 한다.

따라서 신뢰성 높은 카메라 전원 필터(Camera Power Filter)는 단순히 전원에 직렬로 삽입한 LC 네트워크가 아니다. 이는 과도 보호, 벌크 에너지 저장, 고주파 필터링, 로컬 레귤레이션, 제어된 접지, 신중한 PCB 레이아웃, 적절한 하네스 설계를 결합한 통합 전원 무결성 및 EMC 구조(Integrated Power-Integrity and EMC Structure)이다. 이러한 요소를 카메라 통신 인터페이스와 함께 조정하여 설계하면 전기적으로 열악한 로봇 환경에서도 안정적인 영상 획득(Stable Image Acquisition)을 유지할 수 있다.
