# 학습 기반·하이브리드 무장할당(WTA/DWTA) 알고리즘 국제 문헌 지도 (2020–2026)

작성 기준일: 2026-10-05. 조사 범위: 심층강화학습(DRL)·다중에이전트 강화학습(MARL)·GNN/Transformer/Pointer Network 기반 신경 조합최적화(NCO)·메타휴리스틱+학습 하이브리드 접근의 정적/동적 WTA 적용 연구. 고전 계보(Manne 1958; Lloyd & Witsenhausen 1986; Ahuja et al. 2007; Kline, Ahner & Hill 2019; Andersen et al. 2022)는 앵커로만 표기.

접근성 메모: ScienceDirect, IEEE Xplore, Wiley, ACM DL, MDPI, Springer, SSRN, ResearchGate 본문 페이지는 이 환경에서 HTTP 403/리다이렉트로 차단되어 열 수 없었다. 이들 논문은 OpenAlex·Crossref·Semantic Scholar 메타데이터 API(저자·제목·학술지·권호·DOI·초록)를 통해 확인했고, arXiv·AIMS Press·KCI·KICS·Haifa CRIS·BIT Pure·Information and Control·CJA·J. System Simulation·IntechOpen·UF CORE Lab PDF·WSC 논문집 PDF는 직접 열었다. 초록 이상의 세부(규모·베이스라인·수치)를 확인하지 못한 항목은 [확인 필요]로 표기했다.

---

## 핵심질문 1. 2020년 이후 DRL / MARL / GNN·GAT / Pointer Network / Transformer·Attention 기반 NCO로 WTA·DWTA를 푼 논문은 무엇인가 (학술지, 규모, 베이스라인, MILP/GA 대비 격차, 추론 지연)

### Takeaway
2020–2026년 사이 학습 기반 WTA는 (i) 단일 에이전트 DRL(DQN/PPO/DDPG/TD3)로 중앙집중식 할당을 순차 의사결정으로 푸는 계열, (ii) Pointer Network·Transformer 인코더·GNN을 정책망으로 쓰는 NCO 계열, (iii) Dec-MDP/POMDP 위에서 MARL(계층적 선택자, 그래프 어텐션)로 분산 할당을 학습하는 계열로 분화했다. 보고된 핵심 수치는 "NLIP 대비 근사최적·1000배 가속(1.48 ms vs 2,025 ms)", "GA 대비 해 품질 30% 이상 개선·풀이시간 10% 이하", "휴리스틱 대비 목표달성 +27%"처럼 대부분 자체 시뮬레이터 기준이며, MILP 최적해와의 격차를 명시적으로 보고한 논문은 소수(Gaudet et al. 2023; Na et al. 2026의 전이 실험 등)다. 정확한 MILP 비교가 가능한 규모는 메모리 한계로 20×12 수준에 머물렀고, 그 이상에서는 휴리스틱/메타휴리스틱이 베이스라인이다.

### Cited Findings

(A) Pointer Network·Transformer·GNN 기반 NCO 계열

