# 불확실성 하 할당·경로/도착시각 결합 할당·다목적 할당의 기술 계보 (2015–2026) 및 방어측(salvo) 모델

> 작성일 2026-10-05(2026-10-06 보완). 범위: (a) 불확실성 하 WTA/과업할당(stochastic·robust·DRO·CVaR·Bayesian·기만/오식별), (b) 할당+경로/궤적+동시도착(cooperative timing)·유한 교전능력 다층방어, (c) 다목적 할당(효과·탄약·생존성·비용)과 Pareto 기법, (d) 연구용 시뮬레이터에 넣을 수 있는 방어측 모델(Hughes salvo, Armstrong stochastic salvo, leaker/교전능력/탄창, 기만체 효과).
>
> 검증 방법 메모: OpenAlex·Semantic Scholar API는 이 세션에서 rate-limit(429)으로 사용 불가였고, ScienceDirect·IEEE Xplore·AIAA ARC·GMU 저장소는 403이었다. 서지는 Crossref API(DOI 레코드)로 확인했고, 초록은 Crossref/출판사 페이지 또는 DOI 기반 초록 미러(colab.ws)에서 열람했다. 본문 전체를 연 문헌은 Kesler·Lucas·Sanchez(WSC 2019), Hughes(1995, NPS Calhoun), Armstrong & Powell(2005 working paper), Atkinson & Kress(OR 2025 accepted manuscript)이다. "초록 미열람"으로 표시한 항목은 Crossref 서지만 확인한 것이며 내용 요약은 하지 않았다. 기존 노트(01·02·04)에 이미 있는 항목(Kong 2021, Li·Xin 계열 CVaR 등)은 중복 서술을 최소화하고 계보 위치만 표시했다.
>
> **2026-10-06 보완(재시도)**: 이번 재시도에서는 WebFetch가 일부 도메인에서 동작했다. arXiv 초록 페이지(2607.13648, 2608.05256), KFUPM Pure 페이지, HIT 연구자 페이지(Li et al. 2016)와 Crossref API 레코드(Bertsimas & Paskov 2025, Park & El-Amine 2023, Volle & Rogers 2018, Ren et al. 2026, Zhu et al. 2026)를 새로 열람했다. 반면 Wiley, MIT DSpace PDF, INFORMS(PubsOnLine), GMU 디지털컬렉션, MDPI는 403/404/405로 열리지 않았다. Crossref 레코드는 서지 메타데이터만 제공하며 위 5편 모두 초록 필드가 비어 있었다. 따라서 해당 항목은 "서지 확인, 내용 미열람"으로 유지한다.
>
> [앵커]는 2020년 이전 seminal/기준 문헌이다.

---

## Q1. 확률적·강건 할당: 핵심 논문, 교전효과·표적가치·식별·기만 불확실성 모델링, 위험척도, 해법(SAA·robust MILP·DRO·위험민감 RL)과 규모·연산시간

### Takeaway
WTA 계보에서 불확실성은 주로 (i) 살상확률 p_ij 자체가 확률변수/구간인 경우(CVaR·uncertainty theory·robust), (ii) 위협 도착·교전 결과가 순차적으로 드러나는 확률적 동적 문제(MDP/ADP, shoot-look-shoot)로 모델링된다. 2020–2026년에 WTA를 직접 다룬 DRO나 위험민감(CVaR) RL 논문은 찾지 못했다. DRO·adjustable robust·Mean-CVaR two-stage는 인접한 UAV/UAV-USV 과업할당에서만 2025–2026년에 등장했고, 식별·기만 불확실성은 belief-entropy 융합 기반 게임 모델(2019), 기만적 표적전환 탐지(2025 arXiv), 방어측 soft measure(디코이 포함) 사격이론(2025 OR)에 흩어져 있다.

### Cited Findings

