# 07. 적대적 신규성 점검 (Adversarial Novelty Check): 후보 후속주제 T1–T7별 최근접 선행연구와 "이미 했다" 판정 위험

작성 기준일: 2026-10-05. 관점: 회의적인 심사자가 Google Scholar·arXiv·IEEE Xplore에서 30분 안에 찾아낼 최근접 선행을 먼저 찾는다. 노트 01(학습 기반 WTA 지도), 02(USV 군집 MARL), 03(국내 문헌), 04(프런티어 트렌드)에 이미 기록된 항목은 "(노트 0X)"로 표시하고 재조사하지 않았으며, 이 노트는 그 위에 **새로 발견한 최근접 경쟁작**(FORMICA 2026, UC-PSRO 2026, CA-CBBA 2022, ARFA 2025, Qian 2023 포화공격 할당, USV 포화공격 프리프린트 2024, ICORES 2026 통합방공 대상 WTA, WTA unknown hit rate 2023, DRAG 2026 기만 자원배분 게임, NCO 앵커 등)을 더한다.

접근 메모: 이번 세션에서 OpenAlex·Semantic Scholar 검색 API는 HTTP 429(공유 egress 속도제한)로 대부분 실패했고, Crossref 메타데이터/초록 API, arXiv API·abs 페이지, SciTePress 페이지는 직접 열었다. IEEE Xplore·ScienceDirect·Springer 본문은 열지 않았다(노트 01·02와 동일한 차단 조건). 초록을 열지 못하고 메타데이터만 확인한 항목은 "[메타데이터만]"으로, 검색엔진 요약만 본 항목은 "[스니펫]"으로 표시했다.

선행연구 약칭: (a) Lee et al. 2025 KNST 8(4) C2 개념설계, (b) Lee et al. 2026 KNST 9(2) MRCPSPTW + 휴리스틱→RL-VNS→GAT-MAPPO(CTDE) 3계층 하이브리드·80 vs 80·DSR, (c) Lee et al. 2025 KOSSE 21 MRCPSPTW 미사일 할당, (d) 석사논문(2026.3, (b)의 확장판).

---

## T1. 통신 거부·기만 하 완전 분산 학습형 할당: 누가 이미 했고 무엇이 남는가

### Takeaway
"통신 없이 학습으로 암묵 조정하는 다중로봇 과업할당"은 2026년 2월 FORMICA(ANTS 2026)가 정확히 그 문구로 선점했고, "통신 교란·attrition 하 GNN-MARL 회복탄력 조정"은 MAGEC(2024), "제한 대역폭·충돌 하 학습형 통신 스케줄링 CBBA"는 CA-CBBA(IEEE Access 2022), "통신 그래프 엣지 드롭아웃 커리큘럼으로 분산 fallback 학습"은 UC-PSRO(2026.8)가 이미 했다. 따라서 일반 MRTA 수준의 T1은 신규성이 거의 없다. 남는 니치는 **WTA 고유 구조(다대일·확률적 격파·감소수익 목적함수, 탄약·교전창)에서의 무통신/저통신 암묵 조정 + 의도적 재밍 기하·메시지 기만(spoofing)·그래프 분절을 명시적으로 모델링한 비교 벤치마크**다. 단, (b)가 이미 GAT-MAPPO CTDE와 "통신손실 제로마스킹"을 포함하므로(노트 03), 자기중복 위험은 중간 수준이다.