- Hyungho Na, Jaemyung Ahn, Il-Chul Moon, "Weapon–Target Assignment by Reinforcement Learning with Pointer Network", Journal of Aerospace Information Systems 20(1):53–59, 2022/2023(인쇄 2023-01), DOI 10.2514/1.I011150. OpenAlex 기준 피인용 27. Pointer Network를 RL 정책으로 쓴 최초기 WTA 논문. 초록·규모·베이스라인 세부는 본문 미접근 [확인 필요] — [OpenAlex](https://api.openalex.org/works/doi:10.2514/1.I011150); [KAIST KOASAS 레코드](https://koasas.kaist.ac.kr/handle/10203/304166?mode=full)
- Hyungho Na, Jaemyung Ahn, Il-Chul Moon, "Multi-Agent Reinforcement Learning Considering Agent Priority for Weapon–Target Assignment", Journal of Aerospace Information Systems 23:464–479, 2026, DOI 10.2514/1.I011676. 이기종 교전 시간창(heterogeneous engagement time windows) 제약을 가진 WTA를 Dec-MDP로 정식화, "agent selector → target selector"의 계층적 MARL(사격 우선 플랫폼 선택 후 표적 선택). "짧은 실행시간에 고품질 할당", "가장 낮은 위협 생존도(threat survivability)", 특히 타이트한 제약 시나리오에서 베이스라인 대비 우위; 어블레이션, 정성 분석, 학습·시험 환경이 다른 전이(transferability) 실험 포함 — [Semantic Scholar](https://api.semanticscholar.org/graph/v1/paper/DOI:10.2514/1.i011676); [Crossref](https://api.crossref.org/works/10.2514/1.i011676)
- Seung Heon Oh, Geon Woong Byeon, Young-in Cho, Seungmin Kwon, Jong Hun Woo (서울대), "Artificial Intelligence in Combat Decision-Making: Weapon Target Assignment via Reinforcement Learning and Graph Neural Networks", IEEE Transactions on Cybernetics 56(2):631–643, 2025/2026, DOI 10.1109/TCYB.2025.3610606. DRL이 DWTA의 SOTA라고 전제하면서 기존 연구의 한계를 ① 전장 위상관계 표현 부족, ② 문제 규모 확장성, ③ 성능지표의 적합성으로 지목. 그래프 기반 행동 표현·관측 특징·보상 설계를 포함한 새로운 POMDP를 제안, 해상·지상 복수 도메인에서 휴리스틱·메타휴리스틱과 비교 — [OpenAlex](https://api.openalex.org/works/doi:10.1109/TCYB.2025.3610606)
  - 같은 저자군의 TechRxiv 선행판(v1–v3, 2024–2025, DOI 10.36227/techrxiv.171084935.57702557)은 "oversimplified model, computational burden, lack of adaptability to disruptive events, recalculation when the problem size changes"를 기존 연구의 한계로 명시하고 OODA 루프를 반영한 실용성을 강조 — [Crossref](https://api.crossref.org/works/10.36227/techrxiv.171084935.57702557/v3)
  - Seung Heon Oh, "Dynamic Weapon Target Assignment via Simulation, Reinforcement Learning and Graph Neural Network", Proc. 2023 Winter Simulation Conference(확장초록). DWTA를 POMDP로 구성, 발사대(함정)가 에이전트, 객체지향 전장 시뮬레이터(launcher·missile 클래스)에서 경험 수집, MPC 및 휴리스틱과 비교 — [WSC 2023 PDF](https://www.informs-sim.org/wsc23papers/doc122.pdf)
- ZOU Yao, LIU Tianjiao, LYU Xu, ZHANG Yanling, GUO Wenda, "Multi-stage Dynamic Weapon-target Assignment Based on Improved Reinforcement Learning", Information and Control(信息与控制) 55(2):292–305, 2026, DOI 10.13976/j.cnki.xk.2025.3302. 다중 공격파·무장 가용시각·냉각(cooldown) 간격·표적 교전 시간창을 포함하는 다목적 DWTA; Actor-Critic에 Pointer Network(어텐션 + 동적 마스킹)를 결합해 가변 규모의 (무장,표적) 쌍 선택; 이중채널 인코딩-디코딩; 베이스라인 비교·일반화 평가·어텐션/정규화 어블레이션 수행 — [Information and Control](https://xk.sia.cn/en/article/cstr/32166.14.xk.2025.3302)
- Janghee Park, Jaeoh Kim, "A Fast and Scalable Transformer-Pointer Reinforcement Learning Framework for Weapon-Target Assignment", SSRN 5704099 (2025-11-04 게시), DOI 10.2139/ssrn.5704099. Joint-PointerPPO: Dual Transformer 인코더 + Pointer Network형 디코더, PPO 학습; 무장–표적 간 구조적 상호작용·요격확률을 어텐션으로 표현; 상용 솔버 대비 경쟁력 있는 해 품질을 유지하면서 추론이 현저히 빠르다고 보고, 특히 무장 수 < 표적 수인 자원제약 시나리오에서 우위 주장. SSRN 본문 미접근으로 수치·규모 [확인 필요] — [SSRN](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5704099); [Crossref](https://api.crossref.org/works/10.2139/ssrn.5704099)
- Haoyan Yao, Changan Shang, Wenzhe Zhang, Panrong Wang, Shengjie Xu, "Decentralized Weapon-Target Assignment in Aerospace Defense Systems: An Attention-Enhanced Multi-Agent Reinforcement Learning Approach", Research Square 프리프린트 2026, DOI 10.21203/rs.3.rs-10847429/v1. STG-MADAC: 레이더·발사대·표적 간 시공간 그래프 어텐션, 교전효과·자원소모·잔존위협을 균형 잡는 다목적 어드밴티지 분해, 이기종 액터 순차 업데이트. 분산 WTA 대상. 본문 미접근 [확인 필요] — [Crossref](https://api.crossref.org/works/10.21203/rs.3.rs-10847429/v1)
- Qing Wang, Yujue Wang, Bin Xin, Haoran Wang, Jia Zhang (BIT), "Optimized stochastic resource allocation using graph neural networks", Science China Information Sciences 69(5), 2026, DOI 10.1007/s11432-025-4821-6. 검색 결과에서 DWTA·"dynamic graph transformer(DGT): 엣지 정보로 어텐션 가중치를 편향"과 함께 노출됨. 본문·초록 미접근 [확인 필요] — [OpenAlex](https://api.openalex.org/works/doi:10.1007/s11432-025-4821-6)

(B) 단일 에이전트 DRL(값 기반·정책경사) 계열

- Brian Gaudet, Kris Drozd, Roberto Furfaro, "Deep Reinforcement Learning for Weapons to Targets Assignment in a Hypersonic strike", arXiv:2310.18509 (cs.AI, 2023-10-27). PPO(클리핑 0.1) + 두 단계 CNN 정책/가치망, 교전상태를 m×n×k 행렬로 표현해 가변 HSW·표적 수 지원. NLIP 솔버가 HSW 20·표적 12 초과에서 메모리 부족이라 최대 20×12로 비교; 시험 30,000 에피소드(HSW 10–20, 표적 4–12 균일 샘플); 분포가 치우쳐 중앙값 사용. 계산시간(ms) 평균/표준편차/최대: NLIP (2,025 / 988 / 71,627), 다른 시험에서 최대 265,000 ms; RL (1.48 / 0.37 / 28). "near-optimal, 1000× speedup", 신규 시나리오 일반화 양호, 단순 휴리스틱은 열위. 추가로 (40,24), (60,36) 규모로 RL만 확장 실험. 극초음속 종말단계가 8–16 s라 실시간성이 핵심 동기. 저자 명시 한계: 단순화된 공력·센서·위협 모델(향후 고정밀 모델 적용) — [arXiv abs](https://arxiv.org/abs/2310.18509); [arXiv PDF](https://arxiv.org/pdf/2310.18509)
- Shuai Li, Xiaoyuan He, Xiao Xu, Tan Zhao, Chenye Song, Jiabao Li, "Weapon-Target Assignment Strategy in Joint Combat Decision-Making Based on Multi-Head Deep Reinforcement Learning", IEEE Access 11:113740–113751, 2023, DOI 10.1109/ACCESS.2023.3324193. 다중 헤드 DRL. 규모·베이스라인·수치 [확인 필요] — [Crossref](https://api.crossref.org/works/10.1109/access.2023.3324193)
- Chang Liu, Jiang Li, Ye Wang, Yang Yu, Lihong Guo, Yuan Gao, "A Time-Driven Dynamic Weapon Target Assignment Method", IEEE Access 11:129623–129639, 2023, DOI 10.1109/ACCESS.2023.3332513. 데이터 수집 시간간격으로 의사결정 단계를 나누는 시간구동(time-sampling) DWTA 모델(검색 요약). 학습 기반 여부·수치 [확인 필요] — [Crossref](https://api.crossref.org/works/10.1109/access.2023.3332513)
- Tengda Li, Gang Wang, Qiang Fu, Xiangke Guo, Minrui Zhao, Xiangyu Liu, "An Intelligent Algorithm for Solving Weapon-Target Assignment Problem: DDPG-DNPE Algorithm", Computers, Materials & Continua 76(3):3499–3522, 2023, DOI 10.32604/cmc.2023.041253. DDPG 기반. 세부 [확인 필요] — [Crossref](https://api.crossref.org/works/10.32604/cmc.2023.041253)
- Qiang Fu, Chengli Fan, Yong Heng, "Air defense intelligent weapon target assignment method based on deep reinforcement learning", ACM 학술대회 논문집 2023, pp.157–161, DOI 10.1145/3580219.3580247. 고차원 "상태-행동" 공간용 신경망, 노드별 상태·행동공간 설계, 디지털 전장 시뮬레이터에서 클리핑 PPO 비동기 학습 — [OpenAlex](https://api.openalex.org/works/doi:10.1145/3580219.3580247)
- Minrui Zhao, Gang Wang, Qiang Fu 외, "Intelligent Decision-Making System of Air Defense Resource Allocation via Hierarchical Reinforcement Learning", International Journal of Intelligent Systems 2024, Article 7777050, DOI 10.1155/2024/7777050. H-A3C(계층적 A3C) + Bi-GRU 상황특징 추출 + 다중헤드 어텐션 + 이벤트 기반 보상; 기존 알고리즘의 "차원의 저주·열악한 실시간성"을 지적 — [OpenAlex](https://api.openalex.org/works/doi:10.1155/2024/7777050)
- Chong Li, Bin Xin, Yingmei He, Danjing Wang, Yang Li (BIT), "Dynamic Weapon Target Assignment Based on Deep Q Network", 2023 42nd Chinese Control Conference, pp.1773–1778, DOI 10.23919/CCC58697.2023.10240428. Tkinter 시뮬레이터; DQN이 Q-learning보다 "50% 이상 빠르고 정확" — [BIT Pure](https://pure.bit.edu.cn/en/publications/dynamic-weapon-target-assignment-based-on-deep-q-network/)
- Feisheng Yang, Ziming Zhao, Chengliang Fang, Zhenyu Gong, "State-split deep reinforcement learning approach to weapon target assignment problem", 2025 IEEE 14th Data Driven Control and Learning Systems Conference (DDCLS), pp.375–380, DOI 10.1109/DDCLS66240.2025.11065768. 세부 [확인 필요] — [Crossref](https://api.crossref.org/works/10.1109/ddcls66240.2025.11065768)
- Yuheng Liu, Li Yang, Qilong Huang (남경이공대), "Optimizing air and missile defense strategies with explainable hierarchical reinforcement learning", Acta Aeronautica et Astronautica Sinica(航空学报) 47(8):332786, 2026, DOI 10.7527/S1000-6893.2025.32786. EHD-DQN: 상위(순위화)–하위(요격) 2계층 Dueling DQN, 시간감쇠 다중 경험버퍼, Grad-CAM+LIME 설명모듈. 화력단위 5개(장거리 1, 중거리 2, 단거리 2; 탄 16–30발), 3종 위협 플랫폼. 베이스라인: DQN, DDPG, PPO, RH-MILP(수평선 MILP), NSGA-II, ALNS. 요격 수·탄 효율·고가치 표적 교전시점에서 전부 우위 주장 — [CJA/航空学报](https://hkxb.buaa.edu.cn/EN/10.7527/S1000-6893.2025.32786)
- Shuaidi Fei, Changlong Cai, Fei Liu, Minghui Chen, Xiaoming Liu, "Research on the Target Allocation Method for Air Defense and Anti-missile Defense of Naval Ships", Journal of System Simulation 37(2):508–516, 2025, DOI 10.16182/j.issn1004731x.joss.23-1219. 다중파·다단계 함정 방공; 다입력 상태공간 + GRU 특징추출망 + 정책망 다중헤드 어텐션의 개선 DRL; "수렴속도·요격이득 개선" (수치 미기재) — [J. System Simulation](https://dc-china-simulation.researchcommons.org/journal/vol37/iss2/17/)
- Jaehwi Lee, Chanin Eom, Kyeongsoo Kim, Hyunsu Kang, Minhae Kwon, "Deep Reinforcement Learning Based Weapon-Target Assignment to Support Military Decision-Making", 한국통신학회논문지(J-KICS) 50(6):884–895, 2025, DOI 10.7840/kics.2025.50.6.884. WTA를 MDP로 모델링, DDPG·TD3; 휴리스틱 대비 지휘관 목표달성 +27.17%, 탄 효율 +38.61%, 탄 비용 −11.98% — [KICS](https://engjournal.kics.or.kr/digital-library/102718)
- 이가원(Kawon Lee), 서강대 인공지능학과 석사학위논문 "강화학습 기반의 동적 무기 할당 문제 (Dynamic Weapon-Target Assignment Problem Based on Reinforcement Learning)", 2024, 지도 박운상. Q-learning과 REINFORCE를 적용, Greedy·MILP를 베이스라인으로 삼아 무장별 전처리·개별 신경망 REINFORCE가 Greedy를 상회 — [서강대 dCollection](https://dcollection.sogang.ac.kr/dcollection/srch/srchDetail/000000076913)

(C) MARL·분산 학습 계열

- Gleb Merkulov, Eran Iceland, Shay Michaeli, Yosef Riechkind, Oren Gal, Ariel Barel, Tal Shima (Technion/Haifa), "Reinforcement Learning Based Decentralized Weapon-Target Assignment and Guidance", AIAA SciTech Forum 2024, DOI 10.2514/6.2024-0125. 다수 미사일 포화공격 대응; 각 추격자가 "자신 대 전체 표적" 관점에서 분산 결정, 타 요격체의 할당·성공확률을 입력으로 공유; 중간경로 성형용 정적 가상표적; 상태 = 도달가능성(reachability) 커버리지 + 타 요격체 성공확률; 보상 = 팀 성과 집계; 그리디 대비 성능 우위, "실시간·확장 가능·동적 재할당" 주장. 요격체×표적 규모·수치는 PDF 접근 실패로 [확인 필요] — [OpenAlex](https://api.openalex.org/works/doi:10.2514/6.2024-0125); [Haifa CRIS](https://cris.haifa.ac.il/en/publications/reinforcement-learning-based-decentralized-weapon-target-assignme/)
- Gleb Merkulov, Eran Iceland, Shay Michaeli, Oren Gal, Ariel Barel, Tal Shima, "Reinforcement-Learning-Based Cooperative Dynamic Weapon-Target Assignment in a Multiagent Engagement", AIAA SciTech Forum 2025, DOI 10.2514/6.2025-1546. 2파 Shoot-Shoot-Look 교전을 확률적 MDP로 정식화, 순차 분산 의사결정; RL이 "개별 기여 증분 최대화 그리디"를 근소하게(marginally) 상회하며 그리디가 학습해를 잘 근사한다고 솔직히 보고 — [Haifa CRIS](https://cris.haifa.ac.il/en/publications/reinforcement-learning-based-cooperative-dynamic-weapon-target-as/)
- Hu Tao, Xiaoxue Zhang, Xueshan Luo, Tao Chen, "Dynamic Target Assignment by Unmanned Surface Vehicles Based on Reinforcement Learning", Mathematics 12(16):2557, 2024, DOI 10.3390/math12162557. 이동표적 다중 USV 표적할당; 상태공간 정의·우선순위 경험재생·self-attention을 결합한 MARL; 타격위치·시각 모델링; 대규모 시나리오에서 GA 대비 해 품질 ≥30% 개선, 평균 풀이시간은 GA의 10% 미만. (연구자 본인 주제와 가장 가까운 국제 논문) — [OpenAlex](https://api.openalex.org/works/doi:10.3390/math12162557)
- Haoran Wang, Qing Wang, Bin Xin, Yujue Wang, "Optimization of Multi-Platform Dynamic Weapon-Target Assignment Based on Multi-Agent Reinforcement Learning", 2025 44th Chinese Control Conference, pp.2322–2327, DOI 10.23919/CCC64809.2025.11179489. 세부 [확인 필요] — [Crossref](https://api.crossref.org/works/10.23919/ccc64809.2025.11179489)
- Jia-yi Liu, Gang Wang, Qiang Fu, Shao-hua Yue, Si-yuan Wang, "Task assignment in ground-to-air confrontation based on multiagent deep reinforcement learning", Defence Technology 19:210–219, 2023, DOI 10.1016/j.dt.2022.04.001. 세부 [확인 필요] — [Crossref](https://api.crossref.org/works/10.1016/j.dt.2022.04.001)
- Jiayi Liu, Gang Wang, Xiangke Guo, Siyuan Wang, Qiang Fu, "Deep Reinforcement Learning Task Assignment Based on Domain Knowledge", IEEE Access 10:114402–114413, 2022, DOI 10.1109/ACCESS.2022.3217654 — [Crossref](https://api.crossref.org/works/10.1109/access.2022.3217654)
- 신민규(Minkyu Shin), 박순서, Daniel Lee, 최한림(KAIST), "평균 필드 게임 기반의 강화학습을 통한 무기-표적 할당 (Mean Field Game based Reinforcement Learning for Weapon-Target Assignment)", 한국군사과학기술학회지 23(4):337–345, 2020. 평균장 게임 기반 MARL로 실시간 근사최적 할당; 무장 궤적 교차(간섭) 제약을 보상 수정으로 반영 — [KCI](https://www.kci.go.kr/kciportal/ci/sereArticleSearch/ciSereArtiView.kci?sereArticleSearchBean.artiId=ART002613144)
- Alessandro Palmas, "Reinforcement Learning for Decision-Level Interception Prioritization in Drone Swarm Defense", arXiv:2508.00641 (2025-08, 2025-09 개정). 자폭드론 군집 방어에서 복수 효과기(effector)의 요격 우선순위를 이산 행동공간으로 학습; 고정밀 시뮬레이터; 수백 개 공격 시나리오; 수작업 규칙 기반 정책 대비 평균 피해 감소·방어효율 향상; 코드·시뮬레이션 자산 공개. 검색 요약에 따르면 PPO와 action masking 변형(MaskedPPO) 비교 — [arXiv](https://arxiv.org/abs/2508.00641)
- ADDR("Attention-enhanced multi-agent Distributional RL with Dynamic Reward", 2024): 다함정 DWTA용, 수익분포 추정(분포형 RL), 함정·표적 상황을 통합하는 다중헤드 어텐션, 미사일 비행시간에 따른 지연보상 보정 메커니즘. 검색 결과 요약으로만 확인되어 저자·학술지·DOI [확인 필요].

(D) LLM·함수근사·기타 신경 접근

- Johannes Autenrieb, Ole Ostermann, "Generalized Intelligence for Tactical Decision-Making: Large Language Model-Driven Dynamic Weapon Target Assignment", arXiv:2511.10207 (eess.SY, 2025-11-13; IEEE TAES 투고). WTA를 요격체·표적·방어자산 간 공간·시간 관계를 LLM이 평가하는 추론 문제로 재정의, 위협 방향·자산 우선순위·접근속도 등 임무 맥락 반영; MIP·경매 기반의 동적·불확실 환경 한계를 지적; 시뮬레이션에서 "일관성·적응성·임무수준 우선순위화 개선" — 초록 수준에서 정량지표·지연시간 미제시 — [arXiv abs](https://arxiv.org/abs/2511.10207)
- Neelay Junnarkar, Emmanuel Sin, Peter Seiler, Douglas Philbrick, Murat Arcak, "Fast Assignment in Asset-Guarding Engagements using Function Approximation", arXiv:2404.08086 (2022 ACC 발표, 2024 arXiv). n추격자-n표적 자산방어; 최소요격시간을 오프라인 학습 신경망으로 근사해 비용행렬을 실시간 구성 → 할당. 대부분 사례에서 최적 최악요격시간 할당 달성 — [arXiv](https://arxiv.org/abs/2404.08086)
- Marc Schneider, Walter Fichter, "Many-vs-Many Missile Guidance via Virtual Targets", arXiv:2511.02526 (2025). Normalizing Flows 궤적예측으로 가상표적 분포 생성, 표적 1–6/요격체 1–8; 동수에서 0–4.1%, 요격체 우세 시 5.8–14.4% 개선 보고 후 **철회** — "제안 방법이 해당 시나리오를 넘어 일반화되지 않음"을 저자가 명시 — [arXiv](https://arxiv.org/abs/2511.02526)
- Sun Hoon Kim, Seunghoon Lee, "Iterative Self-Learning Framework for Dynamic Assignment of Multiple Targets to Aircraft with Variable Kill Probability", SSRN 5030358, 2024, DOI 10.2139/ssrn.5030358. 세부 [확인 필요] — [Crossref](https://api.crossref.org/works/10.2139/ssrn.5030358)
- 인접 분야(WTA 직접 아님): Xindi Tong, Jia Song, Wenling Li, "Rapid Decision-Making Strategy for UAV Swarms in Complex Adversarial Environments Using Proximal Policy Optimization and Transformer", IEEE TAES 61:13183–13201, 2025, DOI 10.1109/TAES.2025.3577176; Bingsan Yang 외, "A Vehicle-Target Assignment Framework: Collaborative Missions of Multiple High-Speed Flight Vehicles With Multiple Targets", IEEE TAES 61:16403–16418, 2025, DOI 10.1109/TAES.2025.3595106 (방법론 [확인 필요]) — [Crossref 1](https://api.crossref.org/works/10.1109/taes.2025.3577176); [Crossref 2](https://api.crossref.org/works/10.1109/taes.2025.3595106); Junlin Liu 외, "DRG-MAPPO: Hierarchical Dynamic Role-Graph MARL for Cooperative Air Combat", arXiv:2609.11155 (2026) — 그래프 어텐션 + 역할 배정 + 표적우선순위 보조과제, 승률 87% — [arXiv](https://arxiv.org/abs/2609.11155)

### Inferences
- 국제 SCI(E)급에서 WTA 학습 논문이 집중되는 학술지는 IEEE TAES(2025년 Transformer+PPO 계열 2편), IEEE TCYB(GNN+POMDP), AIAA JAIS(Pointer Network 2022→Dec-MDP MARL 2026), IEEE Access, Defence Technology, 中国 학술지(航空学报, 信息与控制, 系统仿真学报)이며, 한국 연구그룹(KAIST Na/Ahn/Moon, 서울대 Woo, KAIST Choi, 숭실대 Kwon)이 국제 지분이 크다. 연구자의 KNST 발표는 이 흐름과 직접 경쟁 관계에 있다.
- "GNN/Transformer로 위상관계 표현 + POMDP/Dec-MDP + 어텐션/포인터 마스킹"은 2024–2026년에 이미 포화 상태(Oh TCYB; Na JAIS; Zou; Yao; Park&Kim)이므로, 후속 연구에서 GAT-MAPPO 자체를 기여로 내세우면 차별성이 인정되기 어렵다.
- MILP 대비 격차를 보고한 사례는 20×12(Gaudet, NLIP 메모리 한계) 등 소규모에 한정된다. Bertsimas & Paskov(2025)의 branch-price-and-cut이 10,000×10,000을 "초 단위"로 정확히 푼다는 점을 고려하면, 후속 연구는 80×80 규모에서도 정확해(또는 강한 하한)를 베이스라인으로 제시해야 심사자 설득력이 생긴다(아래 핵심질문 2 참조).
- 보고된 추론 지연은 ms급(Gaudet 1.48 ms)이 이미 존재하므로, "11.9 ms on Jetson" 자체는 새로운 기록이 아니다. 차별화는 지연이 아니라 통신 거부·불확실성·적응형 적군 등 문제 정의 축에서 와야 한다.

### Gaps
- Na et al. (2022, JAIS Pointer Network)과 Park & Kim (2025, SSRN)의 정량 결과(최적해 대비 격차, 규모, 추론시간)는 본문 미접근으로 확인 불가 [확인 필요].
- IEEE Access(Li 2023; Liu 2023), CMC(Li 2023), Defence Technology(Liu 2023), CCC 2025(Wang), DDCLS 2025(Yang), Research Square(Yao 2026), SCIS(Wang 2026)의 규모·베이스라인·수치는 메타데이터만 확인 [확인 필요].
- ADDR(2024) 논문의 서지 정보를 특정하지 못했다 [확인 필요].
- Nature Scientific Reports 2026 "Graph attention network-enhanced MARL for dynamic interception task allocation in counter-drone defense"(s41598-026-55576-9)는 리다이렉트로 열지 못해 제목만 확인 [확인 필요].

---

## 핵심질문 2. 휴리스틱/메타휴리스틱과 학습을 결합한 연구(RL-guided VNS, RL-강화 GA/PSO/ABC, 학습된 warm start, 학습된 이웃 선택, learning-to-branch)는 무엇을 보였는가

### Takeaway
WTA 분야의 하이브리드는 거의 전부 "RL이 메타휴리스틱의 연산자/이웃 선택을 적응적으로 고르는" 형태(DQN 변이연산자+NSGA-II, Q-learning 기반 ABC 연산자 선택, DQN+MO-ABC)이며, 학습된 warm start→지역탐색 또는 learning-to-branch를 WTA에 적용한 국제 논문은 발견되지 않았다. 반대로 정확해 쪽에서는 Bertsimas & Paskov(2025)가 10,000×10,000 WTA를 초 단위로 정확히 풀어 "메타휴리스틱이 필요한가"라는 질문을 던지고 있어, 하이브리드 연구는 정확해가 다루지 못하는 동적·확률적·통신제약 변형에 초점을 맞춰야 한다.

### Cited Findings
- Shiqi Zou, Xiaoping Shi, Shenmin Song, "MOEA with adaptive operator based on reinforcement learning for weapon target assignment", Electronic Research Archive 32(3):1498–1532, 2024, DOI 10.3934/era.2024069. NSGA-DRL: DQN 기반 적응형 변이연산자 + 도메인지식 그리디 교차연산자를 NSGA-II에 결합; 어블레이션에서 두 연산자가 성능을 "significantly boost"하고 DQN 변이가 후보해 식별에 효과적; MO-WTA 벤치마크에서 기존 MOEA 대비 우위 — [AIMS Press](https://aimspress.com/article/doi/10.3934/era.2024069?viewType=HTML)
- Kadir Yıldız, Emrullah Sonuç, "Q-Learning Driven Artificial Bee Colony Algorithm for Solving the Weapon-Target Assignment Problem", Statistics, Optimization & Information Computing 16:684–697, 2026, DOI 10.19139/soic-2310-5070-3934. Q-learning 기반 적응형 연산자 선택을 ABC에 결합, 5개 순열 기반 이웃연산자; 5–200 규모 벤치마크 12개, 30회 독립 실행; 9/12 인스턴스에서 SOTA 대비 더 낮은 비용·표준편차(대규모에서 특히) — [Crossref](https://api.crossref.org/works/10.19139/soic-2310-5070-3934)
- Tong Wang, Liyue Fu, Zhengxian Wei, Yuhu Zhou, Shan Gao, "Unmanned ground weapon target assignment based on deep Q-learning network with an improved multi-objective artificial bee colony algorithm", Engineering Applications of Artificial Intelligence 117:105612, 2022/2023, DOI 10.1016/j.engappai.2022.105612 (OpenAlex 피인용 48). 세부 [확인 필요] — [OpenAlex](https://api.openalex.org/works/doi:10.1016/j.engappai.2022.105612)
- "Target assignment for multiple stages of weapons systems using a deep Q-learning network and a modified artificial bee colony method", Computers and Electrical Engineering 2024 (ScienceDirect PII S0045790624003069). 검색 요약: Q-learning이 편차 기반 상태(생성/축소)를 정의해 SMABCM(State-based Modified ABC)의 적응형 할당 결정을 생성. 저자·DOI·수치 [확인 필요] — [ScienceDirect(차단됨)](https://www.sciencedirect.com/science/article/abs/pii/S0045790624003069)
- Yuheng Liu 외 (2026, 航空学报) EHD-DQN은 ALNS·NSGA-II·RH-MILP를 베이스라인으로 두어 "학습 vs 메타휴리스틱 vs 수평선 MILP" 3자 비교를 제공 — [CJA](https://hkxb.buaa.edu.cn/EN/10.7527/S1000-6893.2025.32786)
- Junnarkar et al. (2024) — 학습된 비용 근사기(신경망)로 할당의 비용행렬을 구성하는 "학습된 전처리" 형태; 대부분 사례에서 최적 최악요격시간 할당 유지 — [arXiv](https://arxiv.org/abs/2404.08086)
- 정확해 앵커(비교 기준): Dimitris Bertsimas, Alex Paskov, "Solving Large-Scale Weapon Target Assignment Problems in Seconds Using Branch-Price-And-Cut", Naval Research Logistics 72(5):735–749, 2025, DOI 10.1002/nav.22249. 열생성 가능한 재정식화, 가격문제·클리크 컷·분기한정 관리; 노트북에서 10,000 표적·10,000 무장 규모까지 확장, 종전 수 시간 걸리던 문제를 초 단위로 정확히 해결; 변형 문제 확장 논의 — [OpenAlex](https://api.openalex.org/works/doi:10.1002/nav.22249)
- Yiping Lu, Danny Z. Chen, "A new exact algorithm for the Weapon-Target Assignment problem", Omega 98:102138, 2021, DOI 10.1016/j.omega.2019.102138; Yiping Lu, Danny Ziyi Chen, Tianshu Gao, "An Exact Algorithm for the Dynamic Two-Stage Weapon-Target Assignment Problem", SSRN 4485993, 2023 — [Crossref 1](https://api.crossref.org/works/10.1016/j.omega.2019.102138); [Crossref 2](https://api.crossref.org/works/10.2139/ssrn.4485993)
- Alexandre Colaers Andersen, Konstantin Pavlikov, Túlio A. M. Toffolo, "Weapon-target assignment problem: exact and approximate solution algorithms", Annals of Operations Research 312(2):581–606, 2022, DOI 10.1007/s10479-022-04525-6 (앵커; OpenAlex 피인용 61). 검색 요약: 저자 공개 저장소(github.com/tuliotoffolo/wta)에 branch-and-adjust 코드와 인스턴스(최대 1,500 무장×1,000 표적, 2시간 내 gap ≤2.0%)가 있다고 함 — 저장소 직접 미확인 [확인 필요] — [OpenAlex](https://api.openalex.org/works/doi:10.1007/s10479-022-04525-6)
- Jaeoh Kim, Hyun Jin Han, Jaejin Lee, Soomin Kwon, Alice E. Smith, "Dynamic Programming for the Weapon-Target Assignment Problem", SSRN 5165172, 2025 — [Crossref](https://api.crossref.org/works/10.2139/ssrn.5165172)
- 순수 메타휴리스틱(2020–2025, 베이스라인 후보): Han Xu, An Zhang, Wenhao Bi, Shuangfei Xu, "Dynamic Gaussian mutation beetle swarm optimization method for large-scale weapon target assignment problems", Applied Soft Computing 162:111798, 2024, DOI 10.1016/j.asoc.2024.111798; Lingren Kong, Jianzhong Wang, Peng Zhao, "Solving the Dynamic WTA Problem by an Improved Multiobjective PSO", Applied Sciences 11:9254, 2021 (전투이익 최대화·무장비용 최소화, 자원·실행가능성·화력전환 제약); Xiaochen Wu, Chen Chen, Shuxin Ding, "A Modified MOEA/D Algorithm for Solving Bi-Objective Multi-Stage WTA Problem", IEEE Access 9:71832–71848, 2021; Yang Zhao, Yifei Chen, Ziyang Zhen, Ju Jiang, "Multi-weapon multi-target assignment based on hybrid genetic algorithm in uncertain environment", Int. J. Advanced Robotic Systems 17(2), 2020, DOI 10.1177/1729881420905922 (회색구간수 위협평가 + 적응 교차/변이 + 모의담금질); Haonan Shi, Xueping Zhu, "Solving the WTA Problem Based on Dynamic Population Genetic Algorithm", LNEE ICAUS 2024 (2025), DOI 10.1007/978-981-96-3552-8_33 — [Crossref ASOC](https://api.crossref.org/works/10.1016/j.asoc.2024.111798); [Crossref AppSci](https://api.crossref.org/works/10.3390/app11199254); [Crossref IEEE Access](https://api.crossref.org/works/10.1109/access.2021.3079152); [OpenAlex IJARS](https://api.openalex.org/works/doi:10.1177/1729881420905922)
- 양자 접근(추세 참고): Veit Stooß, Martin Ulmke, Felix Govaers, "Adiabatic Quantum Computing for Solving the Weapon-Target Assignment Problem", arXiv:2105.02011 (2021); Erdi Acar, Saim Hatipoğlu, İhsan Yılmaz, "A quantum algorithm for solving weapon target assignment problem", EAAI 125:106668, 2023 — [arXiv API 목록](https://export.arxiv.org/api/query?search_query=all:%22weapon%20target%20assignment%22); [Crossref](https://api.crossref.org/works/10.1016/j.engappai.2023.106668)

### Inferences
- 연구자의 선행연구(b)에 쓰인 "RL-guided VNS(4개 이웃)"는 WTA 문헌에서 Q-learning/DQN 기반 연산자 선택(Zou 2024; Yıldız & Sonuç 2026)과 개념적으로 동일 계열이므로, 후속 연구에서 VNS 이웃 선택 학습을 다시 핵심 기여로 쓰면 중복성 지적을 받을 수 있다.
- "학습된 warm start(NCO 정책) → 시간예산 내 지역탐색 → anytime 품질 보장"(후보 T4)의 조합은 WTA에서 아직 발표되지 않았다. 다만 범용 NCO 커뮤니티에서는 "construct-then-improve"가 익숙한 패턴이므로, WTA 특화 기여(요격확률 구조를 이용한 하한·anytime 보장·규모 일반화 20→400)를 명확히 해야 한다.
- 정확해 비교는 Bertsimas & Paskov(2025)의 BPC 또는 Andersen et al.(2022) branch-and-adjust 코드가 공개돼 있으므로, 후속 연구의 정적 하위문제에 대해 "분 단위 MILP"가 아니라 "초 단위 정확해"를 베이스라인으로 삼지 않으면 심사자가 베이스라인 선택을 문제 삼을 가능성이 높다.

### Gaps
- WTA 전용 learning-to-branch, 학습된 컷/노드 선택, 학습된 warm start 연구는 발견되지 않았다(검색 결과는 범용 MILP용 L2B만 노출).
- Wang et al. (2022/23, EAAI)와 CEE 2024 DQN+ABC 논문의 규모·수치 미확인 [확인 필요].
- github.com/tuliotoffolo/wta의 인스턴스 규모·갭 수치는 검색 요약에 의존 [확인 필요].

---

## 핵심질문 3. anytime 동작, 실시간 예산(초 이하~수 초), rolling/receding horizon, 엣지 배치를 명시적으로 다룬 연구는 무엇인가

### Takeaway
실시간성은 거의 모든 학습 기반 WTA 논문의 동기이지만, (i) 시간예산을 명시하고 예산 내 해 품질 곡선(anytime profile)을 제시한 논문, (ii) 임베디드/엣지 하드웨어에서 측정한 논문은 2020년 이후 국제 문헌에서 발견되지 않았다. receding/rolling horizon은 휴리스틱·메타휴리스틱 DWTA에서 2020–2022년 정형화(OODA 루프 결합, 한계수익 휴리스틱, 이중수준 BBO)되었고, 통신 열화 하의 분산 할당은 UF/AFRL의 비동기 프라이멀-듀얼(2023)과 2026년 CBBA 계열 벤치마크가 기준점이다.

### Cited Findings
- Gaudet et al. (2023): 종말단계 8–16 s를 실시간 요구로 명시; RL 정책 평균 1.48 ms(최대 28 ms), NLIP 평균 2,025 ms(최대 71.6–265 s); "RL 계산시간이 HSW×표적 수에 대략 선형" — [arXiv](https://arxiv.org/abs/2310.18509)
- Kai Zhang, Deyun Zhou, Zhen Yang, Yiyang Zhao, Weiren Kong, "Efficient Decision Approaches for Asset-Based Dynamic Weapon Target Assignment by a Receding Horizon and Marginal Return Heuristic", Electronics 9(9):1511, 2020, DOI 10.3390/electronics9091511. shoot-look-shoot 원리에서 OODA 루프 기반 A-DWTA 모델(OODA/A-DWTA), receding horizon 분해(A-DWTA/RH), 통계적 한계수익 휴리스틱 HA-SMR("자산가치→표적선택→무장결정"의 역계층); 실시간성·강건성, "radical–conservative" 정도를 파라미터로 조절 — [Crossref](https://api.crossref.org/works/10.3390/electronics9091511); 동 저자 JPCS 1651:012062, 2020 — [Crossref](https://api.crossref.org/works/10.1088/1742-6596/1651/1/012062)
- Xiaowen Zhu, Chengli Fan, Shengli Liu, Huaixi Xing, Cheng Qi, "Bi-Level Fuzzy Expectation-Based Dynamic Anti-Missile Weapon Target Allocation in Rolling Horizons", Electronics 11(19):3035, 2022, DOI 10.3390/electronics11193035. 롤링 호라이즌 최적화 + 한계편익 재계획의 이중수준 모델, 개선 이중수준 재귀 BBO; 대규모·동적·불확실 환경에서 동급 휴리스틱보다 효율·시간 우위, 롤링 호라이즌 파라미터 튜닝 — [Crossref](https://api.crossref.org/works/10.3390/electronics11193035)
- Katherine Hendrickson, Prashant Ganesh, Kyle Volle, Paul Buzaud, Kevin Brink(AFRL), Matthew Hale, "Decentralized Weapon-Target Assignment under Asynchronous Communications", Journal of Guidance, Control, and Dynamics 46(2):312–324, 2023. 중앙 계획자의 단일실패점·재계획 불가를 문제로 지목; 각 무장이 결정변수의 분리된 부분집합을 최적화하는 분산 계획; 비용·제약의 연속 볼록 완화 + 분산 프라이멀-듀얼 알고리즘, 비동기 계산·통신에서도 수렴률 보장; 시뮬레이션 및 COTS 지상로봇 실험에서 간헐 통신·예상 밖 무장 손실(attrition) 하 할당 계산 성공 — [UF CORE Lab PDF](https://corelab.mae.ufl.edu/papers/WTA.pdf)
- James Lott, Vahraz Honary, "Decentralized Multi-Robot Task Allocation Under Degraded Communication: A Benchmark of Performance, Reliability, and Computation", arXiv:2609.13711 (2026). CBAA, ACBBA, PI, HIPC, DMCHBA, DGA 6종을 Bernoulli 손실·Gilbert-Elliott 손실·Rayleigh 페이딩 3종 모델, 25개 조건에서 벤치마크; 학습 기반 방법은 포함되지 않음; 계산시간 4.88 ms(DMCHBA)–1.346 s(DGA), 통신 오버헤드 2.08 publications/step(DMCHBA); 심한 손실에서 HIPC·DMCHBA만 안정 — [arXiv](https://arxiv.org/abs/2609.13711)
- Kamal Mammadov, Glen Pearce, Helen Krause, Damith C. Ranasinghe, "Distributed Marginal Return: A Communication-Efficient Algorithm for Multi-Agent Weapon Target Assignment", SSRN 5394364, 2025, DOI 10.2139/ssrn.5394364. 통신 효율적 분산 WTA. 본문 미접근 [확인 필요] — [Crossref](https://api.crossref.org/works/10.2139/ssrn.5394364)
- Peng Zhao, Jianzhong Wang, Lingren Kong, "Decentralized Algorithms for Weapon-Target Assignment in Swarming Combat System", Mathematical Problems in Engineering 2019 (앵커, 2019). 비선형 WTA용 재설계 경매 알고리즘 + 개선 task-swap; 120 무장×110 표적에서 경매 해 품질 37% 개선, task-swap 시간 53–74% 절감 — [OpenAlex](https://api.openalex.org/works/doi:10.1155/2019/8425403)
- Oh (WSC 2023)은 실시간 제어 대안으로 MPC와 휴리스틱을 비교군으로 설정 — [WSC PDF](https://www.informs-sim.org/wsc23papers/doc122.pdf); Liu et al. (2026) EHD-DQN은 RH-MILP(수평선 MILP)를 베이스라인으로 포함 — [CJA](https://hkxb.buaa.edu.cn/EN/10.7527/S1000-6893.2025.32786)
- Louis L. Chen, Ang Xu, Roberto Szechtman, Chiwei Yan, Vince Vanterpool, "Meeting Uncertain Threats with Feedback", arXiv:2607.13648 (math.OC, 2026). 중화 결과가 불확실한 다중 위협에 라운드마다 효과기를 배정하는 MDP; "빠른 구현에 적합한 시간무관(time-oblivious) 단순 정책"(균등 배분, 난이도 인지 그리디)을 분석; 동질 위협/저용량에서는 균등 배분이 세 목적(기대 소거시간 최소화, 기한 내 소거확률, 기한 내 유효배정 수) 모두에 최적, 용량이 위협 수에 선형이면 최적 대비 상수 라운드 이내; 그리디는 상수인자 보장 — [arXiv](https://arxiv.org/abs/2607.13648)
- Bertsimas & Paskov (2025): 정적 WTA 10,000×10,000을 노트북에서 초 단위로 정확 해결 — 정적 하위문제에서는 "실시간 = 정확해"가 가능함을 시사 — [OpenAlex](https://api.openalex.org/works/doi:10.1002/nav.22249)

### Inferences
- "5초 롤링 호라이즌 내 3단계 하이브리드(0.5/2.0/1.0 s)"라는 연구자 선행연구(b)의 시간 분할은 문헌상 유일하지만, 예산을 바꿨을 때의 해 품질 곡선(anytime curve)·최악 지연 분포·하한 대비 갭을 제시한 WTA 논문이 없으므로, 후속 연구에서 이를 체계화하면(anytime profile + 보장) 차별성이 뚜렷하다.
- 통신 열화 모델링은 Hendrickson(간헐 통신·attrition)과 Lott & Honary(Bernoulli/Gilbert-Elliott/Rayleigh) 수준이 현재 기준점이다. 후속 T1에서 "통신 그래프 분절·재밍·기만(deception)"을 명시적 확률모델로 넣고 CBBA 계열·비동기 프라이멀-듀얼·중앙집중 상한과 비교하면 선행문헌 대비 명확한 확장이 된다. 특히 Lott & Honary가 "학습 기반 방법은 미포함"이라고 밝힌 공백을 정면으로 메울 수 있다.
- 엣지 배치(Jetson급)에서 WTA 정책 지연을 보고한 국제 논문은 발견되지 않았다. 연구자의 "Jetson Xavier NX 11.9 ms"는 국제 문헌 기준 선점 가능 포인트이나, 단독으로는 기여가 약하므로 양자화·배치 크기·규모(20→400)별 지연 스케일링 곡선과 함께 제시해야 한다.

### Gaps
- "anytime" 키워드로 검색된 WTA 논문(수정 GA 기반 anytime DWTA)은 ResearchGate 요약만 노출되어 서지·연도 확인 불가 [확인 필요].
- Mammadov et al. (2025) 분산 한계수익 알고리즘의 통신량·성능 수치 미확인 [확인 필요].
- 엣지 하드웨어 측정을 포함한 WTA 논문은 발견되지 않았다(공백).

---

## 핵심질문 4. 2021–2026년 WTA 서베이 논문과 그들이 제시한 open problem은 무엇인가

### Takeaway
2021–2025년에 세 편의 서베이/리뷰(IntechOpen 2021; EAAI 2024 종합 서베이; Defence Technology 2025 서지계량 리뷰)가 나왔고, 공통적으로 "소규모 정적 WTA는 잘 풀리지만 대규모 동적 WTA는 미해결", "근사모델과 실전 적용 사이의 큰 격차", "다목적·시공간 제약·이기종 무장·실시간 구현의 부족"을 open problem으로 꼽는다. 학습 기반 접근의 평가 표준화나 벤치마크 부재는 서베이들이 아직 체계적으로 다루지 않은 상태다.

### Cited Findings
- Jinrui Li, Guohua Wu, Ling Wang, "A comprehensive survey of weapon target assignment problem: Model, algorithm, and application", Engineering Applications of Artificial Intelligence 137(Part B):109212, 2024, DOI 10.1016/j.engappai.2024.109212 (OpenAlex 피인용 40–43). 모델·알고리즘·응용의 3축 분류를 표제로 함. 본문·초록 미접근으로 open problem 목록 [확인 필요] — [OpenAlex](https://api.openalex.org/works/doi:10.1016/j.engappai.2024.109212); [Semantic Scholar](https://api.semanticscholar.org/graph/v1/paper/DOI:10.1016/j.engappai.2024.109212)
- Shuangxi Liu, Zehuai Lin, Wei Huang, Binbin Yan, "Current development and future prospects of multi-target assignment problem: A bibliometric analysis review", Defence Technology 43:44–59, 2025, DOI 10.1016/j.dt.2024.09.006. 검색 요약: Scopus에서 "weapon target assignment" 등 키워드로 2023년까지 463편 수집; 현행 연구는 모델·알고리즘에 집중, 정적 모델 위주이고 동적 모델은 충분히 연구되지 않음; "소규모 정적 WTA는 매우 잘 해결되었으나 대규모 동적 WTA는 효과적으로 해결되지 못함"; "근사모델과 실제 응용 사이에 거대한 격차" — 본문 미접근 [확인 필요] — [Crossref](https://api.crossref.org/works/10.1016/j.dt.2024.09.006)
- Abdolreza Asadi Ghanbari, Mousa Mohammadnia, S. Abbas Sadatinejad, Hossein Alaei, "A Survey on Weapon Target Allocation Models and Applications", in Computational Optimization Techniques and Applications, IntechOpen 2021, DOI 10.5772/intechopen.96318. 분류축: 정적/동적, target-based(subtractive)/asset-based(preferential), 위협별/다위협 관점, 단일/다목적, 단일 플랫폼/전력 협조, 방어할당/게임이론 모델. 향후과제: ① 단순화 모델과 실제(가장 복잡한 경우) 사이 격차, ② 동적 WTA의 차원의 저주를 위한 메타휴리스틱 발전, ③ 다목적 정식화 연구 부족, ④ 교전 중 온라인 실시간 구현, ⑤ 시공간 제약·스케줄링·이기종 무장체계의 통합 처리 — [IntechOpen](https://www.intechopen.com/chapters/75331)
- 앵커: Alexander G. Kline, Darryl K. Ahner, Raymond R. Hill, "The Weapon-Target Assignment Problem", Computers & Operations Research 105:226–236, 2019, DOI 10.1016/j.cor.2018.10.015 (OpenAlex 피인용 192) — [OpenAlex](https://api.openalex.org/works/doi:10.1016/j.cor.2018.10.015)
- Oh et al. (TCYB 2025)이 자체 문헌검토에서 정리한 DRL-WTA의 세 가지 한계(위상관계 표현, 규모 확장성, 성능지표 적합성)와 TechRxiv판의 네 가지 한계(단순화 모델, 계산부담, 교란사건 적응 부족, 규모 변경 시 재계산)는 사실상 2024–2025년 시점의 open problem 목록으로 기능 — [OpenAlex](https://api.openalex.org/works/doi:10.1109/TCYB.2025.3610606); [Crossref](https://api.crossref.org/works/10.36227/techrxiv.171084935.57702557/v3)

### Inferences
- 서베이들이 꼽은 "대규모 동적 WTA", "시공간 제약·스케줄링 통합", "실시간 온라인 구현"은 연구자 선행연구(b)가 이미 겨냥한 축이다. 후속 연구의 차별성은 서베이가 언급하지 않은 축 — 통신 거부·기만, 불확실성 강건성, 적응형 적군, 지휘관 의도 반영, 평가 표준화 — 에서 찾는 것이 서베이 인용 논리상 유리하다.
- 서베이 어느 것도 학습 기반 WTA의 재현성(공개 코드·공통 인스턴스·통계적 보고) 문제를 다루지 않았으므로, 후속 연구가 공개 벤치마크 시나리오·시드·CI를 제공하면 그 자체가 기여로 인용될 가능성이 있다.

### Gaps
- EAAI 2024 종합 서베이의 open problem 원문을 확인하지 못했다 [확인 필요]. 보고서 작성 시 이 서베이를 인용하려면 원문 열람이 필요하다.
- Defence Technology 2025 리뷰의 국가·기관별 통계와 결론부 원문 미확인 [확인 필요].

---

## 핵심질문 5. 고전 비선형 정수계획 외에 어떤 정식화(스케줄링/RCPSP형, MDP/POMDP, Dec-POMDP, 게임이론)가 쓰였는가; WTA를 RCPSP/MRCPSPTW로 정식화한 다른 연구가 있는가

### Takeaway
학습 계열은 MDP(단일 에이전트), 확률적 MDP(SSL 교전), POMDP(그래프 행동표현), Dec-MDP(이기종 시간창), 평균장 게임을 정식화로 채택했고, OR 계열은 강건최적화(구간 격파확률), 불확실성이론, 퍼지기대, 안정성 측도(재할당 안정성)를 추가했다. 스케줄링 요소(시간창·냉각·설정시간·발사순서·간섭·도착시각)는 MINLP/MILP/시간이산화 형태로 다수 등장하지만, WTA를 RCPSP 또는 MRCPSPTW로 명시 정식화한 국제 논문은 발견되지 않았다 — 연구자 선행연구(b)(c)의 MRCPSPTW 프레이밍은 현재까지 문헌상 고유하다.

### Cited Findings

(A) MDP/POMDP/Dec-MDP/게임
- POMDP + 그래프 행동표현: Oh et al., IEEE TCYB 56(2), 2025 — [OpenAlex](https://api.openalex.org/works/doi:10.1109/TCYB.2025.3610606); Oh, WSC 2023(상태 접근 불가·관측 기반) — [WSC PDF](https://www.informs-sim.org/wsc23papers/doc122.pdf)
- Dec-MDP + 이기종 교전 시간창: Na, Ahn, Moon, JAIS 23, 2026 — [S2](https://api.semanticscholar.org/graph/v1/paper/DOI:10.2514/1.i011676)
- 확률적 MDP(2파 Shoot-Shoot-Look, 가상표적): Merkulov et al., AIAA SciTech 2025 — [Haifa CRIS](https://cris.haifa.ac.il/en/publications/reinforcement-learning-based-cooperative-dynamic-weapon-target-as/)
- 피드백 MDP(라운드별 중화결과 관측): Chen et al., arXiv:2607.13648, 2026 — [arXiv](https://arxiv.org/abs/2607.13648)
- 단일 에이전트 MDP + DDPG/TD3: Lee et al., J-KICS 50(6), 2025 — [KICS](https://engjournal.kics.or.kr/digital-library/102718)
- 평균장 게임 기반 MARL(궤적 교차 제약을 보상에 반영): Shin et al., 한국군사과학기술학회지 23(4), 2020 — [KCI](https://www.kci.go.kr/kciportal/ci/sereArticleSearch/ciSereArtiView.kci?sereArticleSearchBean.artiId=ART002613144)
- 게임이론: "Weapon-target assignment for unmanned aerial vehicles: A multi-strategy threshold public goods game approach", Defence Technology 2025 (ScienceDirect PII S2214914725000339) — 협력-이탈 전략 라이브러리와 임계값 효용함수(검색 요약). 저자·DOI [확인 필요]; 양측 동적 게임을 Nash 균형 + Pareto 최적화로 푸는 2024-11 연구도 검색 요약에만 존재 [확인 필요].
- 포화공격 상대의 분산 WTA(각 추격자 vs 전체 표적, 도달가능성 제약 해석적 근사): Merkulov et al., AIAA SciTech 2024 — [OpenAlex](https://api.openalex.org/works/doi:10.2514/6.2024-0125)

(B) 불확실성·강건·안정성
- Jungho Park, Hadi El-Amine, "The Robust Weapon Target Assignment Problem", Military Operations Research 28:27–51, 2023, DOI 10.5711/1082598328127. 검색 요약: 격파확률을 점추정 대신 구간으로 두고 강건최적화 기법으로 정식화; Bertsimas & Paskov(2025)가 "불확실성 하 WTA를 처음 제안"한 연구로 인용. 본문 미접근 [확인 필요] — [Crossref](https://api.crossref.org/works/10.5711/1082598328127)
- Guangjian Li, Guangjun He, Mingfa Zheng, Aoyu Zheng, "Uncertain multi-objective dynamic weapon-target allocation problem based on uncertainty theory", AIMS Mathematics 8(3):5639–5669, 2023, DOI 10.3934/math.2023284. 표적 위협가치·보호자산 가치·요격 추가비용을 불확실변수로 둔 UMDWTA; 기대값·표준편차 원리로 결정론적 MOP로 변환; 3개 신규 진화연산자 + 적응 가중벡터의 개선 MOEA/D — [AIMS Press](https://www.aimspress.com/article/doi/10.3934/math.2023284?viewType=HTML)
- Ahmet Silav, Esra Karasakal, Orhan Karasakal, "Bi-objective dynamic weapon-target assignment problem with stability measure", Annals of Operations Research 311:1229–1247, 2021, DOI 10.1007/s10479-020-03919-8 — 재할당 시 해의 안정성을 목적으로 추가 — [Crossref](https://api.crossref.org/works/10.1007/s10479-020-03919-8)
- 퍼지기대·회색구간수: Zhu et al. 2022 (Electronics 11:3035); Zhao et al. 2020 (IJARS 17(2)) — 위 핵심질문 2·3 참조.

(C) 스케줄링형·시간 제약 정식화
- Kyle Volle, Jonathan Rogers, "Weapon–Target Assignment Algorithm for Simultaneous and Sequenced Arrival", Journal of Guidance, Control, and Dynamics 41(11):2361–2373, 2018 (앵커), DOI 10.2514/1.G003515. 무장 효과와 도착시각 상대 타이밍을 결합한 비용함수; 접근속도 제한 하 도착시간 제약 포함; 사용자 튜닝 파라미터로 "순차 도착 vs 격파확률" 우선순위 조절 — [OpenAlex](https://api.openalex.org/works/doi:10.2514/1.G003515)
- Min-Kyu Shin, Daniel Lee, Han-Lim Choi (KAIST), "Weapon-Target Assignment Problem with Interference Constraints using Mixed-Integer Linear Programming", arXiv:1911.12567 (2019; AIAA SciTech 2020-0388). 물리·시커 간섭 제약을 시간창 이산화·예상요격점(PIP) 집합·간섭표로 MILP화(검색 요약) — [arXiv API 목록](https://export.arxiv.org/api/query?search_query=all:%22weapon%20target%20assignment%22); [Crossref](https://api.crossref.org/works/10.2514/6.2020-0388)
- "Weapon-Target Assignment and Firing Scheduling for Rapid Engagement with Heterogeneous Interceptors", International Journal of Aeronautical and Space Sciences 2023, DOI 10.1007/s42405-023-00572-w — 발사 스케줄링을 할당과 결합. 저자·세부 [확인 필요] — [Springer(차단됨)](https://link.springer.com/article/10.1007/s42405-023-00572-w)
- Caner Arslan, "Weapon-Target Assignment for Air Defense of Naval Forces: Models and Heuristics", METU 박사학위논문, 2024. 함대 방공 계획(NADP)을 MINLP로 정식화, 센서 할당·무장/센서 사각(blind sector)·순서의존 설정시간(sequence-dependent setup times)·레이더 신호특성 포함; 정적·동적 변형 모두에 휴리스틱 제안, "빠르고 효율적" — [METU Open](https://open.metu.edu.tr/handle/11511/111327)
- Zou et al. (2026): 무장 가용시각·냉각 간격·표적 교전 시간창을 가진 다단계 DWTA — [Information and Control](https://xk.sia.cn/en/article/cstr/32166.14.xk.2025.3302)
- Jieun Kim, Chang-Hun Lee, Mun Yong Yi, "A Study on the Weapon–Target Assignment Problem Considering Heading Error", IJASS 25(3):1105–1120, 2024, DOI 10.1007/s42405-024-00717-5. 발사대 방위각 오차가 격파확률에 미치는 영향, 회전 전략 + 회전고정 전략 결합으로 회전시간에 의한 교전기회 손실 보완 — [OpenAlex](https://api.openalex.org/works/doi:10.1007/s42405-024-00717-5)
- Sang-Eun Yoo, Sang-Hyun Lee, Young-Hyeon Cha, Dae-Sung Jang, "Weapon-Target Assignment in Cooperative Engagement for Multi-Layered Ballistic Missile Defense Under Radar Resource Constraints", IJASS 2026, DOI 10.1007/s42405-026-01178-8 (레이더 자원 제약 결합; 초록 미확인 [확인 필요]) — [OpenAlex](https://api.openalex.org/works/doi:10.1007/s42405-026-01178-8)
- 센서-무장-표적 통합(SWTA) 앵커: Bin Xin, Yipeng Wang, Jie Chen, "An Efficient Marginal-Return-Based Constructive Heuristic to Solve the Sensor–Weapon–Target Assignment Problem", IEEE Trans. SMC: Systems 49(12):2536–2547, 2019 — [Crossref](https://api.crossref.org/works/10.1109/tsmc.2017.2784187)

### Inferences
- "RCPSP/MRCPSPTW로서의 WTA"는 2020–2026 국제 문헌에서 발견되지 않았고, 가장 근접한 것은 WASE(무장 할당·스케줄링, 특허/구형 문헌)·NADP MINLP(순서의존 설정시간)·시간창 Dec-MDP(Na 2026)·냉각/시간창 DWTA(Zou 2026)이다. 따라서 연구자 선행연구(b)(c)의 MRCPSPTW 정식화는 독창성이 유지되지만, 후속 연구에서 같은 정식화를 반복하면 자기중복이 된다. 후속 연구는 정식화 축을 바꾸는 것(예: Dec-POMDP + 통신 그래프 확률과정, 분포강건 MDP, 2인 영합 확률게임)이 자기표절 회피와 신규성 확보에 동시에 유효하다.
- 불확실성 축은 OR 쪽(강건·불확실성이론·퍼지)에만 있고, 학습 쪽에서 분포형 RL(ADDR)이 유일 사례(서지 미확정)이므로, CVaR/분포강건 + 위험민감 MARL(T2)은 학습 기반 WTA에서 공백이다.
- 게임이론 축은 공공재 게임·Nash/Pareto 수준의 비학습 연구만 있어, 적응형 적군과의 self-play(T6)도 공백이다. 단, Schneider & Fichter(2025)의 철회 사례처럼 "특정 시나리오에만 통하는 결과"는 심사에서 치명적이므로, 시나리오 다양성 설계가 필수다.

### Gaps
- Park & El-Amine(2023) 강건 WTA의 불확실성 집합 형태·규모·알고리즘 미확인 [확인 필요].
- IJASS 2023 발사 스케줄링 논문과 IJASS 2026 BMD 논문의 초록 미확인 [확인 필요].
- Defence Technology 2025 공공재 게임 WTA의 저자·DOI 미확인 [확인 필요].
- Dec-POMDP(관측 불완전 + 분산)를 명시한 WTA 논문은 발견되지 않았다(Na 2026은 Dec-MDP, Oh 2025는 단일 에이전트 POMDP).

---

## 핵심질문 6. 평가 엄밀성(시드 수, 신뢰구간, 통계검정, 어블레이션)의 전형과 심사자가 약점으로 보는 지점은 무엇인가

### Takeaway
학습 기반 WTA 논문의 전형적 평가는 "자체 시뮬레이터 + 소수 시나리오 + 평균(또는 중앙값) 성능 + 단일 베이스라인군"이며, 시드 수·신뢰구간·통계검정을 명시한 사례는 드물다. 상대적으로 엄밀한 사례는 Gaudet(30,000 에피소드, 중앙값·시간 분포 보고), Yıldız & Sonuç(12 인스턴스×30회, 표준편차), Na 2026(어블레이션·전이), Zou 2026(어블레이션·일반화)이며, 공개 코드는 Palmas(2025)와 Toffolo 저장소 정도다. 심사자가 지적할 약점은 (i) 베이스라인 불일치(GA/그리디만 비교, 정확해 부재), (ii) 단일 시나리오 과적합(Schneider & Fichter 철회 사례), (iii) 보상·지표의 자의성(Oh et al.이 "성능지표 적합성"을 한계로 명시), (iv) 통계적 보고 미비(Agarwal et al. 2021 기준 미충족)다.

### Cited Findings
- Gaudet et al. (2023): 비교에 30,000 시뮬레이션 에피소드 사용; 분포가 0에서 절단되고 긴 꼬리를 가져 평균 대신 중앙값 사용; 계산시간을 평균/표준편차/최대로 보고; 하이퍼파라미터·CNN 구조·롤아웃 에피소드 수 추가 탐색 여지를 한계로 인정 — [arXiv PDF](https://arxiv.org/pdf/2310.18509)
- Yıldız & Sonuç (2026): 12개 벤치마크 인스턴스(5–200), 30회 독립 실행, 비용 평균·표준편차 보고, 9/12 승 — [Crossref](https://api.crossref.org/works/10.19139/soic-2310-5070-3934)
- Na, Ahn, Moon (2026): 어블레이션, 정성 분석(에이전트·표적 선택 학습 메커니즘), 학습·시험 환경 상이한 전이 실험 — [S2](https://api.semanticscholar.org/graph/v1/paper/DOI:10.2514/1.i011676)
- Zou et al. (2026): 목적함수 검증·베이스라인 비교·일반화·어텐션/정규화 어블레이션의 4단 검증 — [Information and Control](https://xk.sia.cn/en/article/cstr/32166.14.xk.2025.3302)
- Oh et al. (2025): 기존 DRL-WTA의 "성능지표 적합성(performance metric relevance)" 부족을 한계로 명시, 복수 도메인(해상·지상) 실험 — [OpenAlex](https://api.openalex.org/works/doi:10.1109/TCYB.2025.3610606)
- Merkulov et al. (2025): RL이 그리디를 "근소하게" 상회하고 그리디가 학습해를 잘 근사한다고 보고 — 과장 없는 보고의 예 — [Haifa CRIS](https://cris.haifa.ac.il/en/publications/reinforcement-learning-based-cooperative-dynamic-weapon-target-as/)
- Schneider & Fichter (2025): 발표 수치(0–4.1%, 5.8–14.4% 개선) 후 "특정 시나리오를 넘어 일반화되지 않음"을 이유로 철회 — [arXiv](https://arxiv.org/abs/2511.02526)
- Palmas (2025): "수백 개" 시나리오, 코드·시뮬레이션 자산 공개 — [arXiv](https://arxiv.org/abs/2508.00641)
- Lee et al. (J-KICS 2025): 개선율(+27.17%, +38.61%, −11.98%)만 보고, 초록 수준에서 CI·시드 미기재 — [KICS](https://engjournal.kics.or.kr/digital-library/102718)
- Tao et al. (2024): "여러 실험", GA 대비 ≥30%·시간 <10% — 시드·CI 미기재(초록) — [OpenAlex](https://api.openalex.org/works/doi:10.3390/math12162557)
- Lott & Honary (2026): 25개 통신조건 전수 벤치마크, 평균 MinMax/MinSum 이동량·통신량·계산시간 다축 보고, 알고리즘별 신뢰성(안정성) 명시 — 분산 할당 벤치마크 설계의 참고 모델 — [arXiv](https://arxiv.org/abs/2609.13711)
- 방법론 앵커: Rishabh Agarwal, Max Schwarzer, Pablo Samuel Castro, Aaron Courville, Marc G. Bellemare, "Deep Reinforcement Learning at the Edge of the Statistical Precipice", NeurIPS 2021 (Outstanding Paper), arXiv:2108.13264. 소수 실행 체제에서 점추정만으로는 결론이 뒤바뀔 수 있음; 더 많은 시드, 구간추정(층화 부트스트랩 CI), 사분위평균(IQM), 성능 프로파일, rliable 라이브러리 권고 — [arXiv](https://arxiv.org/abs/2108.13264)
- 공개 인스턴스: Andersen et al. (2022) 관련 저장소 github.com/tuliotoffolo/wta(검색 요약; 직접 미확인 [확인 필요]) — [OpenAlex](https://api.openalex.org/works/doi:10.1007/s10479-022-04525-6)

### Inferences
- 연구자 선행연구(b)의 "1,000 물리 시뮬 + 100,000 부트스트랩 + CI + Cohen d"는 WTA 문헌 평균보다 엄밀하지만, 국제 심사 기준에서는 (i) 학습 시드 수(정책 학습 반복 횟수)와 시험 에피소드 수를 구분해 보고, (ii) IQM·성능 프로파일(rliable), (iii) 정확해/강한 하한 대비 갭, (iv) 시나리오 분포 외(OOD) 전이 평가, (v) 코드·시나리오 공개가 추가로 요구될 가능성이 높다.
- DSR(0.7×격파율+0.3×생존율)과 같은 합성 지표는 Oh et al.이 지적한 "지표 적합성" 비판 대상이 될 수 있다. 국제 문헌의 표준 지표(잔존 표적 기대가치, threat survivability, 요격 성공률, 탄 소모)와 병기하고 가중치 민감도 분석을 제공하는 것이 안전하다.
- 베이스라인 선택: QMIX/MADDPG/CBBA 비교는 Tao(2024)·Yao(2026)·Na(2026) 등과 중복되는 표준 구성이다. 차별화된 베이스라인(비동기 프라이멀-듀얼, DMCHBA/HIPC 계열, BPC 정확해 상한, LLM 기반)을 포함하면 신규성 인식에 유리하다.

### Gaps
- 학습 기반 WTA 논문 중 통계검정(예: Wilcoxon, 부트스트랩 CI)을 명시적으로 수행한 사례를 초록·메타데이터 수준에서는 확인하지 못했다(본문 접근 제한).
- WTA 학습 연구용 공개 벤치마크(공통 시나리오 생성기·인스턴스·리더보드)는 발견되지 않았다 — 공백이자 기여 기회.

---

## 보조질문. 후보 후속주제 T1–T7에 대한 문헌 대비 판단(신규성·중복 위험)

### Takeaway
문헌 대비로 가장 비어 있는 축은 T1(통신 거부·기만 하 완전 분산 학습 WTA — 학습 기반 벤치마크 부재), T2(위험민감/분포강건 학습 WTA — OR 강건모델만 존재), T6(적응형 적군 self-play — 비학습 게임모델만 존재)이며, T4(NCO warm start + anytime)는 WTA 내 공백이지만 범용 NCO와의 차별화 설명이 필요하다. T5(LLM 의도 반영)는 2025-11 arXiv 선행이 등장해 "LLM이 직접 할당"이 아닌 "LLM이 목적함수·제약을 생성 + XAI·거부권"으로 선을 그어야 한다. T3·T7은 선행이 2018(도착시각 결합)과 다수 이기종 군집 연구로 존재해 상대적 신규성이 낮다.

### Cited Findings
- T1 관련: Hendrickson et al. 2023(비동기·간헐 통신·attrition, 비학습) — [UF PDF](https://corelab.mae.ufl.edu/papers/WTA.pdf); Lott & Honary 2026(6종 분산 할당 벤치마크, 학습 기반 미포함, Bernoulli/Gilbert-Elliott/Rayleigh) — [arXiv](https://arxiv.org/abs/2609.13711); Merkulov 2024(타 요격체 성공확률 공유를 전제한 분산 RL) — [OpenAlex](https://api.openalex.org/works/doi:10.2514/6.2024-0125); Yao 2026(분산 WTA 그래프 어텐션 MARL, 통신 모델 불명 [확인 필요]) — [Crossref](https://api.crossref.org/works/10.21203/rs.3.rs-10847429/v1)
- T2 관련: Park & El-Amine 2023(강건 WTA, 비학습) — [Crossref](https://api.crossref.org/works/10.5711/1082598328127); Li et al. 2023(불확실성이론) — [AIMS](https://www.aimspress.com/article/doi/10.3934/math.2023284?viewType=HTML); Silav et al. 2021(안정성 측도) — [Crossref](https://api.crossref.org/works/10.1007/s10479-020-03919-8); Chen et al. 2026(피드백 MDP, 단순정책 보장) — [arXiv](https://arxiv.org/abs/2607.13648); ADDR 2024(분포형 RL, 서지 [확인 필요])
- T3 관련: Volle & Rogers 2018(동시/순차 도착 비용함수, 앵커) — [OpenAlex](https://api.openalex.org/works/doi:10.2514/1.G003515); Shin/Lee/Choi 2019–2020(간섭 제약 MILP) — [Crossref](https://api.crossref.org/works/10.2514/6.2020-0388); Arslan 2024(순서의존 설정시간·사각) — [METU](https://open.metu.edu.tr/handle/11511/111327); Zou 2026(냉각·시간창) — [Information and Control](https://xk.sia.cn/en/article/cstr/32166.14.xk.2025.3302)
- T4 관련: Na 2022(Pointer), Park & Kim 2025(Transformer-Pointer PPO, 상용 솔버 대비 고속), Zou 2026(Pointer+AC, 가변 규모), Bertsimas & Paskov 2025(10,000 규모 정확해 초 단위) — WTA에서 "학습 warm start + 지역탐색 + anytime 보장"은 미발표 — [OpenAlex](https://api.openalex.org/works/doi:10.2514/1.I011150); [Crossref](https://api.crossref.org/works/10.2139/ssrn.5704099); [OpenAlex](https://api.openalex.org/works/doi:10.1002/nav.22249)
- T5 관련: Autenrieb & Ostermann 2025(LLM이 할당을 직접 생성, TAES 투고) — [arXiv](https://arxiv.org/abs/2511.10207); Liu et al. 2026 EHD-DQN(Grad-CAM+LIME 설명모듈) — [CJA](https://hkxb.buaa.edu.cn/EN/10.7527/S1000-6893.2025.32786)
- T6 관련: 공공재 게임·Nash/Pareto 동적 게임(비학습, 서지 [확인 필요]); 학습 기반 self-play WTA는 검색에서 LLM 안전정렬 분야 결과만 노출되어 WTA 사례 없음.
- T7 관련: 이기종 UAV/UUV/UAV-USV 협조 임무할당 연구가 다수 노출(검색 요약; UAV-USV MADDPG, UUV DECBBA 등) 되나 "무장할당" 관점은 Yao 2026(레이더+발사대 이기종)이 가장 근접 — [Crossref](https://api.crossref.org/works/10.21203/rs.3.rs-10847429/v1)

### Inferences
- 자기표절 회피 관점: 선행연구(b)의 핵심 요소(MRCPSPTW 정식화, 5초 롤링 3단계 하이브리드, GAT-MAPPO CTDE, 80×80 해상 시나리오, DSR 지표)를 후속 논문에서 재사용하면 중복 게재 논란이 생긴다. 후속 연구는 문제 정의(통신 거부·불확실성·적응형 적군), 모델(Dec-POMDP/분포강건 MDP/확률게임), 실험(새 시나리오 생성기·OOD 전이·공개 벤치마크·정확해 상한)을 모두 바꾸고, (b)는 "비교 베이스라인"으로만 인용하는 구성이 안전하다.
- 우선순위 제안(문헌 공백 크기 × 실행 가능성): T1 ≥ T2 > T4 > T6 > T5 > T3 ≈ T7. T1과 T2는 결합 가능(통신 거부 + 격파확률/식별 불확실성 → 위험민감 Dec-POMDP). T4는 시뮬레이터 개발과 궤를 같이해 "공개 벤치마크 + anytime 프로파일" 논문으로 분리 투고할 가치가 있다.
- 투고 대상 관점: 학습 WTA의 국제 수용 학술지는 IEEE TAES, IEEE TCYB, AIAA JAIS, Defence Technology, EAAI, IEEE Access이며, OR 정식화 강조 시 Annals of OR·NRL·Military Operations Research가 적합하다.

### Gaps
- T6용 적응형 적군 모델링(red-team learning)의 WTA 선행이 없어, 비교군을 공군 공중전 MARL(DRG-MAPPO 등 인접분야)에서 차용해야 한다.
- T7의 "무장할당 관점 이기종 USV+UAV+UUV" 선행은 메타데이터로만 파악되어 상세 비교가 불가하다 [확인 필요].