**(1) 기준·정확해 (규모 앵커)**
- [앵커] Kline, Ahner, Hill, "The Weapon-Target Assignment Problem", *Computers & Operations Research* 105:226–236, 2019. 정적·동적 WTA의 정식화와 정확해·휴리스틱을 비교 가능한 형태로 정리한 서베이. Manne(1958)부터 시간 매개변수가 들어간 모형까지 계보를 정리했다 — [DOI 10.1016/j.cor.2018.10.015](https://doi.org/10.1016/j.cor.2018.10.015)
- Lu & Chen, "A new exact algorithm for the Weapon-Target Assignment problem", *Omega* 98:102138, 2021. 비선형 WTA(목표: 표적 기대 생존가치 최소화)를 이진 열(column)로 정확 선형화하고 column enumeration, branch and bound, weapon-number bounding, weapon domination을 결합했다. 기존 정확해법은 80무기×80표적에 16.2 h가 걸렸는데 이 방법은 **0.40 s**로 푼다 — [DOI 10.1016/j.omega.2019.102138](https://doi.org/10.1016/j.omega.2019.102138)
- Bertsimas & Paskov, "Solving Large-Scale Weapon Target Assignment Problems in Seconds Using Branch-Price-And-Cut", *Naval Research Logistics* 72(5), 2025(온라인 2025-01-27; 쪽수 [확인 필요]). WTA를 column generation에 맞게 재정식화하고 초기화, pricing, cut 생성, branching 알고리즘을 제시한다. 초록에 따르면 일반 노트북에서 **표적·무기 각 10,000개** 규모까지 확장되고, 기존에 오래 걸리던 인스턴스를 수 초에 푼다 — [Crossref 레코드](https://api.crossref.org/works/10.1002/nav.22249), [DOI 10.1002/nav.22249](https://doi.org/10.1002/nav.22249) (Wiley·MIT DSpace 본문은 403/405로 미열람; 노트 01에도 항목 있음)

**(2) 살상확률 불확실성: CVaR / uncertainty theory / robust**
- Li, Xin, Pardalos, Chen, "Solving bi-objective uncertain stochastic resource allocation problems by the CVaR-based risk measure and decomposition-based multi-objective evolutionary algorithms", *Annals of Operations Research* 296(1):639–666, 2021. 할당 결과의 확률이 무작위 매개변수에 의존하는 불확실 확률 모형이다. 다단계 WTA와 redundancy allocation에 **CVaR(실패위험) vs 자원비용**의 2목적 모델을 세우고, 선형화·근사선형 정식화 후 MOEA/D-AWA와 DMOEA-εC를 적용했다. 대부분의 인스턴스에서 DMOEA-εC가 우세했다 — [IDEAS/RePEc 초록](https://ideas.repec.org/a/spr/annopr/v296y2021i1d10.1007_s10479-019-03435-4.html), [DOI 10.1007/s10479-019-03435-4](https://doi.org/10.1007/s10479-019-03435-4)
- [앵커] Li, Chen, Xin, Dou, Peng, "Solving the uncertain multi-objective multi-stage weapon target assignment problem via MOEA/D-AWA", *2016 IEEE Congress on Evolutionary Computation (CEC)*, pp.4934–4941, 2016, DOI 10.1109/CEC.2016.7744423(DOI는 연구자 페이지 표기). 확률적 불확실성이 있는 다단계 WTA를 **피해 최대화 vs 탄약 최소화**의 2목적 제약 조합최적화로 두고, MOEA/D-AWA에 **Max-Min robust** 기법을 결합했다. 확정(certain) 및 불확실 다목적 MWTA 모두에서 단일목적 해법보다 낫다고 보고한다. 불확실성 모형과 규모는 초록에 없다 — [HIT 연구자 페이지](https://hit.globalimpact.cn/en/publications/solving-the-uncertain-multi-objective-multi-stage-weapon-target-a/)
- Li, He, Zheng, Zheng, "Uncertain Sensor–Weapon–Target Allocation Problem Based on Uncertainty Theory", *Symmetry* 15(1):176, 2023. 표적 위협가치, 센서 추적성능 편차, 무기 요격성능 편차를 uncertain variable(빈도 기반 확률이 아닌 Liu의 불확실성 이론)로 두고 파괴가치 최대화 USWTA를 세웠다. 기대값 원리로 결정론 모형에 등가 변환한 뒤 permutation 표현, MMR 구성 휴리스틱(MMRCH), 지역탐색을 적용했다 — [DOI 10.3390/sym15010176](https://doi.org/10.3390/sym15010176)
- Park & El-Amine, "The Robust Weapon Target Assignment Problem", *Military Operations Research* 28(1):27–51, 2023 — [DOI 10.5711/1082598328127](https://doi.org/10.5711/1082598328127) **[초록 미열람, 확인 필요]**: 저자(Jungho Park, Hadi El-Amine)와 MOR 28(1):27–51 서지는 Crossref API 레코드로 재확인했다([Crossref](https://api.crossref.org/works/10.5711/1082598328127)). 그러나 레코드에 초록이 없고, DOI가 가리키는 MORS 상점 페이지는 "Page Not Found"였다. 같은 주제의 GMU 학위논문 "The weapon target assignment problem under uncertainty"는 검색 결과에 나왔으나 mars.gmu.edu는 404, digitalcollections.gmu.edu는 403이어서 열지 못했다. 불확실성 집합의 형태(budgeted 여부 등)와 해법은 확인하지 못했다. 웹검색 요약문이 budgeted uncertainty set을 언급했지만 출처가 이 논문인지 불명확하여 채택하지 않았다.
- Dağıstanlı, Bişkin Dursun, Kurtay, Deveci, Kadry, "A stochastic weapon–target assignment framework for air defense systems using artificial bee colony algorithm", *Applied Soft Computing* 202:115932, 2026 — [DOI 10.1016/j.asoc.2026.115932](https://doi.org/10.1016/j.asoc.2026.115932) **[초록 미열람, 확인 필요]**

**(3) 식별·기만·적 의도 불확실성**
- [앵커] Pan, Zhou, Tang, Li, "A Novel Antagonistic Weapon-Target Assignment Model Considering Uncertainty and its Solution Using Decomposition Co-Evolution Algorithm", *IEEE Access* 7:37498–37517, 2019. 두 전투기 편대의 비협력 영합게임(AGWTA)이다. 적 화력과 전자교란에서 오는 불확실성을 belief entropy와 센서자료 유사도 기반 융합으로 처리해 **표적유형 식별 신뢰도**를 높였다. DCEA로 비협력 Nash 균형을 근사한다 — [DOI 10.1109/access.2019.2905274](https://doi.org/10.1109/access.2019.2905274)
- Hughes & Lunday, "The Weapon Target Assignment Problem: Rational Inference of Adversary Target Utility Valuations from Observed Solutions", *Omega* 107:102562, 2022. 관측된 적의 정적 WTA 해로부터 적의 상대적 표적가치를 역추론한다(inverse optimization). 단위 simplex 안의 볼록 polytope(weak dominance)로 가능한 가치 계층 전체를 특성화하고, 수리계획 기반 방법과 mesh-sampling 휴리스틱을 비교했다. 최선 기법조차 대형 문제에서는 계산이 어렵다고 결론냈다 — [DOI 10.1016/j.omega.2021.102562](https://doi.org/10.1016/j.omega.2021.102562)
- Meng, Li, Ornik, "Target Prediction Under Deceptive Switching Strategies via Outlier-Robust Filtering of Partially Observed Incomplete Trajectories", arXiv:2504.03502, 2025. 두 목표 중 하나로 향하다 중간에 **기만적으로 목표를 바꾸는** 에이전트를, 잡음·결손 관측 아래 outlier-robust change detection과 Bayesian 사후확률로 탐지한다. 저자들은 WTA의 기만 탐지에 적용해 검토했다고 밝힌다 — [arXiv 2504.03502](https://arxiv.org/abs/2504.03502)
- Norris, Lee, Vidra, Setty, "Posture and Sustainment Optimization Under Adversarial Uncertainty", arXiv:2608.05256, 2026-08-05(프리프린트, 동료심사 아님). 분쟁 전 전역 거점별 자산 배치를 유한기간 MDP로 정식화하고 Composite Expected Value(CEV)와 RobustCEV를 제안한다. 위협 분포에 지리적 신호가 있으면 CEV가 greedy 대비 최대 19.8%, **적응형 적대자**에 대해 RobustCEV가 최대 158% 상대 효율 이득을 낸다고 보고한다. 베이지안 적대자 모델을 쓴다. 규모는 자산 20개, 거점 5곳이다. 표적할당이 아닌 **자산 배치** 문제이므로 인접 문헌이며, WTA에 대한 직접 근거로 쓰지 않는다 — [arXiv 2608.05256](https://arxiv.org/abs/2608.05256)

**(4) 순차적 확률 동적 할당(MDP/ADP, SLS)**
- [앵커] Davis, Robbins, Lunday, "Approximate dynamic programming for missile defense interceptor fire control", *EJOR* 259(3):873–886, 2017. 다중 salvo 미사일 공격에 대한 요격탄 사격통제를 MDP로 정식화하고 ADP로 풀었다. 가장 현실적인 인스턴스에서 평균 최적성 갭이 **7.74%**이고, 정확 DP는 수 시간인 반면 ADP는 수 분이었다 — [DOI 10.1016/j.ejor.2016.11.023](https://doi.org/10.1016/j.ejor.2016.11.023)
- Summers, Robbins, Lunday, "An approximate dynamic programming approach for comparing firing policies in a networked air defense environment", *Computers & Operations Research* 117:104890, 2020. 네트워크화된 defense-in-depth TBM 방어의 동적 WTA를 MDP로 두고 LSPE·LSTD 기반 ADP로 풀었다. 분쟁 기간이 짧고 공격 무기가 정교하면 ADP가 1발·2발 고정 정책보다 낫지만, 기간이 길고 공격 무기가 단순하면 1발/위협 고정 정책이 낫다 — [DOI 10.1016/j.cor.2020.104890](https://doi.org/10.1016/j.cor.2020.104890)
- Liles, Robbins, Lunday, "Improving defensive air battle management by solving a stochastic dynamic assignment problem via approximate dynamic programming", *EJOR* 305(3):1435–1449, 2023. UCAV가 확률적으로 도착하는 순항미사일 salvo로부터 고가치 자산을 방어하는 tasking+routing을 MDP(ABMP)로 두고 API-LSTD로 풀었다. closest-intercept 벤치마크 대비 평균 성공률이 **+2.8%**였다 — [DOI 10.1016/j.ejor.2022.06.031](https://doi.org/10.1016/j.ejor.2022.06.031)
- Kalyanam & Clarkson, "Sequential attack salvo size is monotonic nondecreasing in both time and inventory level", *Naval Research Logistics* 68(4):485–495 (온라인 2020-12, 권호 2021). 단일 표적에 대한 순차 교전의 최적 salvo 크기가 시간과 재고에 대해 단조 비감소임을 증명했다. Bellman 재귀 대신 확장 가능한 선형 재귀를 제시했다 — [DOI 10.1002/nav.21967](https://doi.org/10.1002/nav.21967)
- Chen, Xu, Szechtman, Yan, Vanterpool, "Meeting Uncertain Threats with Feedback", arXiv:2607.13648, 2026-07. 무력화 여부가 사격 라운드 후에야 관측되는 다위협 방어할당을 MDP로 정식화하고, 위협 소거 시간·마감 내 소거확률·유효할당 수를 평가했다. 동질 위협·저능력 상황에서는 **fair allocation(균등 분산 사격)이 최적**이고, 교전능력이 위협 수에 선형 비례하면 최적 정책보다 최대 상수 라운드만 뒤진다. 이질 위협에서는 난이도 인지 greedy가 준최적이다 — [arXiv 2607.13648](https://arxiv.org/abs/2607.13648)
- Merkulov, Iceland, Michaeli, Gal, Barel, Shima, "Virtual-Target-Based Stochastic Shoot–Shoot–Look Assignment Algorithms", *Journal of Aerospace Information Systems* 23(6):556–570, 2026. 2파 추격자 중 2파를 virtual target으로 유도해 1파 결과를 본 뒤 재할당하는 문제를 확률적 MDP로 정식화했다. greedy와 RL 분산 순차할당이 거의 같은 성능을 내서, 다단계 선행계획이 이 문제군에서는 불필요하다고 결론냈다(이론 상계로 뒷받침) — [DOI 10.2514/1.i011756](https://doi.org/10.2514/1.i011756)

**(5) DRO·adjustable robust·Mean-CVaR(인접 과업할당; WTA 아님)**
- Zheng, Liang, Zhong, Zhang, Lv, Zhang, Zheng, "Distributionally Robust Integrated 'Decision–Control' Task Assignment for Multiple Unmanned Aerial Systems in Emergency Response Under Stochastic Disturbances", *Mathematics* 14(17):3044, 2026. 상위는 최대 임무완료시간 최소화 할당, 하위는 운동학 제약 최소시간 최적제어인 bi-level 모형이다. 평균·공분산·지지집합만 아는 moment-based ambiguity set에서 쌍대성과 SDP로 DR chance constraint를 결정론적 안전여유로 바꿨다. 결정론 계획의 임무성공률은 약 0.7%, 제안 방법은 **>99.9%** — [DOI 10.3390/math14173044](https://doi.org/10.3390/math14173044)
- Gao, Zheng, Zhong, Mei, "Robust Optimization for Cooperative Task Assignment of Heterogeneous Unmanned Aerial Vehicles with Time Window Constraints", *Axioms* 14(3):184, 2025. 연료소모 불확실성을 adjustable robust optimization과 쌍대성으로 결정론 MILP(time window는 big-M)로 변환했다 — [DOI 10.3390/axioms14030184](https://doi.org/10.3390/axioms14030184)
- He, Liu, Liu, Tian, "Robust coordinated path planning for unmanned aerial vehicles and unmanned surface vehicles in maritime monitoring with travel time uncertainty", *Transportation Research Part B* 199:103284, 2025. UAV·USV 이동시간 불확실성을 **budgeted uncertainty set**으로 두었다. 집합분할 master와 robust RCESPP subproblem으로 분해하고 branch-and-price-and-cut으로 풀었다(해양감시, 비전투) — [DOI 10.1016/j.trb.2025.103284](https://doi.org/10.1016/j.trb.2025.103284)
- Xu, Wan, Huang, Zhang, Yuan, Wang, "A Risk-Averse Two-Stage Stochastic Programming Model for Emergency UAV Task Allocation", *Drones* 10(7):529, 2026. 1단계에서 할당·경로·방문순서를, 2단계에서 시나리오별 대기·지연·recourse를 결정한다. **Mean-CVaR**을 쓰고 partial scenario embedding, warm start, cut-pool 관리를 넣은 강화 Benders로 풀었다 — [DOI 10.3390/drones10070529](https://doi.org/10.3390/drones10070529)

**(6) 방어측 기만/soft measure 사격이론(디코이 포함)**
- Atkinson & Kress, "Hard and Soft Defense Against a Sequence of Aerial Threats", *Operations Research* 73:1767–1784, 2025. hard interceptor와 soft measure(재밍, 디코이, 지향성에너지)를 결합한 SLS 사격이론 모델이다. SM에는 kill을 놓치는 **false-negative BDA**가 있다. MOE는 (기대 leaker 수, 기대 요격탄 소모)의 2차원 efficient frontier이다 — [저자 게재승인본 PDF](https://faculty.nps.edu/mkress/docs/salvo_paper_FINAL.pdf), [DOI 10.1287/opre.2024.1025](https://doi.org/10.1287/opre.2024.1025) (상세는 Q3)

**(7) 위험민감·분포강건 RL 기반 WTA**
- Crossref 검색("risk-sensitive reinforcement learning task allocation CVaR multi-agent")에서 WTA 대상 위험민감/CVaR MARL 논문은 나오지 않았다. 학습 기반 WTA는 기대값 최적화가 주류이다. 예: Na, Ahn, Moon, "Multi-Agent Reinforcement Learning Considering Agent Priority for Weapon–Target Assignment", *JAIS* 23(6):464–479, 2026. 이종 교전 time window가 있는 Dec-MDP에서 agent selector→target selector 계층 MARL로 최저 threat survivability를 얻고 전이성을 시험했다 — [DOI 10.2514/1.i011676](https://doi.org/10.2514/1.i011676)

### Inferences
- 규모 면에서 정적 결정론 WTA는 80×80을 0.40 s에 정확히 풀 수 있다(Lu & Chen 2021). 그러므로 선행연구 (b)의 80 vs 80 시나리오에서 "centralized MILP bound"는 연산상 싸고, T2의 SAA 시나리오별 하한 계산에도 쓸 수 있다. 반대로 T2의 기여가 "대규모를 빨리 푼다"에 있다고 주장하기는 어렵다. 기여는 **분포 불확실성 하의 꼬리위험 통제와 재할당**에 두어야 한다.
- WTA 계보의 위험척도는 기대 생존가치, CVaR(Li et al. 2021), 불확실성 이론 기대값(Li et al. 2023) 수준에 머문다. DRO(moment/Wasserstein ambiguity)는 UAV 과업할당(Zheng 2026)과 UAV-USV 경로(He 2025, budgeted robust)에만 있다. "DRO-WTA + 재할당"은 비어 있는 조합으로 보인다(검색 범위 내).
- Merkulov et al.(2026)과 Chen et al.(2026)은 "피드백 있는 순차 방어할당에서 greedy·fair 정책이 준최적"이라고 보고한다. T2에서 위험민감 RL을 제안한다면 이 강한 단순 베이스라인(greedy, fair, ADP)과의 비교가 필수다.
- 식별·기만은 세 갈래로 나뉜다: (i) 센서융합으로 식별확률을 높이고 결정론 할당(Pan 2019), (ii) 기만 의도 탐지(Meng 2025), (iii) 방어측 soft measure의 BDA 오류(Atkinson & Kress 2025). **오식별 확률을 할당 결정변수와 함께 최적화하는**(예: 디코이 확률이 있는 표적에 대한 chance-constrained/DR 할당) 공격측 WTA 정식화는 찾지 못했다.
- 규모 논거 보강: Bertsimas & Paskov(2025)가 정적 WTA를 10,000×10,000까지 노트북에서 푼다고 보고하므로, 80 vs 80 혹은 수백 규모에서 "결정론 해의 계산 난이도"는 T2·T3의 동기가 될 수 없다. 반면 이 해법들은 모두 결정론 정적 문제이다. 불확실성(분포 모호성), 재할당, 방어측 용량 내생화가 들어간 문제에서 이런 정확해의 확장성 결과는 열람 범위에 없다(판단).
- 불확실 다목적 MWTA의 가장 오래된 앵커는 Li et al.(2016, CEC)의 MOEA/D-AWA + Max-Min robust이고, 2021년 Annals OR 논문(CVaR)이 이를 위험척도 쪽으로 확장한 것으로 읽힌다(두 논문의 저자 성(Li, Xin, Chen)이 겹친다는 점에서의 추론일 뿐 동일 연구군인지와 계승 관계는 본문에서 확인하지 않았다 [확인 필요]).

### Gaps
- Park & El-Amine(2023, MOR)의 불확실성 집합, 해법, 규모: 원문·초록 미열람 [확인 필요]. T2의 직접 선행연구일 가능성이 높으므로 원문 확보가 필요하다.
- Dağıstanlı et al.(2026, ASOC) 내용 미열람 [확인 필요].
- 불완전 식별 하의 디코이 효과를 다룬 고전 OR 문헌 "Effectiveness of Imperfect Decoys"(*Operations Research* 16(1), INFORMS, URL: https://pubsonline.informs.org/doi/10.1287/opre.16.1.10)가 검색 결과에 제목으로만 나왔고 페이지는 403이었다. 저자·연도·내용 모두 미확인이므로 인용하지 않으며 [확인 필요], 공격측이 식별 오류와 함께 사격을 배분하는 고전 모형이 있을 가능성의 단서로만 남긴다.
- SAA를 WTA에 직접 적용한 2020–2026 논문은 이번 검색에서 찾지 못했다. Uryasev 계열 CVaR-WTA(2000년대 초)는 검색 스니펫으로만 확인했고 열지 않았다.
- 위험민감·분포강건 MARL을 WTA에 적용한 논문은 발견하지 못했다(검색어와 데이터베이스 한계 가능성 있음).

---

## Q2. 할당과 경로/궤적 결합·협동 도착시각: 정식화(MINLP·bilevel·MDP), 동시도착 제약, TOA 합의, 유한 교전능력 다층방어 대상 할당, 대표 결과, USV 특화 연구

### Takeaway
"할당 + 경로 + 동시도착"은 UAV·미사일 계보에서 GA/EDA/ECNP 같은 메타휴리스틱이나 2단계(할당 후 궤적) 분해로 다수 다뤄졌다. 다만 표적은 대부분 **수동적**(방어 없음 또는 위협구역 회피 수준)으로 취급된다. 반대로 방어측 계보(Karasakal, Park & Choi, Atkinson & Kress)는 교전창, 발사간격, SLS를 갖춘 유한 교전능력을 정교하게 다루지만 공격측 도착시각을 결정변수로 두지 않는다. 두 계보를 잇는 정식화, 즉 **공격측 할당과 도착시각이 방어측 교전능력 포화를 유도하는 모형**은 USV에서 발견되지 않았다. 해상상태·속도 제약을 넣은 USV WTA도 찾지 못했다.

### Cited Findings

**(1) 동시/순차 도착을 포함한 WTA·과업할당**
- [앵커] Volle & Rogers, "Weapon–Target Assignment Algorithm for Simultaneous and Sequenced Arrival", *Journal of Guidance, Control, and Dynamics* 41(11):2361–2373, 2018. 표적 기대생존가치 최소화 WTA를 다목적으로 확장해 동시·순차 도착을 반영했다 — [DOI 10.2514/1.g003515](https://doi.org/10.2514/1.g003515) **[초록 일부만 열람(앞부분 절단), 해법·규모 확인 필요]** 저자(Kyle Volle, Jonathan Rogers, Georgia Tech)와 서지(41(11):2361–2373, 2018-11)는 Crossref 레코드로 재확인했다([Crossref](https://api.crossref.org/works/10.2514/1.g003515)). 레코드에는 초록이 없다.
- Yan, Chu, Hu, Zhu, "Cooperative task allocation with simultaneous arrival and resource constraint for multi-UAV using a genetic algorithm", *Expert Systems with Applications* 245:123023, 2024. 다UAV-다표적 공격의 **할당+경로 결합** 문제에 자원요구와 **동시 도착** 제약을 넣었다. 맞춤 교차·변이 연산자로 제약을 보장하고, 여러 UAV가 무한 대기하는 chromosome deadlock을 unlocking 전략으로 막는다. Monte Carlo로 기존 방법 대비 우위를 보였다 — [DOI 10.1016/j.eswa.2023.123023](https://doi.org/10.1016/j.eswa.2023.123023)
- Shahid, Zhen, Javaid, "Cooperative task assignment of heterogeneous unmanned aerial vehicles for simultaneous multi-directional attack on a moving target", *Engineering Applications of AI* 139:109595, 2025. 이동 고가치표적에 대한 **다방향 동시공격** 위치 할당이다. 각 UAV가 속도제약으로 도달 가능한 공격점과 도착시간을 계산하고, **동시공격 시각에 대한 합의(consensus)** 후 확장 contract net(ECNP)으로 공격점을 할당한다. CNP·GA 대비 자원 균등배분과 임무달성에서 우위였다 — [DOI 10.1016/j.engappai.2024.109595](https://doi.org/10.1016/j.engappai.2024.109595)
- Wang, Liang, Li, Hou, Yang, "Joint Planning Method for Cross-Domain Unmanned Swarm Target Assignment and Mission Trajectory", *Journal of Systems Engineering and Electronics* 36(3):736–753, 2025. 이종 cross-domain 군집에서 할당 단계에 궤적을 초기 계획하고 이후 궤적을 최적화하는 결합 프레임이다. EDA+GA 하이브리드가 GA·EDA 단독보다 나았다 — [DOI 10.23919/jsee.2025.000073](https://doi.org/10.23919/jsee.2025.000073)
- Alqudsi, "Integrated Optimization of Simultaneous Target Assignment and Path Planning for Aerial Robot Swarm", *The Journal of Supercomputing* 81(1):95, 2025(온라인 2024-10). 지역 상호작용 기반 SAPP로 할당과 동역학적으로 실현 가능한 충돌회피 경로를 동시에 만들고, 다단계 재할당을 다룬다 — [DOI 10.1007/s11227-024-06620-w](https://doi.org/10.1007/s11227-024-06620-w)
- Xia(Chen Xia), Liu, Yin, Qi, "Cooperative Task Assignment and Track Planning For Multi-UAV Attack Mobile Targets", *Journal of Intelligent & Robotic Systems* 100(3–4):1383–1400, 2020. PSO 할당, 적응형 양방향 ACO 항적, 이동표적 예측 조우점, 시간민감 불확실성에 대한 온라인 재계획을 결합했다 — [DOI 10.1007/s10846-020-01241-w](https://doi.org/10.1007/s10846-020-01241-w)
- Zheng et al. 2026(Q1 참조): **bilevel**(상위 할당 min-max 완료시간, 하위 최소시간 최적제어)을 DR chance constraint와 결합했다 — [DOI 10.3390/math14173044](https://doi.org/10.3390/math14173044)
- Liles et al. 2023(Q1 참조): tasking+routing을 **MDP/ADP**로 다룬 방어측 사례 — [DOI 10.1016/j.ejor.2022.06.031](https://doi.org/10.1016/j.ejor.2022.06.031)

**(2) 방어측 유한 교전능력(교전창·발사간격·SLS)과 결합된 할당·스케줄링**
- [앵커] Karasakal, "Air defense missile-target allocation models for a naval task group", *Computers & Operations Research* 35(6):1759–1770, 2008. 함정 기동부대 SAM 할당을 SLS 교전정책 하에서 2개의 정수선형모형으로 세웠다. 대형 인스턴스도 수 초 내 최적해를 얻었다 — [DOI 10.1016/j.cor.2006.09.011](https://doi.org/10.1016/j.cor.2006.09.011)
- [앵커] Karasakal, Özdemirel, Kandiller, "Anti-ship missile defense for a naval task group", *Naval Research Logistics* 58(3):304–321, 2011. 다종 SAM·ASM에서 SAM 할당과 **SLS 발사 스케줄링**을 결합한 MAP를 정식화하고, 반복 시나리오 분석용 효율적 휴리스틱을 제시했다 — [DOI 10.1002/nav.20457](https://doi.org/10.1002/nav.20457)
- Park & Choi, "Weapon-Target Assignment and Firing Scheduling for Rapid Engagement with Heterogeneous Interceptors", *International Journal of Aeronautical and Space Sciences* 24(3):890–904, 2023. 대함미사일을 상대하는 함대 이종 방어무기의 WTA와 사격순서를 결합했다. 무기 비행시간, **발사간격 제한**, 표적 기하를 반영한 MINLP를 piecewise linear 근사와 McCormick 완화로 MILP 근사했고, 현실 규모용 greedy를 함께 제시했다 — [DOI 10.1007/s42405-023-00572-w](https://doi.org/10.1007/s42405-023-00572-w)
- Cao & Fang, "Swarm Intelligence Algorithms for Weapon-Target Assignment in a Multilayer Defense Scenario: A Comparative Study", *Symmetry* 12(5):824, 2020. **다층방어** WTA에서 ACO, BPSO, IPSO, SCA를 비교했고 IPSO가 품질·강건성·속도에서 우세했다(대규모 WTA 적용) — [DOI 10.3390/sym12050824](https://doi.org/10.3390/sym12050824)
- Zhong & Zhang, "The combat application of queuing theory model in formation ship to air missile air defense operations", *Journal of Physics: Conference Series* 1570:012083, 2020. 편대 함대공 방어를 대기행렬 서비스 모형(단일·다종 SAM)으로 보고 화력 최적화와 효과도 평가 모형을 세웠다(저등급 학술대회, 참고 수준) — [DOI 10.1088/1742-6596/1570/1/012083](https://doi.org/10.1088/1742-6596/1570/1/012083)

**(3) USV/UUV 특화**
- Gao, Gao, Zhou, Ma, "Artificial intelligence algorithms in unmanned surface vessel task assignment and path planning: A survey", *Swarm and Evolutionary Computation* 86:101505, 2024. 단일·다수 USV 할당·경로계획 AI 기법, 해양 외부 제약·외란, 장애물 회피, 군사 응용을 정리한 서베이 — [DOI 10.1016/j.swevo.2024.101505](https://doi.org/10.1016/j.swevo.2024.101505)
- Hu, Zhang, Luo, Chen, "Dynamic Target Assignment by Unmanned Surface Vehicles Based on Reinforcement Learning", *Mathematics* 12(16):2557, 2024. 이동표적에 대한 다USV 동적 표적할당을 MARL(우선 경험재생, self-attention)로 풀었다. **타격 위치·시간**의 수리모형을 포함한다. 대규모에서 GA 대비 해 품질 ≥30% 향상, 평균 해산출 시간은 GA의 10% 미만이었다 — [DOI 10.3390/math12162557](https://doi.org/10.3390/math12162557)
- Zhou, Li, Hao, "A Novel Region-Construction Method for Multi-USV Cooperative Target Allocation in Air–Ocean Integrated Environments", *Journal of Marine Science and Engineering* 11(7):1369, 2023. 도서 방어 순찰 USV의 실시간 목표위치 할당이다. 시간요인을 넣은 MBM, 동적 K 군집, 비완전그래프 ACO를 썼다. USV 4/6/8/10대에서 MBM 대비 평균 도달시간을 10.9/25/25.7/20% 단축했다 — [DOI 10.3390/jmse11071369](https://doi.org/10.3390/jmse11071369)
- Xia, Luo, Liu, Zhang, Shi, Liu, "Cooperative multi-target hunting by unmanned surface vehicles based on multi-agent reinforcement learning", *Defence Technology* 29:80–94, 2023. USV 다표적 포위(hunting)를 Dec-POMDP로 두고 CTDE의 DPOMH-PPO를 적용했다. 피해 후 자기조직화 능력도 분석했다 — [DOI 10.1016/j.dt.2022.09.014](https://doi.org/10.1016/j.dt.2022.09.014)
- Hamid & Saleh, "ETA-Hysteresis-Based Reinforcement Learning for Continuous Multi-Target Hunting of Swarm USVs", *Applied System Innovation* 9(1):7, 2026. 도착예상시간(ETA) 기반 방어자-표적 쌍 선택에 **이중 임계 hysteresis**를 넣어 재할당 진동을 억제하고 RL과 결합한다. 3D 수중·수상 시뮬레이션에서 기준선 대비 수렴 속도 +20–30%, 요격률 +9.5–20.9%, 평균 포획시간 −9.4–19.0%를 보고한다. ETA를 할당 기준으로 쓰지만 **도착시각을 동기화하는 결정변수가 아니며** 방어측 교전능력 모델도 초록에 없다. 재할당 안정성(T1/T2 관련) 참고용 — [KFUPM Pure](https://pure.kfupm.edu.sa/en/publications/eta-hysteresis-based-reinforcement-learning-for-continuous-multi-/), [DOI 10.3390/asi9010007](https://doi.org/10.3390/asi9010007) (노트 02·07에도 항목 있음)
- Chen, Liu, Yu, Yang, Guo, "Task Allocation and Saturation Attack Approach for Unmanned Underwater Vehicles", *Drones* 9(2):115, 2025. 적 밀도 기반 구역분할, 구역가치·공격능력 기반 할당(Logistic chaos와 DE를 넣은 개선 GWO), 최적매칭과 Bezier 경로로 포위 후 **포화공격**을 수행한다(UUV, 방어측 교전능력 모형은 초록상 없음) — [DOI 10.3390/drones9020115](https://doi.org/10.3390/drones9020115)
- Ren, Zhang, Gao, Suganthan, Pan, "Environment-Aware Task Allocation and Path Planning for Multi-USV in Ocean Environment", *Expert Systems with Applications* 328:132844, 2026 — [DOI 10.1016/j.eswa.2026.132844](https://doi.org/10.1016/j.eswa.2026.132844) **[초록 미열람, 확인 필요]**: 저자(Ranzhen Ren, Lichuan Zhang, Ruobin Gao, P. N. Suganthan, Guang Pan), ESWA 328, 2026-10 서지는 Crossref 레코드로 재확인했다([Crossref](https://api.crossref.org/works/10.1016/j.eswa.2026.132844)). 초록 필드가 비어 있어 제목상 해양환경을 고려한 할당+경로 결합이라는 것만 알 수 있다. 해상상태(sea state)와 속도 제약을 포함하는지는 미확인.
- Zhu, Qiao, Gong, Cai, "Prediction-driven distributed cooperative interception for multi-unmanned surface vehicles via spatio-temporal fusion", *Ocean Engineering* 363:126614, 2026 — [DOI 10.1016/j.oceaneng.2026.126614](https://doi.org/10.1016/j.oceaneng.2026.126614) **[초록 미열람, 확인 필요]** (저자 Yuxuan Zhu, Renjie Qiao, Xiaopeng Gong, Chengtao Cai와 Ocean Engineering 363, 2026-08 서지는 [Crossref](https://api.crossref.org/works/10.1016/j.oceaneng.2026.126614)로 재확인, 초록 없음)
- Chen, Sun, Jiang, Xu, Gao, "Configuration strategy for unmanned surface vehicle coordinated defense system based on particle swarm optimization", *Ships and Offshore Structures*, 2026(온라인 2026-08-19), pp.1–19 — [DOI 10.1080/17445302.2026.2717424](https://doi.org/10.1080/17445302.2026.2717424) **[초록 미열람, 확인 필요]**
- USV 협조 경로추종(시간 협조 제어 계보) 예: Li, Guo, Yu, "Global finite-time control for coordinated path following of multiple underactuated unmanned surface vehicles along one curve under directed topologies", *Ocean Engineering* 237:109608, 2021 — [Crossref 서지 확인, DOI 10.1016/j.oceaneng.2021.109608](https://doi.org/10.1016/j.oceaneng.2021.109608) **[초록 미열람]**. 제어 계보(유한시간 합의 기반 협조 경로추종)는 존재하지만 할당과 결합된 형태는 확인하지 못했다.

### Inferences
- 정식화 유형별 사례: (i) GA/EDA 기반 결합 탐색(Yan 2024, Wang 2025), (ii) 합의 후 시장기반 할당(Shahid 2025), (iii) bilevel(할당 상위, 최적제어 하위; Zheng 2026), (iv) MDP/ADP(Liles 2023), (v) MINLP→MILP 근사(Park & Choi 2023, 방어측). "동시도착"은 거의 모두 **표적에 동시에 닿는다**는 기하·시간 제약으로만 쓰이고, 왜 동시도착이 유리한지(방어 채널 포화)를 목적함수에 내생화한 사례는 열람 범위에서 없었다. Hughes(1995)의 subtractive defense 가정 3(포화 전 leaker 0, 포화 후 전부 명중)이 정확히 그 내생화 근거다(Q3).
- 방어측 계보(Karasakal 2008/2011, Park & Choi 2023)는 발사간격·SLS·교전창을 MILP로 다룰 수 있게 해 두었다. 따라서 T3는 이를 **추종자(follower) 문제**로 넣는 bilevel 또는 Stackelberg 정식화(상위: 공격측 할당+도착시각, 하위: 방어측 Karasakal형 SAM 할당·스케줄링)로 세울 수 있다. 이것이 선행연구 (b)의 MRCPSPTW(공격측 time window만 존재)와 문제 정의상 가장 명확히 갈라지는 지점이다.
- USV 계보는 순찰·감시·포위(hunting)·이동표적 타격시간(Hu 2024) 수준이다. 방어측 교전능력, 해상상태별 속도, 동시도착을 함께 다룬 USV 공격 할당은 이번 검색 범위에서 0건이었다.

### Gaps
- Volle & Rogers(2018)의 해법과 규모: AIAA ARC 403, Georgia Tech 저장소 403이었고, 이번 재시도의 Crossref 레코드도 초록이 비어 있어 여전히 미열람 [확인 필요].
- Ren et al.(2026 ESWA), Zhu et al.(2026 Ocean Eng), Chen et al.(2026 SOS)의 USV 관련 내용 미열람 [확인 필요]. Ren·Zhu는 Crossref 서지만 재확인했고 초록 필드가 비어 있다. 특히 Ren 2026이 해상환경 인지 할당이므로 T3의 가장 가까운 선행연구일 수 있어 원문 확보가 최우선이다.
- 미사일 협동유도(impact-time control, 동시명중 유도법칙) 계보는 범위 확인만 하고(검색 결과 목록) 개별 논문을 열지 않았다.

---

## Q3. 연구 시뮬레이터에 쓸 수 있는 방어측 모델: Hughes salvo, 확률적 확장(Armstrong), 교전율·탄창, raid 크기별 leaker 확률, 기만체 효과 (공개 학술출처와 파라미터)

### Takeaway
Hughes(1995)의 결정론 salvo 방정식과 Armstrong(2005)의 확률적 salvo 모델(SSM: 공격·요격을 binomial로, 피해를 normal로)이 공개 문헌에서 가장 재현하기 쉬운 방어측 모델이다. 파라미터 범위는 Kesler·Lucas·Sanchez(2019, NPS data farming, 14개 요인 범위표)와 Armstrong & Powell(2005, Coral Sea 역사 보정 파라미터)이 공개한다. 2025년 Atkinson & Kress(OR)는 hard interceptor와 soft measure(디코이·재밍·DEW)를 결합한 SLS 모형으로 **leaker 기대값 vs 요격탄 소모** frontier를 제시하고 파라미터(p = 0.7/0.9, K = 1–3, M = 100, W ~ U[10,20])를 공개했다. 이 셋을 조합하면 USV 군집 공격에 대한 다층·유한능력 방어측 모듈을 문헌 근거만으로 구성할 수 있다.

### Cited Findings

**(1) Hughes 결정론 salvo 모델 [앵커]**
- Hughes, "A Salvo Model of Warships in Missile Combat Used to Evaluate Their Staying Power", *Naval Research Logistics* 42:267–289, 1995(NPS Calhoun 공개, hdl 10945/60793). 기본식은 ΔB = (αA − b₃B)/b₁, ΔA = (βB − a₃A)/a₁이다. α, β는 단위당 well-aimed 발사수, a₃, b₃는 단위당 요격수(defensive power), a₁, b₁은 firepower kill에 필요한 명중수(staying power)이다. MOE는 fractional exchange ratio(FER) — [NPS Calhoun PDF](https://calhoun.nps.edu/server/api/core/bitstreams/f6c38a6c-d56e-4dab-b045-8284411f8672/content)
- Hughes(1995)의 핵심 가정: (2) 좋은 사격은 모든 표적에 **균등 분산**된다. 저자 스스로 이것이 최적은 아니며 일부 표적 집중이 유리할 수 있다고 밝힌다. (3) 방어 counterfire는 **방어가 포화될 때까지 leaker 없이** good shot을 제거하고, 포화 후 모든 good shot이 명중한다(subtractive process). leaker 비율을 넣는 수정이 가능하다고 언급한다. (4) staying power는 침몰이 아니라 firepower kill 기준이다(침몰에는 2–4배 필요). (6) 양측 사거리 충분(정찰우위 없음) — [NPS Calhoun PDF](https://calhoun.nps.edu/server/api/core/bitstreams/f6c38a6c-d56e-4dab-b045-8284411f8672/content)
- Hughes의 결론: 전투력이 생존성에 비해 커질수록 불안정해지고, 약한 staying power가 불안정의 근본 원인이다. **수적 우세가 가장 일관되게 유리**하다. A의 타격력·staying power·방어력이 모두 B의 2배여도 B가 2배 수량이면 동등 결과가 나온다 — [NPS Calhoun PDF](https://calhoun.nps.edu/server/api/core/bitstreams/f6c38a6c-d56e-4dab-b045-8284411f8672/content)

**(2) Armstrong 확률적 salvo 모델과 후속**
- [앵커] Armstrong, "A Stochastic Salvo Model for Naval Surface Combat", *Operations Research* 53(5):830–841, 2005 — [DOI 10.1287/opre.1040.0195](https://doi.org/10.1287/opre.1040.0195) (서지는 Crossref, 내용은 아래 Kesler et al. 2019의 서술로 확인; 원문 미열람)
- Kesler et al.(2019)이 정리한 SSM: 각 ASM과 SAM을 Bernoulli로 두어 공격 명중 가능수 N_o와 최대 요격수 N_d는 binomial이고, **명중수 = max(N_o − N_d, 0)**이다. 명중당 피해(함정의 비율 손실)는 normal이다. Armstrong은 binomial의 정규근사로 손실의 평균·분산·전멸확률을 닫힌형으로 근사했다 — [Kesler, Lucas, Sanchez, WSC 2019 PDF](https://www.informs-sim.org/wsc19papers/238.pdf)
- Armstrong(2011)의 검증(Kesler et al. 2019 인용): 486개 시나리오(함정수 6수준 × 공격성공확률 3 × 요격성공확률 3 × 피해함수 3 × 상관 3), 각 50,000회 시뮬레이션. 닫힌형 근사는 대체로 양호하지만 **공격 명중의 양(+)의 상관이 클 때** 성능이 떨어진다 — [WSC 2019 PDF](https://www.informs-sim.org/wsc19papers/238.pdf); 원 논문: Armstrong, "A verification study of the stochastic salvo combat model", *Annals of Operations Research* 186(1):23–38, 2011, [DOI 10.1007/s10479-011-0889-0](https://doi.org/10.1007/s10479-011-0889-0) (Crossref 서지 확인, 원문 미열람)
- Armstrong, "The salvo combat model with area fire", *Naval Research Logistics* 60(8):652–660, 2013. 한쪽 또는 양쪽이 area fire를 쓰는 salvo 모델이다. aimed fire는 상대 규모가 중요하고 square law를 따르지만, area fire는 **절대 규모**가 중요하고 근사적으로 linear law를 따른다. 혼합 시 두 법칙이 섞인다 — [DOI 10.1002/nav.21559](https://doi.org/10.1002/nav.21559)
- Armstrong, "The salvo combat model with a sequential exchange of fire", *Journal of the Operational Research Society* 65(10):1593–1601, 2014 — [DOI 10.1057/jors.2013.115](https://doi.org/10.1057/jors.2013.115) **[초록 미열람]**
- Armstrong, "Effective attacks in the salvo combat model: Salvo sizes and quantities of targets", *Naval Research Logistics* 54:66–77, 2007 — [Wiley 초록 페이지(검색결과 목록)](https://onlinelibrary.wiley.com/doi/abs/10.1002/nav.20187) **[목록만 확인, 미열람]**
- 서지 불일치: "Effects of lethality in naval combat models", *NRL* 51(1):28–43의 연도가 Kesler et al.(2019) 참고문헌에는 2003, 웹검색 요약에는 2004로 나온다(NRL 51권은 2004년) [확인 필요] — [WSC 2019 PDF](https://www.informs-sim.org/wsc19papers/238.pdf)

**(3) 공개 파라미터 출처**
- Kesler, Lucas, Sanchez, "A Data Farming Analysis of a Simulation of Armstrong's Stochastic Salvo Model", *Proceedings of the 2019 Winter Simulation Conference*, pp.2443–2454. 14개 요인 범위는 다음과 같다. 초기 함정수 A, B ∈ [9, 18]; 함정당 salvo당 ASM 수 n_α, n_β ∈ [2, 4]; 단일 ASM 성공확률 p_α, p_β ∈ [0.5, 1.0]; 함정당 SAM 수 n_y, n_z ∈ [1, 2]; 단일 SAM 요격확률 p_y, p_z ∈ [0.5, 1.0]; 명중당 평균손실 u, v ∈ [0.25, 0.50]; 그 표준편차 ∈ [0.1, 0.2] — [WSC 2019 PDF](https://www.informs-sim.org/wsc19papers/238.pdf)
- 같은 논문의 실험 설계와 결과: mixed NOB 설계(SEED Center 512점을 회전·적층)로 **5,120 설계점 × 50,000 반복 = 2.56억 회 전투를 데스크톱에서 30분 미만**에 돌렸다(50,000 반복 < 1 s). ΔB의 10항 회귀 메타모델 R² = 0.903이다. ASM 1발/함/salvo 증가는 ΔB +2.8척, SAM 1발/함 증가는 −2.8척, p_α 0.1 증가는 약 +1척이다. 결론은 "attack effectively first"이고, 닫힌형 근사보다 직접 시뮬레이션을 권고한다 — [WSC 2019 PDF](https://www.informs-sim.org/wsc19papers/238.pdf)
- Armstrong & Powell, "A Stochastic Salvo Model Analysis of the Battle of the Coral Sea", *Military Operations Research* 10(4):27–37, 2005([DOI 10.5711/morj.10.4.27](https://doi.org/10.5711/morj.10.4.27); 열람본은 Carleton CSDS Working Paper 03). 역사 보정 파라미터(squadron 수준): USN/IJN 항모 2/2, 항모당 공격 비행대 3/2, 비행대 공격 성공확률 0.4762/0.6429, 전투기 비행대 1/1, 요격 성공확률 0.2857/0.4286, 명중 비행대당 평균손실 1 CV(SD 0.3333). 평균 손실은 1.55(USN)/1.45(IJN) CV이고 USN이 두 항모를 모두 잃을 확률은 54%이다. 항공기 수준 파라미터(공격기 47/33, 전투기 17/20.5, 전투기 요격확률 0.3529/0.04878 등)도 표로 제시한다 — [Carleton CSDS WP03 PDF](https://www3.carleton.ca/csds/docs/working_papers/ArmstrongWP03.pdf)

**(4) Leaker·교전능력·탄창·soft measure(디코이) 모델**
- Atkinson & Kress, "Hard and Soft Defense Against a Sequence of Aerial Threats", *Operations Research* 73:1767–1784, 2025. Blue는 M발 요격탄(단발 SSPK p, 독립)과 무한 자원으로 가정한 SM을 가진다. 위협 W발이 하나씩 온다. 위협마다 K개의 salvo engagement opportunity(SEO)가 있고 각 SEO 후 BDA가 있다. HD의 BDA는 완벽하고, SM은 kill을 놓치는 false-negative만 있다. MOE는 (기대 leaker 수, 기대 요격탄 소모) — [저자 게재승인본](https://faculty.nps.edu/mkress/docs/salvo_paper_FINAL.pdf), [DOI 10.1287/opre.2024.1025](https://doi.org/10.1287/opre.2024.1025)
- 같은 논문의 공개 파라미터: p는 비관 0.7, 낙관 0.9(요격탄 성공률은 대개 80% 이상이라는 문헌 인용). 단·중거리 위협의 K는 1–3. 초기 재고 M = 100(미 해군 수상함 전형 탑재량, Stöhs 2021 인용). W ~ U[10, 20](실제 시간창 내 위협은 대개 10발 미만이라는 근거로 small-W 집중). 위협당 발사 상한 N은 1–5(p = 0.7, N = 5이면 단일위협 격추확률 0.998) — [저자 게재승인본](https://faculty.nps.edu/mkress/docs/salvo_paper_FINAL.pdf)
- 같은 논문의 결과: 재고를 고갈시키는 large-W에서는 **위협당 1발/salvo**가 효율적이다(Thm 3). small-W이고 p가 충분히 크면 첫 K−1개 SEO에 1발씩, 마지막 SEO에 나머지를 쏜다(Thm 7). BDA 1회(K = 2)에는 투자 가치가 있지만 그 이상은 비용효과가 낮을 수 있다. SM이 있으면 요격탄이 뒤 SEO로 이동한다. 한계로는 **raid(동시 다발) 시 동시 발사능력 제약**을 미반영했다고 명시하고, 다종 위협 raid와 다종 요격탄은 시뮬레이션과 WTA가 필요한 향후과제로 남겼다 — [저자 게재승인본](https://faculty.nps.edu/mkress/docs/salvo_paper_FINAL.pdf)
- 같은 논문의 문헌 정리: 공격측 penetration aid(디코이·채프·재밍)로 방어효과를 낮추는 OR 연구 계보(Gramann 1963, Wilkening 2000, Zhai 2016), 디코이 UAV 시뮬레이션(Carr 2016), Maskery 2007 게임이론 분산 미사일방어 등을 열거한다(2차 인용, 원문 미열람) — [저자 게재승인본](https://faculty.nps.edu/mkress/docs/salvo_paper_FINAL.pdf)
- 탄창·순차 교전: Kalyanam & Clarkson(2021, NRL)은 재고·시간에 대한 salvo 크기 단조성을 증명했고([DOI 10.1002/nav.21967](https://doi.org/10.1002/nav.21967)), Davis 2017(EJOR)과 Summers 2020(C&OR)은 재고 상태를 포함한 MDP/ADP 사격정책을 다뤘다(Q1 참조).
- 교전능력 스케일링: Chen et al.(arXiv 2607.13648)은 교전능력(effector capacity)이 위협 수에 선형 비례하는 체제와 저능력 체제를 구분해 fair allocation의 최적성·근최적성을 보였다 — [arXiv 2607.13648](https://arxiv.org/abs/2607.13648)

**(5) 공격측(공격 군집) 생존성 모델링**
- Hughes(1995)는 생존성을 staying power(firepower kill에 필요한 명중수)로 두고, 공격측 손실 ΔA = (βB − a₃A)/a₁로 상대 반격에 의한 손실을 계산한다 — [NPS Calhoun PDF](https://calhoun.nps.edu/server/api/core/bitstreams/f6c38a6c-d56e-4dab-b045-8284411f8672/content)
- Armstrong SSM은 손실을 확률분포(평균·분산·전멸확률)로 준다. Kesler et al.의 FER 메타모델에서는 초기 force ratio가 가장 강한 비선형 예측변수였다(logit FER, R² 0.90) — [WSC 2019 PDF](https://www.informs-sim.org/wsc19papers/238.pdf)

### Inferences
- **leaker 확률 vs raid 크기(추론, 출처 모형에서 유도)**: Armstrong SSM에서 raid의 good shot 수 N_o ~ Bin(n_α·A, p_α), 방어 요격 가능수 N_d ~ Bin(n_z·B, p_z)이면 P(leaker ≥ 1) = P(N_o > N_d)이고 기대 leaker = E[max(N_o − N_d, 0)]이다. raid 크기(n_α·A)가 방어 채널 용량(n_z·B)을 넘는 순간 기대 leaker가 거의 선형으로 늘어나는 "포화 꺾임"이 생기며, Hughes 결정론 모형에서는 이것이 정확한 꺾인 직선이다. 이 수식은 위 출처의 정의를 조합한 것으로, 별도 논문에서 확인한 결과는 아니다.
- **동시도착의 가치(추론)**: Hughes 가정 3과 SSM의 max(N_o − N_d, 0) 구조는 방어측 요격능력이 **salvo당(=시간창당) 상한**을 갖는다는 뜻이다. 공격측 USV의 도착시각을 같은 시간창에 몰면 N_o가 한 창 안에 집중되어 leaker가 늘고, 분산 도착이면 방어측이 창마다 n_z·B를 재사용한다. 이 효과를 정량화하려면 SEO 수 K(Atkinson & Kress)와 발사간격(Park & Choi 2023)을 시간창 용량으로 쓰면 된다.
- **디코이 효과(추론)**: Hughes 가정 2(사격의 균등분산)에서 방어측이 디코이를 실제 표적과 구별하지 못하면 디코이 수만큼 분모가 커진다. 공격측 good shot이 실제 표적에 덜 배분되는 것이므로 디코이는 사실상 α를 희석하는 효과를 낸다. 공격측(USV) 관점에서 적 디코이에 대한 오식별 확률 q가 있으면 유효 α' = α·(1 − q)로 근사할 수 있다. Atkinson & Kress는 방어측 SM의 BDA 오류로 디코이를 다루므로, 공격측 할당에서 디코이를 다루는 정식화는 별도로 세워야 한다.
- 시뮬레이터 구성 권고(문헌 기반): (i) 방어측 각 함정에 Kesler 범위의 n_z ∈ [1, 2]/salvo, p_z ∈ [0.5, 1.0], (ii) 교전창 K ∈ {1, 2, 3}과 재고 M(Atkinson & Kress), (iii) 다층 방어는 Cao & Fang(2020) 다층 WTA 또는 Karasakal(2011) SLS 스케줄링을 하위 문제로 둔다. 이렇게 하면 "공개 파라미터만으로 재현 가능한 방어측 모델"이라는 검증·재현성 논거가 생긴다.

### Gaps
- USV·소형 고속정 군집 대상으로 salvo 모델을 보정한 공개 학술 파라미터는 찾지 못했다. Kesler와 Armstrong은 함대 대 함대 ASM/SAM 또는 1942년 항공 데이터다.
- raid 크기별 leaker 확률을 실측·시험 데이터로 제시한 공개 학술원은 찾지 못했다(위 수식은 모형 유도).
- Kesler(2019) NPS 석사논문 "A Data Farming Analysis of Multiple Salvo Equations"와 DTIC의 NPS 해상 드론 군집 대 함정 레이저(LWS) 교전 학위논문(AD1165019)은 열람 실패(DTIC 403)로 내용을 검증하지 못했다 [확인 필요].
- 2020–2026년에 salvo 모델을 군집 무인체로 확장한 동료심사 논문은 이번 검색(Crossref "salvo combat model" 등)에서 찾지 못했다. Whitehall Papers 100(2022)의 "Appendix 1: Salvo Combat Models for Surface Warfare"([DOI 10.1080/02681307.2022.2030972](https://doi.org/10.1080/02681307.2022.2030972))는 서지만 확인했다.

---

## Q4. 다목적 할당: NSGA-II/III·MOEA/D·MOPSO(Kong·Wang·Zhao 2021 포함)와 학습 기반 다목적 접근, 자군 생존성을 목적에 넣는 방식

### Takeaway
다목적 WTA는 "기대 피해(효과) 최대화 vs 탄약 비용 최소화"의 2목적이 표준이다. 그 위에 (i) 자군 전투가치/전투력 손실(fighter combat value, damage value of fighting capacity), (ii) CVaR 위험, (iii) 신뢰도(reliability), (iv) leaker vs 요격탄 소모(방어측) 같은 제3목적이 더해진다. 해법은 NSGA-II/III, MOEA/D 변형, MOPSO가 주류이다. 학습 기반 다목적 WTA는 DQN으로 진화연산 연산자를 고르는 하이브리드 수준이고, preference-conditioned MORL로 Pareto front 전체를 학습한 WTA 논문은 찾지 못했다. 생존성은 공중전(전투기) 맥락의 자군 피해기대값으로만 들어가 있고 USV 군집의 손실을 목적에 넣은 사례는 없었다.

### Cited Findings
- Kong, Wang, Zhao, "Solving the Dynamic Weapon Target Assignment Problem by an Improved Multiobjective Particle Swarm Optimization Algorithm", *Applied Sciences* 11(19):9254, 2021. DWTA를 **전투이득 최대화 vs 무기비용 최소화**의 2목적으로 두고 자원·실현가능성·화력이전(fire transfer) 제약을 넣었다. IMOPSO는 지배/비지배 해별 학습전략, SBX와 polynomial mutation 기반 탐색, 동적 아카이브 유지를 쓴다. 3개 최신 MOEA 대비 수렴성과 분포에서 우위였다 — [DOI 10.3390/app11199254](https://doi.org/10.3390/app11199254)
- [앵커] Li, Kou, Li, "An Improved Nondominated Sorting Genetic Algorithm III Method for Solving Multiobjective Weapon-Target Assignment Part I: The Value of Fighter Combat", *International Journal of Aerospace Engineering* 2018:8302324(pp.1–23). 기존 2목적에 **자군 전투기 전투가치 최대화**를 제3목적으로 넣었다(적 기대피해 최대, 미사일 비용 최소, 전투기 전투가치 최대). 적응형 참조점과 온라인 연산자 선택을 갖춘 NSGA-III가 NSGA-II·MPACO보다 나았다 — [DOI 10.1155/2018/8302324](https://doi.org/10.1155/2018/8302324)
- [앵커] Gao, Kou, Li, Li, Xu, "Multi-Objective Weapon Target Assignment Based on D-NSGA-III-A", *IEEE Access* 7:50240–50254, 2019. 양측 게임 과정을 넣은 3목적(적 피해, 미사일 비용, **자군 전투력 피해값**)이다. 지배도 행렬 비지배정렬, niching과 지배비, 적응형 연산자 선택을 쓴다. NSGA-III, MP-ACO, NSGA-II, MOPSO, MOEA/D, DMOEA-εC보다 나았다 — [DOI 10.1109/access.2019.2910241](https://doi.org/10.1109/access.2019.2910241)
- Wu, Chen, Ding, "A Modified MOEA/D Algorithm for Solving Bi-Objective Multi-Stage Weapon-Target Assignment Problem", *IEEE Access* 9:71832–71848, 2021. 다단계 2목적 WTA를 MOEA/D-NRSA(niche, 목적공간 군집별 적응 aggregation)로 풀어 의사결정자 선호별 해를 제공한다 — [DOI 10.1109/access.2021.3079152](https://doi.org/10.1109/access.2021.3079152)
- [앵커] Li et al. 2016 CEC: 불확실 다단계 WTA의 2목적(피해 vs 탄약) MOEA/D-AWA + Max-Min robust (상세는 Q1) — [HIT 연구자 페이지](https://hit.globalimpact.cn/en/publications/solving-the-uncertain-multi-objective-multi-stage-weapon-target-a/)
- Li, Xin, Pardalos, Chen 2021(Annals OR): **CVaR 위험 vs 자원비용** 2목적, MOEA/D-AWA와 DMOEA-εC(ε-constraint 프레임 우세) — [IDEAS](https://ideas.repec.org/a/spr/annopr/v296y2021i1d10.1007_s10479-019-03435-4.html)
- Yi, Yu, Xu, "Solving multi-objective weapon-target assignment considering reliability by improved MOEA/D-AM2M", *Neurocomputing* 563:126906, 2024. 무기 신뢰도와 임무 신뢰도를 다목적 모형에 넣고, MOEA/D-AM2M과 HLMEA를 결합하고 참조점 기반 적응 가중치를 쓴 MOEA/D-iAM2M을 제안했다 — [DOI 10.1016/j.neucom.2023.126906](https://doi.org/10.1016/j.neucom.2023.126906)
- Wang, Xin, Wang, Zhang, Deng, Wang, "Constraint-Feature-Guided Evolutionary Algorithms for Multi-Objective Multi-Stage Weapon-Target Assignment Problems", *Journal of Systems Science and Complexity* 38(3):972–999, 2025. 제약 다목적 다단계 WTA(CMOMWTA)에 대해 NSGA-II, NSGA-III, MOEA/D 기반 CFG-MOEA 3종을 만들었다. 선형제약의 행·열 공통특징 기반 재생산·수리, 가변길이 정수 인코딩, 휴리스틱+무작위 혼합 초기화를 쓴다. **CFG-NSGA-II**가 최우수였다 — [DOI 10.1007/s11424-025-4232-2](https://doi.org/10.1007/s11424-025-4232-2)
- Atkinson & Kress 2025(OR): 방어측 2목적(기대 leaker vs 기대 요격탄)의 efficient frontier를 해석적으로 구성했다. "Pareto 대상 지표" 설계의 OR 앵커 — [저자 게재승인본](https://faculty.nps.edu/mkress/docs/salvo_paper_FINAL.pdf)
- 학습 기반: Li, He, Xu, Zhao, Song, Li, "Weapon-Target Assignment Strategy in Joint Combat Decision-Making Based on Multi-Head Deep Reinforcement Learning", *IEEE Access* 11:113740–113751, 2023. 동적 WTA를 정적 WTA로 이산화한 MDP에서 multi-head Q-network로 결합 행동공간을 분해하고, **masking**으로 제약 만족 행동만 추론한다. 단일 목적이며 대·소규모에서 적응성과 연산효율을 보였다 — [DOI 10.1109/access.2023.3324193](https://doi.org/10.1109/access.2023.3324193)
- 학습 기반 다목적 하이브리드: Wang, Fu, Wei, Zhou, Gao, "Unmanned ground weapon target assignment based on deep Q-learning network with an improved multi-objective artificial bee colony algorithm", *EAAI* 117:105612, 2023 — [DOI 10.1016/j.engappai.2022.105612](https://doi.org/10.1016/j.engappai.2022.105612) (Crossref 서지만 이번 세션에서 확인. 내용은 기존 노트 01 참조)
- 다목적 공방(空防) ABC: Xing & Xing, "An Air Defense Weapon Target Assignment Method Based on Multi-Objective Artificial Bee Colony Algorithm", *Computers, Materials & Continua* 76:2685–2705, 2023 — [DOI 10.32604/cmc.2023.036223](https://doi.org/10.32604/cmc.2023.036223) **[초록 미열람]**

### Inferences
- 자군 생존성을 목적에 넣는 방식은 세 가지다: (a) 자군 전투가치/전투력 피해 기대값을 별도 목적으로 두기(Li 2018, Gao 2019; 적 반격을 게임으로 추정), (b) 위험척도(CVaR)로 실패 꼬리를 목적화하기(Li 2021), (c) 방어측 관점의 leaker 수(Atkinson & Kress)를 공격측 관점으로 뒤집어 **자군 손실 = 방어측 요격 성공 수**로 두기. USV 군집에서는 (c)가 Q3의 salvo 모듈과 바로 연결된다. 자군 손실 기대값 E[ΔA](Hughes/SSM)와 그 CVaR을 목적으로 쓰면 T2·T3의 교집합에서 차별화할 수 있다.
- 선행연구 (b)의 MAPPO는 단일 보상(Defense Success Rate)이다. T4/T5에서 다목적화한다면 preference-conditioned 정책(가중치 벡터를 관측에 넣음)을 써서 NSGA-II/MOEA/D 계보(Kong 2021, Wang 2025)와 hypervolume·IGD로 직접 비교하는 설계가 계보상 빈칸을 채운다. 다만 이번 검색에서 MORL-WTA 직접 선례는 0건이었으므로 "최초" 주장 전에 추가 확인이 필요하다.
- Na·Ahn·Moon(2026, JAIS, KAIST)은 이종 교전 time window를 가진 WTA를 계층 MARL(agent selector→target selector)로 풀었다. 선행연구 (b)(time window MRCPSPTW + MAPPO)와 문제 설정이 가깝고 국내 연구진이므로 심사자가 비교를 요구할 가능성이 높다. 후속연구에서는 인용과 차별점 표에 반드시 넣어야 한다.

### Gaps
- MOEA/D·NSGA 계보의 인스턴스 규모(무기×표적 수)와 연산시간은 초록에 거의 없다. 비교 실험 설계를 하려면 원문을 열람해야 한다(Kong 2021, Wang 2025 등) [확인 필요].
- 학습 기반 Pareto front 근사(MORL, preference-conditioned PPO 등)를 WTA에 적용한 동료심사 논문은 찾지 못했다. 2026-10-06 재검색("multi-objective reinforcement learning Pareto front weapon target assignment preference-conditioned")에서도 일반 MORL 논문과 정적 WTA의 MOPSO 논문만 검색되었고, MORL-WTA 직접 사례는 나오지 않았다. 일반 MORL 결과는 초록 미열람이므로 인용하지 않았다.
- 탄약·생존성·비용을 USV(무인정 손실비용 포함)로 명시한 다목적 할당 논문은 찾지 못했다.

---

## Q5. USV 군집에서 가장 얇은 계보와, 이를 신뢰성 있게 수행하는 데 필요한 데이터·모델

### Takeaway
세 계보 중 USV 군집에서 가장 얇은 것은 **(b) 할당 + 도착시각 협동 + 유한 교전능력 다층방어 + 해상상태/속도 제약(T3형)**이다. 이번 검색 범위에서 이 조합을 USV에 적용한 논문은 0건이었다. UAV에서는 동시도착 할당(Yan 2024, Shahid 2025, Volle 2018)과 방어측 교전 스케줄링(Karasakal, Park & Choi)이 각각 존재하지만 결합되지 않았다. 다음으로 얇은 것은 (a) DRO/CVaR + 오식별·디코이 + 재할당(T2형)이다. WTA-DRO는 0건이고 인접 UAV 과업할당에 2025–2026년 첫 사례가 나오기 시작했다. (c) 다목적 할당은 NSGA/MOEA/D/MOPSO 계보가 두껍고, USV 특화와 학습 기반 다목적만 비어 있다.

### Cited Findings
- USV 할당·경로 서베이(Gao et al. 2024)는 해양 외부 제약·외란을 별도 절로 다룬다. 그러나 열람한 초록 범위에서 전투 WTA와 방어측 교전능력 결합은 언급되지 않는다 — [DOI 10.1016/j.swevo.2024.101505](https://doi.org/10.1016/j.swevo.2024.101505)
- USV 공격·할당 계보의 실제 범위: 이동표적 타격 위치·시간 MARL(Hu 2024, [DOI 10.3390/math12162557](https://doi.org/10.3390/math12162557)), 순찰 목표할당(Zhou 2023, [DOI 10.3390/jmse11071369](https://doi.org/10.3390/jmse11071369)), 포위 MARL(Xia 2023, [DOI 10.1016/j.dt.2022.09.014](https://doi.org/10.1016/j.dt.2022.09.014)), 해양감시 robust 경로(He 2025, [DOI 10.1016/j.trb.2025.103284](https://doi.org/10.1016/j.trb.2025.103284)), 환경인지 할당·경로(Ren 2026, 초록 미열람, [DOI 10.1016/j.eswa.2026.132844](https://doi.org/10.1016/j.eswa.2026.132844)). 포화공격+할당은 UUV(Chen 2025, [DOI 10.3390/drones9020115](https://doi.org/10.3390/drones9020115))에만 있었다.
- 동시도착+할당은 UAV 대상(Yan 2024 [DOI](https://doi.org/10.1016/j.eswa.2023.123023); Shahid 2025 [DOI](https://doi.org/10.1016/j.engappai.2024.109595); Volle & Rogers 2018 [DOI](https://doi.org/10.2514/1.g003515))이고, 열람한 초록에는 방어측 유한 교전능력 모델이 없다.
- 방어측 유한 교전능력·SLS·발사간격 모델은 함정 방공 맥락(Karasakal 2008 [DOI](https://doi.org/10.1016/j.cor.2006.09.011), 2011 [DOI](https://doi.org/10.1002/nav.20457); Park & Choi 2023 [DOI](https://doi.org/10.1007/s42405-023-00572-w))과 사격이론(Atkinson & Kress 2025 [PDF](https://faculty.nps.edu/mkress/docs/salvo_paper_FINAL.pdf))에 있다. Atkinson & Kress는 raid 동시 발사능력 제약과 다종 위협 raid를 미해결 과제로 명시했다 — [저자 게재승인본](https://faculty.nps.edu/mkress/docs/salvo_paper_FINAL.pdf)
- DRO 할당은 UAV 응급대응(Zheng 2026, [DOI](https://doi.org/10.3390/math14173044)), budgeted robust는 UAV-USV 감시(He 2025)에만 확인됐다.

### Inferences
- **T3 신뢰성 확보에 필요한 데이터·모델(우선순위)**
  1. 방어측 교전능력 모듈: Hughes/Armstrong SSM(Kesler 범위표, Armstrong & Powell 보정 사례) + 시간창별 요격 상한(Atkinson & Kress의 K, M, p; Park & Choi의 발사간격) + 다층(장거리 SAM → 단거리 → CIWS/포)을 각 층의 (n, p, K)로 매개화. 모두 공개 학술 파라미터로 범위를 정하고 data farming(NOB 설계)으로 민감도를 보고한다(Kesler et al.의 방법론 차용).
  2. USV 운동·해상상태 모듈: 해상상태별 최대속도(속도손실) 곡선, 선회율, 파랑 중 무장 명중확률 저하 계수. 이번 검색에서 이를 정량화한 공개 학술 데이터는 찾지 못했다. 공개 함정 운동 문헌(seakeeping)이나 국내 무인수상정 해상시험 공개자료(기존 노트 03에 Sea State 4 해상시험 언급)로 범위를 정하고 민감도 분석으로 처리해야 한다.
  3. 탐지·식별 모듈: 소형 저RCS 수상표적의 레이더 탐지거리(해면 클러터, 수평선)와 디코이 오식별 확률 q. T2와 공유하며, 공개 근거가 약하므로 q를 실험요인으로 둔다.
  4. 도착시각 협동 모듈: 할당 후 속도조정형 TOA 합의(Shahid 2025형)와 결합 최적화(Yan 2024형) 둘 다 구현해, "합의 기반 분해 vs 결합 최적"을 비교 축으로 둔다.
- **선행연구 (a)–(d) 대비 차별화·자기표절 위험**: (b)는 MRCPSPTW(공격측 time window), 80 vs 80, DSR, MAPPO 구조이다. T3에서는 (i) 결정변수에 **도착시각/속도 프로파일** 추가, (ii) **방어측 교전능력 하위문제**(bilevel/Stackelberg), (iii) 해상상태 의존 속도·명중률, (iv) 평가지표를 DSR 대신 **기대 leaker 수/자군 손실/FER**로 바꾸면 문제 정의, 모델, 실험이 모두 달라진다. 80 vs 80 시나리오와 DSR 지표, 3계층 하이브리드 서술을 그대로 재사용하면 중복 게재 시비 위험이 있다. 시나리오 생성기·지표·베이스라인 세트를 새로 정의하고, 재사용하는 구성요소(예: GAT 인코더)는 (b)를 명시 인용해야 한다.
- **T2와 T3의 결합 가능성**: Q3의 SSM은 원래 확률모형이다(binomial 공격·요격, normal 피해). 그래서 T3의 방어측 모듈이 곧 T2의 불확실성 원천(p_α, p_z, 디코이 q의 분포 모호성)이 된다. "DRO/CVaR 목적 + 도착시각 결합 할당"은 두 빈칸을 한 번에 겨냥한다. 다만 범위가 넓어지므로 한 편의 논문에서는 T3를 주축으로 두고 위험척도는 CVaR 보고 수준으로 제한하는 편이 현실적이다(판단).

### Gaps
- USV(특히 전투용 고속 무인정) 해상상태별 속도·명중률 공개 학술 데이터: 발견 못함.
- 소형 수상표적 대상 함정 방어체계(CIWS, 함포, 단거리 SAM)의 교전 파라미터를 학술적으로 공개한 출처: 발견 못함. Kesler 범위는 ASM/SAM 함대전 기준이다.
- 2026-10-06 재검색("USV swarm saturation attack time-coordinated arrival target assignment defended ship")에서 새로 열람한 USV 문헌은 Hamid & Saleh(2026, ETA-hysteresis hunting)뿐이며, 방어측 교전능력·해상상태와 결합된 USV 공격 할당은 여전히 발견되지 않았다. 또한 중국어권 학술지 페이지(系统工程与电子技术 2023, 45(8))를 열려 했으나 요약 도구 오류로 열람에 실패해 검토하지 못했다 [확인 필요].
- Ren et al.(2026), Zhu et al.(2026), Chen et al.(2026) USV 논문의 내용 미열람으로, "USV 결합 계보 0건" 판단은 **초록 확인 범위 내** 결론이다 [확인 필요].
- 검색 도구 제약(OpenAlex·Semantic Scholar rate-limit, ScienceDirect·IEEE·AIAA 403)으로 중국어권 저널(兵工学报, 系统工程与电子技术 등)의 USV 협동공격 할당 문헌은 검토하지 못했다. 해당 계보가 존재할 가능성이 있어 원 연구자가 CNKI 검색으로 보완할 것을 권한다.