### Cited Findings
**(1) 최근접: 무통신 학습형 과업할당**
- Antonio Lopez, Jack Muirhead, Carlo Pinciroli, "FORMICA: Decision-Focused Learning for Communication-Free Multi-Robot Task Allocation", arXiv:2602.18622 (2026-02-20), ANTS 2026 게재 표기(13 pp.). 로봇 간 통신 없이 "팀원 입찰 분포를 예측"해 암묵 조정; Field-Oriented Regret-Minimizing Implicit Coordination Algorithm; 평균장 근사로 복잡도 O(NT)→O(T); Smart Predict-then-Optimize에서 착안해 "Task Allocation Regret"을 최소화하도록 예측기를 end-to-end 학습. 16 로봇·64 과업에서 해석적 평균장 기준 대비 시스템 보상 +17%·MILP 최적에 근접, 256 로봇·4,096 과업에서 +7%, 노트북에서 학습 21초. 초록이 "limited bandwidth, degraded infrastructure, or adversarial interference"에서 기존 방법이 급락한다고 명시 — [arXiv abs](https://arxiv.org/abs/2602.18622)
- Jialin Ying, Zhihao Li, Zicheng Dong, Guohua Wu, Yihuan Liao, "Less is More: Robust Zero-Communication 3D Pursuit-Evasion via Representational Parsimony", arXiv:2603.08273 (2026-03, IEEE 투고). 통신 지연·잡음이 취약성 원천이 된다는 문제의식에서 무통신 분산 추격 MARL의 표현 절약(parsimony)을 연구 — [arXiv API 레코드](https://arxiv.org/abs/2603.08273)
- Han Wang, Binbin Chen, Tieying Zhang, Baoxiang Wang, "Learning to Communicate Through Implicit Communication Channels", arXiv:2411.01553 (2024-11). 명시적 메시지 불가 상황에서 행동을 통한 암묵적 통신 학습(ToM 기반 방법의 한계 지적) — [arXiv API 레코드](https://arxiv.org/abs/2411.01553)

**(2) 통신 교란·attrition 하 학습형 회복탄력 조정**
- Anthony Goeckner, Yueyuan Sui, Nicolas Martinet, Xinliang Li, Qi Zhu, "Graph Neural Network-based Multi-agent Reinforcement Learning for Resilient Distributed Coordination of Multi-Robot Systems", arXiv:2403.13093 (2024-03-19; arXiv 코멘트상 "submitted to IEEE"). MAGEC: GNN 기반 MARL을 MAPPO로 학습, agent attrition·부분관측·"limited or disturbed communications" 하 전역목표 분산 조정; ROS 2 시뮬레이터 다중로봇 순찰(patrolling)에서 attrition·통신교란 실험 시 기존 방법 상회, 무교란 시 경쟁적. 과업은 순찰이며 WTA 아님. 노트 00에서 서지 일치 확인 — [arXiv abs](https://arxiv.org/abs/2403.13093)
- Phillip Jiang, "UC-PSRO: Utility-Conditioned Policy-Space Response Oracles with a Communication-Dropout Curriculum for Game-Theoretic Course-of-Action Generation in Adversarial Swarms", arXiv:2608.15372 (2026-08-15, 단독저자, 비심사 프리프린트). 세 번째 메커니즘이 "학습 중 통신 그래프 엣지 드롭아웃을 annealing하는 커리큘럼으로 완전연결 의존 대신 분산 P2P fallback 학습". 요약상 통신 드롭아웃 단독이 가장 큰 강건성 이득(성공률 35%→62%, 드롭아웃 0→0.75 조건 — 세부 해석 [확인 필요]) — [arXiv abs](https://arxiv.org/abs/2608.15372)

**(3) 통신제약 CBBA/경매 계열(학습 결합 포함)**
- Sharan Raja, Golnaz Habibi, Jonathan P. How, "Communication-Aware Consensus-Based Decentralized Task Allocation in Communication Constrained Environments", IEEE Access 10:19753–19767, 2022, DOI 10.1109/ACCESS.2021.3138857. CA-CBBA: 제한 대역폭·메시지 충돌 환경에서 에이전트가 공유 매체 접근을 스스로 스케줄·검열(censor)하도록 DRL로 학습, 임무상 중요한 메시지를 가진 에이전트를 우선; 밀집 영역 에이전트는 검열 — [Crossref](https://api.crossref.org/works/10.1109/access.2021.3138857); 초록은 [Semantic Scholar batch API](https://api.semanticscholar.org/graph/v1/paper/DOI:10.1109/access.2021.3138857)로 확인
- Rodriguez et al. 2026 학습형 입찰 CBBA(arXiv:2605.21932), Yuan et al. 2026 CommHG(arXiv:2609.32935, 16로봇·6인간·112과업) — (노트 04) [arXiv 2605.21932](https://arxiv.org/abs/2605.21932); [arXiv 2609.32935](https://arxiv.org/abs/2609.32935)
- Md Hasibuzzaman, "Trust-Gated Predictive Reallocation: A Bayesian Communication-Reliability Approach to Decentralized Multi-Robot Task Allocation Under Lossy Networks", Research Square 프리프린트 2026-07-31, DOI 10.21203/rs.3.rs-10380825/v1. 로봇별 왕복 통신신뢰도를 Bayesian(평판 모델)으로 연속 추정해 입찰을 할인하고 ack 타임아웃을 로봇별 적응 설정하는 분산 경매(TGPR); "통신신뢰도를 할당 결정 자체에 반영한 기존 연구 없음"을 주장 — [Crossref](https://api.crossref.org/works/10.21203/rs.3.rs-10380825/v1)
- Wang et al. 2026 JMSE 14(3):237(약한 음향통신 하 CBBA, 5개 통신 레짐, 연결 간헐 시 급락), Lott & Honary 2026 arXiv:2609.13711(6종 분산할당 × Bernoulli/Gilbert-Elliott/Rayleigh 25조건 벤치마크, 학습 기반 미포함) — (노트 01·02) [JMSE PDF](https://mdpi-res.com/d_attachment/jmse/jmse-14-00237/article_deploy/jmse-14-00237.pdf); [arXiv 2609.13711](https://arxiv.org/abs/2609.13711)

**(4) WTA 특화 분산(비학습/학습)**
- Hendrickson et al., "Decentralized Weapon-Target Assignment under Asynchronous Communications", JGCD 46(2):312–324, 2023 — 비동기·간헐 통신·attrition 하 분산 프라이멀-듀얼, 수렴률 보장, COTS 지상로봇 실험 (노트 01) — [UF PDF](https://corelab.mae.ufl.edu/papers/WTA.pdf)
- Merkulov et al., AIAA SciTech 2024(DOI 10.2514/6.2024-0125)·2025(DOI 10.2514/6.2025-1546) — 팀원 할당·성공확률 공유를 전제한 분산 RL WTA; RL이 그리디를 "근소하게" 상회 (노트 01·04) — [Haifa CRIS](https://cris.haifa.ac.il/en/publications/reinforcement-learning-based-cooperative-dynamic-weapon-target-as/)
- Yao et al. 2026 Research Square, "Decentralized Weapon-Target Assignment in Aerospace Defense Systems: An Attention-Enhanced MARL Approach", DOI 10.21203/rs.3.rs-10847429/v1 — 통신 모델 불명 (노트 01) — [Crossref](https://api.crossref.org/works/10.21203/rs.3.rs-10847429/v1)

**(5) 메시지 기만(적대적 통신)에 강건한 MARL**
- Yanchao Sun, Ruijie Zheng, Parisa Hassanzadeh, Yongyuan Liang, Soheil Feizi, Sumitra Ganesh, Furong Huang, "Certifiably Robust Policy Learning against Adversarial Communication in Multi-agent Systems", arXiv:2206.10158 (2022-06; 게재처 ICLR 2023으로 알려져 있으나 arXiv 레코드에 미표기 [확인 필요]). 악의적 공격자가 메시지를 조작할 때 통신 기반 정책의 인증 가능한 강건성 — [arXiv API 레코드](https://arxiv.org/abs/2206.10158)
- Wanqi Xue, Wei Qiu, Bo An, Zinovi Rabinovich, Svetlana Obraztsova, Chai Kiat Yeo, "Mis-spoke or mis-lead: Achieving Robustness in Multi-Agent Communicative Reinforcement Learning", AAMAS 2022, arXiv:2108.03803. MACRL의 적대적 통신 공격과 방어를 체계적으로 탐구 — [arXiv API 레코드](https://arxiv.org/abs/2108.03803)

**(6) 연구자 본인 선행과의 중첩**
- (b)는 GNN(3-layer GAT, 4-head, 128-dim)-MAPPO CTDE와 "통신손실 제로마스킹"을 이미 포함한다 — 출처: 노트 03 "자기표절·중복게재 위험 요소" 목록(연구자 2026 원고 정독 기반, 외부 URL 없음; 03_korea_domestic_research.md 92행)

### Inferences
- **"이미 했다" 판정을 부르는 제목/키워드**: "communication-free (multi-robot) task allocation", "implicit coordination for task allocation", "resilient distributed coordination under communication disturbance (GNN-MARL)", "communication-aware CBBA", "decentralized WTA under asynchronous/lossy communications", "communication-dropout curriculum", "robust MARL against adversarial communication". 이 중 어느 하나라도 제목 핵심어로 쓰면 FORMICA·MAGEC·CA-CBBA·Hendrickson·UC-PSRO·Sun 2022가 바로 대조된다.
- **선행이 아직 하지 않은 것(잔여 신규성)**: (i) FORMICA는 가산형(additive) 과업보상 기반 regret 최소화이고, WTA의 다대일·확률적 격파(1−Π(1−p)) 감소수익 구조에서 "몇 척이 같은 표적을 쏘아야 하는가"까지 암묵 조정하는지는 초록상 드러나지 않는다 [본문 확인 필요]. (ii) 의도적 재밍의 기하(재머 위치·출력 → SINR → 링크 단절)와 메시지 기만(spoofed bid/상태)을 동시에 넣은 할당 연구는 MRTA·WTA 모두에서 발견되지 않았다(노트 02 결론과 일치). (iii) 동일 통신 레짐 스윕에서 CBBA·CA-CBBA/학습형 입찰 CBBA·평균장 암묵조정(FORMICA형)·중앙 상한(BPC/MILP)을 한 표에 놓고 "분산화 비용(price of decentralization)" 곡선을 그린 WTA 연구는 없다.
- **방어 가능한 니치**: "확률적 다대일 WTA를 위한 무통신·저통신 암묵 조정 + 적대적 통신(재밍 기하·기만 메시지·분절) 모델 + 레짐 스윕 벤치마크". 핵심 주장을 "통신 없이 할당한다"가 아니라 "WTA의 감소수익·과잉사격(overkill) 구조에서 팀원 사격 예측이 어떻게 달라지는가"와 "기만 메시지 하에서 통신 의존 방법이 무통신 방법보다 나빠지는 임계점"에 두어야 한다.
- **자기중복 판정**: (b)의 CTDE+제로마스킹을 "분산 실행"으로 이미 주장했으므로, T1을 "(b)를 완전 분산으로 바꿨다"로 서술하면 증분(incremental) 판정을 받는다. (b)는 반드시 베이스라인(제로마스킹 CTDE)으로만 인용하고, 정식화를 MRCPSPTW에서 Dec-POMDP(+통신그래프 확률과정)로 교체해야 한다.

### Gaps
- FORMICA 본문(목적함수 형태, 다대일 할당 허용 여부, 이동표적·동적 재할당 여부)을 열지 않았다 [확인 필요]. T1 착수 전 반드시 정독해야 하는 1순위 문헌.
- MAGEC의 최종 게재처(arXiv "submitted to IEEE"; NSF PAR 사본 존재)를 확인하지 못했다 [확인 필요].
- Raja et al. 2022의 실험 규모·수치는 초록 수준만 확인.
- OpenAlex·S2 검색이 429로 막혀 IEEE TASE·RA-L의 "communication-constrained task allocation learning" 저널판 전수조사는 하지 못했다.

---

## T2. 불확실성 강건 동적 할당(격파확률·식별·기만체 불확실성, DRO/CVaR/Bayesian, 위험민감 RL)

### Takeaway
WTA에서 불확실성은 (i) 구간 격파확률 강건최적화(Park & El-Amine 2023), (ii) 불확실성이론(Li 2023), (iii) CVaR 다목적 진화알고리즘(Li·Chen·Xin 2019, 앵커), (iv) "격파확률 미지" DRL(Zhang & Wang 2023)로 다뤄졌고, 위험민감 협력 MARL(RMIX, CVaR QD-learning)과 CVaR 다중로봇 할당(Zhou & Tokekar; Sharma et al.)은 일반 영역에 이미 있다. 기만체는 배치·탐지 게임(Kulkarni 2024; Pan et al. 2026 DRAG; Meng 2025)으로만 다뤄졌다. **분포강건(DRO) WTA, CVaR 목적/제약을 가진 학습형 WTA, 식별 불확실성(진짜 표적/기만체/비전투선박) 신념을 가진 동적 재할당**은 이번 조사에서도 발견되지 않아 T2는 7개 후보 중 직접 경쟁작이 가장 적다. 다만 "risk-sensitive MARL" 알고리즘 자체는 신규성이 아니다.

### Cited Findings
**(1) WTA 특화 불확실성**
- Jungho Park, Hadi El-Amine, "The Robust Weapon Target Assignment Problem", Military Operations Research 28:27–51, 2023, DOI 10.5711/1082598328127 — 격파확률 구간 불확실성 강건최적화 (노트 01; 이번에 Crossref로 서지 재확인) — [Crossref](https://api.crossref.org/works/10.5711/1082598328127)
- Shizheng Zhang, Qingling Wang, "A Reinforcement Learning Method for the Weapon Target Assignment Problem with Unknown Hit Rate", 2023 China Automation Congress (CAC), pp. 900–905, DOI 10.1109/CAC59555.2023.10450202. "기존 WTA는 요격 성공확률이 모두 알려져 있다고 가정"을 비판하고 확률 미지 상황으로 SWTA 모델을 수정·MDP로 분해해 DRL 적용; 두 세트 실험에서 유효성·일반화 보고 — [Crossref](https://api.crossref.org/works/10.1109/cac59555.2023.10450202); 초록은 [Semantic Scholar batch API](https://api.semanticscholar.org/graph/v1/paper/DOI:10.1109/cac59555.2023.10450202)
- (앵커) Li, Chen, Xin, "Optimizing multi-objective uncertain multi-stage weapon target assignment problems with the risk measure CVaR", IEEE ICCA 2019, pp. 61–66 (노트 04) — [BIT Pure](https://pure.bit.edu.cn/en/publications/optimizing-multi-objective-uncertain-multi-stage-weapon-target-as/)
- Li, He, Zheng, Zheng, "Uncertain multi-objective dynamic weapon-target allocation problem based on uncertainty theory", AIMS Mathematics 8(3):5639–5669, 2023 (노트 01) — [AIMS](https://www.aimspress.com/article/doi/10.3934/math.2023284?viewType=HTML)
- Louis L. Chen et al., "Meeting Uncertain Threats with Feedback", arXiv:2607.13648 (2026) — 중화 결과 불확실 하 라운드별 효과기 배정 MDP, 단순정책 최적성/근사보장 (노트 01) — [arXiv](https://arxiv.org/abs/2607.13648)
- 국내 앵커: 이진호·신명인 2016(명중률 불확실성 추계 WTA) (노트 03).

**(2) 위험민감·위험인지 다중에이전트/다중로봇 할당**
- Wei Qiu, Xinrun Wang, Runsheng Yu, Xu He, Rundong Wang, Bo An, Svetlana Obraztsova, Zinovi Rabinovich, "RMIX: Learning Risk-Sensitive Policies for Cooperative Reinforcement Learning Agents", arXiv:2102.08159 (게재처는 NeurIPS 2021로 노트 04에 기록, arXiv 코멘트는 ICLR 2021 제출본 [확인 필요]). CTDE 가치기반 MARL에서 기대값(위험중립) Q가 보상 무작위성·환경 불확실성 하 협조 실패를 낳는다고 보고 CVaR 기반 위험민감 정책 제안 — [arXiv API 레코드](https://arxiv.org/abs/2102.08159)
- Al Maruf et al., "Risk-Aware Distributed Multi-Agent Reinforcement Learning", arXiv:2304.02005 (2023) — 분산 CVaR QD-learning, 합의 수렴 증명 (노트 04) — [arXiv](https://arxiv.org/abs/2304.02005)
- Lifeng Zhou, Pratap Tokekar, "Risk-Aware Submodular Optimization for Multi-Robot Coordination", arXiv:2003.10492 (2020; 저널판 게재처 [확인 필요]). CVaR을 쓰는 이산 부분모듈러 최대화로 불확실성 하 다중로봇 조합결정 — [arXiv API 레코드](https://arxiv.org/abs/2003.10492)
- Vishnu D. Sharma, Maymoonah Toubeh, Lifeng Zhou, Pratap Tokekar, "Risk-Aware Planning and Assignment for Ground Vehicles using Uncertain Perception from Aerial Vehicles", arXiv:2003.11675 (2020). 항공 인지의 불확실성 하 다중로봇·다중수요 위험인지 할당·계획(재난대응) — [arXiv API 레코드](https://arxiv.org/abs/2003.11675)
- Bo Fu, William Smith, Denise Rizzo, Matthew Castanier, Maani Ghaffari, Kira Barton, "Robust Task Scheduling for Heterogeneous Robot Teams under Capability Uncertainty", arXiv:2106.12111 (2021; 게재처 [확인 필요]). 과업 분해·할당·스케줄링을 동시에 최적화하는 확률계획 프레임워크 — [arXiv API 레코드](https://arxiv.org/abs/2106.12111)
- Pei et al., "Distributionally Robust Multi-Agent Reinforcement Learning for Intelligent Traffic Control", arXiv:2512.18558 (2025-12) — DR-MARL 자체는 타 응용(신호제어)에 존재함을 보여주는 사례 — [arXiv API 레코드](https://arxiv.org/abs/2512.18558)

**(3) 기만체·기만 전략**
- Longxu Pan, Yue Guan, Daigo Shishika, Panagiotis Tsiotras, "Asymmetric-Information Resource Allocation Games: An LP Approach to Purposeful Deception", arXiv:2604.25070 (2026-04). DRAG: 방어자가 진짜 자산과 여러 기만체에 자원을 배분해 공격자 신념을 조작, Perfect Bayesian Nash Equilibrium을 LP로 계산, "성능이 개선될 때만 기만하는" purposeful deception — [arXiv API 레코드](https://arxiv.org/abs/2604.25070)
- Kulkarni et al. 2024 arXiv:2407.14436(기만체 배치 + 전략합성, (1−1/e) 그리디 보장), Meng et al. 2025 arXiv:2504.03502(WTA 탐지 시나리오의 기만적 표적전환 식별) (노트 04) — [arXiv 2407.14436](https://arxiv.org/abs/2407.14436); [arXiv 2504.03502](https://arxiv.org/abs/2504.03502)
- (앵커, 2021) Tony A. Wood, Mitchell Khoo, Elad Michael, Chris Manzie, Iman Shames, "Temporal Logic Planning for Minimum-Time Positioning of Multiple Threat-Seduction Decoys", arXiv:2106.09252. 수상 자산 보호용 재사용 기만체의 최소시간 배치(다중 위협 동시 대응) — [arXiv API 레코드](https://arxiv.org/abs/2106.09252)

**(4) 검색 결과의 부재 증거**
- arXiv API(2026-10-05): `"distributionally robust" AND (multi-robot|multi-agent|multi-vehicle|UAV) AND (assignment|allocation)` → 교통신호 DR-MARL, UAV-MEC DR 기회제약, 계약설계 3건만 반환(할당·WTA 0건); `"chance-constrained" AND (task allocation|task assignment|target assignment)` → 0건 — [arXiv API 질의](http://export.arxiv.org/api/query?search_query=abs:%22chance-constrained%22)
- Crossref 질의 "distributionally robust weapon target assignment" / "chance-constrained weapon target assignment" → WTA 관련은 Park & El-Amine 2023 외에 DRO/기회제약 WTA 논문 없음(관련 없는 "Distributionally Robust Generalized Assignment Problem", Far East J. Appl. Math. 116:47–54, 2023만 노출) — [Crossref 질의](https://api.crossref.org/works?query.bibliographic=distributionally+robust+weapon+target+assignment)

### Inferences
- **"이미 했다" 판정을 부르는 제목/키워드**: "robust weapon target assignment"(Park & El-Amine), "WTA with unknown hit rate / uncertain kill probability via DRL"(Zhang & Wang), "CVaR-based WTA"(Li 2019), "risk-sensitive cooperative MARL"(RMIX), "risk-aware multi-robot assignment"(Zhou & Tokekar; Sharma), "decoy allocation game"(Kulkarni; Pan). 특히 "uncertain kill probability + DRL"만으로는 Zhang & Wang 2023과 겹친다.
- **잔여 신규성**: (i) 표적 **식별(class) 불확실성**(진짜 전투함/기만체/비전투선박)을 신념 상태로 갖고, 센서 갱신에 따라 재할당하는 동적 WTA — 기만체 문헌은 방어자 배치·탐지 쪽이고, 할당자(공격·교전 측)가 기만체 혼입 표적군을 상대하는 학습형 WTA는 없다. (ii) 격파확률 분포의 **모호성 집합(Wasserstein/모멘트)** 기반 DRO WTA는 OR 쪽에서도 공백. (iii) 위험지표를 "누출(leaker) 피해의 CVaR", "기만체 낭비사격률", "오인 교전(비전투선박) 확률"처럼 WTA 고유 꼬리위험으로 정의해 위험중립 정책((b)형)과 비교한 연구는 없다.
- **방어 가능한 니치**: "식별·기만 불확실성 하 군집 USV 동적 WTA: 신념 기반 재할당과 CVaR 위험민감 학습". 신규성 주장은 알고리즘(RMIX류)이 아니라 **문제정의(식별 신념 + 기만체 + 사격 후 평가 지연)와 위험지표·실험설계(기만체 비율·센서 잡음 스윕)**에 둬야 한다. 자기중복 측면에서 (b)의 결정론적 격파확률 가정을 명시적으로 넘어서므로 7개 중 가장 깨끗하다.
- 노트 04·09의 결론(ICRC "예측가능성" 비판에 대한 꼬리위험 보고, 운용분석가들이 지목한 표적 식별·오판 위험)과도 정합한다.

### Gaps
- Zhang & Wang 2023의 규모·베이스라인·"미지 확률"을 학습 중 어떻게 추정하는지 본문 미확인 [확인 필요].
- Scopus/IEEE Xplore에서 "distributionally robust" + "assignment" + "interceptor/weapon" 저널 검색은 429·차단으로 미수행(노트 04 Gaps와 동일) [확인 필요].
- RMIX·Zhou & Tokekar·Fu et al.의 최종 게재처 미확인.

---

## T3. 할당 + 궤적/도착시각 동기화(동시도착), 유한 교전용량 다층 방어 상대

### Takeaway
UAV·미사일 영역에서는 "할당+경로계획 동시 최적화"(Qie 2019 STAPP-MADDPG; Alqudsi 2024; Sheng 2026 DA-MAPPO), "동시·순차 도착을 결합한 WTA"(Volle & Rogers 2018), "포화공격용 할당 DRL"(Qian 2023), "할당+동시공격 통합유도"(Zhai & Yang 2023), "이기종 UAV 다방향 동시공격 할당"(Shahid 2025), "통합방공체계 상대 WTA"(Li et al. ICORES 2026)가 이미 있어 키워드 수준에서는 **매우 붐빈다**. USV에서도 "포화공격 + 과업할당 + 동시도착(베지어 경로)" 프리프린트(Chen et al. 2024)가 있다. 남는 것은 **방어 측의 유한 교전용량(사격채널·반응시간·재장전·탄창)을 큐/포화 모델로 할당 문제 안에 넣고, 해상상태 의존 속도·도착시각 불확실성을 결합한 USV 특화 정식화**다.

### Cited Findings
- (앵커) Kyle Volle, Jonathan Rogers, "Weapon–Target Assignment Algorithm for Simultaneous and Sequenced Arrival", JGCD 41(11):2361–2373, 2018, DOI 10.2514/1.G003515 — 무장 효과와 상대 도착시각을 결합한 비용함수, 접근속도 제한 하 도착시간 제약 (노트 01; 이번 Crossref 재확인) — [Crossref 질의](https://api.crossref.org/works?query.bibliographic=target+assignment+simultaneous+arrival+cooperative+attack+swarm)
- Han Qie, Dianxi Shi, Tianlong Shen, Xinhai Xu, Yuan Li, Liujing Wang, "Joint Optimization of Multi-UAV Target Assignment and Path Planning Based on Multi-Agent Reinforcement Learning", IEEE Access 7:146264–146272, 2019, DOI 10.1109/ACCESS.2019.2943253. MUTAPP를 다중에이전트 시스템으로 구성하고 MADDPG 기반 STAPP로 할당과 경로계획을 동시에 학습, 동적 환경 실시간 재계산 문제 해결 주장 — [Crossref](https://api.crossref.org/works/10.1109/access.2019.2943253); 초록 [S2](https://api.semanticscholar.org/graph/v1/paper/DOI:10.1109/access.2019.2943253)
- Feng Qian, Kai Su, Xin Liang, Kan Zhang, "Task Assignment for UAV Swarm Saturation Attack: A Deep Reinforcement Learning Approach", Electronics 12(6):1292, 2023, DOI 10.3390/electronics12061292. 포화공격 과업할당 수학모델 → MDP, 어텐션 정책망 + 정책경사 학습, 다양한 문제 규모에서 고품질 해·실시간성 — [Crossref(초록 포함)](https://api.crossref.org/works/10.3390/electronics12061292)
- Jinpeng Zhai, Jianying Yang, "An integrated cooperative guidance design for target assignment and simultaneous attack on multiple targets", International Journal of Control 97(10):2175–2188, 2023/2024, DOI 10.1080/00207179.2023.2260006. "통합 상대거리(integrated relative distance)" 지표를 정·역 두 관점에서 최소화하는 최적제어 협동유도로 할당과 다표적 동시공격을 1단계 통합, 각 표적이 최소 1기 공격자에 의해 파괴됨을 보장 — [Crossref](https://api.crossref.org/works/10.1080/00207179.2023.2260006); 초록 [S2](https://api.semanticscholar.org/graph/v1/paper/DOI:10.1080/00207179.2023.2260006)
- Sami Shahid, Ziyang Zhen, Umair Javaid, "Cooperative task assignment of heterogeneous unmanned aerial vehicles for simultaneous multi-directional attack on a moving target", Engineering Applications of Artificial Intelligence 139:109595, 2025, DOI 10.1016/j.engappai.2024.109595 (SSRN 선행판 10.2139/ssrn.4871984) [메타데이터만] — [Crossref](https://api.crossref.org/works/10.1016/j.engappai.2024.109595)
- Yunes Alqudsi, "Integrated Optimization of Simultaneous Target Assignment and Path Planning for Aerial Robot Swarm", The Journal of Supercomputing 81(1):95, 2024/2025, DOI 10.1007/s11227-024-06620-w [메타데이터만] — [Crossref](https://api.crossref.org/works/10.1007/s11227-024-06620-w)
- Yuanyuan Sheng, Xianan Xie, Huanyu Liu, Junbao Li, "Dynamic Target Assignment and Cooperative Decision-Making for UAV Swarms Based on Multiagent Reinforcement Learning", IEEE Internet of Things Journal 13(14):30640–30654, 2026, DOI 10.1109/JIOT.2026.3686066 (정정문 13:44002). DA-MAPPO: 온라인 최소비용 표적할당 모듈의 결과를 각 에이전트 국지관측에 삽입(assignment-augmented state)해 지각-할당-결정 통합 루프, 계층적 협력보상, 부분관측·이동표적·충돌회피 — [Crossref](https://api.crossref.org/works/10.1109/jiot.2026.3686066); 초록 [S2](https://api.semanticscholar.org/graph/v1/paper/DOI:10.1109/jiot.2026.3686066)
- **USV 특화**: Qiangqiang Chen, Baisheng Liu, Mingkai Yang, Haonan Guo, Changdong Yu, "Task allocation and saturation attack approach for unmanned surface vehicles", Authorea 프리프린트 2024-12-16, DOI 10.22541/au.173437408.80326280/v1. 적 USV 밀집도로 구역 분할 → 구역가치·아군 공격능력으로 할당(Logistic 카오스 맵 + 차분진화로 개선한 Grey Wolf Optimizer) → 최적매칭 + 베지어 곡선 동적 경로제어로 "균등 각도·동시 도착" 포위 포화공격. 학술지 게재 여부 [확인 필요]. 공저자 Changdong Yu는 노트 02의 대련해사대 USV 군집 대결 연구 저자 — [Crossref(초록 포함)](https://api.crossref.org/works/10.22541/au.173437408.80326280/v1)
- **유한 방어용량 상대**: Xiaozhan Li, Yuanhang Li, Yufan Deng, Jianing Li, Guangquan Cheng (NUDT 시스템공학원), "A Bidding-Collaborative Model for Weapon-Target Assignment against Integrated Defense Systems", Proc. 15th ICORES 2026, pp. 26–36, DOI 10.5220/0014236200004055. "과업공시→입찰→주문배정" 시장형 BCFS, 입찰을 이진계획으로 정식화하고 지휘전략을 목적함수로 변환; 적 레이더·방공/미사일요격 부대·지상 재밍장비를 공격하는 시나리오, Gurobi로 소규모 최적 타격계획 — [SciTePress](https://www.scitepress.org/Link.aspx?doi=10.5220/0014236200004055)
- Zheng et al., Drones 10(3):193, 2026 — UAV+USV+UUV 할당(GA) + 최소시간 최적제어(Radau 의사스펙트럼) 이중수준 (노트 02) — [PDF](https://mdpi-res.com/d_attachment/drones/drones-10-00193/article_deploy/drones-10-00193.pdf)
- Umut Demir, A. Sadik Satir, Gulay Goktas Sever, Cansu Yikilmaz, Nazim Kemal Ure, "Scalable Planning and Learning Framework Development for Swarm-to-Swarm Engagement Problems", arXiv:2212.02909 (AIAA SciTech 2023 채택 표기). 미분게임은 대규모 다중에이전트 추격회피로 확장 실패 → 적 군집 교전용 할당·궤적 계획 RL 프레임워크 — [arXiv API 레코드](https://arxiv.org/abs/2212.02909)
- 운용 맥락: Özyurt 2024(우크라이나 6–10척 다방향 순차 타격, AK-630 CIWS 탐지지연) (노트 04) — [Naval News](https://www.navalnews.com/?p=54371)

### Inferences
- **"이미 했다" 판정을 부르는 제목/키워드**: "joint (simultaneous) target assignment and path planning"(Qie; Alqudsi; Okumura & Défago 2023 AIJ의 MAPF판 STAPP), "WTA for simultaneous and sequenced arrival"(Volle), "saturation attack task assignment"(Qian 2023; Chen 2024 USV), "integrated cooperative guidance for assignment and simultaneous attack"(Zhai & Yang), "assignment-aware MARL"(Sheng 2026), "WTA against integrated defense systems"(Li 2026). USV를 붙여도 Chen et al. 2024가 "USV + task allocation + saturation attack + same-time arrival"을 이미 제목·초록에 갖고 있다.
- **잔여 신규성**: 위 문헌 어느 것도 (i) 방어 측의 **사격채널 수·반응시간·재장전/탄창을 갖는 큐(서비스 용량) 모델**을 할당 목적함수 안에 넣어 "포화 임계(salvo size vs. defender capacity)"를 최적화하지 않았고(Li 2026은 방어체계를 표적으로 다룰 뿐 용량 포화를 모델링한다는 기술이 초록에 없음), (ii) **해상상태 의존 속도·도착시각 불확실성**(USV 특유)을 동시도착 제약의 확률적 버전(기회제약 또는 CVaR)으로 다루지 않았으며, (iii) 다층 방어(장거리 미사일→함포→CIWS) 층별 교전창을 할당 단계에서 명시한 연구는 공개 학술 문헌에서 확인되지 않았다(노트 03: 국내도 없음).
- **방어 가능한 니치**: "용량제한 다층 함정방어 상대 USV 군집의 도착시각 조율형 WTA(확률적 해상상태 하)". 단, (b)가 80 vs 80 교전·시간창(MRCPSPTW)을 다뤘으므로 "시간창 + 할당"만으로는 자기중복이 된다 — 반드시 **공격 측 정식화 전환 + 방어 큐 모델 + 도착시각 불확실성**의 3요소가 함께 있어야 한다. 또한 공세(타격) 연구로 읽혀 윤리·보안 심사 리스크가 다른 후보보다 크다.

### Gaps
- Shahid 2025·Alqudsi 2024의 방법·규모·결과(초록) 미확인 [확인 필요].
- Chen et al. 2024(USV 포화공격)의 학술지 게재 여부·수치 미확인.
- 충돌시간제어(impact-time-control) 유도 + 할당 결합의 KAIST·Cranfield 계열은 노트 04에서도 미열람 [확인 필요].
- CIWS·함대공 사격채널의 공개 수치 모델 부재(노트 03과 동일).

---

## T4. 신경 조합최적화(NCO) warm start + 지역탐색, anytime, 규모 일반화

### Takeaway
WTA 전용 NCO는 2022–2026년에 이미 포화 상태다: Pointer Network RL(Na 2022), GNN+POMDP(Oh·Byeon·Cho·Kwon·Woo, IEEE TCYB 56(2):631–643, 2026 — **제1저자는 Oh, Seung Heon이며 "Byeon et al."은 오기**), Transformer RL로 소규모 학습 후 대규모 전이(Yoon·Lee·Cho ARFA, JDMS 2025), Joint-PointerPPO(Park & Kim SSRN 2025 / 박장희 석사 2026), 포인터+AC(Zou 2026), 포화공격 어텐션 정책(Qian 2023). 범용 NCO에서는 MatNet(행렬형 이분 관계 입력 — WTA의 Pk 행렬과 정확히 대응), Neural LNS, EAS·SGBS(시간예산 활용 = anytime)가 "construct-then-improve"를 이미 정립했다. 여기에 (b)의 "휴리스틱 초기해 → RL-guided VNS → 학습정책" 구조와 동형이라 **7개 중 경쟁도·자기중복 위험이 모두 가장 높다**.

### Cited Findings
**(1) WTA 특화 NCO/학습 정책**
- Seung Heon Oh, Geon Woong Byeon, Young-In Cho, Seungmin Kwon, Jong Hun Woo, "Artificial Intelligence in Combat Decision-Making: Weapon Target Assignment via Reinforcement Learning and Graph Neural Networks", IEEE Transactions on Cybernetics 56(2):631–643, 2026(2월호), DOI 10.1109/TCYB.2025.3610606. DRL을 DWTA의 SOTA로 전제하고 ① 위상관계 표현, ② 문제규모 확장성, ③ 성능지표 적합성의 한계를 GNN + 새 POMDP(그래프 기반 행동표현·관측특징·보상)로 해결; 해상·지상 복수 도메인에서 휴리스틱·메타휴리스틱과 비교 — [Crossref(저자 순서 확인)](https://api.crossref.org/works/10.1109/TCYB.2025.3610606); 초록 [S2](https://api.semanticscholar.org/graph/v1/paper/DOI:10.1109/TCYB.2025.3610606)
- Chaehwan Yoon, Jaejin Lee, Jaeyoung Cho, "A transformer-based reinforcement learning approach for scalable weapon target assignment", The Journal of Defense Modeling and Simulation (SAGE), online first 2025-09-20, DOI 10.1177/15485129251335043. ARFA(attention-based RL framework for assignment): 대규모 문제에서 선정된 정확해·휴리스틱 알고리즘을 상회, **소규모 구성에서 학습 후 대규모에 적용해도 성능 유지(규모 전이)**, 병렬계산 결합으로 해 산출 가속 — [Crossref(초록 포함)](https://api.crossref.org/works/10.1177/15485129251335043)
- Janghee Park, Jaeoh Kim, "A Fast and Scalable Transformer-Pointer Reinforcement Learning Framework for Weapon-Target Assignment", SSRN 5704099, 2025 / 박장희, 인하대 석사학위논문 2026(Joint-PointerPPO) (노트 01·03) — [SSRN](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5704099)
- Na, Ahn, Moon, JAIS 20(1):53–59, 2023(Pointer Network RL WTA); Zou et al., 信息与控制 55(2):292–305, 2026(Pointer + AC, 가변 규모, 동적 마스킹) (노트 01) — [OpenAlex](https://api.openalex.org/works/doi:10.2514/1.I011150); [Information and Control](https://xk.sia.cn/en/article/cstr/32166.14.xk.2025.3302)
- Qian et al., Electronics 12(6):1292, 2023 — 어텐션 정책 + 정책경사로 다양한 규모의 포화공격 할당 (위 T3) — [Crossref](https://api.crossref.org/works/10.3390/electronics12061292)
- Ziheng Wang, Xuewei Yu, Guangming Xie, Jianlei Zhang, "Regional-isolation-aware multi-agent target allocation via adaptive curriculum reinforcement learning and metaheuristic optimization", Swarm and Evolutionary Computation 108:102533, 2026-09, DOI 10.1016/j.swevo.2026.102533 — 제목상 "적응형 커리큘럼 RL + 메타휴리스틱" 결합 표적할당(학습+탐색 하이브리드) [메타데이터만; "regional isolation"이 통신 고립을 뜻하는지 [확인 필요]] — [Crossref](https://api.crossref.org/works/10.1016/j.swevo.2026.102533)
- 국내: 문우현 외 2026(한화시스템, attention·책임기반 보상 MARL-TEWA, 한국컴퓨터정보학회논문지 31(1):261–270) (노트 03).

**(2) 범용 NCO 앵커(심사자가 "그냥 X를 WTA에 적용"이라고 말할 근거)**
- (앵커) Wouter Kool, Herke van Hoof, Max Welling, "Attention, Learn to Solve Routing Problems!", ICLR 2019, arXiv:1803.08475 — 어텐션 인코더-디코더 + REINFORCE(greedy rollout baseline) — [arXiv API 레코드](https://arxiv.org/abs/1803.08475)
- Yeong-Dae Kwon, Jinho Choo, Byoungjip Kim, Iljoo Yoon, Youngjune Gwon, Seungjai Min, "POMO: Policy Optimization with Multiple Optima for Reinforcement Learning", NeurIPS 2020, arXiv:2010.16011 — [arXiv API 레코드](https://arxiv.org/abs/2010.16011)
- Yeong-Dae Kwon, Jinho Choo, Iljoo Yoon, Minah Park, Duwon Park, Youngjune Gwon, "Matrix Encoding Networks for Neural Combinatorial Optimization", NeurIPS 2021, arXiv:2106.11113. "두 집단 간 관계를 행렬로 정량화한" CO 문제(예: 비대칭 TSP, 유연 흐름공장)를 직접 입력받는 MatNet — **무장×표적 격파확률 행렬을 그대로 넣는 WTA NCO의 자연스러운 선행** — [arXiv API 레코드](https://arxiv.org/abs/2106.11113)
- André Hottung, Kevin Tierney, "Neural Large Neighborhood Search for the Capacitated Vehicle Routing Problem", ECAI 2020: 443–450, arXiv:1911.09539 — 학습된 repair 휴리스틱을 LNS에 통합 — [arXiv API 레코드](https://arxiv.org/abs/1911.09539)
- André Hottung, Yeong-Dae Kwon, Kevin Tierney, "Efficient Active Search for Combinatorial Optimization Problems", ICLR 2022, arXiv:2106.05126 — 추론 시 일부 파라미터만 인스턴스별 조정(규모·분포 일반화) — [arXiv API 레코드](https://arxiv.org/abs/2106.05126)
- Jinho Choo, Yeong-Dae Kwon, Jihoon Kim, Jeongwoo Jae, André Hottung, Kevin Tierney, Youngjune Gwon, "Simulation-guided Beam Search for Neural Combinatorial Optimization", NeurIPS 2022, arXiv:2207.06190 — "SOTA 신경 접근은 주어진 풀이시간을 충분히 활용하지 못한다"를 문제로 제기(= anytime 활용) — [arXiv API 레코드](https://arxiv.org/abs/2207.06190)
- Junyoung Park, Sanjar Bakhtiyar, Jinkyoo Park, "ScheduleNet: Learn to solve multi-agent scheduling problems with reinforcement learning", arXiv:2106.03051 (2021) — semi-MDP, 에이전트-과업 그래프 임베딩, 분산 의사결정으로 다중에이전트 스케줄링(makespan) — [arXiv API 레코드](https://arxiv.org/abs/2106.03051)
- Steve Paul, Payam Ghassemi, Souma Chowdhury, "Learning Scalable Policies over Graphs for Multi-Robot Task Allocation using Capsule Attention Networks", ICRA 2022, arXiv:2205.03321 — 마감·작업량·로봇 용량 제약 MRTA를 그래프 RL로, 비학습 방법 대비 성능·확장성 — [arXiv API 레코드](https://arxiv.org/abs/2205.03321)
- 대규모 일반화: LEHD(NeurIPS 2023), ICAM(arXiv:2405.01906) (노트 04) — [arXiv 2405.01906](https://arxiv.org/abs/2405.01906)
- 정확해 위협: Bertsimas & Paskov, NRL 72(5):735–749, 2025 — 정적 WTA 10,000×10,000을 노트북에서 초 단위 정확 해결 (노트 01) — [OpenAlex](https://api.openalex.org/works/doi:10.1002/nav.22249)

### Inferences
- **"이미 했다" 판정을 부르는 제목/키워드**: "transformer/attention-based RL for scalable WTA"(ARFA), "pointer network RL for WTA"(Na; Park & Kim; Zou), "GNN + DRL for DWTA"(Oh TCYB), "learning + metaheuristic hybrid for target allocation"(Wang SWEVO 2026; Zou ERA 2024; Yıldız 2026), "neural LNS / learned local search"(Hottung), "anytime NCO / making use of time budget"(SGBS, EAS). "Scale generalization 20→400"는 ARFA가 "small→large transfer"로 이미 주장했다.
- **(b)와의 중첩(자기표절 위험 최고)**: (b) = 리스트 스케줄링 초기해(0.5 s) → RL-guided VNS(2.0 s) → GAT-MAPPO(1.0 s). T4 = 신경 구성 초기해 → 지역탐색(시간예산) → anytime. 구조가 동형이고, "RL-guided VNS"는 "학습된 지역탐색"의 한 형태이므로 심사자는 "(b)의 Phase 1을 NCO로 바꾼 증분"으로 볼 가능성이 높다. 국내에서도 박장희 2026·문우현 2026과 겹친다(노트 03).
- **잔여 신규성(좁음)**: (i) WTA 하한(라그랑주/BPC 열생성 하한)으로 **시간-갭 곡선(anytime profile)을 인증**하는 연구는 없다(노트 01에서도 미발견). (ii) MatNet형 행렬 인코더를 WTA Pk 행렬에 적용 + EAS형 인스턴스 적응으로 20→400 일반화를 BPC 정확해 대비 갭으로 보고한 연구는 없다. 그러나 이는 "방법론 이식(engineering)"으로 읽히기 쉬워 OR·학습 최상위 심사에서 신규성 점수가 낮다.
- **방어 가능한 니치**: 단독 주제로는 권하지 않는다. T1/T2의 **하위 솔버 구성요소**(예: 중앙 상한 계산 또는 국지 재최적화기)로 흡수하고, 기여 주장은 하지 않는 편이 안전하다. 굳이 택한다면 "인증된 anytime 갭 + 공개 WTA 인스턴스(Andersen et al. 2022) 위 BPC 대비 비교"를 전면에 둬야 한다.

### Gaps
- Yoon·Lee·Cho(ARFA)의 소속·규모·비교 정확해 종류·갭 수치 미확인(SAGE 본문 미열람) [확인 필요].
- Wang et al. SWEVO 2026 초록 미확인(ScienceDirect 미열람, S2 초록 없음) [확인 필요].
- Park & Kim SSRN 본문 수치 미확인(노트 01과 동일).

---

## T5. 지휘관 의도 기반 할당: LLM이 ROE·우선순위를 목적함수 가중치·제약으로 변환 + XAI + Human-on-the-loop

### Takeaway
"LLM이 WTA를 직접 결정"은 Autenrieb & Ostermann(2025)이, "지휘관 의도 가중치 벡터로 단일 정책을 실행 시 재조정(FiLM 조건화)"은 UC-PSRO(2026.8)가, "자연어→MILP/PDDL 제약 생성 및 실행 전 논리검증"은 Peng 2025·PIP-LLM 2025·Lim 2026이, "자연어→보상함수"는 Eureka·Text2Reward가, "자연어→안전성 고려 군집 행동트리"는 CommandSwarm(2026)이, "language-to-objective synthesis"라는 문구 자체는 Saraev et al.(2026)이 이미 사용했다. 따라서 "LLM이 의도를 목적함수 가중치로 바꾼다"는 단독 신규성이 약하다. 남는 니치는 **ROE를 실행 가능한 hard constraint/행동마스크로 '컴파일'하고 형식검증(shield)으로 위반률 0을 보장하는 파이프라인 + 5초급 롤링 호라이즌과 양립하는 지연 예산 + 모호·적대적 명령에 대한 강건성 평가**다. 인간 신뢰 평가는 시뮬레이션만으로는 약하다.

### Cited Findings
- Johannes Autenrieb, Ole Ostermann, "Generalized Intelligence for Tactical Decision-Making: Large Language Model-Driven Dynamic Weapon Target Assignment", arXiv:2511.10207 (2025-11-13; IEEE TAES 투고) — LLM이 위협방향·자산우선순위·접근속도를 추론해 할당 생성, 초록상 정량치 없음 (노트 01·04; 이번 arXiv 최신순 스윕에서도 2025-11 이후 LLM-WTA 신규 프리프린트는 발견되지 않음) — [arXiv](https://arxiv.org/abs/2511.10207)
- Phillip Jiang, UC-PSRO, arXiv:2608.15372 (2026-08-15). 두 번째 메커니즘: "Blue 정책을 Commander's-Intent 가중치 벡터(학습 중 Dirichlet 표본)로 FiLM 조건화 → 재학습 없이 실행 시 재조정 가능". 요약상 효용조건화와 PSRO 추가가 수렴을 상당히 늦춤 — [arXiv abs](https://arxiv.org/abs/2608.15372)
- Kim, Lee, Park, Li, Park, "Human Implicit Preference-Based Policy Fine-tuning for Multi-Agent Reinforcement Learning in USV Swarm", arXiv:2503.03796 (2025) — USV 군집 MARL의 인간 선호 정렬, LLM 평가자 (노트 02·04) — [arXiv](https://arxiv.org/abs/2503.03796)
- Peng et al., arXiv:2503.13813 (2025; LLM으로 MRTA·스케줄링 MILP 자동구성, 제약추출 정확도 82%·코드 정확도 90%); Shi et al. PIP-LLM arXiv:2510.22784 (2025); Lim et al. arXiv:2604.17142 (2026; LLM 생성 과업할당의 시간논리·DES 실행 전 검증); OptiMUS arXiv:2310.06116; Eureka arXiv:2310.12931 (ICLR 2024); Text2Reward arXiv:2309.11489 (ICLR 2024) (노트 04) — [arXiv 2503.13813](https://arxiv.org/abs/2503.13813); [arXiv 2604.17142](https://arxiv.org/abs/2604.17142); [arXiv 2310.12931](https://arxiv.org/abs/2310.12931)
- Mohammed Majid, Amjad Yousef Majid, "CommandSwarm: Safety-Aware Natural Language-to-Behavior-Tree Generation for Robotic Swarms", arXiv:2605.07764 (2026-05). 모호한 사용자 의도를 미지원 행동·잘못된 프로그램·위험 계획 없이 실행 가능한 군집 행동트리로 변환 — [arXiv API 레코드](https://arxiv.org/abs/2605.07764)
- Ivan Saraev et al., "Agentic Language-to-Objective Synthesis for Optofluidic Assembly", arXiv:2605.27643 (2026-05). 인간 설계 의도를 실행 가능한 목적함수로 변환하는 병목을 "language-to-objective synthesis"로 명명(군사 아님) — [arXiv API 레코드](https://arxiv.org/abs/2605.27643)
- Sydney Johns, Heng Jin, Chaoyu Zhang, Y. Thomas Hou, Wenjing Lou, "ARMOR 2025: A Military-Aligned Benchmark for Evaluating Large Language Model Safety Beyond Civilian Contexts", arXiv:2605.00245 (2026-04-30). 신뢰성·법적 준수가 필요한 국방 의사결정 지원용 LLM 안전성 벤치마크(초록 앞부분만 확인) — [arXiv API 레코드](https://arxiv.org/abs/2605.00245)
- XAI 측: Liu et al. 2026 航空学报 47(8):332786 EHD-DQN(Grad-CAM+LIME 설명모듈, 방공 할당) (노트 01); Hamid, Saleh, El Ferik 2026 ICECET "XAI-Driven MARL for Swarm USV Continuous Multi-Target Hunting" [서지만] (노트 02) — [CJA](https://hkxb.buaa.edu.cn/EN/10.7527/S1000-6893.2025.32786)
- 비판: Rivera et al. FAccT 2024(LLM 확전 경향), Drinkall 2025(구별원칙 위반 16.7–66.7%), Shrivastava et al. 2024(결정 비일관성) (노트 04) — [arXiv 2401.03408](https://arxiv.org/abs/2401.03408); [arXiv 2510.03514](https://arxiv.org/abs/2510.03514)
- 연구자 선행 (a)는 "XAI 기반 human-on-the-loop HMI"를 개념 수준으로 이미 제시(과제 배경).

### Inferences
- **"이미 했다" 판정을 부르는 제목/키워드**: "LLM-driven WTA"(Autenrieb), "commander's intent-conditioned policy"(UC-PSRO), "LLM-generated reward"(Eureka/Text2Reward), "natural language to MILP/optimization model"(OptiMUS; Peng), "language-to-objective synthesis"(Saraev), "natural language to swarm behavior with safety"(CommandSwarm), "LLM-assisted COA generation"(COA-GPT), "explainable DRL for air defense allocation"(EHD-DQN).
- **잔여 신규성**: (i) ROE(교전규칙)·무력사용 제한을 **WTA 행동마스크/하드제약으로 컴파일**하고 형식검증으로 위반 불가를 보장, LLM 환각이 제약을 *느슨하게* 만드는 실패를 측정한 연구는 없다(Lim 2026은 제조 할당 검증, CommandSwarm은 행동트리). (ii) 의도 가중치 → 다목적 WTA 파레토 위치 변화의 **설명(대조적·반사실적 설명: "왜 이 표적을 먼저 쐈나")**을 할당 해에 붙인 연구도 미발견. (iii) 지연: LLM 호출을 롤링 호라이즌 바깥(임무 전·명령 변경 시)에 두고 실시간 루프에는 컴파일된 마스크/가중치만 쓰는 구조의 지연·안전 정량화가 없다.
- **방어 가능한 니치**: "LLM-as-ROE-compiler: 검증된 제약 컴파일 + 의도 가중 다목적 WTA + 반사실 설명". 단, UC-PSRO가 "의도 벡터 조건화 정책"을 이미 했으므로 하류(정책 조건화)는 기여로 주장하지 말고, **상류(자연어→검증된 제약)와 안전 지표(제약위반률, 모호명령 처리, 적대적 프롬프트 강건성)**에 기여를 집중해야 한다. 인간 신뢰는 실험참가자 연구(IRB)가 없으면 "신뢰" 대신 "설명 충실도(fidelity)·결정 일관성"으로 바꿔 측정하는 편이 심사에 안전하다.
- **자기중복**: (a)의 XAI-HOTL 개념을 구현·평가하는 형태이므로 개념 재서술을 피하면 중복 위험은 중간 이하.

### Gaps
- ARMOR 2025가 ROE 준수를 명시 항목으로 포함하는지 본문 미확인 [확인 필요].
- LLM-WTA의 2026년 저널판(Autenrieb & Ostermann의 TAES 게재 여부) 미확인.
- 대조적 설명(contrastive explanation)을 할당/스케줄링에 적용한 OR 문헌(예: 반사실적 최적화 설명)은 이번 조사에서 열지 못했다.

---

## T6·T7. Self-play/공진화 대 적응형 적군, 그리고 이기종 USV+UAV+UUV 교차영역 할당

### Takeaway
**T6**: 해양 군집 + 적응형 적군 + PSRO는 UC-PSRO(2026.8, 통합방공 위협 하 방어표적이 있는 합성 해양 시나리오, N=25–200)가 이미 했고, 그 결과는 "self-play의 착취가능성 이점이 고정상대 기준과 통계적으로 구별되지 않음"이라는 **부정적 결과**였다. 다중 USV self-play는 Rao et al.(Applied Intelligence 2025)과 Adv-TransAC 메타적응 상대(Xiong 2025, (b)의 베이스라인!)가, 드론 요격의 PFSP는 Gavin & Bronz(ICUAS 2026)가, 미분게임 기반 할당은 Allen(2026)이 다뤘다. 남는 것은 **WTA 결정 수준의 best-response 공격자(살보 구성·기만체 혼합·접근축)를 학습해 할당 정책의 착취가능성을 정량화**하는 것이다. **T7**: UAV+USV+UUV 교차영역 할당은 Zheng(Drones 2026, GA+최적제어) 외에 리뷰·추적·추격 연구만 있고 MARL 기반 교차영역 **무장·역할** 할당은 여전히 공백이지만, 단일 시뮬레이션 논문으로는 구현 부담이 크고 (b)가 향후과제로 선언했다.

### Cited Findings
**T6**
- Phillip Jiang, UC-PSRO, arXiv:2608.15372 (2026-08-15). PSRO self-play로 Blue·Red가 서로의 근사 best response로 학습; 미 공군 SBIR 공고에서 동기(파생 아님); 합성 해양 시나리오(통합방공 위협 하 방어표적) [시나리오 서술은 검색 요약 기준]; N=25에서 5 시드, N=200까지 확장; 소비자 GPU에서 N=200 기준 step당 한 자릿수 ms; **self-play의 착취가능성 이점이 고정상대 기준과 통계적으로 구별 불가**, PSRO·효용조건화 추가 시 수렴 둔화 — [arXiv abs](https://arxiv.org/abs/2608.15372); [검색 결과 PDF 링크](https://arxiv.org/pdf/2608.15372)
- Jinjun Rao, Cong Wang, Mei Liu, Jinbo Chen, Jingtao Lei, Wojciech Giernacki, "A deep reinforcement learning approach and its application in multi-USV adversarial game simulation", Applied Intelligence 55(7):591, 2025, DOI 10.1007/s10489-025-06380-x [Crossref 메타데이터 확인]. 방법(검색 요약): PPO에 ICM(내재 호기심)·self-play·POCA(사후 credit assignment)를 결합한 PPO-ICMSPPOCA, 가변 USV 수 대응; 노트 02 스니펫상 적군 승률 88.25/86.75/91.33% [스니펫]. 같은 저자군의 다자 비대칭 self-play(MASP, ELO 개선) 존재 [스니펫, 확인 필요] — [Crossref](https://api.crossref.org/works/10.1007/s10489-025-06380-x); [Poznan Univ. of Tech. 레코드](https://sin.put.poznan.pl/publications/details/i60695)
- Xiong et al., JMSE 13(8):1593, 2025 — Adv-TransAC: adversarial meta-learning + 자동 커리큘럼(규칙→DQN 사전학습 상대→메타 적응 상대), 학습 상대 조건 성공률 78.5% (노트 02). **(b)가 이를 베이스라인(DSR 72.2%)으로 이미 재현** — [PDF](https://mdpi-res.com/d_attachment/jmse/jmse-13-01593/article_deploy/jmse-13-01593.pdf)
- Timothée Gavin, Murat Bronz, "Intercepting an Agile Target with Net-Carrying Drones using Competitive Multi-Agent Reinforcement Learning", ICUAS 2026(Corfu), arXiv:2607.05939. 경쟁 MARL로 정식화, 상대 과적합·망각을 막기 위해 MAPPO + Prioritized Fictitious Self-Play(PFSP)로 추격자·회피자 동시 학습, 고충실도 시뮬레이터 — [arXiv API 레코드](https://arxiv.org/abs/2607.05939)
- Allen, arXiv:2609.04394 (2026) 미분게임 드론 군집 방어(방어성공 94.6→96.8%); Luo et al., IEEE TSMC-S 52(7):4426–4437, 2022 적대적 미사일-표적 할당 PODRL(앵커); Czempin & Gleave 2022(PBT 착취가능성); Conflux-PSRO 2024 (노트 04) — [arXiv 2609.04394](https://arxiv.org/abs/2609.04394); [BUAA](https://research.buaa.edu.cn/en/publications/learning-based-policy-optimization-for-adversarial-missile-target/)
- Demir et al., arXiv:2212.02909 (SciTech 2023) 군집 대 군집 교전 할당·궤적 RL 프레임워크 (위 T3) — [arXiv API 레코드](https://arxiv.org/abs/2212.02909)
- 수요 신호: ISL(독일-프랑스 생루이 연구소) 박사과제 공고 "Swarm Defense Strategies through Self-Play in Multi-Agent Reinforcement Learning" [검색 결과만] — [ISL](https://www.isl.eu/en/jobs/thesis/1343-phd-thesis-swarm-defense-strategies-through-self-play-in-multi-agent-reinforcement-learning)

**T7**
- Zheng, Liang, Zhang, Xiao, Zhang, "Research on Integrated Decision-Control Cooperative Target Assignment for Cross-Domain Unmanned Systems Based on a Bi-Level Optimization Framework", Drones 10(3):193, 2026 — UAV·USV·UUV 능력매칭 제약, 상위 개선 GA(최대 완료시간 최소화) + 하위 최소시간 최적제어, 향후과제로 동적 재할당·강건 다목적·대규모 분산 (노트 02) — [PDF](https://mdpi-res.com/d_attachment/drones/drones-10-00193/article_deploy/drones-10-00193.pdf)
- Bitao Jiang, Guanghui Wen, Jialing Zhou, Dezhi Zheng, "Cross-Domain Cooperative Technology of Intelligent Unmanned Swarm Systems: Current Status and Prospects", Strategic Study of CAE(中国工程科学) 26(1):117, 2024, DOI 10.15302/J-SSCAE-2024.01.015 — 교차영역 군집 협동기술 리뷰 [메타데이터만] — [Crossref](https://api.crossref.org/works/10.15302/J-SSCAE-2024.01.015)
- Hongzhi Wu, Miao Wang, Jingshi Wang, Guoqing Wang, "Distributed information fusion based trajectory tracking for USV and UAV clusters via multi-agent deep learning approach", Aerospace Systems 7(2):193–207, 2024, DOI 10.1007/s42401-024-00275-4 — 검색 요약상 action-constrained MADDPG로 해상-공중 분산 정보융합 궤적추적(할당 아님) [메타데이터 + 스니펫] — [Crossref](https://api.crossref.org/works/10.1007/s42401-024-00275-4)
- Shoucong Wang, Yong Xie, Xiaobo Liu, "Research on UAV-USV cooperative pursuit method based on deep reinforcement learning", Swarm and Evolutionary Computation 106:102433, 2026, DOI 10.1016/j.swevo.2026.102433 [메타데이터만] — [Crossref 질의](https://api.crossref.org/works?query.bibliographic=heterogeneous+UAV+USV+cooperative+target+assignment+reinforcement+learning)
- Sun et al., Defence Technology 2026, DOI 10.1016/j.dt.2026.07.002(이기종 화력요소 grabbing-order 할당) [서지만]; Mao et al. 2026 OGR-MARL arXiv:2608.12995(이기종 USV 역할조건 옵션) (노트 02) — [arXiv 2608.12995](https://arxiv.org/abs/2608.12995)
- Rui Zhang, Fuwang Dong, Wei Wang, "ISAC Empowered Air-Sea Collaborative System: A UAV-USV Joint Inspection Framework", arXiv:2511.02592 (2025-11) — UAV-USV 공동 점검 + 통신 유지(무장할당 아님) — [arXiv API 레코드](https://arxiv.org/abs/2511.02592)
- arXiv API 질의 `heterogeneous AND unmanned AND (cross-domain|air-sea|USV) AND (allocation|assignment)` → 위 ISAC 1건만 반환(2026-10-05) — [arXiv API 질의](http://export.arxiv.org/api/query?search_query=abs:%22heterogeneous%22%20AND%20abs:%22unmanned%22)

### Inferences
- **T6 "이미 했다" 키워드**: "PSRO/self-play for adversarial swarms"(UC-PSRO), "self-play multi-USV adversarial game"(Rao 2025), "adversarial meta-learning curriculum for multi-USV games"(Xiong 2025), "fictitious self-play interception"(Gavin & Bronz), "game-theoretic swarm defense assignment"(Allen 2026), "adversarial missile-target assignment"(Luo 2022).
- **T6 잔여 신규성**: 기존 self-play는 기동(추격·포위·요격) 수준이다. **할당 정책 자체를 표적으로 삼는 best-response 공격자**(살보 크기·도착 분산·기만체 비율·접근축을 선택)를 학습해 고정 정책((b)형)과 강건화 정책의 착취가능성(공격자 최적응답 이득)을 비교한 WTA 연구는 없다. 다만 UC-PSRO의 부정적 결과 때문에 심사자는 "self-play가 실제로 도움이 되는가"를 강하게 요구할 것이며, 통계적으로 유의한 차이를 보여주지 못하면 기여가 무너진다.
- **T6 자기중복**: (b)가 "적응형 적군 self-play"를 향후과제로 명시했고 Adv-TransAC를 베이스라인으로 썼으므로, T6 단독은 "(b)의 예고된 후속"으로 읽혀 신규성보다 연속성이 강조된다. T2의 기만체 모델과 결합해 "기만 전략을 학습하는 적"으로 쓰면 T2 논문의 강건성 검증 장(章)으로 흡수하는 편이 효율적이다(노트 02·04 결론과 일치).
- **T7 잔여 신규성**: MARL 기반 교차영역 무장·역할(타격/전자전/기만/ISR) 할당은 여전히 미발견. 그러나 UUV 음향통신·저속, UAV 체공시간 등 이종 동역학을 모두 넣는 시뮬레이터 비용이 크고, Zheng 2026이 "할당+운동학 실행가능성"을 이미 기준으로 세웠으므로 학습형 T7은 실행가능성 지표를 갖춰야 공정 비교가 된다. 단일 논문의 주제로는 범위가 과대하다.

### Gaps
- UC-PSRO 본문(Red 행동공간, 착취가능성 측정법, 통계검정 방식) 미열람 [확인 필요]. 단독저자 비심사 프리프린트라 인용 시 "preprint" 명시 필요.
- Rao et al. 2025 초록 원문(Springer) 미열람; 방법 서술은 검색 요약 기반 [확인 필요].
- 2024–2026 교차영역 MARL 할당의 IEEE TVT·TAES 저널판("UAV-USV-UUV networks for cooperative target hunting" 등)은 검색 요약에만 노출되어 서지를 특정하지 못했다 [확인 필요].

---

## 종합: 가장 방어 가능한 주제, 가장 붐비는 주제, 자기중복이 가장 큰 주제, 그리고 결합 프레이밍

### Takeaway
직접 경쟁작 수와 (b)·(d)와의 중첩을 함께 보면, **가장 방어 가능한 것은 T2(식별·기만 불확실성 + 위험민감 WTA)**, 그다음이 **WTA 특화로 좁힌 T1**이다. **가장 붐비는 것은 T4**(WTA 전용 NCO 6편 이상 + 범용 NCO 앵커)와 키워드 수준의 **T3**(UAV 동시도착·포화공격 할당 7편 이상, USV 프리프린트 1편)이다. **자기중복 위험이 가장 큰 것은 T4**((b)의 3계층 하이브리드와 동형), 그다음 T1((b)의 CTDE+제로마스킹), T6·T7((b)가 향후과제로 선언, Adv-TransAC 베이스라인)이다. UC-PSRO(2026.8)가 T1+T5+T6을 한 편에 묶었으므로 그 조합은 피해야 한다. **권고 결합은 T1+T2**("통신 거부·식별 기만 동시 하의 분산 위험민감 WTA")이며, 대안은 T3+T2(용량제한 방어 상대·도착시각 불확실성)다.

### Cited Findings
- T1 최근접: FORMICA 2026 [arXiv](https://arxiv.org/abs/2602.18622); MAGEC 2024 [arXiv](https://arxiv.org/abs/2403.13093); CA-CBBA 2022 [Crossref](https://api.crossref.org/works/10.1109/access.2021.3138857); UC-PSRO 2026 [arXiv](https://arxiv.org/abs/2608.15372); Hendrickson 2023 [UF PDF](https://corelab.mae.ufl.edu/papers/WTA.pdf)
- T2 최근접: Park & El-Amine 2023 [Crossref](https://api.crossref.org/works/10.5711/1082598328127); Zhang & Wang 2023 [Crossref](https://api.crossref.org/works/10.1109/cac59555.2023.10450202); RMIX [arXiv](https://arxiv.org/abs/2102.08159); DRAG 2026 [arXiv](https://arxiv.org/abs/2604.25070); Li·Chen·Xin 2019 [BIT Pure](https://pure.bit.edu.cn/en/publications/optimizing-multi-objective-uncertain-multi-stage-weapon-target-as/)
- T3 최근접: Volle & Rogers 2018; Qie 2019 [Crossref](https://api.crossref.org/works/10.1109/access.2019.2943253); Qian 2023 [Crossref](https://api.crossref.org/works/10.3390/electronics12061292); Chen et al. 2024 USV [Crossref](https://api.crossref.org/works/10.22541/au.173437408.80326280/v1); Li et al. ICORES 2026 [SciTePress](https://www.scitepress.org/Link.aspx?doi=10.5220/0014236200004055); Sheng 2026 [Crossref](https://api.crossref.org/works/10.1109/jiot.2026.3686066)
- T4 최근접: Oh et al. TCYB 2026 [Crossref](https://api.crossref.org/works/10.1109/TCYB.2025.3610606); Yoon et al. JDMS 2025 [Crossref](https://api.crossref.org/works/10.1177/15485129251335043); Park & Kim 2025 [SSRN](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5704099); MatNet [arXiv](https://arxiv.org/abs/2106.11113); SGBS [arXiv](https://arxiv.org/abs/2207.06190)
- T5 최근접: Autenrieb & Ostermann 2025 [arXiv](https://arxiv.org/abs/2511.10207); UC-PSRO 2026; Peng 2025 [arXiv](https://arxiv.org/abs/2503.13813); CommandSwarm 2026 [arXiv](https://arxiv.org/abs/2605.07764); Lim 2026 [arXiv](https://arxiv.org/abs/2604.17142)
- T6/T7 최근접: UC-PSRO 2026; Rao 2025 [Crossref](https://api.crossref.org/works/10.1007/s10489-025-06380-x); Xiong 2025 [PDF](https://mdpi-res.com/d_attachment/jmse/jmse-13-01593/article_deploy/jmse-13-01593.pdf); Gavin & Bronz 2026 [arXiv](https://arxiv.org/abs/2607.05939); Zheng 2026 [PDF](https://mdpi-res.com/d_attachment/drones/drones-10-00193/article_deploy/drones-10-00193.pdf)
- 인용 정정: "Byeon et al. 2026 IEEE Trans. Cybernetics 56(2):631–643"의 제1저자는 Seung Heon Oh(Byeon은 제2저자)이며, 노트 00도 이 논문의 다른 오기(학술지·권호·저자) 사례를 "EXISTS-DETAILS-WRONG"으로 기록했다 — [Crossref](https://api.crossref.org/works/10.1109/TCYB.2025.3610606)

### Inferences
**(1) 주제별 판정표(직접 경쟁작 수 / 자기중복 위험 / 단일 시뮬레이션 논문 실현성)**
- T1: 경쟁 중~높음(일반 MRTA 수준에서는 FORMICA·MAGEC·CA-CBBA·UC-PSRO가 선점; WTA 특화 무통신 학습은 공백) / 자기중복 중간((b)의 GAT-MAPPO CTDE·제로마스킹) / 실현성 높음.
- T2: 경쟁 낮음(WTA 특화 학습형은 Zhang & Wang 2023 CAC 1편, OR은 Park & El-Amine 2023) / 자기중복 낮음((b)의 결정론적 Pk 가정을 넘어섬) / 실현성 높음.
- T3: 경쟁 높음(UAV 동시도착·포화 할당 다수, USV 프리프린트 1편) / 자기중복 중간(시간창 정식화 재사용 위험) / 실현성 중간(방어 큐 모델 가정 필요), 윤리·보안 리스크 상대적으로 큼.
- T4: 경쟁 매우 높음(WTA NCO 6편+, 국내 2편, 범용 NCO) / 자기중복 최고 / 실현성 높으나 신규성 낮음.
- T5: 경쟁 중간(LLM-WTA 1편, 의도조건화 1편, NL→MILP/BT 다수) / 자기중복 중간 이하((a) 개념 구현) / 실현성 중간(인간 평가 없이 "신뢰" 주장 불가).
- T6: 경쟁 중간(UC-PSRO·Rao·Xiong; 부정적 결과 선행) / 자기중복 중간 이상(향후과제 선언·Adv-TransAC 베이스라인) / 실현성 중간(학습 비용).
- T7: 경쟁 낮음(학습형 교차영역 무장할당 공백) / 자기중복 중간(향후과제 선언) / 실현성 낮음(범위 과대).

**(2) 권고 결합 A — T1+T2 (가장 신규·실현 가능)**: 가제 예시 "Risk-Sensitive Decentralized Weapon-Target Assignment for USV Swarms under Communication Denial and Target-Identification Deception" (국문: "통신 거부·식별 기만 환경에서 군집 USV의 위험민감 분산 무장할당"). 차별 요소: (i) 정식화를 MRCPSPTW → **통신그래프 확률과정 + 표적 class 신념을 가진 Dec-POMDP**로 교체; (ii) 무통신/저통신 암묵 조정(FORMICA의 팀원 입찰 예측 아이디어를 **다대일 확률적 격파 목적**으로 확장)과 **기만 메시지·기만체**에 대한 강건성; (iii) **CVaR(누출 피해)·기만체 낭비사격률·오인 교전률**을 1차 지표로, 통신 레짐(Wang 2026 JMSE 프로토콜·Lott & Honary 3종 손실모델) × 기만체 비율 2차원 스윕; (iv) 베이스라인은 CBBA, CA-CBBA 또는 학습형 입찰 CBBA, 평균장 암묵조정, (b)의 제로마스킹 CTDE(인용만), 완전정보 중앙 BPC/MILP 상한; (v) "분산화 비용"과 "불확실성 비용"을 분리 보고. 이 조합은 문제정의·모델·실험 세 축 모두에서 (b)·(d)와 분리된다.

**(3) 대안 결합 B — T3+T2**: "용량제한 다층 함정방어 상대, 해상상태 의존 도착시각 불확실성 하 군집 USV의 기회제약/CVaR 도착조율 WTA". 신규성은 방어 큐 모델 + USV 도착 불확실성에 있으나, Qian 2023·Chen 2024와의 차별을 1페이지 안에 명확히 해야 하고 공세 연구로서 심사·보안 부담이 있다.

**(4) 피해야 할 결합**: T1+T5+T6(UC-PSRO가 이미 결합), T3+T4(둘 다 붐빔 + T4 자기중복), T4 단독(“(b) Phase 1의 NCO 교체”로 읽힘), T7 단독(범위 과대).

**(5) 제목·초록에서 피해야 할 표현(심사자 트리거)**: "communication-free task allocation", "resilient GNN-MARL coordination", "transformer-based scalable WTA", "joint target assignment and path planning", "saturation attack task assignment", "LLM-driven WTA", "commander's intent-conditioned policy", "self-play for adversarial swarms", "robust WTA". 대신 WTA 고유 구조어(다대일 확률적 격파, 누출 피해 CVaR, 식별 신념, 기만 메시지, 분산화 비용)를 핵심어로 쓰는 편이 안전하다.

### Gaps
- FORMICA·UC-PSRO 본문 정독 전에는 T1+T2 결합의 "다대일 확률적 격파로의 확장"이 정말 비어 있는지 최종 확정할 수 없다 [확인 필요 — 착수 전 필수].
- IEEE Xplore·ScienceDirect·Springer 본문 차단과 OpenAlex·S2 검색 429로, 2025–2026 저널판(특히 IEEE TASE, RA-L, TAES, Defence Technology)의 전수 검색은 불완전하다. 최종 원고 전 Scopus/WoS에서 "weapon target assignment" AND (communication OR jamming OR decoy OR "distributionally robust" OR CVaR) 재검색 필요.
- Shahid 2025, Alqudsi 2024, Wang SWEVO 2026, Rao 2025의 초록 원문 미확인.
