# 06. 투고 학술지·학술대회 선정 및 심사자 기대 기준 (군집 USV 무장할당 AI/OR 논문, 2026-10-05 기준)

> 조사 방법 메모: 이 세션은 WebSearch 예산이 소진된 상태였고, ScienceDirect·Wiley·SAGE·MDPI·Scimago·COPE·ACM·OpenAlex 등 주요 사이트가 봇 차단(403/429)으로 열리지 않았다. 따라서 (1) IEEE Xplore 메타데이터 API, IEEE Open/AESS/MORS/SCS 공식 페이지, Elsevier APC 공식 가격표(xlsx, 2026-10-05 기준), KeAi 공식 페이지, DOAJ API, Crossref API, 국내 학회 공식 사이트(KIMST·KORMS·시뮬레이션학회) 등 **열람에 성공한 1차 자료**와 (2) JIF·백분위는 WoS 데이터를 재게시하는 집계 사이트(wos-journal.info, bioxbio)를 **2차 자료로 명시**하여 사용했다. 집계 사이트 수치는 모두 [확인 필요] 표기. 논문 "증거" 목록은 Crossref 메타데이터 레코드(제목·저자·권호·DOI)를 직접 조회한 것으로, **본문은 열람하지 않았으므로 방법·결과 요약은 생략**하고 서지 정보만 적었다.

---

## KQ1. 국제 학술지 18종: 범위·JIF/분위·심사기간·APC·OA·주제 적합성 증거

### Takeaway
IEEE TAES(JIF 7.0, 심사 약 60일, APC $2,800)·IEEE TSMC: Systems(JIF 8.4)·Defence Technology(JIF 6.4, APC 없음, 완전 OA)·EAAI(JIF 9.0)·ESWA(JIF 9.4)·Ocean Engineering(JIF 6.3)이 "WTA/군집/국방 AI" 주제의 **최근(2023–2026) 게재 실적과 높은 영향력**을 동시에 갖춘 1군이다. OR 정통 저널(NRL·MOR·C&OR)은 영향력 지수는 낮지만 WTA 정확해법·강건 WTA의 본거지이고, JDMS는 ESCI(JIF 1.3)지만 2025년 transformer-RL WTA 논문이 실린 국방 M&S 전용 지면이다.

### Cited Findings

#### (1) 학술지 선정표 (JIF = wos-journal.info "2026 업데이트" 수치 = JCR 2025로 추정 [확인 필요]; 괄호 = bioxbio 게시 JCR 2024 [확인 필요]; 분위는 백분위 순위에서 추정)

| 학술지 | WoS 색인 / JIF(최신) / 최우수 카테고리 백분위 → 추정 분위 | CiteScore | OA·APC | 심사·발행 | 2020–2026 WTA/군집/국방 게재 증거(Crossref) |
|---|---|---|---|---|---|
| IEEE Trans. Aerospace and Electronic Systems (TAES) | SCIE / **7.0** (5.7) / 93.2% → Q1 | 9.4 | Hybrid, APC **USD 2,800** | "typical review cycles in the order of 60 days", 연 6회, EIC Gokhan Inalhan | Huang, Li, Zhang (2026) "A Coupled Two-Stage Dynamic Weapon-Target Assignment for Attacking a Fleet Formation Under Limited Weapon Resources", TAES 62:16847–16856, doi:10.1109/TAES.2026.3719617 |
| IEEE Trans. SMC: Systems | SCIE / **8.4** (8.7) / 89.8% → Q1 | 17.8 | Hybrid, APC USD 2,800 | 연 12회, EIC Huijun Gao | WTA 직접 히트 없음(검색 범위 내) [확인 필요] |
| IEEE Access | SCIE / **4.2** / 66.4% → Q2 | 9.3 | Full OA, APC **USD 2,160** (2026) | "binary" 심사(Accept/Reject), 신속 출판 | 다수: Sung, Lee, Song (2026) "Cluster-Based Weapon-Target Assignment for Large-Scale Drone Swarms" 14:105236–105256; Li, He, Xu (2023) "Weapon-Target Assignment Strategy in Joint Combat Decision-Making Based on Multi-Head Deep Reinforcement Learning" 11:113740–113751; Liu, Li, Wang (2023) "A Time-Driven Dynamic Weapon Target Assignment Method" 11:129623–129639; Kim, Lee, Yi (2022) 10:43738–43750; Wu, Chen, Ding (2021) 9:71832–71848; Huang, Li, Yang (2021) 9:139668–139684 |
| Ocean Engineering | SCIE / **6.3** (5.5) / 96.2% → Q1 | – | Hybrid, APC **USD 4,720** | 심사기간 미확인 [확인 필요] | Zhuang, Long, Zhang (2024) "Research on task allocation for multi-type task of unmanned surface vehicles" 308:118321; Sun, Sun, Li (2022) "An innovative distributed self-organizing control of unmanned surface vehicle swarm with collision avoidance" 254:111342 |
| J. Marine Science and Engineering (MDPI) | SCIE / **3.2** / 74.6% → Q2(경계) | – | Full OA, APC **CHF 2,600** (DOAJ) | 미확인 [확인 필요] | Luo, Zhang, Zhuang (2024) "Intelligent Task Allocation and Planning for USV Using Self-Attention Mechanism and Locking Sweeping Method" 12(1):179; Xue, Huang, Wang (2021) "An Exact Algorithm for Task Allocation of Multiple USVs with Minimum Task Time" 9(8):907 |
| Defence Technology (KeAi/Elsevier, China Ordnance Society) | SCIE / **6.4** / 92.7% → Q1 | 11 | Full OA, **APC 없음**(DOAJ has_apc=False; Elsevier 가격표 "Subsidized"), CC BY-NC-ND | 월간 | Bi, Wang, Xu (2025) "Weapon-target assignment for unmanned aerial vehicles: A multi-strategy threshold public goods game approach" 48:221–237, doi:10.1016/j.dt.2025.01.014 |
| Expert Systems with Applications | SCIE / **9.4** (7.5) / 94.5% → Q1 | – | Hybrid, APC **USD 3,630** | 미확인 | Ismail, Song, Ouelhadj (2025) "Unmanned surface vessel routing and UAV swarm scheduling for off-shore wind turbine blade inspection" 284:127534; Ju, Wang, Chen (2027 issue) "A risk-aware segment-learning evolutionary optimization method for heterogeneous UAV swarm task allocation" 333:134181 |
| Engineering Applications of AI | SCIE / **9.0** (8.0) / 96.6% → Q1 | – | Hybrid, APC **USD 3,040** | 미확인 | Li, Wu, Wang (2024) "A comprehensive survey of weapon target assignment problem: Model, algorithm, and application" 137:109212; Acar, Hatipoğlu, Yılmaz (2023) "A quantum algorithm for solving weapon target assignment problem" 125:106668; Wang, Fu, Wei (2023) "Unmanned ground weapon target assignment based on deep Q-learning network with an improved multi-objective artificial bee colony algorithm" 117:105612; Wang, Mao, Wei (2025) USV swarm target detection 139:109679 |
| Computers & Operations Research | SCIE / **4.6** (4.3) / 77.1% → Q1 | – | Hybrid, APC **USD 3,260** | 미확인 | 검색 범위 내 WTA 직접 히트 없음 [확인 필요]; 대신 Computers & Industrial Engineering에 WTA 3편(Ma et al. 2021 162:107717; Chang et al. 2023 181:109303; Tashakori et al. 2024 "Dynamic soft-kill weapon-target assignment in naval environments" 197:110606) |
| J. Defense Modeling and Simulation (SAGE/SCS) | **ESCI** / **1.3** / 38.8% → Q3 | – | Hybrid(APC 미확인) | 계간 refereed | Yoon, Lee, Cho (2025) "A transformer-based reinforcement learning approach for scalable weapon target assignment", doi:10.1177/15485129251335043 |
| Military Operations Research (MORS) | SCIE / **0.3** / 0.9% → Q4 | – | 구독형; 비회원 온라인 $100 | 미확인 | Park, El-Amine (2023) "The Robust Weapon Target Assignment Problem" 28:27–51, doi:10.5711/1082598328127 |
| Naval Research Logistics (Wiley) | SCIE / **2.3** (2.1) / 49.5% → Q3(경계) | – | Hybrid(APC 미확인) | 미확인 | Bertsimas, Paskov (2025) "Solving Large-Scale Weapon Target Assignment Problems in Seconds Using Branch-Price-And-Cut" 72:735–749, doi:10.1002/nav.22249 |
| Aerospace Science and Technology | SCIE / **6.4** (5.8) / 88.1% → Q1 | – | Hybrid, APC **USD 4,280** | 미확인 | 검색 범위 내 WTA 직접 히트 없음 [확인 필요] |
| Swarm and Evolutionary Computation | SCIE / **9.6** / 93.8% → Q1 | – | Hybrid, APC **USD 3,160** | 미확인 | Gao, Gao, Zhou (2024) "Artificial intelligence algorithms in unmanned surface vessel task assignment and path planning: A survey" 86:101505 |
| Applied Soft Computing | SCIE / **7.8** (6.6) / 86.5% → Q1 | – | Hybrid, APC **USD 3,270** | 미확인 | Xu, Zhang, Bi (2024) "Dynamic Gaussian mutation beetle swarm optimization method for large-scale weapon target assignment problems" 162:111798; Sun, Zeng, Zhu (2024) multi-AUV confrontational task allocation 153:111295 |
| Journal of Field Robotics (Wiley) | SCIE / **5.1** (5.2) / 66.7% → Q2 | – | Hybrid(APC 미확인) | 미확인 | 히트 없음(필드 실험 중심) [확인 필요] |
| Autonomous Agents and Multi-Agent Systems (Springer) | SCIE / **2.4** (2.6) / 50% → Q2/Q3 경계 | – | Hybrid(APC 미확인) | 미확인 | 히트 없음 [확인 필요] |
| Simulation Modelling Practice and Theory | SCIE / **4.6** (4.6) / 78.9% → Q1 | – | Hybrid, APC **USD 2,970** | 미확인 | 히트 없음 [확인 필요] |

