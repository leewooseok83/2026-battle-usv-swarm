# 04. 프런티어 트렌드 2024–2026: LLM 기반 C2·계획, XAI, Human-on-the-loop 정책, 강건·불확실성 인지 최적화, Self-play·공진화, 디지털트윈·Sim-to-Real (군집 USV 무장할당 후속연구 관점)

작성 기준일: 2026-10-05. 아래 모든 인용은 실제로 열어 본 페이지(초록 페이지·DOI·PDF·기사)만을 대상으로 하였고, 열지 못한 항목은 [확인 필요] 또는 Gaps에 명시하였다. 2020년 이전 또는 2022년 이전 문헌은 "(anchor)"로 표시하였다. 본 노트의 마지막 절에서는 후보 주제 T1–T7을 문헌 대비로 판단한다. 리서치 과정의 제약: 세션 웹검색 예산이 중간에 소진되어 후반부는 arXiv API(export.arxiv.org) 질의와 직접 URL 열람으로 보완하였다. 따라서 Google Scholar·Scopus 기반의 체계적 검색은 수행되지 못했으며, 특히 국내 학술지(국방정책연구·국방연구·한국군사학논집)의 개별 논문은 KCI 검색 결과 목록 수준에서만 확인하였다.

---

## KQ1. 2024–2026년 LLM/파운데이션모델을 군사 COA 생성·전술계획·C2·'지휘관 의도→목적함수/제약' 변환에 사용한 연구·배치 사례와 그 비판

### Takeaway
LLM 기반 C2는 2024–2025년에 연구(COA-GPT, Mil-SCORE)에서 실제 획득(DIU Thunderforge, Palantir Maven/AIP)으로 이동했으나, 모든 공개 사례는 "항상 인간 감독 하(under human oversight)"의 참모 보조·COA 초안·워게임 역할에 한정되어 있다. 한편 2025년 11월에는 LLM이 직접 WTA 결정을 내리는 논문(Autenrieb & Ostermann)이 등장했고, 비군사 영역에서는 LLM이 보상함수·MILP 제약·PDDL 과업분해를 생성하는 "LLM-as-objective/constraint designer" 계열(Eureka, Text2Reward, OptiMUS, PIP-LLM, Peng et al.)이 성숙하여 T5(지휘관 의도 기반 WTA)로의 전이 근거가 충분하다. 동시에 LLM의 확전 편향·비일관성·IHL 위반율에 대한 실증 비판(Rivera et al., Schneider et al., Drinkall)이 축적되어, "LLM은 결정자가 아니라 목적함수·제약 설계자"로 위치시키는 프레이밍이 방어 가능한 설계 선택이다.

### Cited Findings

