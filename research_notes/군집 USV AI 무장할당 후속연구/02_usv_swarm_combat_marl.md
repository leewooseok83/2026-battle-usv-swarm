# 군집 USV 협동 교전·표적/임무 할당·MARL 국제 문헌 조사 (2020–2026)

조사 기준일: 2026-10-05. 아래 기록은 실제로 열어 본 자료(전문 PDF, 초록 페이지, DOI/arXiv 페이지, Crossref 메타데이터)만 인용한다. 검색 결과 스니펫만 확인하고 본문을 열지 못한 항목은 "[검색 스니펫만 확인]" 또는 [확인 필요]로 표시했다. 접근 차단(403/429)으로 열지 못한 항목은 Gaps에 명시했다.

---

## KQ1. 2020–2026년 USV 군집 대결·추격회피·협동 교전·표적 할당에 MARL(MAPPO, QMIX, MADDPG, GAT/Transformer, meta-RL)을 적용한 논문은 무엇인가?

### Takeaway
2024–2026년 USV 군집 MARL 문헌은 중국 그룹(NUDT, 大连海事大学, 哈尔滨工程大学, 上海海洋大学, 昆明理工, 大连民族大学 등)이 주도하며, 과제는 대부분 "추격–포위(round-up/encirclement)", "경호–방어(escort/perimeter defense)"이고 **무장-표적 할당(WTA)을 명시적으로 다룬 USV MARL 논문은 Hu et al. 2024(NUDT) 단 한 편**이 확인되었다. 서구는 MIT Lincoln Lab/NRL의 Pyquaticus(해상 CTF) 축이 유일한 공개 축이며, 규모는 2v2~4v4 또는 3v1/6v2가 전형적이고 Hu 2024의 5척×25표적이 최대급이다.

### Cited Findings