출처:
- IEEE TAES/TSMC:S/Access의 JIF·CiteScore·APC·범위: IEEE Xplore 메타데이터 API — [TAES pubid=7](https://ieeexplore.ieee.org/rest/publication/home/metadata?pubid=7), [TSMC:S pubid=6221021](https://ieeexplore.ieee.org/rest/publication/home/metadata?pubid=6221021), [IEEE Access pubid=6287639](https://ieeexplore.ieee.org/rest/publication/home/metadata?pubid=6287639). TAES 범위 원문: "focuses on the organization, design, development, integration, and operation of complex systems for space, air, ocean, or ground environment … navigation, avionics, spacecraft, aerospace power, radar, sonar, telemetry, defense, transportation, automated testing, and command and control." TSMC:S 범위: "systems engineering … decision making … optimization, modeling and simulation." IEEE Access: "reviews are 'binary' … Accept or Reject."
- TAES 심사기간·APC·투고 시스템: [IEEE AESS TAES 페이지](https://ieee-aess.org/publications/taes) — "typical review cycles in the order of 60 days", APC "$2,800 USD", 투고 https://ieee.atyponrex.com/journal/taes (2025-03-04 이후).
- IEEE APC 2026: [IEEE Open APC](https://open.ieee.org/for-authors/article-processing-charges/) — IEEE Access "$2,160 USD", 하이브리드 "$2,800 USD", 학회(Society) 회원 20% 할인, 일반 IEEE 회원 5%, 학생 미적용.
- Elsevier 8종 APC: [Elsevier APC price list xlsx (Prices as of 05-Oct-2026)](https://legacyfileshare.elsevier.com/els_com_pricing/article-publishing-charge.xlsx) (링크 출처: [Elsevier pricing](https://www.elsevier.com/about/policies-and-standards/pricing), 전체 범위 "approximately $200 and $11,400 US Dollars").
- Defence Technology: [KeAi 공식 페이지](https://www.keaipublishing.com/en/journals/defence-technology/) — "Impact Factor 6.4", "CiteScore 11", 월간, 완전 OA; [DOAJ API](https://doaj.org/api/search/journals/issn:2214-9147) — has_apc=False, CC BY-NC-ND, 표절검사 실시.
- JMSE APC: [DOAJ API](https://doaj.org/api/search/journals/issn:2077-1312) — APC 2,600 CHF, CC BY. IEEE Access: [DOAJ](https://doaj.org/api/search/journals/issn:2169-3536) — 2,160 USD.
- MOR: [MORS MOR Journal](https://www.mors.org/Publications/MOR-Journal) — "operations research methodologies and theories in military and national security contexts", 비회원 $100 온라인, 투고 https://mc04.manuscriptcentral.com/mor_journal.
- JDMS 범위: [SCS Publications](https://scs.org/publications/) — "advancing the practice, science, and art of modeling and simulation as it relates to the military and defense mission areas", "quarterly refereed archival journal".
- JIF·색인·백분위(2차 자료): [wos-journal.info](https://wos-journal.info/) 각 저널 상세 페이지(예: [Ocean Engineering #13912](https://wos-journal.info/journalid/13912), [JDMS #3181](https://wos-journal.info/journalid/3181), [MOR #2407](https://wos-journal.info/journalid/2407), [TAES #15413](https://wos-journal.info/journalid/15413)). JCR 2024 비교값(2차 자료): [bioxbio](https://www.bioxbio.com/journal/OCEAN-ENG) 등.
- 게재 증거(메타데이터): [Crossref API: weapon target assignment](https://api.crossref.org/works?query.bibliographic=weapon+target+assignment&filter=from-pub-date:2020-01-01,type:journal-article&rows=40), [weapon-target assignment reinforcement learning](https://api.crossref.org/works?query.bibliographic=weapon-target+assignment+reinforcement+learning&filter=from-pub-date:2020-01-01,type:journal-article&rows=40), [unmanned surface vehicle swarm task allocation](https://api.crossref.org/works?query.bibliographic=unmanned+surface+vehicle+swarm+task+allocation&filter=from-pub-date:2020-01-01,type:journal-article&rows=40).

#### (2) 선정표 밖에서 발견된, 후속연구(T1–T7) 신규성 판단에 직접 관련된 2023–2026 논문 (Crossref 메타데이터, 본문 미열람)
- Oh, S. H., Byeon, G. W., Cho, Y. (2026) "Artificial Intelligence in Combat Decision-Making: Weapon Target Assignment via Reinforcement Learning and Graph Neural Networks", IEEE Trans. Cybernetics 56:631–643, doi:10.1109/TCYB.2025.3610606 — 한국 저자, GNN+RL WTA: 연구자 (b)의 GNN-MAPPO와 **중복성 검토 최우선 대상**.
- Peng, Z., Lu, Z., Mao, X. (2025) "Multi-Ship Dynamic Weapon-Target Assignment via Cooperative Distributional Reinforcement Learning With Dynamic Reward", IEEE TETCI 9:1843–1859, doi:10.1109/TETCI.2024.3451338 — 분포형 RL: T2(위험민감 RL)와 겹침 가능.
- Na, H., Ahn, J., Moon, I. (2023) "Weapon–Target Assignment by Reinforcement Learning with Pointer Network", J. Aerospace Information Systems 20:53–59, doi:10.2514/1.I011150; 동 저자 (2026) "Multi-Agent Reinforcement Learning Considering Agent Priority for Weapon–Target Assignment", JAIS 23:464–479, doi:10.2514/1.I011676 — 한국 저자, 포인터 네트워크/MARL: T4(신경 조합최적화)와 겹침 가능.
- Yoon, C., Lee, J., Cho, J. (2025) transformer-based RL WTA, JDMS (위 표) — T4 확장성 주장과 겹침 가능.
- Zhao, C., Li, M., Zhu, X. (2026) "Assignment-Consistent Dynamic Multi-UAV Task Allocation: Communication-Efficient … Under Stale and Asymmetric Information", Drones 10(7):523; Liu, T., Wei, S., Liu, C. (2026) "A resilient task allocation method for unmanned aerial vehicle swarm considering local information", Reliability Eng. & System Safety 272:112442 — T1(통신거부·국소정보) 선행 유사연구.
- Hu, T., Zhang, X., Luo, X. (2024) "Dynamic Target Assignment by Unmanned Surface Vehicles Based on Reinforcement Learning", Mathematics 12:2557; Nan, M., Zhu, Y., Kang, L. (2022) "A Modified RL-IGWO Algorithm for Dynamic Weapon-Target Assignment in Frigate Defensing UAV Swarms", Electronics 11:1796; Zong, J., Gao, X., Zhang, Y. (2024) "Research on Target Allocation for Hard-Kill Swarm Anti-UAV Swarm Systems", Drones 8:666.
- Hughes, M., Lunday, B. (2022) "The Weapon Target Assignment Problem: Rational Inference of Adversary Target Utility Valuations from Observed Solutions", Omega 107:102562; Lu, Y., Chen, D. (2021) "A new exact algorithm for the Weapon-Target Assignment problem", Omega 98:102138 — 정확해법·역추론 기준선.
- 국내: Jeong, H. (2020) "Hierarchical Lazy Greedy Algorithm for Weapon Target Assignment", J. KIMST 23(4):381–388, doi:10.9766/kimst.2020.23.4.381; Shin, M., Park, S., Lee, D. (2020) "Mean Field Game based Reinforcement Learning for Weapon-Target Assignment", J. KIMST 23(4):337–345; Eom, C., Lee, J., Kwon, M. (2025) "A Survey on Weapon-Target Assignment for Realistic Battlefield Environments: From Exact Algorithm to Deep Reinforcement Learning", J. KICS 50(2):205–216; Lee, J., Eom, C., Kim, K. (2025) DRL WTA, J. KICS 50(6):884–895; Yang, S., Kim, I. (2025) artillery DRL WTA, J. KAIS 26(12):162–170.
- 연구자 본인 (b)의 Crossref 레코드: "Multi-Agent Reinforcement Learning-Based Real-Time Distributed Decision-Making Framework for Swarm USV Weapon Target Assignment", Journal of the KNST 9(2):504–522 (2026), doi:10.31818/jknst.2026.6.9.2.504 — Crossref에는 이미 권·호·쪽수가 등록되어 있어 "in press"가 아닌 **출판 완료** 상태로 보임 [확인 필요]. 후속논문의 선행연구 인용·차별화 서술 시 이 DOI를 명시해야 함.

### Inferences
- JIF 수치는 IEEE Xplore 공식값(TAES 7.0, TSMC:S 8.4, Access 4.2)과 wos-journal.info 값이 일치하므로, wos-journal.info의 다른 저널 수치도 최신 JCR(2025)일 가능성이 높다. 다만 공식 JCR 확인 전까지 [확인 필요].
- "최근 WTA 게재 실적 + Q1 + 국방 주제 수용"을 동시에 만족하는 1순위 후보: **IEEE TAES**(정확한 범위 적합, 60일 심사), **Defence Technology**(APC 없음, Q1, WTA·무인체계 다수), **EAAI/ESWA**(AI 응용·서베이 수용, 고 JIF), **Ocean Engineering**(USV 특화). OR 지향 결과(정확해법 대비 격차 보증, 강건 WTA)는 **NRL·MOR·C&OR**(또는 Computers & Industrial Engineering)이 심사자 풀이 맞다. JDMS는 국방 M&S·V&V 서술이 강점인 원고에 적합하나 ESCI임을 감안.
- MOR의 백분위 0.9%는 SCIE 신규 편입 초기 효과일 가능성이 있으나 확인 불가 [확인 필요].
- Journal of Field Robotics·JAAMAS·SIMPAT·AST는 검색 범위에서 WTA 게재 증거를 찾지 못했으므로, 실해상 실험(JFR), 에이전트 이론(JAAMAS), 시뮬레이션 방법론(SIMPAT) 중심으로 원고를 재구성하지 않으면 scope 부적합 반려 위험이 있다.

### Gaps
- Elsevier 8종·Wiley 2종·SAGE·MDPI·Springer의 공식 "time to first decision/acceptance rate"는 Journal Insights·저널 홈페이지가 403으로 차단되어 미확인.
- NRL·JFR(Wiley), JAAMAS(Springer), JDMS(SAGE)의 하이브리드 APC 금액 미확인.
- 공식 JCR 분위(Q1~Q4)는 Clarivate 로그인 필요로 미확인; 위 분위는 백분위 순위에서 추정.

---

## KQ2. 국내 학술지 6종: KCI 등재 여부·심사기간·게재료·유사도 기준·영문 투고 가능 여부

### Takeaway
공식 사이트 열람에 성공한 한국군사과학기술학회지(KIMST)와 한국경영과학회지(KORMS)는 투고·게재료, 중복게재 금지 규정, 언어 정책을 명시하고 있으나 **유사도 수치 기준은 어느 학회도 명시하지 않았다**(KORMS는 "KCI 문헌 유사도 검사를 권장"). KNST·JKSSE·시뮬레이션학회논문지·대한산업공학회지는 JAMS/동적 페이지 또는 서버 장애로 규정 본문을 확인하지 못했고, KCI 포털의 학술지 검색도 질의가 적용되지 않아 **등재 등급은 전부 [확인 필요]**이다.

### Cited Findings
- **한국군사과학기술학회지(KIMST)**: 투고규정 — "논문의 내용은 군사과학기술에 관련된 것으로 하며, 다른 간행물에 표절 및 중복게재 되지 않아야 한다", "논문의 종류는 학술논문, 기술논문으로 구분", "심사료: 6만원(논문 1편)", "게재료: 기본 8면 160,000원 + 초과 1면당 30,000원 (가산/용역 또는 연구비를 지원받은 논문은 게재료의 50% 가산)", "모든 저자가 학회 회원인 경우에 한하여 논문게재 가능", 원고는 "한글" 원칙이되 "한문이나 영어를 병용할 수 있다", "초록(Abstract)은 영문으로 200단어 이내", "Reference는 전체 영문" — [KIMST 투고안내](https://www.kimst.or.kr/business/index.kin?gubun=2), [KIMST 학회 규정](https://www.kimst.or.kr/info/index.kin?gubun=7). 연구윤리규정 제5조 "연구물의 중복 게재 혹은 이중 출판의 금지: 가. 저자는 국내외를 막론하고 이전에 출판된 자신의 연구물(게재 예정이거나 심사 중인 연구물 포함)을 새로운 연구물인 것처럼 투고해서는 안 된다. 나. 이미 학회지에 발표된 연구물을 상당부분 중복 사용하여 재출판하고자 할 경우에는, 출판하고자 하는 학회지의 편집자에게 이전 출판에 대한 정보를 제공하고 중복 게재나 이중 출판의 여부를 확인하는 절차를 거쳐야 한다." — [KIMST 학회 규정](https://www.kimst.or.kr/info/index.kin?gubun=7). 온라인 투고 시스템: http://acoms.atit.co.kr:9090/kimst/ — [KIMST 홈](https://www.kimst.or.kr/). KCI 등재 등급·심사기간·영문 전문 투고 허용 여부·유사도 수치: 미기재 [확인 필요]. WTA 게재 실적: Jeong (2020), Shin et al. (2020) (KQ1 참조).
- **한국경영과학회지(KORMS)**: "투고 논문의 작성 언어는 국문 또는 영문으로 한다 … 영문 논문의 적극적인 투고를 권장", "논문 투고료: 일반심사는 투고료 없음 (단, 교신저자나 주저자가 학회 회원이어야함) 긴급심사는 투고료 200,000원", "일반심사 논문: 10쪽까지는 200,000원, 초과분에 대해서는 1쪽당 20,000원 — 긴급심사 논문: 15쪽까지는 300,000원 … (개정: 2026.7.10)", "긴급 심사의 경우 논문 접수일로부터 15일 이내에 1차 심사결과를, 한달 이내에 최종 심사결과를 통보", "본 학회에서는 논문 투고 시 KCI 문헌 유사도 검사를 권장합니다"(수치 기준 없음), 발간 2·5·8·11월(한국경영과학회지), 3·6·9·12월(경영과학) — [KORMS 편집방침 및 투고요령](https://korms.or.kr/homepage/custom/rules1), [KORMS 학회지 안내](https://www.korms.or.kr/). 연구윤리규정: "부당한 중복게재: 연구자가 자신의 이전 연구결과와 동일하거나 실질적으로 유사한 저작물을 출처표시 없이 타 학술지에 게재한 후 실질적인 중복 성과로 부당한 이익을 취하는 행위", "중복투고" 별도 정의, 중복투고·부당한 중복게재에는 계도기간 미적용 — [KORMS 연구윤리규정](https://korms.or.kr/homepage/custom/rules2). KCI 등급 미확인 [확인 필요].
- **Journal of the KNST(한국해군과학기술학회)**: 학회 홈페이지(www.knst.kr)는 503/연결 재설정, JAMS(knst.jams.or.kr)는 로그인 전용 셸 페이지(2.7 KB)만 반환 — 규정 미확인. Crossref상 DOI 접두 10.31818, 연구자 본인 논문 9(2):504–522 (2026) 등록 확인 — [Crossref](https://api.crossref.org/works?query.bibliographic=weapon-target+assignment+reinforcement+learning&filter=from-pub-date:2020-01-01,type:journal-article&rows=40).
- **한국시스템엔지니어링학술지(JKSSE, KOSSE)**: [KOSSE JAMS](https://kosse.jams.or.kr/) — 기관 정보(대표자 이성용, master@kosse.or.kr, 서울 중구 중림동)와 "논문투고/논문접수·심사" 메뉴만 노출, 규정 본문은 로그인 필요. systemseng.or.kr·kosse.or.kr는 DNS 실패.
- **한국시뮬레이션학회논문지**: 학회 사이트에 "한국시뮬레이션학회논문지 / 논문투고요령 / 논문작성요령 / 논문투고신청 / 윤리규정 / 편집위원회규정" 메뉴 존재([?pmode=Thesistips](https://www.simulation.or.kr/?pmode=Thesistips), [?pmode=Ethics](https://www.simulation.or.kr/?pmode=Ethics), [?pmode=Editorialrule](https://www.simulation.or.kr/?pmode=Editorialrule))하나 본문이 동적 로딩되어 추출 실패. JAMS(scs.jams.or.kr)는 셸 페이지만 반환.
- **대한산업공학회지**: jkiie.jams.or.kr·www.jkiie.org 모두 본문 없음(셸/빈 페이지), kiie.org DNS 실패 — 미확인.
- **KCI 문헌 유사도 검사 서비스**: "KCI에 등록되어 있는 약 100만 여건의 국내 학술지 논문과 비교 검사", "문서 대 문서인 1:1 유사도 검사 가능", "어절 및 문장 단위 검사 설정 가능", "목차/참고문헌 제외 검사 가능", "인용 문장 제외 검사 가능", "출처표시문장 제외 검사 가능"; KCI 또는 JAMS 로그인 후 이용; **유사도 임계값에 대한 안내 없음** — [KCI 유사도 검사 안내](https://check.kci.go.kr/guide), [서비스 홈](https://check.kci.go.kr/).

### Inferences
- 국내 학회는 KCI 유사도 검사 결과 제출을 요구/권장하되 수치 기준은 편집위원회 재량으로 두는 경향이 확인된 범위(KORMS·KIMST)에서 일관된다. 따라서 "n% 이하" 같은 공식 임계값을 인용하는 것은 위험하며, 각 학회 편집위원회 규정 PDF를 직접 확인해야 한다.
- 영문 전문 투고: KORMS는 명시적으로 허용·권장. KIMST는 "한글 원칙, 영어 병용"으로 영문 전문 허용 여부가 불명확 — 편집위원회 문의 필요 [확인 필요].

### Gaps
- 6종 모두 KCI 등재/등재후보/우수등재 등급 미확인(KCI 포털 검색 GET/POST 모두 질의 미적용, 7,866건 전체 반환). 확인 경로: https://www.kci.go.kr 학술지 검색에서 발행기관명으로 직접 조회.
- KNST·JKSSE·시뮬레이션학회·대한산업공학회의 심사기간·심사료·게재료·유사도 기준·영문 허용 여부 전부 미확인.
- KIMST 게재료 "무지원 16만원 / 지원받은 경우 24만원" 표기와 "기본 8면 160,000원 + 50% 가산" 표기가 페이지별로 상이하게 보임(동일 규정의 두 표현일 가능성) [확인 필요].

---

## KQ3. 목표 학술대회

### Takeaway
2026-10-05 기준으로 **아직 투고 가능한 가장 가까운 창**은 ICRA 2027(서울, 2027-05-24~28; 단 2026-09 공지에 "Submission Closed"), WSC 2027(2026년 일정 기준 매년 4월 초 전문 마감), MODSIM World 2027(2026년 기준 3~5월 500단어 초록), KIMST 2027 종합학술대회(2026년은 6월 10~12일 제주 ICC)다. WSC는 12쪽 전문 심사·IEEE/ACM 등재와 "Military & National Security" 트랙을 갖춰 시뮬레이터 기반 연구에 가장 적합하다.

### Cited Findings
- **Winter Simulation Conference 2026**: "December 6-9, 2026 Scottish Event Campus & Crowne Plaza Glasgow, Scotland"; 트랙에 "Military & National Security" 포함 — [WSC 2026](https://meetings.informs.org/wordpress/wsc2026/). CFP: "April 12, 2026: Submissions due for Contributed Papers", "May 25, 2026: Notification of acceptance", "June 26, 2026: … corrected papers", 확장초록 "August 7, 2026"; 전문 "at most 12 pages, including an abstract of not more than 150 words"; "All submissions will be peer reviewed"; 채택 전문은 "IEEE and ACM repositories"에, 확장초록은 "INFORMS Simulation Society archives"에만 게재; 투고 자격 "papers not previously published or presented" — [WSC 2026 Call for Papers](https://meetings.informs.org/wordpress/wsc2026/call-for-papers/).
- **MODSIM World 2026**: "18 – 19 August 2026", "Hilton Alexandria Mark Center … Alexandria, VA", 주제 "Ignite and Innovate: Fueling What's Next with Modeling, Simulation, and AI", "18th International MODSIM World Conference" — [MODSIM World](https://www.modsimworld.org/). 투고: 초록 접수 "18 March – 22 May 2026", "500-word abstract", "No Full Paper Required: For the 2026 conference, only the abstract is necessary", 트랙 "Emerging Capabilities, Mission Readiness, or Autonomy", 초록 통보 "11 June 2026", Review Presentation(15분+5분 Q&A) 제출 "13 July 2026", 결정 "31 July 2026", "presentations focused heavily on sales pitches will not be accepted" — [MODSIM Submissions](https://www.modsimworld.org/submissions).
- **IEEE/MTS OCEANS 2026 Monterey**: "September 21-24, 2026 Monterey Conference Center", "500 technical papers", "1000+ attendees", Student Poster Competition — [OCEANS 2026 Monterey](https://monterey26.oceansconference.org/). 마감·주제 목록은 페이지에 없음 [확인 필요].
- **ICRA 2027**: "Coex, Seoul, South Korea", "May 24–28, 2027"; 내비게이션에 "Call for Papers – Submission Closed", 2026년 9월 마감 연장 공지 — [ICRA 2027](https://2027.ieee-icra.org/).
- **IROS 2026**: "SEPTEMBER 27 - OCTOBER 1, 2026", "PITTSBURGH, PA, USA", 투고 마감 "March 2, 2026", 통보 "June 16, 2026" — [IROS 2026](https://2026.ieee-iros.org/). (이미 종료)
- **AAMAS 2026**: "25–29 May 2026 in Paphos, Cyprus", 트랙: Main, Blue Sky Ideas, **JAAMAS Track**, AAAI Track, Demos, Doctoral Consortium 등; 통보 2025-12-22, 카메라레디 2026-02-11 — [AAMAS 2026](https://cyprusconferences.org/aamas2026/); IFAAMAS는 AAMAS 주최 — [IFAAMAS](https://www.ifaamas.org/). AAMAS 2027 정보 없음 [확인 필요].
- **IEEE Conference on Games**: ieee-cog.org는 2025 사이트(https://cog2025.inesc-id.pt)로 리다이렉트; 2026 사이트(2026.ieee-cog.org)는 TLS 인증서 불일치로 접속 불가 — [IEEE CoG](https://ieee-cog.org/). [확인 필요]
- **I/ITSEC**: iitsec.org(홈·/papers·/attend/call-for-papers)는 JS 렌더링으로 본문 추출 실패 — [I/ITSEC](https://www.iitsec.org/). 마감·분과·발표 절차 [확인 필요].
- **KIMST 2026 종합학술대회**: "일시 2026년 6월 10(수) ~ 12(금)", "장소 제주국제컨벤션센터(ICC)", 주관 한국군사과학기술학회·아주대 미래전투체계 네트워크기술 특화연구센터; 발표분야(과거 안내) "지상무기, 해양무기, 항공무기, 유도무기, 정보·통신, 감시…" — [KIMST 종합학술대회](https://www.kimst.or.kr/symposium/index.kin?gubun=1); 공지 "2026 종합학술대회 일정집 안내", "논문 발표시간표 최종 안내" — [KIMST 홈](https://www.kimst.or.kr/). 대회 전용 사이트(conference.kimst.or.kr/?event=16)는 503.
- **한국시뮬레이션학회 2026 춘계공동학술대회**: 공지 "2026년 춘계공동학술대회 논문모집 안내"(2026-02-17), "2026 춘계 공동학술 대회 포스터 발표 관련 안내"(2026-04-23), "2026 춘계공동학술대회 셔틀 안내 (경주역↔하이코)"(2026-05-11), "(최종) 2026 춘계공동학회 프로그램(발표일정) 안내"(2026-05-26), "2026 공동학술 대회 초록집"(2026-06-12); 자료실에 "추계학술대회 초록 & 확장 초록 양식" 존재 → 초록/확장초록 체계 — [한국시뮬레이션학회](https://www.simulation.or.kr/). 개최일·장소(경주 HICO 추정) [확인 필요].

### Inferences
- WSC의 "not previously published or presented" 조건과 IEEE/ACM 등재 때문에, WSC 논문을 먼저 내고 저널로 확장할 때는 WSC판을 인용하고 차별점을 명시해야 한다(KQ5의 IEEE 규정과 일치).
- MODSIM World는 전문 없이 초록만 요구하므로 "선행 발표"로 간주될 위험이 낮아(SAGE·Wiley 정책상 초록/포스터는 통상 선행출판 아님) 저널 투고 전 공개 발표 장소로 유리하다.
- 시뮬레이션학회 춘계대회는 초록/확장초록 기반이므로 동일 논리로 저널 선행출판 부담이 낮다; 반면 KIMST 종합학술대회는 발표논문집 쪽수가 있는 경우 국내 학회지 중복게재 심사에서 "학술대회 발표논문의 확장"임을 명시해야 한다.

### Gaps
- I/ITSEC 2026 일정·분과·논문 절차, IEEE CoG 2026, AAMAS 2027, OCEANS 2026/2027 마감 미확인.
- WSC 2027 CFP 미공개(2026 일정으로 유추).

---

## KQ4. 2025–2026 심사자가 RL/최적화 논문에 요구하는 것 (시드 수·신뢰구간·통계검정·ablation·기준선·코드·연산자원)

### Takeaway
ML 학회 체크리스트(NeurIPS)와 RL 평가방법론 논문(Agarwal 2021, Patterson 2024, Jordan 2024), 최적화 벤치마킹 지침(Bartz-Beielstein 2020, López-Ibáñez 2021, Beiranvand 2017)이 수렴하는 요구는 **(i) 다수 시드와 구간추정(층화 부트스트랩 CI·IQM), (ii) 최대값-over-seeds 금지, (iii) 하이퍼파라미터 민감도·ablation, (iv) 코드·데이터·연산자원 공개, (v) 정확해법 포함 적절한 기준선과 성능 프로파일**이다.

### Cited Findings
- NeurIPS Paper Checklist(원문): 5. "If you ran experiments, did you include the code, data, and instructions needed to reproduce the main experimental results?"; 6. "did you specify all the training details (e.g., data splits, hyperparameters, how they were chosen)?"; 7. "Does the paper report error bars suitably and correctly defined or other appropriate information about the statistical significance?" — 오차막대가 표준편차인지 표준오차인지, 변동 요인, 계산 방법 명시 요구; 8. "For each experiment, does the paper provide sufficient information on the computer resources (type of compute workers, memory, time of execution) needed?" — [NeurIPS Paper Checklist](https://neurips.cc/public/guides/PaperChecklist).
- Agarwal, R., Schwarzer, M., Castro, P. S., Courville, A., Bellemare, M. G. (2021) "Deep Reinforcement Learning at the Edge of the Statistical Precipice", NeurIPS 2021 (Outstanding Paper), arXiv:2108.13264 — 점추정 대신 구간추정, **interquartile mean(IQM)**, **stratified bootstrap CI**, **performance profiles**, 소수(3–5) 런 체제의 불확실성 경고: "reliable evaluation in the few run deep RL regime cannot ignore the uncertainty in results without running the risk of slowing down progress"; 오픈소스 라이브러리 rliable — [arXiv](https://arxiv.org/abs/2108.13264).
- Patterson, A., Neumann, S., White, M., White, A. (2024) "Empirical Design in Reinforcement Learning", JMLR 2024, arXiv:2304.01315 — "common empirical practice leads to weak statistical evidence", maximum-over-seeds 보고 금지, 하이퍼파라미터 민감도 보고, 환경 선택·실험자 편향 — [arXiv](https://arxiv.org/abs/2304.01315).
- Jordan, S. M., White, A., Castro da Silva, B., White, M., Thomas, P. S. (2024) "Position: Benchmarking is Limited in Reinforcement Learning Research", ICML 2024, arXiv:2406.16241 — "experimental practices continue to produce misleading or unsupported claims"; 엄밀한 벤치마킹의 계산비용을 분석하고 "an additional experimentation paradigm"(가설 주도 실험) 병행 권고 — [arXiv](https://arxiv.org/abs/2406.16241).
- Bartz-Beielstein, T., Doerr, C., van den Berg, D., … Weise, T. (2020) "Benchmarking in Optimization: Best Practice and Open Issues", arXiv:2007.03488 — 8대 주제: clearly stated goals, well-specified problems, suitable algorithms(기준선), adequate performance measures, thoughtful analysis(통계), effective designs, comprehensible presentations, guaranteed reproducibility; "guidelines (rules) that might be useful for authors and reviewers" — [arXiv](https://arxiv.org/abs/2007.03488).
- López-Ibáñez, M., Branke, J., Paquete, L. (2021) "Reproducibility in Evolutionary Computation", ACM Trans. Evolutionary Learning and Optimization, arXiv:2102.03380 — ACM 재현성 배지 체계 정교화 제안, 문화적·기술적 장애 식별, 도구·지침 제시 — [arXiv](https://arxiv.org/abs/2102.03380).
- (앵커) Beiranvand, V., Hare, W., Lucet, Y. (2017) "Best practices for comparing optimization algorithms", Optimization and Engineering, arXiv:1709.08242 — 테스트셋 선택, 성능척도, data/performance profiles, 파라미터 튜닝 보고, 계산환경 명시 — [arXiv](https://arxiv.org/abs/1709.08242).
- 저널 측 심사 형태: IEEE Access는 "reviews are 'binary' … Accept or Reject an article in the form it is submitted" — [IEEE Xplore 메타데이터](https://ieeexplore.ieee.org/rest/publication/home/metadata?pubid=6287639); TAES "rigorous web-based peer-review … order of 60 days" — [AESS](https://ieee-aess.org/publications/taes).
- OR 심사자 풀의 기준선 기대를 보여주는 최근 게재: Bertsimas & Paskov (2025) NRL "Solving Large-Scale WTA Problems in Seconds Using Branch-Price-And-Cut" — 대규모 WTA의 정확해법이 이미 "seconds" 수준임을 제목에 명시 — [Crossref](https://api.crossref.org/works?query.bibliographic=weapon+target+assignment&filter=from-pub-date:2020-01-01,type:journal-article&rows=40) (본문 미열람).

### Inferences
- 후속연구는 (b)의 "1,000회 물리 시뮬 + 100,000 부트스트랩"을 넘어 **학습 시드 ≥ 10(가능하면 20–30) × 평가 시나리오 다수**로 IQM·층화 부트스트랩 CI·performance profile을 보고하고, 각 구성요소(위협지수/VNS/GNN-MAPPO, 마스킹, 통신손실 처리)에 대한 ablation과 하이퍼파라미터 민감도를 포함해야 ML·OR 양쪽 심사자를 통과할 가능성이 높다.
- OR 저널(NRL·C&OR·MOR)에서는 MILP뿐 아니라 branch-price-and-cut 등 최신 정확해법 대비 **최적성 격차(optimality gap)와 시간–품질 anytime 곡선**을 요구할 것으로 보인다(Bertsimas & Paskov 2025가 "초 단위" 정확해법을 보였기 때문).
- 코드 공개는 NeurIPS 체크리스트와 EC 재현성 지침이 공통 요구하므로, 국방 민감정보를 제외한 시뮬레이터·학습 코드의 공개 범위를 사전에 설계할 필요가 있다(비공개 시 심사 불리).

### Gaps
- INFORMS(IJOC/OR)의 공식 코드·데이터 정책 페이지는 401/403으로 열리지 않아 원문 인용 불가.
- Elsevier 저널별 Guide for Authors(C&OR·SWEVO 등)의 계산실험 보고 요건은 사이트 차단으로 미확인.
- ICLR/ICML 2025–2026 reviewer guide, RA-L/ICRA 심사 지침 원문 미확인.

---

## KQ5. COPE/ICMJE·출판사 규정: 텍스트 재활용, 자기표절, 중복출판, 학회→저널 확장, 프리프린트

### Takeaway
확인된 모든 규정(ICMJE·TRRP·IEEE·Elsevier·Springer Nature·Wiley·SAGE·KIMST·KORMS)은 **중복투고 금지, 선행 발표물 공개·인용, 재활용 텍스트 명시**를 요구하지만, **"학회→저널 확장 시 신규 내용 30–50%" 같은 수치 기준을 명문화한 출판사는 확인된 범위에 없다**(IEEE는 "very clearly states how the new submission differs", IEEE T-RO/T-RL은 "not … a mere extension … new results of substantive research significance"). arXiv 프리프린트는 IEEE·Elsevier·Springer Nature·Wiley가 허용(IEEE는 소정 문구 부착), SAGE는 저널별 불허 가능.

### Cited Findings
- **ICMJE**: "Authors should not submit the same manuscript, in the same or different languages, simultaneously to more than one journal"; 중복출판 정의 "publication of a paper that overlaps substantially with one already published, without clear, visible reference to the previous publication"; 선행 보고가 있으면 "the letter of submission should clearly say so"; 예비보고(프리프린트·학회 초록/포스터) 후 완전보고는 허용; 프리프린트는 저널에 고지하고 출판본으로 연결 — [ICMJE Overlapping Publications](https://www.icmje.org/recommendations/browse/publishing-and-editorial-issues/overlapping-publications.html).
- **TRRP(Text Recycling Research Project) Best Practices**: 텍스트 재활용 정의 "(1) the material in the new document is identical to that of the source (or substantively equivalent in form and content), (2) the material is not presented … as a quotation …, and (3) at least one author of the new document is also an author of the prior document"; 허용 맥락 "methods and instrumentation that are common across studies", "descriptions of conceptual models, theoretical frameworks, or definitions"; 일부 정책은 "do not allow recycling of previously published material in Results or Discussion sections"; 공개 방식: 커버레터에 "citations to the prior work(s) and brief explanations", 독자용 "a footnote at the beginning of the document"; salami slicing 정의 "The unnecessary splitting of a study into multiple, separate publications"; 저작권: 출판물 재활용은 "limited by copyright laws" — [TRRP Best Practices for Researchers](https://textrecycling.org/resources/best-practices-for-researchers/); 연구자용 가이드 PDF: https://textrecycling.org/files/2021/06/Understanding-Text-Recycling_A-Guide-for-Researchers-V.1.pdf, 모델 정책: https://textrecycling.org/resources/text-recycling-policy/ — [TRRP Resources](https://textrecycling.org/resources/).
- **IEEE(Submission and Peer Review Policies)**: 다중투고 정의 "concurrently under active consideration by two or more publications", 허용 여부는 "at the discretion of each IEEE Organization Unit"; 선행 학회논문: 저자는 "disclose whether there are prior publications, e.g., conference articles, by the authors that are similar" 하고 "include information that very clearly states how the new submission differs from the previously published work(s). Such articles should be cited"; 재활용 콘텐츠: "clearly indicate all recycled material and provide a full reference to the original publication"; 전자 게시(프리프린트) 문구 "This work has been submitted to the IEEE for possible publication. Copyright may be transferred without notice, after which this version may no longer be accessible", 출판 후 "(1) the full citation to the IEEE work or (2) the pdf of the final accepted manuscript"로 교체 — [IEEE Submission and Peer Review Policies](https://journals.ieeeauthorcenter.ieee.org/become-an-ieee-journal-author/publishing-ethics/guidelines-and-policies/submission-and-peer-review-policies/).
- **IEEE RAS(T-RO/T-RL Information for Authors)**: "If your submission is based on previously published papers, your manuscript must not be just a mere extension of the previous version(s)…", "the new submission must contain new results of substantive research significance and impact beyond the previous papers"; 프리프린트 "a preprint server operated by an approved not-for-profit third party such as ArXiv or TechRxiv"; 2026-01-01부 APC "USD $2,800"; 12쪽 한도 — [IEEE RAS Information for Authors](https://www.ieee-ras.org/publications/t-ro/information-for-authors).
- **Elsevier(Publishing Ethics)**: "An author should not in general publish manuscripts describing essentially the same research in more than one journal of primary publication. Submitting the same manuscript to more than one journal concurrently constitutes unethical behaviour and is unacceptable"; 선행 공개 허용 예외 "in the form of an abstract or as part of a published lecture or academic thesis or as an electronic preprint"; "Crossref Similarity Check reports for all submissions"를 편집자에게 제공, **유사도 % 기준 없음** — [Elsevier Publishing Ethics](https://www.elsevier.com/about/policies-and-standards/publishing-ethics). 프리프린트: "Authors can share their preprint anywhere at any time", "Authors can update their preprints on arXiv or RePEc with their accepted manuscript", 단 "add to or enhance" 금지 — [Elsevier Sharing Policy](https://www.elsevier.com/about/policies-and-standards/sharing).
- **Springer Nature(Editorial Policies)**: "routinely using the Crossref Similarity Check powered by iThenticate on submitted manuscripts"; "a unified policy that encourages posting of preprints on preprint servers" — [Springer Nature Editorial Policies](https://www.springernature.com/gp/policies/editorial-policies). 중복출판·학회확장 세부는 브랜드별 페이지로 분산되어 미확인.
- **Wiley(Best Practice Guidelines on Publishing Ethics)**: 중복출판 "the publication, or attempted publication, of whole or substantial parts of work/data/analysis that have already been published"; 자기 텍스트 재사용 시 "transparent" 하고 "cite the source"(COPE 지침 준용); 학회 proceedings 전문은 "typically considered prior publication"(초록/포스터는 공개 시 허용); 프리프린트 허용(저널 정책 범위 내); "routinely screens submitted manuscripts for duplicated text using tools such as Crossref Similarity Check", **% 기준 없음** — [Wiley Ethics Guidelines](https://authors.wiley.com/ethics-guidelines/index.html).
- **SAGE(Prior Publication)**: "If a substantial portion of your manuscript has been previously published, your manuscript will generally not be acceptable"; "Manuscripts based on papers that have been presented at conferences may be considered for publication as long as they have not been published"; 초록·포스터는 "generally not impact the manuscript's eligibility"; 학위논문 발췌는 "generally be eligible"; 프리프린트는 지지하나 "some journals will not consider submissions that have been shared as a preprint prior to submission"; 모든 선행 공개를 편집자에게 "disclose" — [SAGE Prior Publication](https://www.sagepub.com/en-us/nam/prior-publication).
- **국내 규정**: KIMST 연구윤리규정 제5조(KQ2 인용), KORMS "부당한 중복게재"·"중복투고" 정의(KQ2 인용).
- **WSC**: "papers not previously published or presented" — [WSC 2026 CFP](https://meetings.informs.org/wordpress/wsc2026/call-for-papers/).

### Inferences
- 연구자 (a)(b)(c)(d)와 후속논문의 관계는 TRRP 분류상 "학위논문(d) → 저널"은 SAGE/Elsevier가 명시적으로 허용하는 경로이나, (b)가 이미 DOI로 출판된 저널논문이므로 (b)의 결과·논의 텍스트 재사용은 **중복출판 위험**이다. 안전한 설계: 문제 정의(새 제약·불확실성·통신모델), 모델(새 아키텍처), 실험(새 시나리오·기준선·통계)을 모두 바꾸고, 공통 배경(MRCPSPTW 정식화, 위협지수 정의)은 (b)·(c)를 인용하며 요약만 재진술한다.
- "30–50% 신규 내용"은 관행적 경험치일 뿐 확인된 출판사 정책 어디에도 없다. 심사자 설득에는 비율보다 "new results of substantive research significance"(IEEE RAS 표현)와 커버레터의 차별점 표(선행 vs 신규)가 유효하다.
- arXiv 선공개는 IEEE·Elsevier·Springer Nature·Wiley 모두 가능하므로 우선권 확보용으로 권장되나, JDMS(SAGE)를 목표로 할 경우 저널별 프리프린트 정책을 먼저 확인해야 한다.

### Gaps
- COPE 텍스트 재활용 지침 원문(publicationethics.org)은 403으로 미열람 — Wiley·SAGE가 "COPE 준용"을 명시한 것으로 간접 확인.
- IEEE PSPB Operations Manual 8.2.4의 표절 5단계(비율·제재) 원문 미열람(PDF 링크가 HTML로 응답, ieee.org 표절 페이지는 202 빈 응답).
- ACM "25% 신규" 정책, MDPI 정책 페이지 미열람(403).

---

## KQ6. 유사도 임계값(국내 학술지·Elsevier/IEEE iThenticate)과 후속논문의 유사도 관리 실무

### Takeaway
확인한 어떤 공식 문서(Elsevier·Wiley·Springer Nature·KCI 유사도 서비스·KORMS·KIMST)도 **수치 임계값을 명시하지 않는다**; 출판사는 Crossref Similarity Check(iThenticate) 보고서를 편집자에게 제공하고 판단을 편집자에게 맡긴다. 따라서 "n% 이하면 안전"이라는 접근 대신, 재활용 가능 구간(방법·정의)만 최소 재진술하고 결과·논의는 전면 신규 작성하며, 선행 4편을 명시 인용·각주 고지하는 것이 유일하게 규정에 근거한 전략이다.

### Cited Findings
- Elsevier: "Crossref Similarity Check reports for all submissions" 제공, % 기준 없음 — [Elsevier Publishing Ethics](https://www.elsevier.com/about/policies-and-standards/publishing-ethics).
- Wiley: "routinely screens … using tools such as Crossref Similarity Check", "No specific similarity percentage threshold" — [Wiley Ethics Guidelines](https://authors.wiley.com/ethics-guidelines/index.html).
- Springer Nature: "Crossref Similarity Check powered by iThenticate" 상시 사용 — [Springer Nature Editorial Policies](https://www.springernature.com/gp/policies/editorial-policies).
- IEEE: 재활용 자료를 "clearly indicate" + "full reference" — [IEEE Submission and Peer Review Policies](https://journals.ieeeauthorcenter.ieee.org/become-an-ieee-journal-author/publishing-ethics/guidelines-and-policies/submission-and-peer-review-policies/).
- KCI 유사도 서비스: 문장/어절 단위, 참고문헌·인용문·출처표시문장 제외 옵션, 임계값 안내 없음 — [KCI 유사도 검사 안내](https://check.kci.go.kr/guide).
- KORMS: "KCI 문헌 유사도 검사를 권장" — [KORMS 투고요령](https://korms.or.kr/homepage/custom/rules1). KIMST: 중복게재 금지·편집자 사전 고지 절차 — [KIMST 규정](https://www.kimst.or.kr/info/index.kin?gubun=7).
- TRRP: 방법·개념모형·정의의 재활용은 허용 맥락, 결과·논의 재활용은 다수 정책이 불허, 커버레터·각주 고지 — [TRRP Best Practices](https://textrecycling.org/resources/best-practices-for-researchers/).
- DOAJ 레코드상 JMSE·Defence Technology·IEEE Access 모두 "plagiarism detection: True"(각 저널 윤리 페이지 URL 명시) — [DOAJ JMSE](https://doaj.org/api/search/journals/issn:2077-1312), [DOAJ Defence Technology](https://doaj.org/api/search/journals/issn:2214-9147), [DOAJ IEEE Access](https://doaj.org/api/search/journals/issn:2169-3536).

### Inferences
- 실무 지침(규정에서 도출): (1) 투고 전 KCI 유사도 검사(국내)와 iThenticate(가능하면 기관 계정)로 **단일 출처당 중복률**을 특히 (b)·(d)에 대해 점검하고, 공통 수식·정의는 인용 후 표현을 바꿔 쓴다; (2) 서론·관련연구는 전면 신규 작성(2023–2026 신규 문헌 — Oh et al. 2026 TCYB, Peng et al. 2025 TETCI, Bertsimas & Paskov 2025 NRL, Yoon et al. 2025 JDMS, Li et al. 2024 EAAI 서베이 — 반영); (3) 시나리오(80 vs 80, DSR 가중 0.7/0.3)와 지표를 그대로 재사용하지 말고 새 문제 정의에 맞는 지표(예: 통신거부 하 임무성공률, CVaR, anytime gap)로 교체; (4) 커버레터에 (a)–(d) 서지와 차별점 표를 첨부하고 본문 첫 페이지 각주로 선행연구 관계를 고지(TRRP·IEEE·ICMJE 공통 요구).
- 국내 학회가 흔히 쓰는 "15–20%" 식 수치는 본 조사에서 1차 출처로 확인되지 않았으므로 보고서에 수치로 적지 말고 "편집위원회 재량"으로 기술해야 한다 [확인 필요].

### Gaps
- 국내 6개 학회 중 유사도 수치 기준을 명문화한 편집규정 원문 미확인(접근 불가 또는 미기재).
- IEEE CrossCheck 운용 기준(접수 시 자동 스크리닝 비율 등) 원문 미확인.
- MDPI(JMSE) 자체 iThenticate 운용 기준 페이지(https://www.mdpi.com/journal/jmse/instructions#ethics) 미열람(403).