**(a) 배치·획득 사례**
- DIU는 2025-03-05 Scale AI에 Thunderforge 프로토타입 계약을 부여했다. 기능은 참모 계획 프로세스 자동화, 작전계획 초안 작성, 대안 COA에 대한 AI 워게임, 비정형 보고서 요약으로, Anduril Lattice와 Microsoft·Scale의 LLM을 결합하며 INDOPACOM·EUCOM에 우선 배치되고 CJADC2의 일부로 설명된다. 계약금액은 비공개. Scale은 "always under human oversight"를 강조했다 — [Breaking Defense 2025-03-05](https://breakingdefense.com/2025/03/ai-for-war-plans-pentagon-innovation-shop-taps-scale-ai-to-build-thunderforge-prototype/); [Scale AI 블로그 2025-03-05](https://scale.com/blog/thunderforge-ai-for-american-defense)
- Scale 블로그는 "custom agentic workflows (always under human oversight)"와 "critical human judgment"를 반복하며 정량 성과는 제시하지 않았다 — [Scale AI 블로그](https://scale.com/blog/thunderforge-ai-for-american-defense)
- Palantir Maven Smart System: 2023-05 미 육군이 Palantir를 유일 공급자로 인증(후속 계약 $12.98M, 선행 $91.2M). Palantir AIP가 LLM을 컴퓨터비전·"effects pairing"·시뮬레이션 등 군사 모델과 연결하는 구조로 설명되며, 유일 공급 사유는 "수십~수백 개의 추가 데이터 통합"이 필요한 연결성 요건이었다. 해당 1차 자료에는 시간당 표적 추천 수나 human-in-the-loop 절차는 기재되어 있지 않았다 — [Jack Poulson, Substack 2023-05-13](https://jackpoulson.substack.com/p/pentagon-certified-palantir-as-only). (검색 스니펫에 등장한 "Maven은 시간당 1,000건의 표적 추천 생성" 주장은 2차 자료이며 1차 출처를 열지 못함 — [확인 필요])
- 영국 Dstl 지원 Frazer-Nash 연구(2025-04-23): Command: Modern Operations(CMO) 워게임 출력에 대해 로컬 LLM+RAG로 질의·요약을 수행, "LLM이 복잡한 워게임 시나리오의 출력 정보를 유용하게 심문·전파할 수 있음"을 보였으나 로컬 LLM이 온라인 모델보다 약하고, LLM 생성 정보의 정확도·신뢰도를 정량화하는 프레임워크가 필요하다고 명시 — [Frazer-Nash 2025-04-23](https://editor.fnc.co.uk/discover-frazer-nash/news/how-large-language-models-could-change-the-game-in-battlefield-simulation/)
- DoD SBIR 토픽 OSW26BZ02-DV004 "Game-Theoretic AI for Robust COA Generation and Wargaming"(마감됨): 사전 레이블 데이터 없이 대규모 불완전정보 게임의 근사 Nash 균형을 계산하여 COA를 생성, 고충실도 시뮬레이션 내 self-play로 아군·적군 전략을 동시에 정련, "모듈형·해석가능 전략"을 요구하며 Phase II에 CPE·AFSIM 연동과 열화 조건 검증을 요구 — [SBIR 토픽 요약 페이지](https://www.bwcoconsulting.com/dod-sbirs/osw26bz02-dv004-game-theoretic-ai-for-robust-course-of-action-coa-generation-and-wargaming)
- CRS Insight IN12669(2026-03-13/04-21): 2026-02 대통령이 연방기관의 Anthropic 기술 사용 중단을 지시하고 국방장관이 Anthropic을 공급망 위험으로 지정. 쟁점은 DoD의 "all lawful purposes" 사용 요구에 대해 Anthropic이 "mass domestic surveillance and fully autonomous weapon systems" 두 용도를 거부하고 "frontier AI systems are simply not reliable enough to power fully autonomous weapons"라고 밝힌 것 — [CRS IN12669](https://www.everycrsreport.com/reports/IN12669.html)

**(b) 연구: LLM 기반 COA·전술계획**
- Goecks & Waytowich, "COA-GPT: Generative Pre-trained Transformers for Accelerated Course of Action Development in Military Operations", NATO STO ICMCIS 2024(Koblenz, 2024-04-23/24), arXiv:2402.01786. 교리 발췌를 in-context learning으로 주입, 텍스트·이미지 임무정보를 입력받아 수 초 내 COA 초안을 생성하고 지휘관 피드백으로 실시간 정련. 군사화된 StarCraft II 환경에서 SOTA RL보다 "전략적으로 건전한 COA를 더 빠르게" 생성했다고 보고 — [arXiv 2402.01786v2](https://arxiv.org/abs/2402.01786v2)
- Palnitkar, Mao, Waytowich, Goecks, Lin, "Mil-SCORE: Benchmarking Long-Context Geospatial Reasoning and Planning in Large Language Models", arXiv:2601.21826 (2026-01-29). 시뮬레이션 군사계획 시나리오(지도·전술명령·정보자료) 기반의 전문가 작성 다단계 질문 7종. 최신 VLM들이 "substantial headroom"을 보인다고 결론 — [arXiv 2601.21826](https://arxiv.org/abs/2601.21826)
- Autenrieb & Ostermann, "Generalized Intelligence for Tactical Decision-Making: Large Language Model-Driven Dynamic Weapon Target Assignment", arXiv:2511.10207 (2025-11-13, IEEE TAES 투고, 8p). 전술 결정을 "추론 문제"로 정식화해 LLM이 위협방향·자산우선순위·접근속도 등 맥락을 평가하여 요격기-표적 할당을 생성. 정적/동적 모드 시뮬레이터에서 MIP·경매 기반 대비 "일관성·적응성·임무 수준 우선순위화" 개선을 주장하나 초록에 정량치 없음. 저자 소속 미확인 [확인 필요] — [arXiv 2511.10207](https://arxiv.org/abs/2511.10207)
- Caballero & Jenkins, "On Large Language Models in National Security Applications", arXiv:2407.03453 (2024-07-03, 20p). 기회(정보처리 가속, Bayesian 추론과 결합, USAF 워게임·훈련)와 위험(환각, 프라이버시, 적대적 공격)을 정리하고 "LLMs are best suited for supporting roles rather than leading strategic decisions"라고 결론 — [arXiv 2407.03453](https://arxiv.org/abs/2407.03453)
- arXiv API 목록에서만 확인(초록 미열람) [확인 필요]: Sun, Zhao, Yu, Wang, "Self Generated Wargame AI: Double Layer Agent Task Planning Based on Large Language Model", arXiv:2312.01090 (2023-12); Yin et al., "WGSR-Bench: Wargame-based Game-theoretic Strategic Reasoning Benchmark for LLMs", arXiv:2506.10264 (2025-06); Jin et al., "SAGA: Scene-Aware, Goal-Evolving Agents for Long-Horizon Strategy Game Planning", arXiv:2606.29932 (2026-06).

**(c) 비군사 영역의 'LLM-as-objective/constraint designer' (전이 가능)**
- Ma et al., "Eureka: Human-Level Reward Design via Coding Large Language Models", ICLR 2024, arXiv:2310.12931. 환경 코드를 컨텍스트로 제공하고 보상 코드에 대한 진화적 탐색+reward reflection을 수행, 29개 환경 중 83%에서 인간 설계 보상을 상회, 평균 정규화 개선 52% — [arXiv 2310.12931](https://arxiv.org/abs/2310.12931)
- Xie et al., "Text2Reward: Reward Shaping with Language Models for Reinforcement Learning", ICLR 2024, arXiv:2309.11489. 자연어 목표→실행가능 dense reward 코드 생성, 17개 조작 과제 중 13개에서 전문가 보상과 동등 이상, 6개 보행 행동 >94% 성공, sim-to-real 전이 및 인간 피드백 반복 정련 지원 — [arXiv 2309.11489](https://arxiv.org/abs/2309.11489)
- Mo, "Chain of Uncertain Rewards with Large Language Models for Reinforcement Learning", arXiv:2604.13504 (2026-04-15). 보상 코드 항목별 불확실성 정량화(CodeBERT 유사도)+Bayesian 분리 최적화. IsaacGym human-normalized score 5.62 vs Text2Reward 2.78, 양손 조작 65.63% vs 56.87% — [alphaXiv 2604.13504](https://www.alphaxiv.org/abs/2604.13504.md)
- Urgun & Gungor, "Large Language Model Guided Incentive Aware Reward Design for Cooperative Multi-Agent Reinforcement Learning", arXiv:2603.24324 (2026-03-25). MAPPO 하에서 LLM이 보조 보상 프로그램을 합성(형식적 유효성 검사 포함), Overcooked-AI 4개 레이아웃에서 상호작용 병목이 큰 환경일수록 이득 — [arXiv 2603.24324](https://arxiv.org/abs/2603.24324)
- AhmadiTeshnizi, Gao, Udell, "OptiMUS: Optimization Modeling Using MIP Solvers and large language models", arXiv:2310.06116 (2023-10). 자연어 문제 설명→MILP 정식화·코드·검증, NLP4LP 데이터셋, 기본 프롬프팅 대비 약 2배 문제 해결. (학회 게재 여부는 해당 페이지에 미표기 [확인 필요]) — [arXiv 2310.06116](https://arxiv.org/abs/2310.06116)
- Peng et al., "Automatic MILP Model Construction for Multi-Robot Task Allocation and Scheduling Based on Large Language Models", arXiv:2503.13813 (2025-03-18). 로컬 LLM(DeepSeek-R1-Distill-Qwen-32B로 제약 추출, 미세조정 Qwen2.5-Coder-7B로 코드 생성)으로 프라이버시 보존, 제약 추출 정확도 82%, MILP 코드 정확도 90%, 단일 항공기 외피 제조 사례로만 검증 — [arXiv 2503.13813](https://arxiv.org/abs/2503.13813)
- Shi, Wu, Kumar, Sukhatme, "PIP-LLM: Integrating PDDL-Integer Programming with LLMs for Coordinating Multi-Robot Teams Using Natural Language", arXiv:2510.22784 (2025-10-26). 팀 수준 PDDL 분해→의존 그래프→정수계획으로 로봇 할당, 계획 성공률·최대/평균 이동비용·부하균형 개선 — [arXiv 2510.22784](https://arxiv.org/abs/2510.22784)
- Zhang et al., "LaMMA-P: Generalizable Multi-Agent Long-Horizon Task Allocation and Planning with LM-Driven PDDL Planner", ICRA 2025, arXiv:2409.20560. LM 추론+PDDL 휴리스틱 탐색, MAT-THOR 벤치마크에서 기존 LM 기반 다중에이전트 플래너 대비 성공률 105%↑, 효율 36%↑ — [arXiv 2409.20560](https://arxiv.org/abs/2409.20560)
- Li, An, Abrar, Zhou, "Large Language Models for Multi-Robot Systems: A Survey", arXiv:2502.03814 (2025-02, 2026-05 개정). 고수준 과업할당/중수준 운동계획/저수준 행동생성/인간개입으로 분류하고, 수학적 추론 한계·환각·지연시간·벤치마크 부재를 핵심 장애로 지목 — [arXiv 2502.03814](https://arxiv.org/abs/2502.03814)
- Li et al., "HMCF: A Human-in-the-loop Multi-Robot Collaboration Framework Based on Large Language Models", arXiv:2505.00820 (2025-05-01). 로봇별 LLM 에이전트+과업 검증+필요 시에만 인간 개입, 시뮬레이션 성공률 4.76%p 개선, 실로봇 zero-shot 일반화 — [arXiv 2505.00820](https://arxiv.org/abs/2505.00820)
- Lim, Tavakkoli Anbarani, Meira-Góes, Kovalenko, "Logic-Based Verification of Task Allocation for LLM-Enabled Multi-Agent Manufacturing Systems", arXiv:2604.17142 (2026-04-18). 시간논리·이산사건시스템으로 LLM이 생성한 과업할당을 실행 전 검증 — [arXiv 2604.17142](https://arxiv.org/abs/2604.17142)
- Kim, Lee, Park, Li, Park, "Human Implicit Preference-Based Policy Fine-tuning for Multi-Agent Reinforcement Learning in USV Swarm", arXiv:2503.03796 (2025-03-05, 7p). USV 군집 MARL 정책을 RLHF로 정련, 피드백을 intra-agent/inter-agent/intra-team으로 범주화하는 Agent-Level Feedback, LLM 평가자로 검증, 시나리오는 영역제약·충돌회피·과업할당(탐색구조·감시·선박보호). 소속 미표기 [확인 필요] — [arXiv 2503.03796](https://arxiv.org/abs/2503.03796)

**(d) 비판·실증적 한계**
- Rivera, Mukobi, Reuel, Lamparth, Smith, Schneider, "Escalation Risks from Language Models in Military and Diplomatic Decision-Making", FAccT 2024, arXiv:2401.03408. 5개 상용 LLM 모두가 워게임에서 확전 경향과 예측 어려운 패턴을 보였고 군비경쟁 역학, 드물게 핵사용까지 권고 — [arXiv 2401.03408](https://arxiv.org/abs/2401.03408)
- Schneider, Lamparth, Corso, Ganz, Mastro, Trinkunas, "Human Vs. Machine: Behavioral Differences Between Expert Humans And Language Models In Wargame Simulations", Hoover Institution Working Paper, 2024-07-31. 107명 국가안보 전문가 vs LLM 팀 시뮬레이션: 고수준 전략은 유사하나 개별 행동에서 LLM이 더 공격적, 시나리오 변화에 과민, 팀 대화 품질 저하·인위적 합의 — [Hoover](https://www.hoover.org/research/human-vs-machine-behavioral-differences-between-expert-humans-and-language-models-wargame)
- Shrivastava, Hullman, Lamparth, "Measuring Free-Form Decision-Making Inconsistency of Language Models in Military Crisis Simulations", arXiv:2410.13204 (2024-10-17). BERTScore 기반 의미 비일관성 측정, 5개 LM 모두 유의한 비일관성, 프롬프트 민감도가 온도 샘플링보다 큰 비일관성 유발 — [arXiv 2410.13204](https://www.arxiv.org/abs/2410.13204)
- Drinkall, "Red Lines and Grey Zones in the Fog of War: Benchmarking Legal Risk, Moral Harm, and Regional Bias in Large Language Model Military Decision-Making", arXiv:2510.03514 (2025-10-03). GPT-4o·Gemini-2.5·LLaMA-3.1 모두 구별원칙 위반(민간 물체 타격) 16.7–66.7%, 턴 진행에 따라 사상자 허용치 16.5→27.7 상승, LLaMA-3.1 시뮬레이션당 민간 타격 3.47회 vs Gemini-2.5 0.90회 — [arXiv 2510.03514](https://arxiv.org/abs/2510.03514)
- Elbaum & Panter, "Managing Escalation in Off-the-Shelf Large Language Models", arXiv:2508.01056 (2025-08). 두 가지 비기술적 개입으로 워게임 내 확전 권고를 "substantially reduce", LLM 사용 제한보다 정렬 조치를 권고 — [arXiv 2508.01056](https://arxiv.org/abs/2508.01056)

### Inferences
- 공개 배치 사례(Thunderforge, Maven/AIP)는 모두 "LLM이 인간 참모의 초안·요약·워게임을 보조"하는 수준이고, LLM이 직접 교전 결정을 내리는 배치 사례는 확인되지 않았다. 따라서 T5를 "LLM이 WTA를 결정"으로 설계하면 Autenrieb & Ostermann(2025)과 중복되면서 동시에 비판 문헌의 표적이 되지만, "LLM이 ROE·우선순위·의도를 목적함수 가중치/제약(마스크)으로 컴파일하고, 결정은 기존의 검증가능한 최적화/MARL 계층이 수행"하는 구조는 (i) Eureka/Text2Reward/OptiMUS/PIP-LLM/Peng et al.의 성숙한 방법론을 군사 WTA에 처음 결합하는 것이고 (ii) Lim et al.(2026)식 형식 검증을 붙이면 Drinkall식 IHL 위반 문제를 구조적으로 차단할 수 있어 차별성과 방어가능성을 모두 갖는다.
- Peng et al.(2025)이 보여준 "로컬 오픈웨이트 LLM으로 제약 추출 82%/코드 90%"는 CRS IN12669가 드러낸 상용 프런티어 모델의 무기용도 사용정책 리스크를 회피하는 설계 근거가 된다. 연구자의 로컬 PC 기반 개발 계획과도 부합한다.
- Kim et al.(2025)의 USV 군집 MARL+인간 선호 정련은 연구자의 선행연구(b)와 가장 인접한 국내외 경쟁 연구이므로, 후속연구에서 반드시 인용·대조해야 하며, "인간 선호로 정책을 정련"(Kim et al.)과 "지휘관 의도를 제약·가중치로 컴파일하고 veto·설명을 평가"(T5)는 문제 정의가 다르다는 점을 명시해야 한다.
- 비판 문헌은 일관되게 "LLM의 비일관성·확전·IHL 위반"을 지적하므로, T5의 평가지표에는 의도→제약 변환의 일관성(동일 의도 반복 프롬프트 간 제약 집합 일치율), IHL/ROE 위반 0건 보장(형식 검증), 그리고 인간 veto 지연시간이 포함되어야 설득력이 있다.

### Gaps
- Thunderforge의 계약금액·성과지표, Maven의 "시간당 1,000건" 주장의 1차 출처는 확인하지 못했다.
- Autenrieb & Ostermann(2025)의 본문(정량 결과, 지연시간, LLM 종류)은 초록만 확인하였다. IEEE TAES 게재 여부 미확인.
- Army War College의 LLM 심판(adjudication) 실험 기사는 DNS 오류로 열지 못했다.
- 군사 영역에서 "LLM이 목적함수 가중치/제약을 생성하고 하위 최적화기가 결정"하는 구조를 명시적으로 구현·평가한 논문은 본 리서치에서 발견되지 않았다(부재가 곧 신규성 근거일 수 있으나, 웹검색 예산 소진으로 Scholar 전수조사는 못했음).

---

## KQ2. WTA/TEWA·MARL 결정에 대한 설명가능성(XAI) 연구와, Human-on-the-loop 거부권(veto)의 신뢰·지연에 관한 국방 인간공학 실증

### Takeaway
WTA 전용 XAI는 2026년 중국 항공학보의 EHD-DQN(Grad-CAM+LIME)이 거의 유일한 직접 사례이며, MARL 일반에서는 반사실(counterfactual) 기반 설명(EMAI AAAI 2025, AXIS 2025)과 LLM 요약이 주류다. 인간공학 실증은 2024–2026년에 급격히 축적되었는데(이스라엘 군인 2,015명, 웨스트포인트 생도 236명), 공통 결론은 "자동화 편향보다 알고리즘 회피(algorithmic aversion)가 관찰되며 XAI가 회피를 줄인다"이다. 그러나 '5초 롤링 호라이즌 내 veto 지연시간'과 같은 전술 시간척도의 정량 연구는 찾지 못했다.

### Cited Findings
- Liu, Yang, Huang, "Optimizing air and missile defense strategies with explainable hierarchical reinforcement learning", Acta Aeronautica et Astronautica Sinica 47(8):332786, 2026, DOI 10.7527/S1000-6893.2025.32786. EHD-DQN: 순위결정과 요격결정의 계층 분리, 시간감쇠 다중 경험버퍼, Grad-CAM+LIME 설명 모듈. DQN·DDPG·PPO·RH-MILP·NSGA-II·ALNS 대비 요격성공률·탄 효율·고가치표적 교전시점에서 우수하며 지휘체계에 해석가능한 근거 제공 주장 — [hkxb.buaa.edu.cn](https://hkxb.buaa.edu.cn/EN/Y2026/V47/I8/332786)
- Chen et al., "Understanding Individual Agent Importance in Multi-Agent System via Counterfactual Reasoning", AAAI 2025, 39(15):15785–15794, DOI 10.1609/aaai.v39i15.33733. EMAI: 에이전트 행동을 무작위화했을 때 보상 변화량으로 개별 에이전트 중요도를 학습(희소성 제약), 7개 다중에이전트 과제에서 기준선보다 높은 설명 충실도, 적대적 공격·정책 강건화에도 활용 — [AAAI](https://ojs.aaai.org/index.php/AAAI/article/view/33733)
- Gyevnár, Lucas, Albrecht, Cohen, "Integrating Counterfactual Simulations with Language Models for Explaining Multi-Agent Behaviour", arXiv:2505.17801 (2025-05, 2025-10 개정). AXIS: LLM이 시뮬레이터에 'what-if'·'remove' 질의를 반복하여 반사실 효과크기를 수집·요약, 자율주행 10개 시나리오·5개 LLM에서 설명 정확도 ≥7.7% 개선, 4개 모델에서 목표 예측 정확도 23% 개선 — [arXiv 2505.17801](https://arxiv.org/abs/2505.17801)
- CDAO JATIC(2024-11-12 Kitware 설명): DoD 전반의 AI T&E 도구 표준화 프로그램. XAITK(visual saliency 기반 설명), NRTK(센서 특유의 섭동으로 CV 강건성 평가) 등을 오픈소스로 제공 — [Kitware](https://www.kitware.com/cdao-jatic-empowering-responsible-ai-adoption/)
- Shandler, Gross, Shereshevsky, "Black Box Warfare: Human Judgment and Military Decision-Making in the Age of AI", DOI 10.1177/00220027261463443 (ISSN 0022-0027 = Journal of Conflict Resolution; Schneier 블로그는 Journal of Peace Research로 표기 — 게재지 [확인 필요]). IDF가 실제 사용하는 표적 DSS의 고충실도 복제품으로 이스라엘 군인 2,015명 대상 2개 실험. 자동화 편향 대신 특히 고(高) 부수피해 시나리오에서 강한 알고리즘 회피가 관찰되었고, XAI 기능 통합이 회피를 줄이고 숙고를 촉진. 신뢰는 개인 성향·지각된 작전 이해관계·인터페이스 정보 특성에 따라 동적 — [Schneier 2026-08](https://www.schneier.com/blog/archives/2026/08/ai-for-military-support.html); [citedrive 서지](https://www.citedrive.com/en/discovery/black-box-warfare-human-judgment-and-military-decision-making-in-the-age-of-ai/) (SAGE 원문은 403으로 미열람)
- Kahn, Horowitz, Resnick Samotin, "What is Human in Judgment? Comparing Automation Bias and Algorithm Aversion Between the United States Military Academy and the General Public", arXiv:2604.04333 (2026-04-06). 웨스트포인트 생도 236명 vs 유사 인구통계 일반인: 표적식별 과제 후 알고리즘/인간 분석관 조언을 받고 수정 허용. 생도가 자동화 편향·알고리즘 회피 모두에서 더 잘 보정된 판단을 보임 — [arXiv 2604.04333](https://arxiv.org/abs/2604.04333)
- (anchor) Pearson et al., "Differences in Trust Between Human and Automated Decision Aids", ACM HotSoS 2016. 126명, 군 호송 경로선택 과제에서 인지부하 증가 시 자동화 신뢰 감소, 위험 증가 시 인간 조언자 신뢰 증가 — [CPS-VO](https://archive.cps-vo.org/node/26914)
- Puscas, "Human-Machine Interfaces in autonomous weapon systems: Considerations for human control", UNIDIR, 2022-07-21, 40p. HMI는 인간통제의 핵심요소이나 효과는 작전맥락·인간공학 설계·훈련·동적 환경의 결정 복잡성·AI/ML 학습체계의 고유 난제에 의존하며, 감시·재통제(override)·비활성화 설계와 훈련 요건을 다룬다 — [UNIDIR](https://unidir.org/?p=9072); [UNIDIR 행사 페이지](https://unidir.org/?p=7868)
- SIPRI, Blanchard & Bruun, "Autonomous Weapon Systems and AI-enabled Decision Support Systems in Military Targeting: A Comparison and Recommended Policy Responses", 2025-06, DOI 10.55163/YQBY3151 (국문 번역: 피스모모, 2025-11). AI-DSS의 핵심 위험은 자동화 편향으로 인간이 권고를 "수동적으로 동의"하는 상황이며, AWS는 오식별→즉각 치명행동의 직접 위험, AI-DSS는 간접 위험으로 구분 — [SIPRI 영문 페이지](https://www.sipri.org/publications/2025/other-publications/autonomous-weapon-systems-and-ai-enabled-decision-support-systems-military-targeting-comparison-and); [SIPRI 국문 PDF](https://www.sipri.org/sites/default/files/2025-12/ko_laws_v.pdf)
- ICRC GGE 작업문서(2026-08): GGE 초안 보고서 para 39(c)가 LAWS의 작동에 대해 "predictability, reliability, traceability and explainability" 요건을 두고 있음을 보존 대상 핵심요소로 지목 — [ICRC working paper Aug 2026](https://www.icrc.org/sites/default/files/2026-08/ICRC_working_paper_GGE_LAWS_August-2026-ICRC.pdf)
- arXiv API 목록만 확인(미열람) [확인 필요]: Amitai et al., "Explaining Reinforcement Learning Agents Through Counterfactual Action Outcomes" (COViz), AAAI 2024 — [AAAI 페이지 링크(미열람)](https://ojs.aaai.org/index.php/AAAI/article/view/28863).

### Inferences
- WTA에 특화된 XAI는 EHD-DQN(2026)이 Grad-CAM/LIME 수준의 사후 설명에 머물러 있으므로, 군집 USV WTA에 (i) 반사실 기반 "이 USV가 이 표적을 맡지 않았다면 DSR이 얼마나 변했나"(EMAI/AXIS 계열) 설명과 (ii) 할당 근거를 ROE·위협지수 항목별 기여도로 분해하는 설명을 결합하면 명확한 신규성이 있다. 특히 선행연구(b)의 Phase 1 위협지수(5요인)는 본질적으로 가산적 구조여서 항목별 기여도 설명이 자연스럽다.
- 실증 문헌(Shandler et al. 2026; Kahn et al. 2026)의 공통 결론인 "군인은 알고리즘 회피 성향이 있고 XAI가 이를 완화한다"는 T5의 "XAI+veto" 설계가 단순 규제 준수용이 아니라 실제 운용 수용성(acceptance) 제고 수단이라는 논거를 제공한다. 다만 두 연구 모두 분(min) 단위의 표적 심의 맥락이며, 수 초 단위 군집 교전에서의 veto 가능성은 별도 검증이 필요하다.
- GGE para 39(c)의 "traceability·explainability" 요건은 설계 요구사항으로 직접 인용 가능하며, 후속연구가 "규범이 요구하는 설명가능성을 구현·측정한 최초의 군집 USV WTA 연구"로 프레이밍될 수 있다.

### Gaps
- 전술 시간척도(수 초)에서 human-on-the-loop veto의 지연시간·정확도를 측정한 정량 연구는 찾지 못했다. UNIDIR HMI 보고서 본문(시간압박·자동화편향 세부)은 열지 못했다.
- Black Box Warfare의 게재지(JCR vs JPR)·권호·실험 설계 세부는 원문 403으로 미확인.
- HPCMP의 "Explainable AI for Multi-Domain Combat Simulation" 과제 PDF는 랜딩 페이지만 열려 내용 미확인.
- 국방 분야에서 XAI 설명이 실제로 결정 품질(오류 교정률)을 높였는지에 대한 통제실험은 Shandler et al. 외에 확인하지 못했다.

---

## KQ3. 분포강건(DRO)·CVaR/위험민감 RL·Bayesian/신념공간 계획을 WTA·과업할당·교전(센서/식별 불확실성·기만체) 에 적용한 연구

### Takeaway
WTA에 CVaR을 적용한 연구는 2019년 BIT 그룹(anchor)에 멈춰 있고, 분포강건최적화(DRO)를 WTA 또는 다중로봇 과업할당에 적용한 arXiv 논문은 API 질의에서 0건이었다. 위험민감 분산 MARL(CVaR QD-learning 2023), STL 강건도 기반 실시간 할당(CDC 2024), 기만적 표적전환 탐지(2025), 기만체 배치 게임(2024), 성공확률 기반 분산 WTA(AIAA 2024–2025)가 인접 연구로 존재하므로, T2(불확실성 강건 동적 WTA)는 "DRO/CVaR + 식별·기만 불확실성 + 재할당"을 결합하는 지점에서 문헌상 공백이 명확하다.

### Cited Findings
- (anchor) Li, Chen, Xin, "Optimizing multi-objective uncertain multi-stage weapon target assignment problems with the risk measure CVaR", IEEE ICCA 2019, pp. 61–66, DOI 10.1109/ICCA.2019.8899501. 살상확률이 확률 매개변수에 의존한다고 가정, 표적 미격파 위험을 CVaR로 측정하고 탄 소모와 함께 다목적화, MOEA/D-AWA·DMOEA-εC에 계층비교 전략 추가 — [BIT Pure](https://pure.bit.edu.cn/en/publications/optimizing-multi-objective-uncertain-multi-stage-weapon-target-as/)
- Al Maruf, Niu, Ramasubramanian, Clark, Poovendran, "Risk-Aware Distributed Multi-Agent Reinforcement Learning", arXiv:2304.02005 (2023-04). CVaR 가치함수용 Bellman 연산자(축약성 증명), 분산 CVaR QD-learning, 에이전트 가치함수 합의 수렴 증명, 위험 매개변수가 합의 가치함수에 미치는 영향 시뮬레이션 — [arXiv 2304.02005](https://arxiv.org/abs/2304.02005)
- Engelaar, Zhang, Vlahakis, Dimarogonas, Lazar, Haesaert, "Risk-Aware Real-Time Task Allocation for Stochastic Multi-Agent Systems under STL Specifications", CDC 2024, arXiv:2404.02111. 이종 확률 선형 MAS에 STL 사양을 실시간 할당: 사양을 에이전트 수준 하위사양으로 분해, STL 강건도 기반 휴리스틱 필터, 경매 알고리즘, tube-based MPC로 확률적 만족 보증 — [arXiv 2404.02111](https://arxiv.org/abs/2404.02111)
- Meng, Li, Ornik, "Target Prediction Under Deceptive Switching Strategies via Outlier-Robust Filtering of Partially Observed Incomplete Trajectories", arXiv:2504.03502 (2025-04). 에이전트가 한 표적을 향하다 중간에 전환하는 기만전략을, 잡음·이상치가 큰 부분관측 궤적에서 이상치강건 변화탐지로 식별. WTA 탐지 시나리오(외력 포함 운동학 모델)에서 검증 — [arXiv 2504.03502](https://arxiv.org/abs/2504.03502)
- Kulkarni, Cohen, Kamhoua, Fu, "Integrated Resource Allocation and Strategy Synthesis in Safety Games on Graphs with Deception", arXiv:2407.14436 (2024-07). 불완전정보 2인 게임에서 trap·fake target(기만체) 배치와 전략 합성을 통합한 hypergame, 기만체 배치 목적함수가 단조·(초)모듈러임을 보여 (1−1/e) 근사 그리디 보장 — [arXiv 2407.14436](https://arxiv.org/abs/2407.14436)
- Merkulov, Iceland, Michaeli, Riechkind, Gal, Barel, Shima, "Reinforcement Learning Based Decentralized Weapon-Target Assignment and Guidance", AIAA SciTech 2024, DOI 10.2514/6.2024-0125. 각 요격기가 자기 도달가능영역과 "다른 미사일들의 성공확률"을 상태로 받아 독립적으로 표적 선택, 팀원이 할당·성공확률을 공유, 그리디 대비 RL 우위·실시간 재할당 — [Haifa CRIS](https://cris.haifa.ac.il/en/publications/reinforcement-learning-based-decentralized-weapon-target-assignme/)
- Merkulov, Iceland, Michaeli, Gal, Barel, Shima, "Reinforcement-Learning-Based Cooperative Dynamic Weapon-Target Assignment in a Multiagent Engagement", AIAA SciTech 2025, DOI 10.2514/6.2025-1546. 2파 Shoot-Shoot-Look 교전을 확률적 MDP로 정식화, 요격확률 예측 기반 보상, RL이 그리디를 "slightly" 상회하고 제안 그리디가 RL을 잘 근사 — [IUCC CRIS](https://cris.iucc.ac.il/en/publications/reinforcement-learning-based-cooperative-dynamic-weapon-target-as/)
- Schneider & Fichter, "Many-vs-Many Missile Guidance via Virtual Targets", arXiv:2511.02526 (2025-11-04; 2026-05-07 철회). Normalizing Flows 궤적예측기로 가상표적을 생성해 요격기 할당, 1–6 표적×1–8 요격기 Monte Carlo에서 n>m일 때 5.8–14.4% 개선을 보고했으나 "해당 시나리오 밖으로 일반화되지 않음"을 이유로 저자 철회 — [arXiv 2511.02526](https://arxiv.org/abs/2511.02526)
- Czempin & Gleave 등 self-play 계열은 KQ4 참조. CVaR 기반 협력 MARL의 대표작 RMIX(NeurIPS 2021)는 검색 목록으로만 확인(미열람, anchor) [확인 필요] — [NeurIPS 2021 포스터 링크(미열람)](https://neurips.cc/virtual/2021/poster/27971)
- arXiv API 질의 결과: `"distributionally robust" AND "task allocation"` → 0건; `"weapon target assignment" AND (robust OR uncertain OR CVaR OR risk)` → Autenrieb & Ostermann(2025)과 Meng et al.(2025) 2건만 반환(2026-10-05 기준, export.arxiv.org).

### Inferences
- DRO(Wasserstein/모멘트 기반 ambiguity set)로 살상확률·식별확률의 분포 불확실성을 다루는 WTA 연구는 공개 arXiv에서 발견되지 않았고, CVaR WTA는 2019 진화알고리즘 수준에 머물러 있다. 따라서 T2는 "분포강건 또는 CVaR 제약을 가진 동적 WTA + 위험민감 MARL(CVaR QD-learning 계열) + 재할당"을 군집 USV에 결합하는 첫 연구로 위치시킬 수 있다. 다만 "risk-sensitive MARL" 일반론은 RMIX 등 선행이 많으므로, 신규성은 알고리즘 자체보다 "식별 불확실성·기만체·센서 잡음이 결합된 WTA 문제 정의와 강건성 평가 프로토콜"에 두어야 한다.
- Meng et al.(2025)과 Kulkarni et al.(2024)은 "기만체/기만전략"을 다루지만 각각 탐지(통계)와 배치(게임)에 국한되어, "기만체가 포함된 적 군집에 대한 할당의 강건성"을 다루는 연구는 부재하다. 이는 T2와 T6의 교차점(기만적 적 전략)에 대한 공백이다.
- Schneider & Fichter(2025)의 철회 사례는 "소규모 시나리오에서만 검증된 학습 기반 할당의 일반화 실패"가 실제로 발생함을 보여주는 중요한 반면교사이며, 후속연구의 평가에서 규모·분포 외 시나리오 일반화 검증을 필수 항목으로 넣어야 하는 근거가 된다.
- Merkulov et al.(2025)의 "그리디가 RL을 잘 근사" 결과는 선행연구(b)의 "Phase1 휴리스틱→Phase2 VNS→Phase3 MARL" 하이브리드 설계가 타당함을 간접 지지하면서, 후속연구가 RL의 이득을 "불확실성·적대성·통신제약" 조건에서 입증해야 함을 시사한다.

### Gaps
- DRO를 WTA/과업할당에 적용한 저널 논문(IEEE/Elsevier)은 웹검색 예산 소진으로 전수조사하지 못했다. [확인 필요: Scopus에서 "distributionally robust" + "assignment" + "weapon/interceptor" 재검색]
- Bayesian/신념공간(POMDP) 기반 교전 결정 연구는 검색 결과가 특허·구형 문헌(Dempster-Shafer CID)만 반환되어 2024–2026 학술 문헌을 확인하지 못했다.
- 2023 BIT/HIT 그룹의 UMWTA 후속 연구(저널판) 존재 여부 미확인.

---

## KQ4. Self-play·개체군 기반 훈련(PBT)·공진화로 교전/할당 정책을 적응적 적에 대해 훈련한 연구와 착취가능성(exploitability)·강건성 보고

### Takeaway
Self-play/PBT/PSRO의 착취가능성 감소 결과는 일반 게임(Czempin & Gleave 2022; Conflux-PSRO 2024)과 LLM 안전(Self-RedTeam, Nash 보증)에서 확립되었고, 군사 교전에서는 미분게임 기반 드론 군집 방어(Allen 2026: 방어성공 94.6→96.8%)·AlphaDogfight(anchor)·DoD SBIR 2026 토픽이 수요를 보여준다. 그러나 WTA 정책을 self-play/공진화로 훈련하고 착취가능성을 정량 보고한 논문은 발견되지 않았다. 해양 영역에서는 MIT LL/USNA의 Aquaticus 깃발뺏기(CTF)가 적대적 USV 자율성 평가의 사실상 표준 테스트베드다.

### Cited Findings
- Czempin & Gleave, "Reducing Exploitability with Population Based Training", ICML 2022 New Frontiers in Adversarial ML Workshop, arXiv:2208.05083. self-play 정책은 명시적으로 훈련된 적대 정책에 파국적으로 실패할 수 있으며, PBT로 다양한 상대 개체군과 훈련하면 "공격자가 피해자를 착취하는 데 필요한 훈련 스텝 수"로 측정한 강건성이 증가하고 개체군 크기와 상관 — [arXiv 2208.05083](https://arxiv.org/abs/2208.05083)
- Huang, Lian, Wang, Ma, Wen, "Conflux-PSRO: Effectively Leveraging Collective Advantages in Policy Space Response Oracles", arXiv:2410.22776 (2024-10/11). 상태 수준 정책 선택·라우팅으로 best response를 구성, 여러 환경에서 기존 PSRO 변형 대비 착취가능성 유의 감소 — [arXiv 2410.22776](https://arxiv.org/abs/2410.22776)
- Liu, Jiang, Liang, Du, Choi, Althoff, Jaques, "Chasing Moving Targets with Online Self-Play Reinforcement Learning for Safer Language Models", arXiv:2506.07468 (2025-06; 게재는 ICML로 표기되나 페이지 간 2025/2026 표기 불일치 [확인 필요]). Self-RedTeam: 단일 정책이 공격자·방어자를 교대 수행하는 완전 온라인 self-play MARL, 2인 영합게임 기반 "Nash 균형 수렴 시 방어자가 임의 적대 입력에 안전" 보증, 14개 벤치마크에서 최대 95% 안전성 개선, 공격 다양성 17.80% 증가 — [arXiv 2506.07468](https://arxiv.org/abs/2506.07468)
- Allen, "Game-Theoretic Drone Swarm Defense: A Case Study in Applied Differential Game Theory", arXiv:2609.04394 (2026-09-03). 고가치자산을 지키는 방어 군집 vs 회피기동 가능한 침입 군집의 표적할당·중간유도 문제를 미분게임으로 정식화(침입자를 합리적 에이전트로 보고 Nash 균형 탐색). Monte Carlo에서 방어성공 94.6%→96.8%(잔여 격차의 약 41% 해소), Bayesian 분석상 우위 사후확률 99.9% — [arXiv 2609.04394](https://arxiv.org/abs/2609.04394)
- (anchor) Pope et al., "Hierarchical Reinforcement Learning for Air Combat at DARPA's AlphaDogfight Trials", IEEE Trans. Artificial Intelligence 4(6):1371–1385, 2023, arXiv:2105.00990. 고수준 정책 선택자+개별 훈련된 저수준 정책, 최대엔트로피 off-policy, 대회 2위·인간 조종사 상회 — [arXiv 2105.00990](https://arxiv.org/abs/2105.00990)
- (anchor) Luo, Lu, Liu, Chen, "Learning-Based Policy Optimization for Adversarial Missile-Target Assignment", IEEE Trans. SMC: Systems 52(7):4426–4437, 2022, DOI 10.1109/TSMC.2021.3096997. PODRL: 적대 환경에서의 미사일 돌파를 데이터 기반으로 암묵적 모델링, 대규모 인스턴스에서 할당과 수요예측 동시 수행 — [BUAA](https://research.buaa.edu.cn/en/publications/learning-based-policy-optimization-for-adversarial-missile-target/)
- DoD SBIR OSW26BZ02-DV004: "self-play learning within high-fidelity simulations to refine strategies for both friendly and adversary forces simultaneously", 해석가능·모듈형 전략, AFSIM 연동 요구 — [SBIR 토픽](https://www.bwcoconsulting.com/dod-sbirs/osw26bz02-dv004-game-theoretic-ai-for-robust-course-of-action-coa-generation-and-wargaming)
- Beason, Novitzky, Kliem, Errico, Serlin, Becker, Paine, Benjamin, Dasgupta, Crowley, O'Donnell, James, "Evaluating Collaborative Autonomy in Opposed Environments using Maritime Capture-the-Flag Competitions", ICRA 2024 Workshop on Field Robotics, arXiv:2404.17038. 실제 USV 팀 CTF 대회 Aquaticus와 경량 Gymnasium 시뮬레이터 Pyquaticus. 규칙 기반 협력 행동이 DRL 훈련 에이전트를 능가했으며, 보상 설계·sim-to-real이 향후 과제 — [arXiv 2404.17038](https://arxiv.org/abs/2404.17038)
- Crowley, Serlin, Paine, Mann, Benjamin, Belta, "SPLASH! Sample-efficient Preference-based inverse reinforcement learning for Long-horizon Adversarial tasks from Suboptimal Hierarchical demonstrations", arXiv:2507.08707 (2025-07). 해양 CTF에서 비최적 시연으로부터 보상 학습, 시뮬레이션 후 실제 ASV에 sim-to-real 전이, 비최적 시연 기반 보상학습 SOTA 상회 — [arXiv 2507.08707](https://arxiv.org/abs/2507.08707)
- arXiv API 질의 `("self-play" OR "population-based" OR "co-evolution") AND swarm AND (defense OR attack OR pursuit)` → 0건; `"target assignment" AND ("self-play" OR adversarial OR Nash)` → Allen(2026) 외 2021·2015 문헌만 반환(2026-10-05).

### Inferences
- "WTA 정책의 self-play/공진화 훈련 + 착취가능성(Czempin & Gleave식 '착취까지의 공격자 훈련 스텝' 또는 PSRO식 NashConv) 보고"는 문헌상 공백이며, T6의 핵심 신규성으로 삼을 수 있다. Allen(2026)이 미분게임(해석적)으로 2.2%p 개선을 보인 것과 대비하여, 학습 기반 공진화가 적의 기만·전환 전략(Meng et al. 2025)까지 포함한 더 넓은 전략공간에서 어떤 강건성을 주는지가 차별화 질문이다.
- Beason et al.(2024)의 "규칙 기반이 DRL을 이겼다"는 결과는 해양 적대 환경에서 학습 기반 정책의 일반화·강건성 입증이 아직 열린 문제라는 뜻이며, 후속연구의 비교군에 강한 규칙/휴리스틱 적군(red team)을 반드시 포함해야 함을 시사한다. Pyquaticus는 로컬 PC에서 재현 가능한 공개 USV 적대 시뮬레이터로서 시뮬레이터 설계 벤치마크로 참고할 수 있다.
- SBIR 2026 토픽의 "해석가능·모듈형 전략" 요구는 T6과 T5(XAI)의 결합이 미 국방 수요와 정합함을 보여준다.

### Gaps
- 공중전 self-play 리그 훈련(2024–2025 중국·미국 논문)은 웹검색 예산 소진으로 확인하지 못했다.
- Allen(2026)의 소속·게재지, Self-RedTeam의 정확한 ICML 연도는 미확인.
- 적대적 공진화에서 "적의 전략 다양성(기만·전환·포화 패턴)"을 측정하는 표준 지표는 발견하지 못했다.

---

## KQ5. 해양 자율체계·군집 RL의 디지털트윈, Sim-to-Real, HILS, VV&A 관행(미 DoD Replicator/CDAO T&E, NATO STO 등)

### Takeaway
2024–2026년에 (i) 정책 측에서는 CDAO "Test and Evaluation of AI Models"(2024-04, 6개 영역)·JATIC 도구·Replicator에 대한 의회의 T&E 계획 요구·DoDD 3000.09의 V&V/T&E 심사기준, (ii) 기술 측에서는 USV 디지털트윈(Unity 기반 NTNU 테스트베드, Rezayan의 IMO/ITTC 추적가능 가상 해상시험), 17톤 실선 zero-shot 전이(Sim2Sea 2026), IEEE T-FR의 sim-to-real 강건성 평가(구동계 모델 충실도가 주 열화원)가 축적되었다. 그러나 전투 군집 USV WTA에 대한 HILS/디지털트윈 VV&A 사례는 공개 문헌에서 찾지 못했고, NATO STO 보고서는 접근 불가였다.

### Cited Findings

**(a) 정책·T&E 프레임워크**
- CDAO "Test and Evaluation of AI Models"(2024-04): Performance·Testing Methods·Data·AI Models·Context·Documentation의 6개 영역, "Correctness is just the tip of the iceberg"(편향·강건성·드리프트·지연시간 평가), A/B 테스트부터 레드팀까지 다양한 방법, 데이터 카드·모델 카드·감사 추적, 실제 운용 맥락(네트워크·컴퓨팅 제약) 내 평가 — [Domino 블로그(2차 자료; ai.mil 원문은 403)](https://domino.ai/blog/domino-automates-the-cdao-ai-test-and-evaluation-framework) [확인 필요: 원문]
- JATIC(XAITK·NRTK·MAITE 등)으로 DoD 전반 AI 보증 도구 표준화 — [Kitware 2024-11-12](https://www.kitware.com/cdao-jatic-empowering-responsible-ai-adoption/)
- Replicator: FY2024 약 $500M 확보, FY2025 $500M 추가 요청에 상원 세출위가 전액 권고하면서도 "T&E 계획이 미완"이라며 DOTMLPF-P 함의와 선정 체계별 T&E 마스터플랜 60일 내 브리핑을 요구, DIU에 DOT&E와의 조율 지시, 국방부 IG가 평가 착수 — [DefenseScoop 2024-08-02](https://defensescoop.com/2024/08/02/senate-appropriations-bill-fiscal-2025-replicator/)
- DoDD 3000.09(2023-01-25) 고위급 심사 기준: V&V, 현실적 조건의 T&E, 시간·지리 제약 내 운용, 교전 중단·이탈 능력, DoD AI 윤리원칙·RAI 정합. 학자들은 집행수단 부족과 "appropriate levels of human judgment"의 해석 재량을 비판 — [Harvard IHRC Review 2023-02](https://humanrightsclinic.law.harvard.edu/wp-content/uploads/2023/02/Review-of-the-2023-US-Policy-on-Autonomy-in-Weapons-Systems.pdf)
- Fasano & Silva, "Managing the Development and Integration of AI-Based Mission Autonomy in Unmanned Systems: A Programmatic and System Engineering Approach", NPS-AM-26-238, 2026-06. AI 기반 임무자율성은 창발적·확률적·비결정적 행동을 낳으므로 "무엇을 해야 하는가"의 긍정 요구사항에 더해 "어떤 조건에서도 하지 말아야 하는가"의 부정 요구사항(negative requirements) 개발·관리·시험 방법이 필요하며 현 획득·검증 프로세스에 부재 — [NPS DAIR](https://dair.nps.edu/handle/123456789/5602)
- DSTA(싱가포르)–한국선급(KR) MOU(2026-01-08): USV의 인식(perception)·자율성 기술에 대한 V&V 프레임워크 공동개발(인식 알고리즘 평가, AI 기반 USV 검증 방법론, 안전 가이드라인) — [Digital Ship](https://thedigitalship.com/news/electronics-navigation/dsta-and-kr-shape-trust-in-autonomy/)
- NATO ACT RFI(2025-01, 해양자율체계): MAS "와 함께, 그리고 MAS에 대항하여" 훈련, 자율성 수준, 상호운용성, T&E 방법론, 신뢰 요소에 관한 정보 요청(PDF 텍스트 추출 불완전 [확인 필요]) — [NATO ACT RFI Q&A](https://www.act.nato.int/wp-content/uploads/2025/01/rfi025007_qa1.pdf)

**(b) 디지털트윈·Sim-to-Real·테스트베드**
- Gezer, Moreau, Høgden, Nguyen, Skjetne, Sørensen, "Digital-physical testbed for ship autonomy studies in the Marine Cybernetics Laboratory basin", arXiv:2505.06787 (2025-05, 2026-07 v5). NTNU MC Lab: 소형 모형선+선박별 시뮬레이터+Unity 디지털트윈, 저충실도→고충실도 시뮬레이션→모형시험→R/V milliAmpere1 준실선→R/V Gunnerus 실선의 단계적 V&V 파이프라인 — [arXiv 2505.06787](https://arxiv.org/abs/2505.06787)
- Rezayan, "Traceable Virtual Sea Trials in the Marine Robotics Unity Simulator for Manoeuvring Assessment of Unmanned Surface Vehicles", arXiv:2606.12349 (2026-06). IMO·ITTC 기준 선회/지그재그 시험 자동 실행, 명령-구동 분리 로깅으로 추적가능성·감사가능성 제공, 좌/우현 선회 advance 차이 3.9%, tactical diameter 4.6–4.7%, 시스템식별용 데이터셋 생성 — [arXiv 2606.12349](https://arxiv.org/abs/2606.12349)
- Cui et al., "Sim2Sea: Sim-to-Real Policy Transfer for Maritime Vessel Navigation in Congested Waters", arXiv:2603.04057 (2026-03). GPU 가속 시뮬레이터, 속도장애물(VO) 유도 행동 마스킹을 가진 이중스트림 시공간 정책, 도메인 랜덤화, 시뮬레이션만으로 훈련한 정책이 17톤 무인선에 zero-shot 전이 — [arXiv 2603.04057](https://arxiv.org/abs/2603.04057)
- Batista, Aravecchia, Pradalier, "Sim-to-Real Transfer and Robustness Evaluation of Reinforcement Learning Control with Integrated Perception on an ASV for Floating Waste Capture", IEEE Trans. Field Robotics, 2026, arXiv:2605.02529. 2단계 시뮬레이션 프로토콜+실카메라 거동을 모사하는 인식 추상화 모듈, 14개 교란조건 현장시험에서 cm 수준 종단 정확도, 주요 열화원은 "구동계 모델 충실도 부족", 표적화된 도메인 랜덤화와 지연시간 관리 권고 — [arXiv 2605.02529](https://arxiv.org/abs/2605.02529)
- Menges, von Brandis, Rasheed, "Digital Twin of Autonomous Surface Vessels for Safe Maritime Navigation Enabled through Predictive Modeling and Reinforcement Learning", arXiv:2401.04032 (2024-01). Unity 기반 DT, AIS+합성 LiDAR 표적추적, NMPC 예측 안전필터 — [arXiv 2401.04032](https://arxiv.org/abs/2401.04032)
- Li, Lei, Shen, Liu, Liu, "Digital Twin-Enabled Deep Reinforcement Learning for Safety-Guaranteed Flocking Motion of UAV Swarm", Trans. Emerging Telecommunications Technologies 35(11):e70011, 2024, DOI 10.1002/ett.70011. 고충실도 DT로 MAPPO 기반 군집 정책 훈련, 분산 군집중심 추정·충돌방지 반발 — [BIT Pure](https://pure.bit.edu.cn/en/publications/digital-twin-enabled-deep-reinforcement-learning-for-safety-guara/)
- Vasconcellos et al., "Reinforcement-learning robotic sailboats: simulator and preliminary results", NeurIPS 2023 Workshop on Robot Learning, arXiv:2402.03337. 실제 로봇 세일링 선박 기반 USV 디지털트윈 구축의 모델링·구현 단계와 난제 정리 — [arXiv 2402.03337](https://arxiv.org/abs/2402.03337)
- Beason et al.(2024) Pyquaticus/Aquaticus(KQ4 참조)와 SPLASH(2025)의 sim-to-real — [arXiv 2404.17038](https://arxiv.org/abs/2404.17038); [arXiv 2507.08707](https://arxiv.org/abs/2507.08707)
- arXiv API 목록만 확인(미열람) [확인 필요]: Vekinis & Perantonis, "Aeolus Ocean — A simulation environment for the autonomous COLREG-compliant navigation of USVs using DRL and maritime object detection", arXiv:2307.06688 (2023); Torroba et al., "Marinarium: A Modular Experimental Facility for Reproducible Maritime and Space-Analog Field Robotics", arXiv:2602.23053 (2026); El-Hariry et al., "RoboRAN", arXiv:2505.14526 (2025).

### Inferences
- 해양 자율성의 VV&A는 "단계적 충실도(저→고→모형→준실선→실선)"와 "추적가능한 명령-구동 로깅", "부정 요구사항(절대 금지 행동)의 시험"으로 수렴하고 있다. 후속연구의 시뮬레이터는 (i) 선행연구(b)의 12항목 V&V 표를 CDAO 6영역+NPS 부정요구사항 체계로 재구성하고, (ii) ROE/NLL 마스크 위반 0건을 "부정 요구사항 시험"으로 보고하며, (iii) 시나리오 로그의 추적가능성(명령/실현 분리)을 갖추면 국제 심사에서 "VV&A 관행 정합"을 주장할 수 있다.
- Batista et al.(2026)의 "구동계 충실도가 주 열화원"과 Sim2Sea의 "VO 기반 행동 마스킹+도메인 랜덤화"는 USV WTA 시뮬레이터에서 교전 결과보다 먼저 "기동·해상상태·구동 지연"의 충실도를 확보해야 한다는 설계 우선순위를 준다(T3의 USV 속도·해상상태 제약과 직결).
- 전투 군집 USV의 HILS/디지털트윈 WTA 검증 사례는 공개 문헌에 없으므로, 후속연구가 "Jetson급 엣지 HW-in-the-loop + 디지털트윈 + 추적가능 로그"를 갖춘 첫 공개 WTA VV&A 사례가 될 수 있다(기밀성으로 인한 공개 부재 가능성은 감안).

### Gaps
- NATO STO(AVT/SET/SCI) 보고서는 403으로 열지 못했다(MP-SCI-313-08 등). [확인 필요]
- CDAO T&E 원문(ai.mil)·DOT&E의 자율체계 시험 전략 원문은 접근 실패.
- Replicator 선정 체계의 자율 SW 시험 프로토콜, "Replicator sandbox"의 세부는 유료 기사(Inside Defense)로 미확인.
- 한국 국방부/ADD/방사청의 USV 자율성 V&V 지침 공개 문서는 찾지 못했다.

---

## KQ6. 비판자(ICRC, UNIDIR, 윤리학자, 한국 정책문헌)의 AI 무장할당 비판과, 선도 논문들이 이를 선제적으로 다루는 방식

### Takeaway
ICRC는 2025-12 입장문서와 2026-08 GGE 작업문서에서 (1) 예측불가 AWS 금지(ML 포함 시스템과 "certain swarm technologies"를 예시로 명시), (2) 대인 AWS 금지, (3) 표적을 "military objectives by nature"로 제한·시간/지리/교전횟수 제한·감독·개입·비활성화 요구를 제시했고, GGE 초안 para 39(c)는 predictability·reliability·traceability·explainability를 요구한다. SIPRI(2025)는 AI-DSS의 자동화 편향을, 미 의회(2026)는 DoDD 3000.09가 "AI 기반 표적화와 자율탄"의 속도를 따라가지 못한다고 지적했다. 선도 기술 논문들은 "인간 감독 하 보조", "지원 역할", "형식 검증·마스킹"으로 선제 대응하며, 연구자의 문제 설정(함정·고속정 등 '성질상 군사목표'만을 대상으로 하는 해상 교전)은 ICRC의 허용 범위와 정확히 겹친다.

### Cited Findings
- ICRC, "Autonomous Weapon Systems and International Humanitarian Law: Selected Issues", Position Paper, 2025-12. (요지) AWS는 이미 미사일·레이더·함정 등 성질상 군사목표에 대해 민간인이 없는 환경에서 주로 인간 감독 하에 사용되고 있으나, 군집 기술과 AI의 표적화 통합이 IHL 제한을 침식할 위험. "Complex swarm technologies may also exhibit emergent behaviours... predictability... will need to be based upon probability distributions... such machine learning-based AWS would likely be indiscriminate by nature." 신규 규칙은 (i) 사용자가 작동과 효과를 "understand, predict and explain"할 수 없는 예측불가 AWS 금지(예시: ML 포함, certain swarm technologies), (ii) 대인 AWS 금지, (iii) 성질상 군사목표로 표적 제한, 운용 기간·지리범위·교전 횟수(scale) 제한, 민간인 부재 상황으로 제한, 효과적 감독과 적시 개입·비활성화(불가 시 자폭/자기무력화) — [ICRC 2025 PDF](https://www.icrc.org/sites/default/files/2026-03/4896_002_Autonomous_Weapons_Systems_-_IHL-ICRC.pdf)
- ICRC, Working Paper to CCW GGE LAWS, 2026-08. GGE 2024–2026 초안 보고서(2026-07)의 요소들을 기준선으로 보존하라고 요구: para 25 LAWS 정의, para 31–34 금지(특히 para 32 효과를 예측·제한할 수 없는 LAWS 사용 금지), para 36 인간 판단·통제의 구체 조치 (a)–(d), para 38–39 수명주기 요건(현실적·가변적 운용환경에서의 T&E, 식별·선택·교전 기능의 예측가능성·신뢰성), para 39(c) predictability·reliability·traceability·explainability. 추가 제안: 35bis(사람의 존재·근접·접촉으로 격발되거나 표적 프로파일이 사람인 LAWS 개발·사용 금지), 36(b)bis(성질상 군사목표로 제한). 2026-11 제7차 검토회의에서 2027년 법적 구속력 있는 문서 협상 권한 부여를 촉구 — [ICRC Aug 2026 PDF](https://www.icrc.org/sites/default/files/2026-08/ICRC_working_paper_GGE_LAWS_August-2026-ICRC.pdf)
- (anchor) ICRC 2021-08-03 입장: 예측불가 AWS 금지, 대인 AWS 금지, 나머지 규제; "AI/ML로 critical functions를 제어하려는 시도가 증가하여 효과 예측·제한의 어려움을 악화" — [ICRC 2021](https://www.icrc.org/en/document/autonomous-weapons-icrc-recommends-new-rules)
- UNIDIR(Puscas 2022): HMI는 인간통제의 핵심이나 설계만으로 부족, AI/ML 학습체계의 고유 난제 — [UNIDIR](https://unidir.org/?p=9072)
- SIPRI(Blanchard & Bruun 2025-06): AWS(임무실행 단계 국한, 직접 위험)와 AI-DSS(표적선정 주기 전반, 자동화 편향에 의한 간접 위험)를 비교, 3개 권고(AI-DSS 전담 다자 프로세스 필요성 검토, AWS 거버넌스의 인간-기계 상호작용·감독·책무성 교훈 활용, 무력 사용 결정에서 인간 주체성을 지원하는 연구 추진). 국문 번역본 2025-11(피스모모) — [SIPRI 영문](https://www.sipri.org/publications/2025/other-publications/autonomous-weapon-systems-and-ai-enabled-decision-support-systems-military-targeting-comparison-and); [국문 PDF](https://www.sipri.org/sites/default/files/2025-12/ko_laws_v.pdf)
- DoDD 3000.09(2023-01-25): "select and engage targets without further intervention"(자율), 운용자가 표적 선정·교전을 승인(반자율), "appropriate levels of human judgment over the use of force", 고위급 심사(USD(P)·USD(R&E)·VCJCS 등)와 Autonomous Weapon Systems Working Group(CDAO·DOT&E 포함) — [Harvard IHRC](https://humanrightsclinic.law.harvard.edu/wp-content/uploads/2023/02/Review-of-the-2023-US-Policy-on-Autonomy-in-Weapons-Systems.pdf); [CRS IN12669](https://www.everycrsreport.com/reports/IN12669.html)
- Army Times 2026-05-20: Ernst·Slotkin 상원의원이 "AI-driven targeting with autonomous munitions"가 DoDD 3000.09가 예상한 속도를 넘어섰다며 정책 아키텍처의 확장을 요구, DAWG 예산 요청 $55B(현행 $225M) — [Army Times](https://development.armytimes.com/?p=84888)
- 한국: 국방부 AI 윤리원칙(2020-02-21 채택)은 의도치 않은 편견 최소화, 관계자의 기술·절차 이해, AI의 비의도 행동 감지·방지와 "오프 스위치"를 요구(2023-01-27 노컷뉴스의 DoDD 3000.09 개정 기사 중 국내 원칙 소개) — [노컷뉴스](https://www.nocutnews.co.kr/news/5885334)
- 한국 학술(KCI 검색 목록만 확인, 본문 미열람) [확인 필요]: 임예준, "자율무기체계 협약 논의의 쟁점과 전망", 법학논고, 2026, pp. 425–474; 김민혁·김재오, "자율살상무기체계에 대한 국제적 쟁점과 선제적 대응방향", 국방연구, 2020; 김보연, "인공지능을 통한 전쟁수행은 정당한가", 고려법학, 2022; 한정우, "치명적 자율무기체계(LAWS)의 공법적 규율 방안 연구", 성균관법학, 2025 — [KCI 검색](https://www.kci.go.kr/kciportal/po/search/poTotalSearList.kci?poSearchBean.keyword=%EC%9E%90%EC%9C%A8%EB%AC%B4%EA%B8%B0%EC%B2%B4%EA%B3%84%20%EC%9D%B8%EA%B0%84%ED%86%B5%EC%A0%9C). DBpia 동일 키워드 검색은 0건 — [DBpia](https://www.dbpia.co.kr/search/topSearch?searchOption=all&query=%EC%9E%90%EC%9C%A8%EB%AC%B4%EA%B8%B0%EC%B2%B4%EA%B3%84%20%EC%9D%B8%EA%B0%84%ED%86%B5%EC%A0%9C)
- 선도 논문의 선제 프레이밍 사례: Caballero & Jenkins(2024) "supporting roles rather than leading strategic decisions"; Scale/DIU "always under human oversight"; Lim et al.(2026) LLM 할당의 실행 전 형식 검증; HMCF(2025) "intervening only when necessary"; Elbaum & Panter(2025) 금지 대신 정렬 조치 — 출처는 KQ1 참조.
- 운용 맥락: Özyurt(퇴역 해군소장), "An Operational View on the USV Attacks in the Black Sea from an Admiral's Eyes", Naval News 2024-02-18. 우크라이나는 6–10척 패를 다방향 순차 타격으로 운용, 2,000–3,000야드 후방 예비대, Ivanovets의 AK-630 CIWS는 탐지 지연으로 무력, 조타·기관실 등 부위 정밀타격 — [Naval News](https://www.navalnews.com/?p=54371)

### Inferences
- 연구자의 시나리오(80 USV vs LCAC·PTG·PTB·LST 등 함정)는 ICRC가 "significantly lower risk"로 분류한 "military objectives by nature"에 대한 교전이며, 민간인 부재 해상 전장이다. 따라서 후속 논문의 서론·윤리 절에서 ICRC 2025/2026 문구를 직접 인용하여 (i) 대인 표적 배제, (ii) 성질상 군사목표 한정, (iii) 시간·지리·교전횟수 제한(롤링 호라이즌·ROE 마스크·교전 상한), (iv) 감독·개입·비활성화(human-on-the-loop veto, 자기무력화)를 설계 요구사항으로 명시하면 "규범 정합성"을 심사자에게 선제적으로 보일 수 있다.
- ICRC가 "ML 포함 시스템과 특정 군집 기술은 예측불가하여 성질상 무차별적일 수 있다"고 명시한 점은 MARL 기반 군집 WTA 연구의 가장 직접적인 규범적 반론이다. 이에 대한 기술적 응답은 (a) 행동 마스킹·형식 검증으로 금지행동의 확률 0 보장, (b) 예측가능성의 정량화(분포 외 시나리오에서의 성능 분포·CVaR 보고), (c) 추적가능 로그·설명(GGE 39(c))이며, T2·T5·VV&A 설계가 이 세 응답에 각각 대응한다. 논문에서 이를 "ICRC/GGE 요건 대응표"로 제시하는 것이 차별화된 프레이밍이다.
- SIPRI의 "AI-DSS 자동화 편향" 비판과 Shandler et al.(2026)의 "알고리즘 회피" 실증은 서로 긴장 관계에 있어, 후속연구가 XAI·veto 인터페이스의 효과를 실측하면 두 담론 모두에 기여하는 실증을 제공할 수 있다.

### Gaps
- 대한민국 정부의 CCW GGE 공식 입장문(2024–2026)과 국방부 "국방 AI 전략"·자율무기 관련 지침의 원문은 찾지 못했다. 국방정책연구·한국군사학논집의 개별 논문은 확인하지 못했다. [확인 필요]
- UNIDIR의 2024–2026 신규 보고서(AI 표적화 관련)는 확인하지 못했다(검색 예산 소진).
- ICRC 2026-08 문서가 인용한 GGE 초안(CCW/GGE.1/2026/CRP.1)의 원문 para 36(a)–(d)의 구체 조치는 직접 열지 못했다.
- 윤리학자 개별 논문(예: 자율무기 책임 공백 논의)은 본 리서치 범위에서 체계적으로 수집하지 못했다.

---

## 보조 질문. 후보 주제 T1–T7의 문헌 대비 위치(차별성·중복 위험·시의성)

### Takeaway
문헌상 공백이 가장 뚜렷한 것은 T2(DRO/CVaR 기반 불확실성 강건 WTA: 관련 arXiv 0건, CVaR WTA는 2019에 정지), T6(WTA의 self-play/공진화+착취가능성: 0건, 2026 미분게임 1건), T5(의도→제약 컴파일형 LLM-WTA: LLM-결정형 1건 존재, 컴파일형 0건)이다. T1(통신거부 완전분산 WTA)은 2024–2026 다중로봇 할당 문헌(CommHG, 학습형 CBBA, QMIX 재밍 대응)과 인접하여 "신규 모델"보다 "통신 거부·기만 모델링과 벤치마크"로 차별화해야 한다. T4(NCO+국소탐색 anytime)는 라우팅 NCO의 대규모 일반화 문헌(LEHD, ICAM)이 두터워 WTA로의 전이 자체는 신규지만 방법론 신규성 주장은 신중해야 한다. T3·T7은 운용적 시의성이 높으나(흑해 USV 전술, Replicator) 2024–2026 학술 공백 여부를 본 리서치에서 충분히 확인하지 못했다.

### Cited Findings
- T1 관련: Yuan, Wang, Yang, Min, "Communication-Aware Heterogeneous Graph Learning for Decentralized Multi-Human Multi-Robot Task Allocation", arXiv:2609.32935 (2026-09). 정보 가용성·연령에 조건화된 국소 그래프, "언제·누구에게 질의/공유할지"를 할당과 함께 협력 MARL로 공동최적화, 16로봇·6인간·112과업까지 확장 — [arXiv 2609.32935](https://arxiv.org/abs/2609.32935)
- T1 관련: Rodriguez, Tarawneh, Koenig, Dong, Lu, "Auction-Consensus Algorithm with Learned Bidding Scheme for Multi-Robot Systems", 23rd Int. Conf. on Ubiquitous Robots, 2026, arXiv:2605.21932. CBBA의 수작업 입찰함수를 PPO로 학습한 신경 입찰정책(NAM·LSTM·Set Transformer)으로 대체, MILP 최적해 근접도를 보상으로 사용, 다양한 군집 규모에서 고전 CBBA 상회 — [arXiv 2605.21932](https://arxiv.org/abs/2605.21932)
- T1 관련: Abolhassani, Erpek, Davaslioglu, Sagduyu, Kompella, "Coordinated Anti-Jamming Resilience in Swarm Networks via Multi-Agent Reinforcement Learning", arXiv:2512.16813 (2025-12). 반응형 재머에 대해 각 에이전트가 채널·전력을 선택, QMIX(CTDE)로 genie-aided 상한에 근접 — [arXiv 2512.16813](https://arxiv.org/abs/2512.16813)
- T1·T2 관련: Merkulov et al. AIAA 2024/2025(팀원 간 할당·성공확률 공유를 가정한 분산 RL WTA) — KQ3 참조.
- T4 관련: Luo et al., "Neural Combinatorial Optimization with Heavy Decoder: Toward Large Scale Generalization", NeurIPS 2023 (LEHD; TSP/CVRP 1,000 노드까지 근최적) — 검색 목록만 확인 [확인 필요]; Zhou, Lin, Wang, Tong, Yuan, Zhang, "Instance-Conditioned Adaptation for Large-scale Generalization of Neural Routing Solver", IEEE Trans. ITS 2026, arXiv:2405.01906(2024-05, 2026-06 v3). 인스턴스 조건화 적응 모듈로 수백~수천 노드 일반화, 빠른 추론 — [arXiv 2405.01906](https://arxiv.org/abs/2405.01906). arXiv API `"weapon target assignment" AND (transformer OR attention OR pointer)` → 0건. (검색 스니펫에 보인 "A transformer-based reinforcement learning approach for scalable weapon target assignment"는 원문 페이지 접속 시간초과로 서지 미확인 [확인 필요])
- T5 관련: Autenrieb & Ostermann 2025(LLM 결정형 WTA), Kim et al. 2025(USV 군집 MARL 인간 선호 정련), Peng et al. 2025·PIP-LLM 2025·Lim et al. 2026(의도→MILP/PDDL/검증) — KQ1 참조.
- T6 관련: Allen 2026, Czempin & Gleave 2022, Conflux-PSRO 2024, Beason et al. 2024, SBIR OSW26BZ02-DV004 — KQ4 참조.
- T3 관련: Özyurt 2024(다방향 순차 포화·CIWS 탐지지연) — KQ6 참조. 충돌시간제어 유도(impact-time-control) 계열 KAIST·Cranfield 문헌은 검색 목록에만 노출되고 원문 403으로 미열람 [확인 필요]. Schneider & Fichter 2025(가상표적 기반 다대다 유도, 철회) — KQ3 참조.
- T7 관련: 본 리서치에서 USV+UAV+UUV 이종 교차영역 WTA 2024–2026 논문은 확인하지 못했다(검색 예산 소진).
- 선행연구(b) 대비 공통: Kim et al.(2025)과 Beason et al.(2024)·SPLASH(2025)는 모두 USV 군집 학습 정책을 다루나 WTA/MRCPSPTW 정식화·3계층 하이브리드·DSR 지표를 쓰지 않으므로 선행연구(b)와는 문제 정의가 다르다.

### Inferences
- 우선순위 제안(문헌 공백·시의성·규범 정합·선행연구와의 비중복을 종합): (1) T2 — 공백이 가장 뚜렷하고 ICRC의 "예측가능성" 비판에 직접 응답(CVaR/DRO로 꼬리위험 보고)하며, 선행연구(b)의 결정론적 살상확률 가정을 명확히 넘어선다. (2) T6 — 선행연구(b)가 스스로 향후과제로 명시했으나 모델·실험이 전무한 영역이며, Czempin & Gleave식 착취가능성 지표와 Allen(2026)식 Bayesian 비교 보고가 차별 포인트. (3) T5 — "LLM-as-constraint-compiler + 형식 검증 + XAI + veto 실측"으로 정의하면 Autenrieb & Ostermann(결정형)·Kim et al.(선호 정련)과 구분되며, 미 의회·CRS·ICRC 담론과 가장 시의적. (4) T1 — CommHG·학습형 CBBA·QMIX 재밍을 기준선으로 "통신 거부·기만 그래프 모델"과 합의 없는 암묵적 충돌회피를 입증해야 하며, 선행연구(b)의 zero-masking 통신손실 처리와의 차이(단절 토폴로지·기만 메시지)를 명시해야 자기중복을 피한다. (5) T4 — 방법론 신규성보다 "WTA에 대한 규모 일반화 벤치마크(20→400)와 anytime 품질곡선"을 기여로 삼는 것이 안전. T3·T7은 운용적 가치가 크나 학술 공백 확인이 미완이므로 T2/T6/T5의 실험 시나리오(포화공격·이종 역할)로 흡수하는 방안을 권한다.
- 자기표절·중복게재 방지 관점: 후속연구는 (i) 목적함수(DSR 가중합)를 위험측도(CVaR-DSR) 또는 게임값(exploitability)으로 교체, (ii) 불확실성·적대성·의도 변환이라는 새 문제 변수를 정식화에 추가, (iii) 기준선을 2024–2026 문헌(CommHG, 학습형 CBBA, Allen 2026 미분게임, Autenrieb LLM-WTA)으로 갱신, (iv) 시나리오 로그의 추적가능성·부정요구사항 시험을 포함한 VV&A를 재설계해야 선행연구(b)·(d)와 문제 정의·모델·실험 세 측면에서 모두 구분된다.

### Gaps
- T3(동기화 포화공격 최적화)·T7(이종 교차영역)의 2024–2026 학술 공백 여부는 웹검색 예산 소진으로 확정하지 못했다. [확인 필요: Scopus/IEEE Xplore에서 "impact time" + "USV swarm", "heterogeneous" + "USV UAV UUV" + "assignment" 재검색]
- Transformer/attention 기반 확장가능 WTA 논문의 서지 미확인.
- Kim et al.(2025)·Autenrieb & Ostermann(2025)·Allen(2026)의 소속·게재 상태 미확인.