**(1) WTA를 직접 다룬 USV MARL (유일)**
- Hu, Tao; Zhang, Xiaoxue; Chen, Tao; Luo, Xueshan. "Dynamic Target Assignment by Unmanned Surface Vehicles Based on Reinforcement Learning." *Mathematics* 2024, 12(16), 2557. DOI 10.3390/math12162557. 소속: National Key Laboratory of Information Systems Engineering, National University of Defense Technology(NUDT), 长沙. 이동 표적에 대한 다중 USV WTA를 "MTWTA"라 명명하고, MADDPG 임베딩을 Seq2seq 원리로 수정하고 우선순위 경험재생(preferential experience replay)과 self-attention을 결합. 타격 위치·시각을 함께 모델링. 사례연구 규모 (5 USV, 25 표적); 비교 대상은 GA와 Grey Wolf(300 iter). 대규모에서 GA 대비 해 품질 ≥30% 개선, 평균 풀이 시간 GA의 10% 미만. 실험 하드웨어 AMD Ryzen 7 5800H, RTX 3060, 16 GB RAM, Python 3.10. 데이터는 군 데이터 제약으로 전부 난수 생성(표적 좌표 (−10,10), 속도 (1,2), USV 속도 10, 최대 공격능력 5). 향후연구: "연속 행동의 화력 분배와 대결(confrontation) 고려". — [PDF 전문](https://mdpi-res.com/d_attachment/mathematics/mathematics-12-02557/article_deploy/mathematics-12-02557.pdf)

**(2) 하이브리드 GAT-Transformer 메타강화학습 (경호·방어 대결)**
- Xiong, Yang; Wang, Shangwen; Tian, Hongjun; Liu, Guijie; Shan, Zihao; Yin, Yijie; Tao, Jun; Ye, Haonan; Tang, Ying. "Spatiotemporal Meta-Reinforcement Learning for Multi-USV Adversarial Games Using a Hybrid GAT-Transformer." *J. Mar. Sci. Eng.* 2025, 13(8), 1593. DOI 10.3390/jmse13081593. 소속: Shanghai Ocean University(공학부), Ocean University of China. 알고리즘 "Adv-TransAC": GAT가 순간 전술 대형(그래프)을, transformer가 시간 전개를 처리해 상대 의도 추론; adversarial meta-learning + 자동 커리큘럼(규칙 기반 → DQN 사전학습 상대 → 메타 적응 상대, 승률 임계값으로 단계 전환). 시뮬레이션은 PettingZoo 1.15.0 "waterworld" 환경을 다중 USV 공방 시나리오로 커스터마이즈(Python 3.8, PyTorch 1.10, 단일 RTX 3090, 200만 step). 과제: HVU(고가치 유닛) 경호, 공격 USV 돌파 저지; 레이더(광역·저해상)+광학(협역·고해상) 2종 모의 센서; ISO 23860의 200 ms 실시간 제약을 준수한다고 명시. 1,000회 테스트 에피소드 평균 결과(Table 2): QMIX 임무성공률 65.4%(규칙 상대)/38.2%(학습 상대), MADDPG 81.0/59.5, Adv-TransAC 85.5(규칙)/78.5(학습); 동료 간 충돌률 Adv-TransAC 3.3% vs GNN-AC 2.9%. 모델 파라미터 수와 단일 step 추론시간을 RTX 3090 batch 1로 비교(엣지 배치 고려). "통신 효율적 연합(federated) 최적화 구조"로 실용성 검증. 5.4절 "Limitation Analysis and Future Work"에서 도메인 랜덤화 등 sim-to-real 과제를 언급. — [PDF 전문](https://mdpi-res.com/d_attachment/jmse/jmse-13-01593/article_deploy/jmse-13-01593.pdf)

**(3) MADDPG 기반 USV 군집 게임 대결(중국어 학술지)**
- YU Changdong(于长东); LIU Xinyang; CHEN Cong; LIU Dianyong; LIANG Xiao. "Research on Game Confrontation of Unmanned Surface Vehicles Swarm Based on Multi-Agent Deep Reinforcement Learning." *Journal of Unmanned Undersea Systems(水下无人系统学报)* 2024, 32(1), 79–86. DOI 10.11993/j.issn.2096-3920.2023-0159. 소속: 大连海事大学 인공지능학원·선박해양공정학원, 哈尔滨工程大学 자율해양운반체기술 국가중점실험실. 분산 실행 MADDPG로 협동 포위(round-up); 3 vs 1, 6 vs 2 병력비 시나리오에서 검증. — [학술지 영문 초록 페이지](https://sxwrxtxb.xml-journal.net/en/article/doi/10.11993/j.issn.2096-3920.2023-0159)

**(4) ROS/Gazebo MADDPG USV 군집**
- Shrudhi R S; Mohanty, Sreyash; Elias, Susan. "Control and Coordination of a SWARM of Unmanned Surface Vehicles using Deep Reinforcement Learning in ROS." arXiv:2304.08189 (2023, 13 pp., 10 figs). MA-DDPG, 분산 제어·공유 보상, ROS+Gazebo, 실시간 표적 추적. 정량 결과는 초록에 없음. — [arXiv](https://arxiv.org/abs/2304.08189)

**(5) MAPPO 계열 추격회피·방어**
- Li, Fanbiao; Yin, Mengmeng; Wang, Tengda; Huang, Tingwen; Yang, Chunhua; Gui, Weihua. "Distributed Pursuit-Evasion Game of Limited Perception USV Swarm Based on Multiagent Proximal Policy Optimization." *IEEE Trans. Systems, Man, and Cybernetics: Systems* 2024, 54(10), 6435–6446. DOI 10.1109/TSMC.2024.3429467. (Crossref 메타데이터로 서지 확인; 초록 페이지는 IEEE Xplore 접근 불가 → 방법 세부 [확인 필요]) — [Crossref](https://api.crossref.org/works?query.bibliographic=Distributed+pursuit-evasion+game+of+limited+perception+USV+swarm+based+on+multiagent+proximal+policy+optimization&rows=2)
- Pu, Huayan; Wang, Jinduo; Gao, Senhui; Shi, Zhaoxiang; Deng, Qun; Xie, Yangmin. "A velocity-domain MAPPO approach for perimeter defensive confrontation by USV groups." *Expert Systems with Applications* 2025, 265, 125980. DOI 10.1016/j.eswa.2024.125980. VD-MAPPO: 속도영역 대결 해석을 MAPPO에 결합, 희소 보상 해결용 velocity-domain advantage 추정 [검색 스니펫만 확인]. — [Crossref](https://api.crossref.org/works?query.bibliographic=velocity-domain+MAPPO+approach+perimeter+defensive+confrontation+USV+groups&rows=2); [ScienceDirect(403)](https://www.sciencedirect.com/science/article/abs/pii/S0957417424028471)
- Chen, Lang; Liu, Zengli; Zhao, Xuanzhi. (적응 커리큘럼 학습 + MAPPO 기반 USV 군집 포위 의사결정) *Journal of Zhejiang University (Engineering Science)* 2026, 60(7), 1369–1380. DOI 10.3785/j.issn.1008-973X.2026.07.001. 소속: 昆明理工大学. ACL-MAPPO(CTDE, 환경 복잡도·탐색 노이즈 동적 조정), 암초 장애물·동적 표적, 2v2/3v3/4v4; 비교 NOCL-MAPPO, CL-MAPPO, MADDPG; 포위 성공률·완료시간·경로길이·충돌수 개선 보고. — [학술지 영문 초록](https://www.zjujournals.com/eng/EN/abstract/abstract47328.shtml)
- Tan, Huihui; Zhang, Shuang; Lin, Shiwei; Huang, Bomin. "GR-MAPPO Algorithm for Perimeter Defense Problem in Multi-Agent Systems." *Entropy* 2026, 28(6), 659. DOI 10.3390/e28060659. 초록: "제한된 국지 통신 하에서 협조·시간 정보를 활용하지 못하고 군집 규모 변동에 일반화가 부족"한 기존 DRL의 한계를 지적. — [Crossref](https://api.crossref.org/works?query.bibliographic=velocity-domain+MAPPO+approach+perimeter+defensive+confrontation+USV+groups&rows=2)

**(6) MADDPG/MASAC 계열 포위·침투·추격**
- Wang, Cheng-Cheng; Wang, Yu-Long; Shi, Peng; Wang, Fei. "Scalable-MADDPG-Based Cooperative Target Invasion for a Multi-USV System." *IEEE Trans. Neural Networks and Learning Systems* 2024, 35(12), 17867–17877. DOI 10.1109/TNNLS.2023.3309689. (서지만 확인) — [Crossref](https://api.crossref.org/works?query.bibliographic=Scalable-MADDPG-Based+Cooperative+Target+Invasion+for+a+Multi-USV+System&rows=2)
- Qu, Xingru; Li, Chu; Jiang, Yuze; Long, Feifei; Zhang, Rubo. "Cooperative Pursuit of Unmanned Surface Vehicles Using Multi-Agent Reinforcement Learning." *J. Shanghai Jiaotong Univ. (Sci.)* 2026, 31(1), 187–194. DOI 10.1007/s12204-025-2816-6. 소속: 大连民族大学. MASAC + LSTM, CTDE, 다단계 보상 유도(단순→복잡), "lazy capturer" 문제 완화, 거리·각도 성공 조건. — [학술지 초록](https://xuebao.sjtu.edu.cn/sjtu_en/EN/abstract/abstract51078.shtml)
- Xue, Shan; Zhao, Ning; Wang, Liqi; Zhang, Weidong; Zhang, Jilan; Zhu, Fengxian. "Multi-agent self-attention reinforcement learning for multi-USV hunting target." *Neural Networks* 2025, 189, 107574. DOI 10.1016/j.neunet.2025.107574. 다중헤드 self-attention MARL; 수렴속도 17%·헌팅 성공률 8% 개선 [검색 스니펫만 확인]. — [Crossref](https://api.crossref.org/works?query.bibliographic=multi-agent+self-attention+reinforcement+learning+multi-USV+hunting+target+Neural+Networks&rows=3)
- Zhang, Chenming; Zeng, Rijie; Lin, Bin; Zhang, Yibo; Xie, Wei; Zhang, Weidong. "Multi-USV cooperative target encirclement through learning-based distributed transferable policy and experimental validation." *Ocean Engineering* 2025, 318, 120124. DOI 10.1016/j.oceaneng.2024.120124. (서지만 확인; 실험 검증 포함 제목) — [Crossref](https://api.crossref.org/works?query.bibliographic=Multi-USV+cooperative+target+encirclement+through+learning-based+distributed+transferable+policy+and+experimental+validation&rows=2)
- Hamid, Nur; Dharmawan, Willy; AbouOmar, Mahmoud S.; Kurniawan, Hendra; Saleh, Haitham; El Ferik, Sami. "Swarm unmanned surface vehicle encirclement task with multi-agent reinforcement learning." *Transportation Research Procedia* 2026, 97, 468–475. DOI 10.1016/j.trpro.2026.04.017. 소속: KFUPM. MAPPO vs MAPPO-LSTM, 방어 USV 3척, 실제 지형 기반 수역, Unity 3D ML-Agents. MAPPO-LSTM이 누적보상·시간 안정성 우수, 기본 MAPPO는 공간 커버리지 우수. — [KFUPM Pure](https://pure.kfupm.edu.sa/en/publications/swarm-unmanned-surface-vehicle-encirclement-task-with-multi-agent/)
- Hamid, Nur; Saleh, Haitham; El Ferik, Sami. "XAI-Driven Multi-Agent Reinforcement Learning for Swarm USV Continuous Multi-Target Hunting." *2026 6th Int. Conf. on Electrical, Computer and Energy Technologies (ICECET)*, pp. 1–6. DOI 10.1109/icecet65726.2026.11633110. (서지만 확인) — [Crossref](https://api.crossref.org/works?query.bibliographic=multi-agent+self-attention+reinforcement+learning+multi-USV+hunting+target+Neural+Networks&rows=3)

**(7) 잔차(residual)·옵션 기반 MARL, 이기종 USV**
- Tao, Jiyue; Shen, Tongsheng; Zhao, Dexin; Zhang, Feitian. "ARBoids: Adaptive Residual Reinforcement Learning With Boids Model for Cooperative Multi-USV Target Defense." arXiv:2502.18549 (2025); *IEEE Robotics and Automation Letters*, DOI 10.1109/LRA.2026.3662620. Boids 힘 기반 기저 정책 + DRL 잔차; 고기동 공격 USV 대응; Gazebo 고충실도 검증. — [arXiv](https://arxiv.org/abs/2502.18549)
- Mao, Jiayang; Wang, Lanfeng; Peng, Zhao-Han. "OGR-MARL: Option-Guided Residual Multi-Agent Reinforcement Learning for Heterogeneous USV Cooperative Pursuit in Constrained Port Waterways." arXiv:2608.12995 (2026). 공유 회피자 belief, 역할조건 옵션, 적응 규칙 페널티, 잔차 정책; MADDPG/MATD3/MAPPO/MASAC 4개 백본에 적용; 추상 Xiazhimen 항만 수로에서 OGR-MASAC 포획률 75.0%; QGIS/AIS 기반 시나리오로 zero-shot 전이. — [arXiv](https://arxiv.org/abs/2608.12995)

**(8) 계층형 RL·게임이론·인간 피드백**
- Wu, Qizhen; Liu, Kexin; Chen, Lei; Lü, Jinhu. "Hierarchical Reinforcement Learning for Swarm Confrontation with High Uncertainty." arXiv:2406.07877 (2024). 이산 표적할당 계층 + 연속 경로계획 계층 + 확률 앙상블 불확실성 정량화; 사전학습+교차학습; 약 90% 승률. (플랫폼 비특정 군집 추격회피; 에이전트 20–40 규모라는 요약은 [확인 필요]) — [arXiv](https://arxiv.org/abs/2406.07877)
- Yuwen, Cheng; Zhou, Jialing; Luan, Meng; Wen, Guanghui; Huang, Tingwen. "Nash equilibrium seeking in coalition games for multiple Euler-Lagrange systems: Analysis and application to USV swarm confrontation." arXiv:2504.04475 (2025.4, 2025.10 개정). 연합 게임 분산 NE 탐색(적응·부호함수, primal-dual+합의, 동적 평균 합의), EL 동역학·외란, 대형·포위·요격 과제; Lyapunov 수렴 증명, 수치 시뮬레이션. — [arXiv](https://arxiv.org/abs/2504.04475)
- Kim, Hyeonjun; Lee, Kanghoon; Park, Junho; Li, Jiachen; Park, Jinkyoo. "Human Implicit Preference-Based Policy Fine-tuning for Multi-Agent Reinforcement Learning in USV Swarm." arXiv:2503.03796 (2025). 에이전트 수준 피드백(intra-agent/inter-agent/intra-team), LLM을 평가자로 사용한 RLHF형 MARL 미세조정; 정량 결과는 초록에 없음(소속 [확인 필요]). — [arXiv](https://arxiv.org/abs/2503.03796)
- Qu, Xingru; Zeng, Linghui; Qu, Shihang; Long, Feifei; Zhang, Rubo. "An Overview of Recent Advances in Pursuit–Evasion Games with Unmanned Surface Vehicles." *J. Mar. Sci. Eng.* 2025, 13(3), 458. DOI 10.3390/jmse13030458. 大连民族大学. 1v1/다대1/다대다 PE 종합 리뷰; 2023년 이후 우크라이나의 자폭 USV 운용을 연구 동기로 명시. — [PDF 전문](https://mdpi-res.com/d_attachment/jmse/jmse-13-00458/article_deploy/jmse-13-00458.pdf)
- (자기대결) "A deep reinforcement learning approach and its application in multi-USV adversarial game simulation." *Applied Intelligence* 2025 (Springer s10489-025-06380-x). ICM+self-play+POCA를 PPO에 결합, 적군(red) 승률 88.25/86.75/91.33%(100 에피소드) [검색 스니펫만 확인, 저자 미확인]. — [Springer 링크(미열람)](https://link.springer.com/article/10.1007/s10489-025-06380-x)

**(9) 서구: MIT Lincoln Laboratory / NRL Pyquaticus**
- Beason, Jordan; Novitzky, Michael; Kliem, John; Errico, Tyler; Serlin, Zachary; Becker, Kevin; Paine, Tyler; Benjamin, Michael; Dasgupta, Prithviraj; Crowley, Peter; O'Donnell, Charles; James, John. "Evaluating Collaborative Autonomy in Opposed Environments using Maritime Capture-the-Flag Competitions." arXiv:2404.17038 (2024), IEEE ICRA 2024 Workshop on Field Robotics. 2v2 USV CTF(2023년 가을 경기); 행동기반 최적화 vs DRL; **규칙 기반 협동이 DRL 학습 에이전트를 능가**; 향후 과제로 reward shaping, sim-to-real, 안전·보안 이벤트 처리. — [arXiv](https://arxiv.org/abs/2404.17038)
- Crowley, Peter; Long, Brendan; Schoer, Andrew; Serlin, Zachary; Mann, Makai; Gonsalves, Tyler; Kliem, John; Belta, Calin. "Pyquaticus: A Sim-to-Real Pipeline for Learning in Multi-Agent Maritime Strategy Games." 2025(© 2025 MIT; 게재 학술행사 [확인 필요]). 소속: Boston Univ., MIT Lincoln Laboratory, U.S. Naval Research Laboratory, Univ. of Maryland. PettingZoo parallel API, RLlib 예제, 이산·연속 행동, PyquaticusMoosBridge(PyMOOS로 MOOSDB 구독/발행); Clearpath Heron USV 동역학 + MOOS-IvP 속도·방위 PID; 2v2 MCTF를 50개 시연으로 Behavioral Cloning 학습 후 MOOS-IvP 시뮬 → Charles River 실선(Heron, backseat Raspberry Pi 4) 배치; SeaRobotics Surveyor 3v3 실험 진행 중. — [PDF](https://calinbelta.com/wp-content/uploads/2026/03/pyquaticus-1.pdf)
- Pyquaticus GitHub README: MOOS-IvP uSimMarine 기반 동역학, 팀 규모 파라미터화, 탈중앙·에이전트 상대 관측 옵션, DFARS 무제한 권리 라이선스. — [GitHub](https://github.com/mit-ll-trusted-autonomy/pyquaticus/blob/main/README.md)

### Inferences
- USV MARL 문헌의 과제 정의는 "누가 누구를 쫓는가(추격·포위·경호)"에 집중되어 있고, 무장 종류·탄약·교전 창을 포함한 WTA 정식화는 Hu 2024 외 부재하다. 연구자의 (b)에서 사용한 MRCPSPTW+DSR 정식화는 이 영역에서 희소하며, 후속연구의 차별 포인트는 "WTA를 유지하면서 문제 정의(통신거부·불확실성·시간동기)를 바꾸는 것"에 있다.
- 비교 기준(baseline)은 거의 QMIX/MADDPG/MAPPO 변형이며, CBBA·MILP 등 OR 기준과의 교차 비교는 Hu 2024(GA, Grey Wolf)만 수행했다. (b)의 MILP·CBBA·QMIX·MADDPG·Adv-TransAC 동시 비교는 국제 기준으로도 드문 구성이다.
- Xiong 2025가 Adv-TransAC를 "학습 상대" 조건에서 78.5% 성공률로 보고한 점은, (b)에서 Adv-TransAC를 72.2% DSR 기준선으로 재현한 수치와 직접 비교되므로, 후속 논문에서 재현 조건(환경·상대 유형)을 명시해야 재현성 논란을 피할 수 있다.
- Beason 2024의 "규칙 기반이 DRL을 이겼다"는 결과는 후속연구에서 규칙/휴리스틱 기준선을 반드시 포함해야 함을 시사한다.

### Gaps
- Li 2024(TSMC), Pu 2025(ESWA), Wang 2024(TNNLS), Xue 2025(Neural Networks), Zhang 2025(Ocean Eng.)의 초록·수치는 IEEE Xplore/ScienceDirect 403으로 열지 못해 서지만 확보했다 [확인 필요].
- 哈尔滨工程大学·NUDT·上海交通大学·武汉理工大学의 USV 군집 "교전(WTA)" 전용 MARL 논문은 검색에서 특정되지 않았다(哈工程은 Changdong 2024 공저 및 AUV CBBA; 武汉理工은 AUV 협동 헌팅 JMSE 2025로만 확인). NPS·NRL의 USV 군집 WTA MARL 논문도 발견되지 않았다.
- Changdong 2024 외 中文 학술지(兵工学报, 系统工程与电子技术 등)는 조사 범위에 포함하지 못했다.

---

## KQ2. CBBA/합의/경매/헝가리안/탐욕 기반 USV·해양 다중 운반체 할당 연구와 통신 지연·패킷손실·재밍·그래프 분절 처리 방식은?

### Takeaway
해양 분산 할당 연구의 통신 열화 모델링은 **AUV(수중음향) 영역**에서 가장 정교하며(5단계 통신 레짐, 범위·지연·패킷손실·대역폭 파라미터), USV 영역에서는 재밍·기만·그래프 분절을 명시적으로 모델링한 할당 연구가 확인되지 않았다. 과제가 지칭한 "Xie 2024 IEEE Access"는 USV 할당 논문이 아니라 Hui Xie의 다중에이전트 협조제어(지연·패킷손실) 논문으로 확인된다.

### Cited Findings
- Wang, Hailin; Li, Shuo; Qiu, Tianyou; Wang, Yiqun; Li, Yiping. "Dynamic Task Allocation for Multiple AUVs Under Weak Underwater Acoustic Communication: A CBBA-Based Simulation Study." *J. Mar. Sci. Eng.* 2026, 14(3), 237. DOI 10.3390/jmse14030237. 소속: 中国科学院沈阳自动化研究所(SIA), UCAS. Dubins 운동학, 설정가능 음향통신 모델(범위·지연·패킷손실·대역폭), 5개 통신 레짐(이상적 완전연결 → 단거리·고손실 SEVERE); 지표: 총 번들 가치·임무 완료율, 수렴 반복수·수렴률, 메시지 전달률·평균 지연·네트워크 연결성, 동적 재할당 충돌수. 기본 시나리오 4 AUV, 10–20 임무, 2000×2000×200 m; 규모 확장 3/4/6/8 AUV. **결론: CBBA는 양호·보통 조건에서 최적 근접이나 연결이 간헐적이 되면 급격히 저하**; 근접 트리거형 "국지 통신 기반 충돌 해소"(이웃 한정 교환, 임무 구역 내 협상, 분산 국지 결정)로 충돌 감소·완료율 개선. 향후: 6-DOF 동역학 모듈로 대체. — [PDF 전문](https://mdpi-res.com/d_attachment/jmse/jmse-14-00237/article_deploy/jmse-14-00237.pdf)
- Li, Juan; Liu, Baohua; Liu, Caiyun; Lin, Cong. "Dynamic Task Allocation for Heterogeneous Multi-Autonomous Underwater Vehicle Collaboration Under Mine Countermeasures Missions." *J. Mar. Sci. Eng.* 2025, 13(3), 465. DOI 10.3390/jmse13030465. 소속: 哈尔滨工程大学 智能系统科学与工程学院. SWCBBA-PR(소프트 시간창 + 부분 재할당 CBBA), 이기종 AUV MCM(탐색→처리→확인 시간결합 서브태스크), 신규 임무점 출현 시 실시간 재할당. 서론에서 "통신 지연·고 비트오류율·고 패킷손실 등 비이상 통신 환경 연구는 현재 제한적"이라고 명시; 4대 과제로 실시간성·계산복잡도·통신·이기종성을 열거. — [PDF 전문](https://mdpi-res.com/d_attachment/jmse/jmse-13-00465/article_deploy/jmse-13-00465.pdf)
- Xie, Hui. "Cooperative Control of Multi-Agent Systems Under Communication Delays and Packet Loss Scenarios." *IEEE Access* 2024, 12, 149804–149813. DOI 10.1109/ACCESS.2024.3477713. Crossref 검색에서 "Xie + USV task allocation + delay/packet loss + IEEE Access 2024" 조건에 유일하게 부합하는 논문. 제목상 다중에이전트 **협조제어**(합의)이며 USV 할당 특화 여부·모델링 방식은 미확인 [확인 필요]. — [Crossref](https://api.crossref.org/works?query.author=Xie&query.bibliographic=unmanned+surface+vehicle+task+allocation+communication+delay+packet+loss&filter=container-title:IEEE+Access,from-pub-date:2023-06,until-pub-date:2025-06&rows=5)
- 비해양 영역의 통신제약 할당(참고 앵커, 스니펫만 확인): "Assignment-Consistent Dynamic Multi-UAV Task Allocation: Communication-Efficient ... Under Stale and Asymmetric Information" *Drones* 10(7), 523 (DOI 10.3390/drones10070523); "CC-OPI: Online Distributed Task Allocation for UAV Swarms under Communication Constraints" arXiv:2609.19208; "Grouping Auction-Consensus Algorithm for Decentralized Task Allocation in Multi-Robot Systems" arXiv:2608.15884; "Event-Triggered Adaptive Consensus for Multi-Robot Task Allocation" arXiv:2604.06813; "Task Assignment of UAV Swarms Based on Auction Algorithm in Poor Communication" (BIT). — [검색 결과](https://doi.org/10.3390/drones10070523)
- 재밍 관련(스니펫만 확인): "Robust Communication-Aware Jamming Detection and Avoidance for UAS Swarms"(ResearchGate 397404927); "Agent-Based Anti-Jamming Techniques for UAV Communications in Adversarial Environments: A Comprehensive Survey" arXiv:2508.11687; "Multi-Agent Reinforcement Learning Based UAV Swarm Communications Against Jamming"(IEEE). 모두 UAV·통신층 연구이며 할당 알고리즘과 결합한 사례는 없음. — [arXiv 2508.11687](https://arxiv.org/pdf/2508.11687)
- 미국 해군연구청(ONR) Code 33 "Cooperative Autonomous Swarm Technology(CAST)" 프로그램은 UUV·USV·무장의 협동 운용을 목표로 하며, 연구 과제에 분산 알고리즘, 협동 항법, 동종·이기종 그룹, 결함 관리, **대군집(counter-swarm) 전술**, "참가자 간 통신이 전혀 없는 상태에서 군집이 작동하는 능력"을 명시(FY25 Long Range BAA). — [ONR 페이지](https://www.onr.navy.mil/organization/departments/code-33/division-333/cooperative-autonomous-swarm-technology)

### Inferences
- Wang 2026(JMSE 14:237)의 "통신 레짐 스윕 + 할당 품질·수렴·통신효율 3축 지표" 설계는 USV WTA에 그대로 이식 가능한 평가 프로토콜이다. 후속연구 T1에서 CBBA를 동일 레짐에서 재현 비교하면 국제적으로 통용되는 기준선이 된다.
- 해양 할당 문헌의 통신 모델은 "확률적 손실·지연"에 머물고, **의도적 재밍 기하(jammer 위치·출력 기반 SINR), 기만(spoofed bid/상태), 그래프 분절(connected component) 지표**를 결합한 연구는 확인되지 않아 명확한 공백이다.

### Gaps
- Xie 2024의 본문(모델링, USV 언급 여부)은 IEEE Xplore 접근 불가로 미확인.
- USV 전용 CBBA/경매 할당 논문(2020–2026)은 이번 검색에서 특정되지 않았다(AUV·UAV로 치환됨). 헝가리안/탐욕 기준 USV 교전 할당 논문도 미발견.

---

## KQ3. 이기종·교차영역 군집(USV+UAV, USV+UUV) 표적 할당 연구와 방법은?

### Takeaway
교차영역(UAV+USV+UUV) 표적 할당은 2026년 초 중국 공군공정대학의 **이중계층(bi-level) 최적화**(상위 GA 할당 + 하위 최소시간 최적제어)가 가장 직접적인 선행이며, MARL 기반 교차영역 WTA는 확인되지 않았다. 이기종 USV(동일 영역 내 역할 차이) MARL은 OGR-MARL(2026)이 있다.

### Cited Findings
- Zheng, Aoyu; Liang, Xiaolong; Zhang, Zhiyang; Xiao, Yuyan; Zhang, Jiaqiang. "Research on Integrated Decision-Control Cooperative Target Assignment for Cross-Domain Unmanned Systems Based on a Bi-Level Optimization Framework." *Drones* 2026, 10(3), 193. DOI 10.3390/drones10030193. 소속: 空军工程大学(Air Force Engineering University, 西安). UAV(Ma)·USV(Ms)·UUV(Mu) 3종, 수상·수중 등 표적 유형별 능력 매칭 제약; 상위: 최대 임무완료시간 최소화(개선 GA), 하위: 비선형 운동학 기반 최소시간 최적제어(미분평탄성 변환 + Radau 의사스펙트럼법 → NLP), 실행시간을 상위로 피드백하는 폐루프. 유클리드 거리 기반 할당 대비 최대 완료시간 "현저히" 단축(수치는 본문 표 [확인 필요]). 향후: 동적 재할당, 강건 다목적 최적화, 대규모 분산 풀이 구조. — [PDF 전문](https://mdpi-res.com/d_attachment/drones/drones-10-00193/article_deploy/drones-10-00193.pdf)
- Sun, Haolun; Guo, Xiangke; Bu, Xiangwei; Wang, Gang. "A collaborative target assignment method for heterogeneous multi-firepower elements based on an adaptive grabbing-order mode." *Defence Technology* 2026. DOI 10.1016/j.dt.2026.07.002. (서지만 확인; 이기종 화력 요소 대상 "주문 선점" 방식) — [Crossref](https://api.crossref.org/works?query.bibliographic=collaborative+target+assignment+method+heterogeneous+multi-firepower+elements+adaptive+grabbing-order+mode&rows=2)
- Mao, Wang, Peng 2026 OGR-MARL(위 KQ1(7)): 이기종 USV 협동 추격, 역할조건 옵션. — [arXiv](https://arxiv.org/abs/2608.12995)
- 교차영역 USV-UAV 대형 제어 RL(스니펫만 확인): "Cooperative Formation Control of USVs and UAVs Based on Reinforcement Learning" Springer chapter DOI 10.1007/978-981-96-5373-7_58; "Risk-Aware Order Dispatching–Grabbing Framework for Cross-Domain Swarm Task Allocation" Springer chapter DOI 10.1007/978-981-95-8435-2_66; 특허 동향 분석(PatSnap 2026)은 哈尔滨工程大学·西北工业大学·清华大学의 AUV-USV-UAV 통합 아키텍처 출원 증가를 언급. — [검색 결과](https://link.springer.com/chapter/10.1007/978-981-96-5373-7_58)
- 교차영역 USV-UAV 할당에서 "최대 140개 동적 표적 처리, 할당 지연 감소" 주장은 검색 요약에 등장했으나 출처 논문을 특정하지 못함 [확인 필요].

### Inferences
- 교차영역 할당은 "운동학 제약을 할당에 통합"하는 OR 접근이 선행하므로, MARL/학습 기반 T7은 "실행 가능성(kinematic feasibility)·시간 동기화"를 평가 축에 넣어야 Zheng 2026과 공정 비교가 가능하다.
- UUV의 저속·음향통신 제약은 Wang 2026(JMSE 14:237)의 음향 레짐을 재사용해 모델링할 수 있어 T1과 T7은 통신 모델을 공유할 수 있다.

### Gaps
- MARL 기반 UAV+USV+UUV **무장** 할당(자폭/미사일/EW/기만 역할 분담) 논문은 발견하지 못했다. 열람 불가(403)로 Defence Technology 2026의 세부도 미확인.

---

## KQ4. 사용된 시뮬레이션 환경·충실도, 군집 규모(전형/최대), 지표는?

### Takeaway
공개 문헌의 USV 군집 MARL은 **커스텀 2D Python(PettingZoo 포함) → Unity ML-Agents → ROS/Gazebo(VRX) → Pyquaticus(MOOS-IvP 연동, 실선 전이)** 순으로 충실도가 올라가며, 규모는 2v2~4v4(최대 3v1·6v2, 5척×25표적)로 작다. 연구자의 80v80은 공개 USV MARL 문헌 중 최대 규모로 판단된다(단, 20–40 에이전트 계층 RL과 25 USV 항법 사례가 존재).

### Cited Findings
- 커스텀 Python/PettingZoo: Xiong 2025는 PettingZoo 1.15.0 "waterworld"를 공방 시나리오로 수정, RTX 3090 단일 GPU, 200만 step, 1,000 에피소드 평가; 지표 임무성공률·HVU 피해량·동료충돌률·상대파괴율·파라미터 수·단일 step 추론시간. — [PDF](https://mdpi-res.com/d_attachment/jmse/jmse-13-01593/article_deploy/jmse-13-01593.pdf)
- 커스텀 Python(MADDPG): Hu 2024는 Ryzen 7 5800H + RTX 3060 노트북급 하드웨어, 5 USV × 25 표적, 지표 해 품질·풀이시간·해 안정성(분산). — [PDF](https://mdpi-res.com/d_attachment/mathematics/mathematics-12-02557/article_deploy/mathematics-12-02557.pdf)
- Unity 3D ML-Agents: Hamid et al. 2026(KFUPM) 3 방어 USV, 실제 지형 수역. — [KFUPM](https://pure.kfupm.edu.sa/en/publications/swarm-unmanned-surface-vehicle-encirclement-task-with-multi-agent/)
- ROS/Gazebo: Shrudhi 2023(MA-DDPG); Tao 2025 ARBoids("고충실도 Gazebo"). VRX(Virtual RobotX)는 Gazebo 기반 오픈소스 해양 환경(Open Robotics, Maritime RobotX 경연) [검색 스니펫]. — [arXiv 2304.08189](https://arxiv.org/abs/2304.08189); [arXiv 2502.18549](https://arxiv.org/abs/2502.18549)
- Pyquaticus(MIT LL/NRL): 순수 Python, 실시간 이상 속도, 클러스터 병렬화, MOOS-IvP uSimMarine 동역학, Heron·Surveyor 모델, PettingZoo·RLlib·Stable Baselines 연동, Charles River 실선 2v2, 3v3 진행 중; AAMAS 2024/2025 Maritime CTF 경연 CfP 존재 [스니펫]. — [PDF](https://calinbelta.com/wp-content/uploads/2026/03/pyquaticus-1.pdf); [GitHub](https://github.com/mit-ll-trusted-autonomy/pyquaticus/blob/main/README.md)
- GIS 연계: OGR-MARL은 QGIS/AIS 기반 Xiazhimen 항만 시나리오로 zero-shot 전이. — [arXiv](https://arxiv.org/abs/2608.12995)
- 규모: Changdong 2024 3v1·6v2; Chen 2026(ZJU) 2v2/3v3/4v4; Beason 2024 2v2; Wu 2024 계층 RL 수십 에이전트(약 90% 승률); "Communication-aware MARL for cooperative navigation of multiple USVs" *Ocean Engineering* 2025(S0029801825033086)는 최대 25 USV, 임무성공 >90% [스니펫만 확인]. 대규모 UAV 대결 앵커: Weighted mean-field RL(*Applied Intelligence* 2022, DOI 10.1007/s10489-022-03840-6), Hierarchical attention actor-critic(*Applied Intelligence* 2024, DOI 10.1007/s10489-024-05293-5) [스니펫만 확인]. — [검색 결과](https://www.sciencedirect.com/science/article/abs/pii/S0029801825033086)
- 미 해군 M&S: NPS는 MANA(Map Aware Non-uniform Automata), LITMUS(Tanalega 2018 "Analyzing Unmanned Surface Tactics with LITMUS", 지도교수 Thomas Lucas) 등 에이전트 기반 시뮬레이션으로 USV 전술을 분석. — [NPS SEED theses](https://nps.edu/web/seed/theses)
- 실선 검증: Li, Yan; Li, Xiaowen; Wei, Xiangwei; Wang, Hao. "Sim-real joint experimental verification for an unmanned surface vehicle formation strategy based on multi-agent deterministic policy gradient and line of sight guidance." *Ocean Engineering* 2023, 270, 113661. DOI 10.1016/j.oceaneng.2023.113661 (개방 호수 실선 시험 [스니펫]). — [Crossref](https://api.crossref.org/works?query.bibliographic=Sim-real+joint+experimental+verification+unmanned+surface+vehicle+formation+strategy+multi-agent+deterministic+policy+gradient+line+of+sight+guidance&rows=2)
- 산업 실증: Scientific Systems의 OPTIMUS 협동 자율 SW가 2025년 8월 9척 sUSV(VENOM 6/9/13 m) 주간 해상시험에서 탐색·감시·교전·동적 재경로를 수행, "운용자는 임무 규칙·의도·권한만 정의", 통신 단절 시 임무 지속(2025-11-18 발표). — [Soldier Systems](https://soldiersystems.net/2025/11/19/scientific-systems-autonomy-software-achieves-a-major-milestone-in-test-with-group-of-unmanned-boats/)

### Inferences
- 로컬 PC(단일 GPU) 수준에서 수행된 연구(Hu: RTX 3060; Xiong: RTX 3090)가 SCI급에 게재되므로, 연구자의 PC 기반 시뮬레이터 개발은 국제 관행과 부합한다. 공개 재현성을 위해 PettingZoo parallel API 준수 + 설정 가능한 통신 레짐(JMSE 14:237 방식) + Pyquaticus/MOOS-IvP 브리지 호환을 설계 목표로 삼으면 서구 커뮤니티와의 접점이 생긴다.
- 표준 지표가 부재하므로 (b)의 DSR(0.7 파괴율 + 0.3 생존율) 외에 국제 문헌이 쓰는 임무성공률·HVU 피해·동료충돌률·추론시간·메시지 전달률을 병기해야 비교가 가능하다.

### Gaps
- AFSIM 사용 USV 군집 공개 논문은 발견되지 않았다(배포 제한 추정). NATO/미 해군의 고충실도 교전 시뮬레이터 공개 사례도 미확인.

---

## KQ5. 저자들이 미해결로 지목한 문제는?

### Takeaway
반복적으로 지목되는 미해결 과제는 (i) sim-to-real/도메인 랜덤화, (ii) 간헐·저대역 통신 및 불완전 정보(사이버 공격 포함), (iii) 군집 규모 변동에 대한 일반화·확장성, (iv) 적응형 상대에 대한 비정상성, (v) 동적 임무 할당과 안전 제어, (vi) 규칙 기반 대비 DRL의 열세(보상 설계)이며, 설명가능성(XAI)은 2026년에야 USV 군집 MARL에 등장했다.

### Cited Findings
- Xiong 2025: 세 가지 근본 문제로 다중 모달 센서 융합, 정교한 협동 적대 전략 학습, "해양 작전 고유의 간헐·저대역 통신"을 명시; 고정 상대 분포에 학습한 정책의 취약성(brittleness); 5.4절에서 도메인 랜덤화 등 향후 과제. — [PDF](https://mdpi-res.com/d_attachment/jmse/jmse-13-01593/article_deploy/jmse-13-01593.pdf)
- Qu et al. 2025 리뷰: 향후 방향으로 **표적 예측, 동적 임무 할당, 뇌모사 의사결정, 안전 제어, PE 실험**; 불완전 정보는 불완전 인지·불완전 상호작용·사이버 공격으로 분류; 해상 통신의 저전송률·고지연·제한 커버리지·고패킷손실을 장애로 명시. — [PDF](https://mdpi-res.com/d_attachment/jmse/jmse-13-00458/article_deploy/jmse-13-00458.pdf)
- Beason 2024: 규칙 기반 협동이 DRL을 능가; reward shaping과 sim-to-real 방법론, 전문가 의도에 맞는 안전·보안 이벤트 처리가 우선 과제. — [arXiv](https://arxiv.org/abs/2404.17038)
- Wang 2026(JMSE 14:237): CBBA는 연결이 간헐적이면 급격히 저하, 분절(fragmentation) 주도 불일치·거짓 수렴(false convergence) 탐지 문제; 6-DOF 동역학 미반영. — [PDF](https://mdpi-res.com/d_attachment/jmse/jmse-14-00237/article_deploy/jmse-14-00237.pdf)
- Li 2025(JMSE 13:465): 비이상 통신(지연·비트오류·패킷손실) 하 할당 연구 부족; 실시간성·계산복잡도·통신·이기종성 4대 과제. — [PDF](https://mdpi-res.com/d_attachment/jmse/jmse-13-00465/article_deploy/jmse-13-00465.pdf)
- Tan 2026(GR-MAPPO): 제한된 국지 통신에서 협조·시간 정보 활용 부족, 동적 군집 규모 변동 일반화 부족. — [Crossref](https://api.crossref.org/works?query.bibliographic=velocity-domain+MAPPO+approach+perimeter+defensive+confrontation+USV+groups&rows=2)
- Hu 2024: 연속 행동 화력 분배와 대결(confrontation) 미반영. — [PDF](https://mdpi-res.com/d_attachment/mathematics/mathematics-12-02557/article_deploy/mathematics-12-02557.pdf)
- Zheng 2026(Drones): 동적 재할당, 강건 다목적 최적화, 대규모 분산 풀이 구조가 후속 과제; 실시간 구현과 대규모 확장성 제약 언급. — [PDF](https://mdpi-res.com/d_attachment/drones/drones-10-00193/article_deploy/drones-10-00193.pdf)
- ONR CAST: 무통신 군집 운용, 대군집 전술이 미해결 연구 과제로 공모. — [ONR](https://www.onr.navy.mil/organization/departments/code-33/division-333/cooperative-autonomous-swarm-technology)
- NATO S&T Trends 2023–2024(검색 요약): RAS 발전은 SWaP-C·AI·군집 행동에 기반하며 **swarm-on-swarm 교전은 열린 연구 영역**으로 식별 [스니펫만 확인]. — [ResearchGate 397906776](https://www.researchgate.net/publication/397906776_NATO_Science_Technology_Trends_2023-2024_Volume_1)
- XAI: Hamid, Saleh, El Ferik 2026 ICECET "XAI-Driven MARL for Swarm USV Continuous Multi-Target Hunting"이 확인된 유일한 USV 군집 MARL+XAI 논문(서지만). — [Crossref](https://api.crossref.org/works?query.bibliographic=multi-agent+self-attention+reinforcement+learning+multi-USV+hunting+target+Neural+Networks&rows=3)
- LLM: Din, Muhayy Ud; Akram, Waseem; Bakht, Ahsan B.; Dong, Yihao; Hussain, Irfan. "Maritime Mission Planning for Unmanned Surface Vessel using Large Language Model." arXiv:2503.12065 (2025), IEEE SIMPAR. 자연어 명령 → 기호적 임무계획, 하위 제어기 피드백으로 계획 정제; 시뮬레이션 검증. — [arXiv](https://arxiv.org/abs/2503.12065)

### Inferences
- 미해결 과제 목록과 연구자의 (b) 향후과제(HILS/sim-to-real, 적응 상대 self-play, 이기종 확장)는 겹치므로, 후속연구는 "아직 어떤 USV 논문도 다루지 않은 조합"(통신거부+기만 하의 학습형 WTA; 불확실성 강건 WTA; 지휘관 의도→제약 변환)을 택해야 중복성 논란을 피한다.

### Gaps
- Hong et al. 2025 리뷰(arXiv:2506.21063 "Control of Marine Robots in the Era of Data-Driven Intelligence")는 초록만 확인되어 구체 미해결 목록은 미확인.

---

## KQ6. NPS(Calhoun), DTIC, NATO STO의 USV 군집 교전 의사결정 보고서(2020–2026)는?

### Takeaway
NPS Calhoun에는 USV 운용 분석(DMO, MANA 기반)·협동 무인체계 MCM(2020) 등 운용분석 논문이 있으나 **USV 군집 WTA/MARL 전용 학위논문은 특정되지 않았고**, NATO STO는 SET-263(ISR 군집, CATL, REPMUS22/DYMS22) 중심으로 ISR·C2 계층에 집중한다. DTIC 전문은 접근 차단(403)으로 열지 못했다.

### Cited Findings
- NPS SEED Center 논문 목록: Ling, Tong Hai (2020.9) "Use of Cooperative Unmanned Systems for Mine Countermeasures"(지도 Thomas Lucas, MORS Tisdale 최종후보); Tanalega, John (2018.3) "Analyzing Unmanned Surface Tactics with the Lightweight Interstitials Toolkit for Mission Engineering Using Simulation (LITMUS)"(MORS Tisdale 수상); 2020년 이후 USV 군집 교전 전용 논문은 목록에 없음. — [NPS SEED](https://nps.edu/web/seed/theses)
- NPS Calhoun 10945/64162 "Analysis of Unmanned Surface Vessel Employment in Distributed Maritime Operations": 2030–2035 DMO 시나리오를 MANA 에이전트 기반 모델에 반영 [검색 스니펫; 페이지 본문은 DSpace 로딩만 반환, 저자·연도 확인 필요]. — [Calhoun](https://calhoun.nps.edu/handle/10945/64162)
- NPS SEA-18B 캡스톤 "Tailorable Remote Unmanned Combat Craft(TRUCC)": 비대칭 군집 공격으로부터 함정을 방어하는 USV 패밀리 개념, Strait of Hormuz DRM 에이전트 기반 시뮬레이션으로 핵심 성능기준 도출 [스니펫만 확인]. — [Calhoun bitstream](https://calhoun.nps.edu/server/api/core/bitstreams/c4a79edc-4afc-49bd-acc5-13505dfb4bb2/content)
- NPS Wargaming "Developing New Tactics and Technologies in Naval Warfare: The MDUSV Example"(2019): LITMUS로 MDUSV 전술 연구 [스니펫]. — [NPS](https://nps.edu/documents/120849547/0/NPS+Wargaming+-+Article1+-+Developing+New+Tactics+and+Technologies+in+Naval+Warfare_+The+MDUSV+Example.pdf/dd1841b7-3b1b-cf81-bed6-ed3680486467?t=1594335766541)
- NATO STO-TR-SET-263 "Swarm System for Intelligence Surveillance and Reconnaissance"(2022.8): 군집 중심 ISR 고수준 참조 아키텍처(SS4ISR); 2023 STO Highlights에 따르면 SET-263이 인간-군집 상호작용과 **Collaborative Autonomy Tasking Layer(CATL)** 를 개발, REPMUS22·DYMS22에서 시연; CATL은 통신 제한 환경에서 이기종 무인체계 상호운용 협업을 위한 표준 프레임워크로 STANAG 4817의 골격이며 현재 해양(특히 수중)에 가장 관련 [스니펫만 확인; 전문 PDF는 용량 초과·ES 403]. — [STO 2023 Highlights](https://www.sto.nato.int/wp-content/uploads/2023-NATO-STO-Highlights-Web.pdf); [RMA CATL workshop](https://researchportal.rma.ac.be/en/activities/workshop-introduction-to-catl/)
- Project Aquaticus(MIT 2015 → West Point RRC 2019): 인간-로봇 팀 CTF 테스트베드, moos-ivp-pLearn(TensorFlow/Keras)로 DRL 지원; NPS가 인간 훈련·전술 학습 연구에 참여 [스니펫]. — [West Point](https://www.westpoint.edu/research/west-point-werx/robotics-research-center/project-aquaticus)

### Inferences
- 서구 공식 보고서는 ISR·C2·인간-군집 상호작용(CATL, Aquaticus)에 집중하고 "교전 WTA"는 공개 보고서에서 거의 다루지 않으므로, 연구자의 교전 WTA 연구는 공개 학술 영역에서 서구 대비 선점 여지가 있다. 단, STANAG 4817/CATL 호환 과업 메시지 구조를 참조하면 국제 표준 정합성 측면에서 설득력이 커진다.

### Gaps
- DTIC(AD1165019, AD1164238 등) PDF·인용 페이지는 403으로 미열람. SET-263 전문·요약(ES)도 미열람. 2024–2026 NPS 학위논문 중 USV 군집 RL 교전 주제는 확인 못 함(목록 접근 제한).

---

## KQ7. 후보 후속주제 T1~T7의 문헌 대비 차별성·중복성 판단

### Takeaway
문헌 공백이 가장 크고 자기표절 위험이 가장 낮은 조합은 **T1(통신거부·기만 하 완전분산 학습형 WTA) > T2(불확실성 강건 WTA) > T5(지휘관 의도→제약 변환 WTA) > T3(WTA+시간동기 포화공격)** 순이며, **T4(신경 조합최적화 하이브리드)는 (b)의 3계층 하이브리드와 구조적으로 가장 겹치고 경쟁도 치열**하다. T6·T7은 (b)가 이미 "향후연구"로 선언했고 선행(Adv-TransAC 메타적응 상대, Drones 2026 교차영역)이 존재해 차별화 장치가 필수다.

### Cited Findings
- T1 관련 선행: CBBA는 간헐 연결에서 급락(Wang 2026); 국지 통신 제약 하 MAPPO 일반화 부족(Tan 2026); ONR CAST가 "무통신 군집"을 과제로 공모; 무통신 추격회피·암묵 조정은 비해양 arXiv에 존재("Toward multi-target self-organizing pursuit in a partially observable Markov game" arXiv:2206.12330; "Less is More: Robust Zero-Communication 3D Pursuit-Evasion via Representational Parsimony" arXiv:2603.08273; "Learning to Construct Implicit Communication Channel" arXiv:2411.01553 — 스니펫만 확인). USV WTA에서 재밍·기만·그래프 분절을 명시 모델링한 연구는 미발견. — [JMSE 14:237](https://mdpi-res.com/d_attachment/jmse/jmse-14-00237/article_deploy/jmse-14-00237.pdf); [ONR](https://www.onr.navy.mil/organization/departments/code-33/division-333/cooperative-autonomous-swarm-technology); [arXiv 2603.08273](https://arxiv.org/pdf/2603.08273)
- T2 관련 선행: 검색("distributionally robust / CVaR / risk-averse WTA, kill probability uncertainty 2023–2025")에서 WTA 대상 DRO·CVaR 논문은 **발견되지 않음**(전력·물류 응용만 검색됨); USV 항법에는 "Perturbation-mitigated USV Navigation with Distributionally Robust RL" arXiv:2512.00030이 존재 [스니펫]. Wu 2024 계층 RL은 확률 앙상블로 불확실성을 정량화하나 WTA 특화 아님. — [arXiv 2406.07877](https://arxiv.org/abs/2406.07877)
- T3 관련 선행: Zheng 2026(Drones)의 할당+최소시간 최적제어 통합이 가장 근접; "Synchronous Saturation Attack: Coordinated Maneuvering Strategies for Multi-UAV Air Combat"(Springer chapter DOI 10.1007/978-981-95-7641-8_52, 속도·거리 기반 동기 타격 조정 지표) [스니펫]; CNA 2025 "PRC Concepts for UAV Swarms in Future Warfare"·CASI 2025 PLA 군집 개념이 포화공격 교리를 기술 [스니펫]. USV 특유 해상상태·속도 제약 + CIWS 살보 용량 모델과 결합한 WTA는 미발견. — [Drones 10:193](https://mdpi-res.com/d_attachment/drones/drones-10-00193/article_deploy/drones-10-00193.pdf); [CNA](https://www.cna.org/reports/2025/07/PRC-Concepts-for-UAV-Swarms-in-Future-Warfare.pdf)
- T4 관련 선행(경쟁 치열): Hu 2024(MADDPG+Seq2seq, GA 대비 규모 확장); Oh, Seung Heon; Byeon, Geon Woong; Cho, Young In; Kwon, Seungmin; Woo, Jong Hun. "Artificial Intelligence in Combat Decision-making: Weapon Target Assignment via Reinforcement Learning and Graph Neural Networks." TechRxiv 2024 (DOI 10.36227/techrxiv.171084935.57702557/v1) → *IEEE Trans. Cybernetics* 2025(DOI 10.1109/TCYB.2025.3610606 보충자료로 확인) — **한국 그룹의 GNN+RL WTA**; Park, Janghee; Kim, Jaeoh "A Fast and Scalable Transformer-Pointer Reinforcement Learning Framework for Weapon-Target Assignment"(SSRN 5704099, Joint-PointerPPO, 상용 솔버 대비 고속 추론) [스니펫, 403]; "A transformer-based reinforcement learning approach for scalable weapon target assignment"(ARFA, 2025.9) [스니펫]; 포인터 네트워크 Actor-Critic WTA(中国科学院沈阳自动化研究所 학술지 2025) [스니펫]. — [Crossref TechRxiv](https://api.crossref.org/works?query.bibliographic=Artificial+Intelligence+in+Combat+Decision-Making+Weapon+Target+Assignment+via+Reinforcement+Learning+and+Graph+Neural+Networks&rows=2); [SSRN](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5704099)
- T5 관련 선행: Din 2025(LLM 임무계획, 단일 USV); Kim 2025(LLM 평가자 기반 선호 미세조정, USV 군집); Hamid 2026(XAI MARL USV 헌팅); OPTIMUS 실증("운용자는 규칙·의도·권한만 정의"). LLM이 ROE/우선순위를 WTA 목적함수 가중·제약으로 변환하고 veto·신뢰·지연·안전을 평가한 연구는 미발견. — [arXiv 2503.12065](https://arxiv.org/abs/2503.12065); [arXiv 2503.03796](https://arxiv.org/abs/2503.03796); [Soldier Systems](https://soldiersystems.net/2025/11/19/scientific-systems-autonomy-software-achieves-a-major-milestone-in-test-with-group-of-unmanned-boats/)
- T6 관련 선행: Xiong 2025의 adversarial meta-learning + 메타 적응 상대 커리큘럼; *Applied Intelligence* 2025 self-play 다중 USV(ICM/SP/POCA) [스니펫]; Yuwen 2025 연합 게임 NE; Pyquaticus/AAMAS MCTF 경연. 착취가능성(exploitability) 지표를 USV 교전에 적용한 사례는 미발견. — [JMSE 13:1593](https://mdpi-res.com/d_attachment/jmse/jmse-13-01593/article_deploy/jmse-13-01593.pdf); [arXiv 2504.04475](https://arxiv.org/abs/2504.04475)
- T7 관련 선행: Zheng 2026(UAV+USV+UUV bi-level, GA+최적제어); Sun 2026(이기종 화력 요소 grabbing-order); OGR-MARL(이기종 USV). MARL 기반 교차영역 무장 역할(자폭/미사일/EW/기만) 할당은 미발견. — [Drones 10:193](https://mdpi-res.com/d_attachment/drones/drones-10-00193/article_deploy/drones-10-00193.pdf); [arXiv 2608.12995](https://arxiv.org/abs/2608.12995)

### Inferences
- **자기표절 회피 원칙**: (b)의 핵심 자산(MRCPSPTW 정식화, 5인자 위협지수, RL-VNS 4 이웃, 3층 GAT-MAPPO, DSR, 80v80 시나리오)을 "재사용"하면 중복 게재 논란이 생기므로, 후속연구는 (i) 문제 정의 변경(통신거부·기만 또는 확률적 살상·식별 불확실성), (ii) 모델 변경(CTDE 중앙 critic 의존 제거 또는 위험민감 목적함수), (iii) 실험 변경(통신 레짐 스윕·분절 지표·CBBA 동일 레짐 비교, 또는 CVaR/후회 지표)의 3요소를 모두 바꾸어야 한다. T1·T2는 이 3요소를 자연스럽게 모두 바꾼다.
- T4는 Hu 2024·Oh/Woo 2025(한국)·Park/Kim(SSRN)·ARFA와 정면 경쟁하며 (b)의 "휴리스틱→RL-VNS→GNN" 구조와 유사해 심사자가 중복으로 볼 위험이 가장 크다. anytime 품질 보증(이론)과 20→400 규모 일반화가 있어야 차별화되지만, 우선순위를 낮추는 것이 안전하다.
- T3는 Zheng 2026과 "할당+궤적 통합"이라는 틀이 같으므로, 확률적 방어(CIWS 살보·재장전) 모델과 학습 기반 동기화를 핵심으로 두어야 한다.
- T6·T7은 단독 주제보다 T1 또는 T2의 "확장 실험" 장(章)으로 배치하면 (b) 향후연구 선언과의 중복을 논문 1편 추가 없이 소화할 수 있다.

### Gaps
- Oh/Woo 2025(IEEE TCYB)와 Park/Kim(SSRN)의 본문(문제 규모·최적성 갭·추론시간)은 403으로 미확인 → T4 경쟁 강도 정량 판단에 [확인 필요].
- 2020년 이전 확률적(stochastic) WTA OR 문헌(앵커)은 이번 조사 범위 밖으로, T2의 OR 선행 검토가 추가로 필요하다.
- 한국 국내 문헌(KNST, KIMST, 한국군사과학기술학회지 등)은 본 노트 범위(국제 문헌) 밖이며 별도 조사자가 다룬다고 가정했다.
