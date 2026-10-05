# 군집 USV 무장할당(WTA) 연구용 로컬 PC 시뮬레이터: 오픈소스 시뮬레이션·ML 툴링 비교 및 용량 추정

- 대상 PC: Windows 11 Home 25H2, Intel Core i5-14400F (10코어/16스레드), 32 GB DDR4-3200, NVIDIA GeForce RTX 5060 8 GB (Blackwell, compute capability 12.0), 1.84 TB 저장장치, VS Code 개발.
- 조사 방법: 본 세션에서는 WebSearch 예산이 소진되어 모든 조사를 1차 출처(GitHub 저장소, 공식 문서, arXiv 초록 페이지, PyTorch/NVIDIA 공식 페이지, Semantic Scholar API) 직접 열람(WebFetch)으로 수행함. 열람에 실패한 출처(HTTP 403/404/429, DNS 실패)는 각 절 Gaps에 명시하고 추정값은 [확인 필요]로 표기함.
- 조사 기준일: 2026-10-05.

---

## KQ1. 벡터화 MARL 환경·라이브러리 (VMAS/BenchMARL/TorchRL, JaxMARL, PettingZoo, MAgent2, RLlib, CleanRL, skrl, MARLlib, EPyMARL)

### Takeaway
2-D 해상 교전(20~400 에이전트)을 단일 소비자 GPU에서 수천 개 병렬 환경으로 돌리려면, PyTorch 텐서 기반 벡터화(VMAS 방식) 또는 JAX 기반 벡터화(JaxMARL 방식)로 **자체 환경을 직접 구현**하는 것이 유일하게 현실적인 경로이며, 학습 스택은 BenchMARL(TorchRL+Hydra, MIT) 또는 JaxMARL(Apache-2.0)이 가장 적합하다. PettingZoo/MAgent2/EPyMARL/MARLlib는 비벡터화이거나 Windows 미지원·유지보수 정체 상태이고, "Moco"라는 VMAS 후속 프로젝트는 어떤 1차 출처에서도 확인되지 않았다.

### Cited Findings
- **VMAS** (Bettini, Kortvelesy, Blumenkamp, Prorok, "VMAS: A Vectorized Multi-Agent Simulator for Collective Robot Learning", arXiv:2207.03530, DARS 2022/Springer): "a vectorized 2D physics engine written in PyTorch and a set of twelve challenging multi-robot scenarios"; "VMAS is able to execute 30,000 parallel simulations in under 10s, proving more than 100x faster" than OpenAI MPE, MPE는 시뮬레이션 수에 선형으로 시간 증가 — [arXiv 2207.03530](https://arxiv.org/abs/2207.03530)
- VMAS 저장소: 라이선스 **GPL-3.0**, main 브랜치 614 커밋으로 활발, BenchMARL·TorchRL 생태계에 통합, 후속/대체 프로젝트 공지 없음, Windows 지원 명시 없음(CI는 Linux), 공식 steps/s 수치 미공개, 관련 시나리오 `navigation`, `passage`, `discovery`, `flocking`, `simple_tag`, `simple_spread`, `road_traffic` — [GitHub proroklab/VectorizedMultiAgentSimulator](https://github.com/proroklab/VectorizedMultiAgentSimulator)
- **BenchMARL** (Bettini et al., "BenchMARL: Benchmarking Multi-Agent Reinforcement Learning", JMLR 25(217):1–10, 2024): 알고리즘 9종(MAPPO, IPPO, MADDPG, IDDPG, MASAC, ISAC, QMIX, VDN, IQL), 환경 VMAS(27 task)/SMACv2/PettingZoo MPE/MeltingPot/MAgent2/SISL, 모델 레이어 "MLP, GRU, LSTM, GNN, CNN, Deepsets"(중앙/분산 구성 가능, 시퀀스 합성), 의존성 TorchRL+Hydra+marl-eval, 라이선스 MIT — [GitHub facebookresearch/BenchMARL](https://github.com/facebookresearch/BenchMARL)
- **TorchRL** (Bou et al., "TorchRL: A data-driven decision-making library for PyTorch", arXiv:2306.00577, ICLR 2024): 0.13 버전은 "Python 3.10+, PyTorch 2.1+, TensorDict 0.13.x" 요구, "MAPPO and IPPO losses", VMAS/PettingZoo/MeltingPot/SMACv2 래퍼, `ParallelEnv`, 0.13에서 "MultiAgentGAE" 추가, CUDA 휠은 "Linux" 전용 표기, Windows 지원 명시 없음, MIT — [GitHub pytorch/rl](https://github.com/pytorch/rl)
- **JaxMARL** (Rutherford, Ellis, Gallici, Cook, Lupu, Ingvarsson, Willi, Hammond, Khan, Schroeder de Witt, Souly, Bandyopadhyay, Samvelyan, Jiang, Lange, Whiteson, Lacerda, Hawes, Rocktäschel, Lu, Foerster, "JaxMARL: Multi-Agent RL Environments and Algorithms in JAX", arXiv:2311.10090v6, NeurIPS 2024 Datasets and Benchmarks Track): "around 14 times faster than existing approaches", "up to 12500x when multiple training runs are vectorized" — [arXiv 2311.10090](https://arxiv.org/abs/2311.10090); [GitHub FLAIROx/JaxMARL](https://github.com/FLAIROx/JaxMARL)
- JaxMARL 논문 Table 3 (NVIDIA RTX 2080 기준 steps/s): MPE Simple Spread 원본 8.3e4 → JAX 1 env 5.5e3, 100 env 5.2e5, 10k env **4.0e7**; SMAX(2s3z) 원본 8.3e1 → 10k env 2.7e6; Overcooked 10k env 1.7e7; Hanabi 10k env 5.0e6; MABrax 10k env 7.6e5. 학습 벽시계: SMAX IPPO 단일 run 약 10분, Overcooked IPPO 약 1분, MPE Q-learning 130초(PyMARL >1시간 대비) — [arXiv HTML 2311.10090v6](https://arxiv.org/html/2311.10090v6)
- JaxMARL 저장소: 환경 12종(MPE, SMAX, Overcooked/V2, Hanabi, MABrax, Coin Game, STORM, Switch Riddle, JaxNav, JaxRobotarium), 알고리즘 IPPO/MAPPO/IQL/VDN/QMIX/TransfQMIX/SHAQ/PQN-VDN, "JAX with GPU support (CUDA 13 recommended)", Apache-2.0, 986 커밋으로 활발, Windows/WSL 언급 없음 — [GitHub FLAIROx/JaxMARL](https://github.com/FLAIROx/JaxMARL)
- **PettingZoo** (Terry et al., NeurIPS 2021, 34:15032–15043): AEC/Parallel API, "Official support: Linux and macOS; Windows: community contributions accepted but not officially maintained", 내장 벡터화 없음(SuperSuit 별도), MIT — [GitHub Farama-Foundation/PettingZoo](https://github.com/Farama-Foundation/PettingZoo)
- **MAgent2**: 대규모 그리드월드 픽셀 에이전트 전투 환경, PettingZoo API, Farama 유지, "Linux and macOS with Python 3.8+", **Windows 공식 미지원**, MIT — [GitHub Farama-Foundation/MAgent2](https://github.com/Farama-Foundation/MAgent2)
- **EPyMARL** (Papoudakis et al., "Benchmarking Multi-Agent Deep Reinforcement Learning Algorithms in Cooperative Tasks", NeurIPS 2021 Datasets and Benchmarks, arXiv:2006.07869): IA2C/IPPO/MAA2C/MAPPO/IQL/PAC(개별 보상), COMA/VDN/QMIX/QTRAN(공통 보상), MADDPG; Gymnasium(2024-07 전환)/PettingZoo/VMAS/SMAC(v2, lite)/LBF/RWARE 지원 — [GitHub uoe-agents/epymarl](https://github.com/uoe-agents/epymarl)
- **MARLlib** (Hu et al., JMLR 2023): Ray/RLlib 기반, 알고리즘 18종·환경 17종, "Python 3.8-3.9", "gym version around 0.20.0", **Linux 전용**, 마지막 주요 업데이트 2023-03, 이후 2023-05~11 릴리스, MIT — [GitHub Replicable-MARL/MARLlib](https://github.com/Replicable-MARL/MARLlib)
- **skrl** (Serrano-Muñoz, Chrysostomou, Bøgh, Arana-Arexolaleiba, "skrl: Modular and Flexible Library for Reinforcement Learning", JMLR 24(254):1–9, 2023): PyTorch/JAX/NVIDIA Warp 백엔드, Gymnasium/PettingZoo/Isaac Lab/MuJoCo Playground/ManiSkill/Brax, 환경 부분집합(scope) 단위 동시 학습, MIT — [GitHub Toni-SM/skrl](https://github.com/Toni-SM/skrl)
- **CleanRL** (Huang et al., JMLR 2022): 단일 파일 구현, PPO 변형(envpool, JAX, multi-GPU, PettingZoo MA-Atari `ppo_pettingzoo_ma_atari.py`), envpool로 "3-4x side-effects free speed up", MIT — [GitHub vwxyzjn/cleanrl](https://github.com/vwxyzjn/cleanrl)
- **RLlib**: 신 API 스택, 독립/협력/적대(self-play, league) MARL, PettingZoo 래퍼, 알고리즘 PPO/APPO/SAC/DQN/IMPALA/BC/CQL/MARWIL/DreamerV3 — [Ray RLlib docs](https://docs.ray.io/en/latest/rllib/index.html); Ray 플랫폼 표: Windows x86_64 **"Beta"**, "Multi-node Ray clusters are untested", Windows 파일 I/O로 느림, copy-on-write fork 부재로 메모리 요구 증가, Python 3.10–3.13(3.13 beta) — [Ray installation](https://docs.ray.io/en/latest/ray-overview/installation.html)
- **Unity ML-Agents**: Release 23 (2025-08-28), Unity 패키지 4.0.0/Python 패키지 1.1.0, MA-POCA 알고리즘, 협력·경쟁 다중 에이전트 지원, Apache-2.0 — [GitHub Unity-Technologies/ml-agents](https://github.com/Unity-Technologies/ml-agents)

### Inferences
- 20~400 에이전트 2-D 해상 교전은 기존 벤치마크 환경(VMAS 시나리오, MPE, SMAX)에 그대로 대응되지 않으므로, **VMAS `BaseScenario` 상속(GPL-3.0 전염성 주의) 또는 순수 PyTorch/JAX 자체 벡터화 엔진** 중 선택해야 한다. 논문 코드 공개 시 GPL-3.0은 상용·국방 재사용에 제약이 되므로 자체 엔진(MIT/Apache) 구현이 장기적으로 유리하다.
- 이전 연구(b)의 GNN(GAT)-MAPPO·CTDE 구조는 BenchMARL의 "GNN" 레이어 + MAPPO 조합과 설정 파일 수준에서 재현 가능하므로, 후속 연구는 BenchMARL을 **베이스라인 재현 및 공정 비교 프레임**으로 쓰고 새 모델(T4 NCO, T2 risk-sensitive 등)은 TorchRL 손실 함수 커스텀으로 얹는 구성이 재현성 심사에 유리하다.
- JaxMARL 수치(10k env에서 MPE 4.0e7 SPS, RTX 2080)는 Blackwell RTX 5060에서도 같은 자릿수 이상이 기대되지만, JAX GPU는 Windows 네이티브 불가(KQ4)이므로 JAX 경로는 WSL2 전제다.
- "Moco"를 VMAS 후속 명칭으로 보는 가설은 **근거 없음**으로 판단한다(VMAS 저장소에 후속·폐기 공지 없음).

### Gaps
- VMAS·BenchMARL·TorchRL의 Windows 네이티브 동작 여부는 문서상 명시가 없어 [확인 필요]. CPU 텐서 기반 VMAS는 PyTorch만 있으면 동작할 가능성이 높지만 미검증.
- VMAS 공식 steps/s 벤치마크 표는 없음(논문의 "30,000 parallel simulations in under 10s"만 존재, 스텝 수 미명시).
- EPyMARL·MARLlib의 최신 릴리스 번호·날짜는 저장소 페이지에서 확인 불가.

---

## KQ2. 해군/USV 특화 오픈 시뮬레이터와 국방용 폐쇄 도구

### Takeaway
개인 연구자가 즉시 쓸 수 있는 해상 MARL 환경은 **Pyquaticus**(MIT LL, BSD-3, PettingZoo API, 순수 Python, MOOS-IvP 동역학)가 유일하게 "경량·학습용"이고, VRX/HoloOcean/USVSim은 고충실도 로보틱스 시뮬레이터(ROS 2/Gazebo, Unreal)로 수천 병렬 RL 학습용으로는 부적합하다. 국방용 폐쇄 도구 중 **Command: Modern Operations Professional Edition**은 학술 티어(Student/Academic)가 존재하나 가격 비공개이며, AFSIM·NGTS·국내 국방 M&S 도구는 본 세션에서 접근 조건을 1차 출처로 확인하지 못했다.

### Cited Findings
- **Pyquaticus**: "a lightweight multi-agent reinforcement learning environment for maritime capture-the-flag scenarios using uncrewed surface vehicles", "standard PettingZoo interface", 에이전트 수 파라미터화, 동역학은 MOOS-IvP `uSimMarine`(MIT LAMSS) 기반으로 실기체 이식성 강조, "pure-Python implementation without many dependencies"로 실시간 이상 속도·클러스터 병렬 가능, 분산·에이전트 상대 관측 공간 설정 가능, RLlib 예제 포함, Python 3.10, BSD-3-Clause, Docker는 "out-of-date, do not use", 논문 인용 정보 없음 — [GitHub mit-ll-trusted-autonomy/pyquaticus](https://github.com/mit-ll-trusted-autonomy/pyquaticus); [README raw](https://raw.githubusercontent.com/mit-ll-trusted-autonomy/pyquaticus/main/README.md)
- **VRX (Virtual RobotX)**: 해상 USV(WAM-V) 시뮬레이션, 권장 **Gazebo Harmonic + ROS 2 Jazzy**(레거시 Garden/Humble 브랜치), Release 2.3, Apache-2.0, 인용 Bingham et al., "Toward Maritime Robotic Simulation in Gazebo", MTS/IEEE OCEANS 2019 Seattle — [GitHub osrf/vrx](https://github.com/osrf/vrx)
- **HoloOcean**: "a high-fidelity simulator" (Unreal Engine, BYU Field Robotics Systems Lab), "Linux and Windows support", 센서 DVL/IMU/광학 카메라/각종 소나/깊이/레이캐스트 LiDAR, "Multi-agent missions, including optical and acoustic communications", 최신 v2.3.0(UE4.27은 archival 브랜치), 인용 Potokar et al., "HoloOcean: An Underwater Robotics Simulator", IEEE ICRA 2022 — [HoloOcean docs v2.3.0](https://byu-holoocean.github.io/holoocean-docs/v2.3.0/index.html); [version list](https://byu-holoocean.github.io/holoocean-docs/versionList.html)
- **USVSim (usv_sim_lsa)**: 재난 시나리오용 USV 테스트베드, 선체 4종(airboat, differential, rudder, sailboat), HEC-RAS 수류·OpenFOAM 풍·UWSim 파랑/부력, v0.3, Apache-2.0, 인용 Paravisi et al., "Unmanned Surface Vehicle Simulator with Realistic Environmental Disturbances", Sensors 2019 — [GitHub disaster-robotics-proalertas/usv_sim_lsa](https://github.com/disaster-robotics-proalertas/usv_sim_lsa)
- **Stone Soup** (Dstl): "a framework for the development and testing of tracking and state estimation algorithms", Python 3.10+, MIT, Zenodo DOI 10.5281/zenodo.4663993, CITATION.cff 제공 — [GitHub dstl/Stone-Soup](https://github.com/dstl/Stone-Soup)
- **Unity ML-Agents**: Release 23 (2025-08-28), MA-POCA, Apache-2.0 (KQ1 참조) — [GitHub Unity-Technologies/ml-agents](https://github.com/Unity-Technologies/ml-agents)
- **Command: Modern Operations Professional Edition (Command PE)**: "air, naval, near-space, strategic and ground (limited) operations" 모델링, 대상 "commercial, government and military organizations", 라이선스 5단계 — Mil/Gov, **Student**("military academies and other teaching/training environments"), **Academic**(데이터 수정 없는 분석용), Standard(DB 편집+Monte Carlo), Premium(커맨드라인 실행 포함); 기능 "Monte-Carlo (headless) analysis", "Lua Event-hooks", "TCP/IP socket access to Lua API", 이벤트/데이터 파일·DB 내보내기, "Configurable mechanics overrides", DIS 연동; 라이선스 "per-seat, site-wide and enterprise-wide"; 고객 "25+ nations, 150+ orgs, 3000+ users"; 가격 비공개 — [Command PE page](http://command.matrixgames.com/?page_id=3822)

### Inferences
- Pyquaticus는 CTF 규칙(깃발·태그) 중심이라 WTA 연구에 그대로 쓸 수 없지만, (i) `uSimMarine` 기반 USV 운동학 모델, (ii) PettingZoo 인터페이스 설계, (iii) 에이전트 상대 관측 공간 설계를 **참조 구현**으로 차용하고, 이를 PyTorch/JAX 벡터화 엔진으로 재작성하는 것이 적절하다. 벤치마크 비교군으로 Pyquaticus CTF를 "표준 해상 MARL 환경"으로 병행 보고하면 국제 심사에서 외적 타당성 근거가 된다.
- VRX/HoloOcean은 Sim-to-real·HILS 단계(연구자가 이미 (b)에서 향후 과제로 명시)에서 **검증용 고충실도 환경**으로 유보하고, 학습 루프에는 넣지 않는 것이 PC 사양상 합리적이다(ROS 2 Jazzy는 Ubuntu 24.04 전제이므로 WSL2 또는 듀얼부트 필요, Windows 네이티브 Gazebo Harmonic은 미지원 가능성 [확인 필요]).
- Command PE의 Student/Academic 티어는 "데이터 수정 불가·분석용"이므로, 자체 WTA 알고리즘을 주입하는 실험 플랫폼으로는 Standard/Premium(Lua API) 이상이 필요하며 개인 구매 가능성은 낮다. 대신 **공개 DB의 플랫폼 제원(속도·무장·CIWS 교전률)을 시나리오 파라미터 근거로 인용**하는 용도가 현실적이다.

### Gaps
- Pyquaticus를 소개한 학술 논문(저자·venue)은 저장소에 인용 정보가 없고 Semantic Scholar API가 429로 차단되어 미확인 [확인 필요].
- AFSIM(AFRL)의 배포 제한(미 정부·계약자·동맹 한정 여부, 수출통제)은 Wikipedia 두 가지 URL 모두 404, Semantic Scholar 429로 1차 확인 실패 [확인 필요]. 개인 외국 연구자 접근은 사실상 불가한 것으로 알려져 있으나 본 세션에서 출처로 뒷받침하지 못함.
- NGTS(Next-Generation Threat System, NAVAIR) 및 국내 국방 M&S 도구(예: 해군 전투발전용 M&S, AddSIM 등)의 접근 조건은 조사하지 못함.
- VRX의 다중 USV 지원, 파랑·풍 모델 세부, HoloOcean의 수상함(surface vessel) 에이전트 유형·라이선스는 열람한 페이지에 없음.

---

## KQ3. Python API 최적화 솔버 (CP-SAT, HiGHS, SCIP, CBC, Gurobi, pymoo, DEAP)와 80×80 WTA 베이스라인

### Takeaway
2026년 기준 **OR-Tools v9.15(2026-01-12)** 하나로 CP-SAT + HiGHS 1.12 + SCIP 10.0을 Windows x64 휠로 받을 수 있고, Gurobi는 학술 Named-User 라이선스(1년, 갱신 가능, 모델 크기 제한 없음, 대학 네트워크 인증)로 무료 사용 가능하다. 80×80 WTA 인스턴스의 정확해 솔브 시간은 본 세션에서 수치 출처를 확보하지 못했으며(Andersen et al. 2022 초록 비공개), 비선형 생존확률 목적식의 선형화 방식에 따라 수 초~수 분으로 크게 달라지므로 자체 벤치마크가 필요하다.

### Cited Findings
- **OR-Tools v9.15** (2026-01-12): Python 최소 3.9, "Python 3.14 support", Windows x64 포함 플랫폼별 빌드, CP-SAT `no_overlap_2d` presolve/propagation/cuts 개선, 실험적 set variables, enforcement literal 확장, "improved shared tree workers and clause sharing", 번들 **HiGHS v1.12.0, SCIP v10.0.0**, XpressMP(MathOpt) 지원 — [GitHub google/or-tools releases](https://github.com/google/or-tools/releases)
- **CP-SAT**: "generally faster than MPSolver", "designed for integer programming problems", "The CP-SAT solver works over the integers...you must define your optimization problem using integers only", 상태값 OPTIMAL/FEASIBLE/INFEASIBLE/MODEL_INVALID/UNKNOWN — [OR-Tools CP-SAT docs](https://developers.google.com/optimization/cp/cp_solver)
- CP-SAT Primer(파라미터 장): "By default, CP-SAT leverages all available cores (including hyperthreading)"; 2 workers부터 "incomplete subsolvers, i.e., heuristics such as LNS" 사용, 32 workers에서 "all 15 full problem subsolvers are used"; "For many models, you can boost performance by manually reducing the number of workers to match the number of physical cores, or even fewer"(메모리 대역폭·간섭 감소); 시간 제한 "I typically start with a time limit between 60 and 300 seconds"; `relative_gap_limit`(예: 0.05) / `absolute_gap_limit`; `log_search_progress` 개발 초기 필수 — [CP-SAT Primer parameters](https://d-krupke.github.io/cpsat-primer/parameters.html)
- **HiGHS**: LP/QP/MIP 솔버, 코어 MIT(일부 배포는 Apache-2.0), `pip install highspy`, Windows/macOS/Linux(x64/x86/ARM64) 바이너리, 인용 Huangfu & Hall, "Parallelizing the dual revised simplex method", Mathematical Programming Computation 10(1):119–142, 2018 — [GitHub ERGO-Code/HiGHS](https://github.com/ERGO-Code/HiGHS)
- `scipy.optimize.milp`는 "a wrapper of the HiGHS linear optimization software"; 옵션 `time_limit`, `mip_rel_gap`(기본 1e-4), `node_limit`, `presolve`, `disp` — [SciPy milp](https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.milp.html)
- **SCIP**: "one of the fastest academically developed solvers for mixed integer programming (MIP) and mixed integer nonlinear programming (MINLP)", 라이선스 **Apache-2.0**(저장소 표기), 49,588 커밋 — [GitHub scipopt/scip](https://github.com/scipopt/scip) (공식 사이트 scipopt.org는 429로 미열람)
- **Cbc**: 오픈소스 MILP(C++), 최신 안정 2.10.10(3.0 준비 중), **EPL-2.0**, Python 접근 python-mip/PuLP/OR-Tools/cvxpy/CyLP, GitHub 릴리스에 바이너리 첨부 — [GitHub coin-or/Cbc](https://github.com/coin-or/Cbc)
- **Gurobi 학술 라이선스**: 대상 "students, faculty, and staff at accredited degree-granting institutions", 용도 "non-commercial use, including teaching, coursework, and academic research"; Named-User는 "valid for up to one year", "a single person, on a single machine", 인증은 "connect from your institution's academic network", 자격 유지 시 User Portal에서 재발급; "no limits on the model size", "Full-featured access"; Academic WLS(여러 기기·클라우드), Academic Site(대학 관리자 전용) — [Gurobi academic program](https://www.gurobi.com/academia/academic-program-and-licenses/); [Academic Named-User License](https://www.gurobi.com/features/academic-named-user-license/)
- **pymoo** 0.6.2 (2026-06-27): NSGA-II, NSGA-III, MOEA/D, R-NSGA, SPEA2, RVEA, SMS-EMOA, AGE-MOEA, C-TAEA, D-NSGA-II; 이진·이산·순열·혼합 변수, 제약 처리, 병렬화 "Vectorized operations, Joblib, GPU acceleration"; 지표 Hypervolume/GD/IGD; 인용 Blank & Deb, "pymoo: Multi-Objective Optimization in Python", IEEE Access 8:89497–89509, 2020 — [pymoo.org](https://pymoo.org/)
- **DEAP**: GA/GP/ES/CMA-ES, NSGA-II/NSGA-III/SPEA2/MO-CMA-ES, 공진화(co-evolution) 지원, LGPL-3.0, 인용 Fortin et al., "DEAP: Evolutionary Algorithms Made Easy", JMLR 13:2171–2175, 2012 — [GitHub DEAP/deap](https://github.com/DEAP/deap)
- **WTA 문헌 anchor**: Kline, Ahner, Hill, "The Weapon-Target Assignment Problem", Computers & Operations Research 105:226–236, 2019, DOI 10.1016/j.cor.2018.10.015 — Manne(1958) 기원, static/dynamic WTA 분류, 정확해·휴리스틱 기법 정리, 정식화 표준화 — [Semantic Scholar record](https://api.semanticscholar.org/graph/v1/paper/DOI:10.1016/j.cor.2018.10.015?fields=title,authors,year,venue,journal,abstract,externalIds)
- Andersen, Pavlikov, Toffolo, "Weapon-target assignment problem: exact and approximate solution algorithms", Annals of Operations Research 312:581–606, 2022, DOI 10.1007/s10479-022-04525-6 — 초록은 출판사 비공개로 인스턴스 규모·솔브 시간 미확인 — [Semantic Scholar record](https://api.semanticscholar.org/graph/v1/paper/DOI:10.1007/s10479-022-04525-6?fields=title,authors,year,venue,journal,abstract,externalIds)

### Inferences
- 80×80 WTA(6,400 이진/정수 변수)에서 전통적 목적식 Σ V_j Π(1−p_ij)^x_ij 는 비선형이므로, (a) 로그 변환 후 정수 발사 수 변수로 선형화(HiGHS/SCIP/Gurobi MILP), 또는 (b) CP-SAT용 정수 스케일링(확률×10^4)과 테이블/piecewise 제약으로 모델링해야 한다. 연구자의 이전 연구(b)가 "MILP 91.2(분 단위)"를 보고한 점과 일관되게, 정확해 베이스라인은 **분 단위**, CP-SAT는 `max_time_in_seconds=5~60`으로 anytime 하한·상한을 함께 기록하는 것이 T4(anytime 품질 보증)와 직접 연결된다.
- i5-14400F는 물리 10코어(6P+4E)이므로 CP-SAT Primer 권고에 따라 `num_workers=8~10`으로 고정하고, 1,000 인스턴스 × 60 s 제한 시 단일 프로세스 순차 실행은 약 17시간(계산: 1,000×60 s), 2개 프로세스(각 5 workers) 병렬 시 약 8.5시간으로 추정된다(추정치).
- Gurobi는 "학술 네트워크 접속 인증"이 필수이므로 한남대 캠퍼스망(또는 대학 VPN [확인 필요])에서 발급해야 하며, 국방 과제와의 연계 시 "non-commercial academic research" 범위 해석이 쟁점이 될 수 있어 EULA 재확인이 필요하다. 논문용 재현성 관점에서는 **HiGHS(MIT)·SCIP(Apache-2.0)·CP-SAT(Apache-2.0)** 등 오픈 솔버를 주 베이스라인으로, Gurobi를 보조 검증으로 두는 것이 공개 코드 배포에 유리하다.
- 다목적(DSR vs 생존률 vs 탄 소모) 파레토 분석은 pymoo 0.6.2(NSGA-II/III, 혼합 변수, Joblib 병렬)로 충분하고 DEAP는 공진화(T6 red-team co-evolution) 실험에 한정해 쓰는 것이 적합하다.

### Gaps
- 80×80 WTA의 CP-SAT/HiGHS/SCIP/Gurobi 실제 솔브 시간 비교 수치는 1차 출처를 확보하지 못함(Elsevier/Springer 403, Semantic Scholar 초록 비공개). 자체 벤치마크 필수 [확인 필요].
- `pip install gurobipy` 기본 제한 라이선스의 크기 한도(변수/제약 2,000개로 알려짐)는 PyPI 페이지 렌더 실패로 미확인 [확인 필요]; 80×80 인스턴스는 이 한도를 초과하므로 학술 라이선스 발급이 선행되어야 함.
- SCIP 10.0의 정확한 릴리스일, PySCIPOpt 버전, Windows 바이너리 제공 여부는 scipopt.org 429로 미확인.

---

## KQ4. RTX 5060 (Blackwell, CC 12.0)용 딥러닝 스택: PyTorch/CUDA/cuDNN/Triton, PyG/DGL, JAX, WSL2 vs 네이티브

### Takeaway
RTX 5060은 compute capability **12.0(sm_120)**이며, PyTorch는 **2.7 + CUDA 12.8 휠**부터 Blackwell을 지원(2.7에서는 prototype, 2.8부터 cu128 stable)하므로 cu126/cu118 휠을 설치하면 커널 이미지 부재 오류가 난다. 2026-10 기준 최신 안정판은 PyTorch 2.14.1(Python ≥3.10)로 cu126/cu130 휠이 기본이며, 2.15는 CUDA 13.2 기반으로 예정되어 있다. PyG는 순수 PyTorch만으로 동작(옵션 휠은 cu128/cu130 제공)하지만 **DGL은 2024-09 v2.4.0(PyTorch 2.1~2.4, CUDA ≤12.4)에서 멈춰 Blackwell 미지원**이다. JAX GPU는 Windows 네이티브 불가·WSL2 "experimental"이므로 JAX 경로는 WSL2 필수다.

### Cited Findings
- NVIDIA CUDA GPUs 목록: GeForce RTX 5090/5080/5070 Ti/5070/5060 Ti/**5060**/5050 모두 compute capability **12.0** — [NVIDIA CUDA GPUs](https://developer.nvidia.com/cuda-gpus)
- PyTorch 2.7 (2025-04): "[Prototype] NVIDIA Blackwell Architecture Support ... ships pre-built wheels for CUDA 12.8", "cuDNN, NCCL, and CUTLASS have been upgraded", "Triton 3.3, which adds support for the Blackwell architecture with torch.compile compatibility", 설치 `pip install torch==2.7.0 --index-url https://download.pytorch.org/whl/cu128`, 추적 이슈 #145949 — [PyTorch 2.7 blog](https://pytorch.org/blog/pytorch-2-7/)
- Blackwell 추적 이슈 #145949 (2025-01-29 개설): SM 10.0·SM 12.0 대상, Triton 업그레이드, cuDNN 9.7.0+, NCCL 2.25.1, CUTLASS 3.8.0, CUDA 12.8 통합 등 22항목 추적 — [GitHub pytorch/pytorch#145949](https://github.com/pytorch/pytorch/issues/145949)
- PyTorch RELEASE.md 호환 매트릭스: **2.7** Python 3.9–3.13, stable CUDA 11.8/12.6, experimental 12.8, cuDNN 9.1.0.70/9.5.1.17/9.7.1.26; **2.8** stable 12.6/**12.8**, exp 12.9, cuDNN 9.10.2.21; **2.9** Python 3.10–3.14, stable 12.6/12.8, exp 13.0; **2.10** stable 12.6/12.8, exp 13.0, cuDNN 9.10.2.21/9.15.1.9; **2.15** Python 3.11–3.15, stable CUDA 13.2, exp 13.4, cuDNN 9.26.0.51; 릴리스 주기 약 3개월 — [RELEASE.md](https://github.com/pytorch/pytorch/blob/main/RELEASE.md)
- PyPI torch JSON: `info.version` = **2.14.1**, `requires_python` ">=3.10" — [PyPI torch JSON](https://pypi.org/pypi/torch/json)
- GitHub Releases 요약(열람 도구가 날짜를 잘못 추출했을 가능성이 높아 날짜는 [확인 필요]): 2.11.0 휠 cu126/cu128, "CUDA 13.0 default on PyPI"; 2.12.x~2.14.x 휠 cu126/cu130; "Blackwell (sm_120): Mentioned in 2.14.0+ for FlexAttention and performance improvements"; Windows CUDA 12.9.1 빌드 스택오버플로 이슈 언급 — [GitHub pytorch/pytorch releases](https://github.com/pytorch/pytorch/releases)
- CUDA Toolkit 릴리스 노트: CUDA 12.8의 최소 Windows 드라이버 ">=570.65"; "The NVIDIA driver is no longer bundled with the CUDA Toolkit – on Windows starting with CUDA 13.1"; CUDA 13.4(R615 브랜치) 최소 드라이버 ">=580"; 최신 문서 버전 CUDA 13.4 Update 1 — [CUDA Toolkit Release Notes](https://docs.nvidia.com/cuda/cuda-toolkit-release-notes/index.html) (※ 열람 결과 중 "Blackwell 지원이 13.2에서 시작"이라는 요약은 cuBLAS NVFP4 항목을 오독한 것으로 판단, PyTorch 2.7 블로그의 CUDA 12.8 기술과 상충하므로 채택하지 않음)
- **Triton on Windows**(woct0rdho/triton-windows): "RTX 50xx (Blackwell, sm120): This is officially supported by Triton. It only works with Triton >= 3.3, PyTorch >= 2.7, and CUDA >= 12.8"; 버전 매핑 PyTorch 2.7→Triton 3.3, 2.8–2.10→3.4–3.6; "triton.jit and torch.compile just work"; Windows 경로 길이 260자 제한으로 `torch.compile` 실패 가능(long path 활성화 필요); TinyCC 번들(v3.2.0.post13+), CUDA 12+ 번들, VC++ 재배포 패키지 필요; Proton 프로파일러 미완 — [GitHub woct0rdho/triton-windows](https://github.com/woct0rdho/triton-windows)
- **PyTorch Geometric**: "PyG 2.3 onwards ... without any external library required except for PyTorch"; 옵션 패키지(pyg_lib, torch_scatter, torch_sparse) 휠은 PyTorch 1.13~2.12 제공, 예: PyTorch 2.10.* → `cpu|cu126|cu128|cu130`, PyTorch 2.12.* → `cpu|cu126|cu130|cu132`; cu129 휠 없음 — [PyG installation](https://pytorch-geometric.readthedocs.io/en/latest/install/installation.html)
- **DGL**: 최신 v2.4.0 (2024-09-03), 지원 PyTorch 2.1–2.4, CUDA 11.7/11.8/12.1/12.4, 직전 v2.3.0 (2024-06-28) — [GitHub dmlc/dgl releases](https://github.com/dmlc/dgl/releases)
- **JAX**: Windows x86_64 — CPU "yes", NVIDIA GPU "no"; "These pip installations do not work with Windows, and may fail silently"; WSL2 NVIDIA GPU "experimental"; `jax[cuda12]` 요구 "CUDA >=12.1", "CUDNN >=9.10.2, <10.0", 드라이버 ≥525(Linux) — [JAX installation](https://docs.jax.dev/en/latest/installation.html)
- **CUDA on WSL2**: Windows 11 지원, Pascal 이상 GPU, WSL2 커널 5.10.16.3+ 권장; "This is the only driver you need to install. Do not install any Linux display driver in WSL"(Windows 드라이버가 `libcuda.so` 제공); 제한: Unified/Managed Memory 미지원, pinned 메모리 제한("may impact large deep learning workloads"), OpenGL-CUDA interop 미지원, `nvidia-smi` 질의 제한; 툴킷은 WSL-Ubuntu 패키지 또는 `cuda-toolkit-12-x` 메타패키지만 설치(`cuda`, `cuda-drivers` 금지) — [NVIDIA CUDA on WSL User Guide](https://docs.nvidia.com/cuda/wsl-user-guide/index.html)

### Inferences
- **권장 스택(2026-10)**: (A) 안정 우선 — PyTorch 2.9.x 또는 2.10.x + **cu128**(stable), Python 3.11/3.12, cuDNN 9.10+, Triton 3.5/3.6(Windows는 triton-windows), PyG 최신(순수 PyTorch 모드, 필요 시 cu128 옵션 휠); (B) 최신 — PyTorch 2.14.1 + cu130, 드라이버 ≥580. 두 경우 모두 sm_120 포함. **피해야 할 조합**: cu126/cu118 휠(sm_120 미포함 → "no kernel image is available" 유형 오류), DGL 전부(PyTorch ≤2.4 고정), cu129 PyG 옵션 휠(존재하지 않음).
- GAT 구현은 PyG `GATConv`/`GATv2Conv`(순수 PyTorch 경로)로 충분하며, 400 노드 × k-NN 희소 그래프에서 `torch_scatter` 없는 기본 경로의 성능 저하는 제한적일 것으로 추정(미측정).
- **WSL2 vs 네이티브 결정**: PyTorch 전용이면 Windows 네이티브로 충분(cu128/cu130 Windows 휠 존재, triton-windows로 `torch.compile` 가능). JAX(JaxMARL), Ray 멀티노드, ROS 2/Gazebo(VRX), MAgent2/PettingZoo 공식 지원이 필요하면 **WSL2 Ubuntu 24.04 + VS Code Remote-WSL**이 사실상 필수. WSL2의 pinned-memory 제한은 1,000~4,000 병렬 환경의 대형 롤아웃 버퍼를 CPU↔GPU로 전송할 때 병목이 될 수 있어, 롤아웃 버퍼를 **GPU 상주**(VRAM 8 GB 내)로 설계하거나 네이티브 Windows에서 측정 비교가 필요하다.
- 혼합정밀도: Blackwell은 bf16/fp16 텐서코어를 지원하므로 GAT 어텐션·MLP를 `torch.autocast(bfloat16)`으로 돌려 VRAM과 시간을 절감할 수 있으나, PPO의 어드밴티지·로그확률 계산은 fp32 유지가 안전하다(일반 관행; 출처 미확보).

### Gaps
- PyTorch 2.8~2.14 각 버전의 정확한 릴리스일은 PyPI 페이지 렌더 실패·GitHub 요약 오류로 미확정 [확인 필요]. 버전-휠 조합(2.11 cu128, 2.12+ cu130)은 GitHub 요약과 PyG 매트릭스가 일치하므로 신뢰도 중간.
- RTX 5060의 CUDA 코어 수·메모리 대역폭·FP32 TFLOPS는 본 세션에서 1차 출처 미열람 [확인 필요].
- Windows 네이티브 PyTorch cu130 휠의 Blackwell 안정성(cuDNN 9.x 이슈 등) 관련 포럼 보고는 조사 못함.

---

## KQ5. 이 PC에서의 현실적 처리량·학습 시간 추정 (MAPPO 10M–50M steps, 100,000-run Monte Carlo, CP-SAT, 클라우드 필요성)

### Takeaway
공개 벤치마크(JaxMARL RTX 2080: MPE 10k env 4.0e7 SPS; VMAS 30,000 병렬 시뮬레이션 <10 s)를 근거로 외삽하면, 80v80 2-D 교전 벡터화 환경에서 MAPPO 10M~50M env-steps는 **수 시간 이내**, 100,000-run Monte Carlo는 **수 분~1시간**, CP-SAT 1,000 인스턴스 베이스라인은 **반나절**이 현실적이며, 8 GB VRAM 한계는 "400 에이전트 × 완전연결 어텐션 × 1,000 env" 조합에서만 문제가 된다. 따라서 Colab/클라우드는 필수가 아니라 다중 시드 스윕 가속·완전연결 400 에이전트 대규모 실험용 선택지다. (본 절 수치는 모두 추정치임.)

### Cited Findings
- JaxMARL(RTX 2080): MPE Simple Spread 10k env **4.0e7 SPS**, SMAX 10k env 2.7e6 SPS; SMAX IPPO 단일 run 약 10분, MPE Q-learning 130초 — [arXiv HTML 2311.10090v6](https://arxiv.org/html/2311.10090v6)
- VMAS: "30,000 parallel simulations in under 10s", MPE 대비 ">100x" — [arXiv 2207.03530](https://arxiv.org/abs/2207.03530)
- CP-SAT: 기본 전체 코어 사용, 물리 코어 수로 줄이면 성능 향상 가능, 시간 제한 60~300 s 권고 — [CP-SAT Primer parameters](https://d-krupke.github.io/cpsat-primer/parameters.html)
- WSL2 제한: pinned 메모리 제한, Unified Memory 미지원 — [CUDA on WSL User Guide](https://docs.nvidia.com/cuda/wsl-user-guide/index.html)
- Ray on Windows: Beta, copy-on-write 부재로 메모리 요구 증가 — [Ray installation](https://docs.ray.io/en/latest/ray-overview/installation.html)
- Gurobi 학술 라이선스는 "no limits on the model size" — [Gurobi Academic Named-User](https://www.gurobi.com/features/academic-named-user-license/)
- W&B(CoreWeave Forge) 학술 플랜: "Free Pro license for students, professors and postdoctoral researchers", 추적 시간 무제한, 저장 200 GB, 학술 이메일 필요 — [CoreWeave Forge pricing](https://coreweave.com/forge-pricing)

### Inferences (추정 계산, 모두 자체 벤치마크로 검증 필요)
- **VRAM 예산(3-layer GAT, 4-head, 128-dim, 400 에이전트)**: 파라미터는 수십만 개 수준으로 무시 가능. 활성값: 노드 특징 400×128×4 B ≈ 205 KB/layer/env. 어텐션 계수: 완전연결 그래프(160,000 edge)×4 head×4 B ≈ 2.56 MB/layer/env → 1,000 env × 3 layer ≈ **7.7 GB**(autograd 저장 포함 시 초과) → 8 GB에서 불가. 반면 **k-NN/통신반경 희소 그래프(k=10~20, 4,000~8,000 edge)**는 64~128 KB/layer/env → 1,000 env × 3 layer ≈ 0.6~1.0 GB로 여유. 결론: T1(통신 거부·단절 모델)의 **희소 통신 그래프 설계가 곧 메모리 설계**이며, 완전연결 어텐션은 128~256 env 미니배치로 쪼개야 한다.
- **롤아웃 버퍼**: 에이전트 관측 64 float 가정 시 400 에이전트 → 102 KB/env-step; 1,000 env × 100 step ≈ 10 GB → VRAM 초과, 32 GB RAM에 저장 또는 bf16 관측(5 GB)/32-step 호라이즌(3.3 GB)으로 축소. 80v80(160 에이전트)에서는 4,000 env × 64 step ≈ 2.6 GB(fp32)로 GPU 상주 가능.
- **env-step 처리량**: 80v80 벡터화 환경(쌍별 거리 160×160, 센서·무장 마스크, 운동학 적분)은 커널 수십~수백 개/스텝으로 커널 런치 지배 → 1,000~4,000 env에서 배치 스텝 300~1,000/s 추정 → **3e5~4e6 env-steps/s**. GAT 정책 추론(1,000 env × 160 node 희소)은 1~5 ms 추가. PPO 업데이트(여러 epoch)가 롤아웃과 비슷하거나 2~3배 소요 → 종합 1e5~1e6 env-steps/s.
- **MAPPO 10M~50M env-steps**: 상기 가정 시 10M ≈ 10초~2분(순수 처리량) + 업데이트 오버헤드 → 현실적으로 **10M: 수십 분, 50M: 1~5시간**(80v80). 400 에이전트(200v200)는 3~5배 → 50M steps 5~20시간. 5 시드 × 7 조건 스윕은 수 일 단위이며, 여기서 클라우드 병렬화 가치가 생긴다.
- **100,000-run Monte Carlo**(교전 300 step 가정): 벡터화 GPU 환경 1,000 env 배치 → 100 배치 × 300 스텝 = 30,000 배치 스텝 → 1~3분. CPU-only Python 환경(1,000 steps/s/process × 10 프로세스)이라도 3e7 steps ≈ 50분. 부트스트랩 100,000 리샘플(scipy.stats.bootstrap BCa)은 초 단위.
- **CP-SAT 1,000 인스턴스 × 60 s**: 순차 17시간, 2프로세스 병렬 8.5시간; 5 s 제한(실시간 조건 대응) 시 1.4시간. 정확해(최적성 증명) 비교군은 10% 샘플(100 인스턴스)만 장시간(600 s) 돌리는 2단계 설계가 현실적.
- **클라우드 필요성**: 핵심 실험(80v80, 희소 GAT)은 로컬 충족. 필요 조건은 (i) 400 에이전트 완전연결 어텐션, (ii) 20+ 시드 대규모 스윕, (iii) JAX 경로의 Windows 비호환 시 Linux VM. Colab 무료 티어는 세션 제한으로 재현성 실험에 부적합하며, 학술 W&B(200 GB)로 로컬 결과를 집계하는 것이 비용 효율적이다.
- 저장장치 1.84 TB: 1,000 물리 시뮬레이션 궤적(400 에이전트 × 300 step × 32 float × 4 B ≈ 15 MB/run)을 전부 저장해도 15 GB → 충분. 100,000-run은 요약 통계만 저장(궤적 전부 저장 시 1.5 TB로 한계 근접).

### Gaps
- 모든 처리량 수치는 외삽·추정이며 RTX 5060 실측 자료가 없음 [확인 필요]. 연구 초기 1주차에 "env-step 마이크로벤치마크"를 수행해 논문 부록에 실측치를 넣는 것이 재현성 기준 충족에 필수.
- WSL2와 네이티브 Windows 간 PyTorch 처리량 비교 벤치마크 출처 없음.

---

## KQ6. 실험 관리·재현성·통계·M&S V&V 표준

### Takeaway
Hydra(1.3 안정/1.4 pre, MIT, hydra-ecosystem으로 이관) + MLflow(Apache-2.0, 로컬 추적) 또는 W&B(학술 무료 Pro) + Optuna(v5, NSGA-II/MOTPE 다목적) + SciPy(`qmc.LatinHypercube` strength=2 직교 LHS, `stats.bootstrap` BCa 기본) + statsmodels(`TTestIndPower`)가 2026년 표준 조합이다. V&V 표준은 **NASA-STD-7009B(2024-03-05, 공개)**가 유일하게 본 세션에서 1차 열람되었고, DoDI 5000.61·MIL-STD-3022·DoD VV&A RPG·NATO AMSP-01·국방 M&S VV&A 지침은 호스트 접근 실패로 서지 정보만 [확인 필요]로 남긴다.

### Cited Findings
- **Hydra**: 1.3 안정, 1.4 개발(pre-release), "Facebook Research → hydra-ecosystem" 이관, Python 3.10–3.14, 계층 구성·합성·multirun/sweep, Optuna/Ax sweeper 플러그인, MIT — [GitHub facebookresearch/hydra](https://github.com/facebookresearch/hydra)
- **Optuna**: v5 (2026-09-07), 4.9.0 (2026-06-01); 샘플러 TPE/CMA-ES/NSGA-II/MOTPE; SQLite/RDB 스토리지; Optuna Dashboard; MIT; 인용 Akiba et al., KDD 2019 — [GitHub optuna/optuna](https://github.com/optuna/optuna)
- **MLflow**: Apache-2.0, Tracking/Model Registry/Evaluation, 로컬 추적 서버·파일 백엔드, Windows 사용 가능, 최근 LLM 추적 강화 — [GitHub mlflow/mlflow](https://github.com/mlflow/mlflow)
- **W&B → CoreWeave Forge**: 무료 개인 플랜(5 seat, 5 GB/월 저장, Weave 1 GB/월); 학술 "Free Pro license for students, professors and postdoctoral researchers ... non-commercial research", 추적 시간 무제한, 200 GB 저장, Weave 25 GB/월, 100 seat, 학술 이메일 필요; self-hosting 언급 없음 — [CoreWeave Forge pricing](https://coreweave.com/forge-pricing) (wandb.ai/site/pricing에서 301 리다이렉트됨)
- **SciPy LHS**: `scipy.stats.qmc.LatinHypercube(d, scramble=True, strength=1|2, optimization=None|"random-cd"|"lloyd", rng)`; strength=2는 "orthogonal array based LHS of strength 2", n=p² (p 소수), d ≤ p+1; `random-cd`는 centered discrepancy 감소, `lloyd`는 Lloyd-Max 변형; strength·lloyd는 SciPy 1.8.0 추가(1.10.0 개선) — [SciPy LatinHypercube](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.qmc.LatinHypercube.html)
- **SciPy bootstrap**: `scipy.stats.bootstrap(data, statistic, n_resamples=9999, batch=None, vectorized=None, paired=False, confidence_level=0.95, method='BCa', rng=None)`; 기본 BCa(bias-corrected and accelerated); 1.15.0에서 `rng` 키워드(SPEC-007) 전환 — [SciPy bootstrap](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.bootstrap.html)
- **statsmodels 검정력**: `TTestIndPower.solve_power/power/plot_power`, 파라미터 `effect_size`(Cohen's d), `nobs1`, `alpha`, `power`, `ratio`, `alternative` — [statsmodels TTestIndPower](https://www.statsmodels.org/stable/generated/statsmodels.stats.power.TTestIndPower.html)
- **NASA-STD-7009B** "Standard for Models and Simulations", Change 1, 문서일 2024-03-05(최초 승인 2009-07-13), 공개 PDF(NASA-STD-7009B-Final-3-5-2024.pdf), 범위: V&V, 입력 데이터 pedigree, 결과 불확실성·강건성, 사용 이력, M&S 관리, 인력 자격 등 신뢰성 평가 요소 — [NASA Technical Standards](https://standards.nasa.gov/standard/NASA/NASA-STD-7009)
- Sargent, R. G. (2011) "Verification and Validation of Simulation Models"; Schlesinger et al. (1979) "Terminology for model credibility"; Banks et al. (2010) Discrete-Event System Simulation 5th ed. — 검증·타당성 검증 고전 anchor(2차 출처 경유) — [Wikipedia: Verification and validation of computer simulation models](https://en.wikipedia.org/wiki/Verification_and_validation_of_computer_simulation_models)

### Inferences
- 재현성 프로토콜 권고: (1) Hydra 구성 스냅샷 + git commit hash + 시드(환경/정책/부트스트랩 각각 분리)를 MLflow run에 아티팩트로 저장; (2) 시나리오 요인(위협 수, 교전 거리, 통신 손실률, 해상상태)은 `LatinHypercube(strength=2, optimization="random-cd")`로 설계해 DOE 근거 명시; (3) 효과크기는 Cohen's d + BCa 95% CI를 기본 보고, 사전 검정력 분석(`TTestIndPower.solve_power(effect_size=0.5, power=0.8, alpha=0.05)`)으로 시드 수 결정; (4) 이전 연구(b)의 "1,000 physical sims + 100,000 bootstrap resamples"와 동일한 통계 설계를 반복하면 중복성 지적 가능성이 있으므로, 후속 연구는 **다중 비교 보정(Holm/BH)·순열검정·강건성 곡선(robustness-vs-jamming curve)** 등 상이한 통계 설계로 차별화할 필요가 있다.
- V&V 보고는 NASA-STD-7009B의 8개 신뢰성 요소 척도(0~4)를 적용한 "credibility assessment matrix"를 부록에 넣는 것이 공개·인용 가능한 표준 기반이라 국제 심사에 유리하고, 국방 심사자를 위해 DoDI 5000.61/MIL-STD-3022(VV&A Plan/Report 템플릿) 체계를 병기한다.

### Gaps
- DoDI 5000.61(DoD M&S VV&A), MIL-STD-3022(VV&A 문서화 표준, 2008 제정·2012 Change 1로 알려짐), DoD M&S VV&A Recommended Practices Guide: esd.whs.mil 403, msco.mil/vva.msco.mil DNS 실패, everyspec 404, acqnotes 404로 **전부 미열람** [확인 필요].
- NATO AMSP-01(NATO M&S Standards Profile)·STANAG 4603(HLA): nso.nato.int 404, NATO M&S COE 홈페이지에 언급 없음 → 서지 미확인 [확인 필요].
- 국방 M&S VV&A 업무지침(국방부/방사청 행정규칙)은 접근 수단 부재로 미조사 [확인 필요].
- Hydra 1.3의 정확한 릴리스일, MLflow 최신 버전 번호 미확인.

---

## KQ7. 모듈형 연구 시뮬레이터 아키텍처 패턴과 경량 2-D 시각화

### Takeaway
BenchMARL(algorithm/model/task/experiment 분리 + Hydra 합성), VMAS(시나리오 클래스가 월드·에이전트·보상을 선언), Stone Soup(센서·트래커·지표 컴포넌트 조립)의 공통 패턴은 "**구성 파일로 조립되는 독립 컴포넌트 + 벡터화 코어 + 분석 분리**"이며, 시각화는 학습 루프와 분리된 로그 재생(replay) 방식으로 pygame-ce/Arcade(실시간 2-D), Rerun(시계열·공간 데이터 디버깅), Streamlit(실험 대시보드)을 조합하는 것이 적절하다.

### Cited Findings
- BenchMARL 구조: 알고리즘·모델(MLP/GRU/LSTM/GNN/CNN/Deepsets 시퀀스 합성, 중앙/분산)·환경(task)·실험 구성을 Hydra로 조립, marl-eval로 표준 보고 — [GitHub facebookresearch/BenchMARL](https://github.com/facebookresearch/BenchMARL)
- VMAS: 시나리오 단위 정의, "extremely lightweight, using only tensor operations", 수만 병렬 환경 — [GitHub proroklab/VectorizedMultiAgentSimulator](https://github.com/proroklab/VectorizedMultiAgentSimulator)
- TorchRL: `ParallelEnv`, 환경 래퍼, MAPPO/IPPO 손실, MultiAgentGAE 등 모듈 분리 — [GitHub pytorch/rl](https://github.com/pytorch/rl)
- Stone Soup: 추적·상태추정 컴포넌트 프레임워크(Dstl), MIT, Python 3.10+ — [GitHub dstl/Stone-Soup](https://github.com/dstl/Stone-Soup)
- Pyquaticus: "configurable observation space", "decentralized and agent-relative observation space", 순수 Python 경량 설계 — [Pyquaticus README](https://raw.githubusercontent.com/mit-ll-trusted-autonomy/pyquaticus/main/README.md)
- **pygame-ce**: 커뮤니티 포크, 2.5.8, Python 3.10+/PyPy3, SDL 2.0.20+, LGPL 2.1, 12,397 커밋 — [GitHub pygame-community/pygame-ce](https://github.com/pygame-community/pygame-ce)
- **Arcade**: "Easy to use Python library for creating 2D video games" (pyglet/OpenGL), MIT, 6,361 커밋 — [GitHub pythonarcade/arcade](https://github.com/pythonarcade/arcade)
- **Rerun**: "a single toolchain for logging, storing, querying, transforming, visualizing, and training on multimodal data", Python/C++/Rust SDK, 네이티브·웹 뷰어, 이미지·비디오·점군·변환·텐서·텍스트·시계열·메시·지도 — [rerun.io](https://rerun.io/)
- **Streamlit**: "transform Python scripts into interactive web apps in minutes", Apache-2.0, 대시보드·리포트 — [GitHub streamlit/streamlit](https://github.com/streamlit/streamlit)

### Inferences
- 권장 패키지 레이아웃(연구자 요청 구조 반영): `sim/` (벡터화 코어: `world`, `entities`(USV/표적 상태 텐서), `sensors`(탐지·식별 확률, 기만체), `weapons`(RCWS/유도로켓/배회탄 교전률·시간창), `comms`(그래프 단절·재밍 모델)), `solvers/` (CP-SAT/HiGHS/SCIP/Gurobi 래퍼, VNS, CBBA 베이스라인), `agents/` (GAT-MAPPO, NCO 정책, risk-sensitive 손실), `scenarios/` (Hydra YAML + LHS 요인), `experiments/` (Hydra multirun → MLflow/W&B), `analysis/` (bootstrap/effect size/power, V&V 매트릭스), `viz/` (pygame-ce 실시간 재생, Rerun 로그, Streamlit 대시보드). 핵심 원칙은 **학습 루프에서 렌더링을 완전히 제거**하고 궤적을 Parquet/NumPy로 저장한 뒤 재생하는 것(처리량 보존).
- Stone Soup은 T2(센서 잡음·식별 불확실성·기만체)에서 **다표적 추적 전단(front-end)**으로 결합할 수 있는 유일한 성숙 오픈소스이며, 추적 품질 → WTA 입력 불확실성의 연결 고리를 표준 라이브러리로 구현하면 재현성 심사에 유리하다.
- Unity ML-Agents는 시각적 데모(국내 발표·HMI/XAI 연구 T5)에는 유용하나 수천 병렬 학습에는 부적합하다.

### Gaps
- "모듈형 연구 시뮬레이터 아키텍처"를 명시적으로 권고한 실무자 논문·블로그는 본 세션에서 1차 열람하지 못함(위 패턴은 열람한 라이브러리 구조에서 귀납한 것).
- Plotly/Dash는 미열람(인용 불가), Rerun 라이선스·버전 미확인, Arcade 현재 버전 미확인.

---

## 부록 A. 후보 주제 T1~T7에 대한 툴링 함의 (요약)
- **T1(통신 거부·기만 하 완전분산 WTA)**: 희소 통신 그래프가 GAT VRAM을 10배 이상 절감(KQ5 추정) → 로컬 PC에 가장 적합. 그래프 단절·재밍은 `comms` 모듈의 인접행렬 마스크로 벡터화 구현 가능. CBBA/합의 베이스라인은 자체 구현(출처 미확보).
- **T2(불확실성 강건 WTA, CVaR/DRO/Bayesian)**: Stone Soup 추적 전단 + 위험민감 손실(TorchRL 커스텀) + pymoo 다목적. 몬테카를로 100,000-run은 로컬에서 수 분(KQ5).
- **T3(WTA+기동·TOT 동기화 포화공격)**: 운동학 적분이 스텝당 비용을 지배하므로 벡터화 필수; CP-SAT `no_overlap`/시간창 제약(v9.15 개선)이 베이스라인에 유리.
- **T4(일반화 가능한 anytime 하이브리드 NCO)**: 20→400 유닛 스케일 일반화 실험은 400 에이전트 완전연결 어텐션에서 VRAM 한계(KQ5) → 희소화 또는 미니배치 필수; anytime 품질은 CP-SAT 상·하한 기록으로 정량화.
- **T5(지휘관 의도 → LLM → 목적함수·제약, XAI, human-on-the-loop)**: 8 GB VRAM에서 로컬 LLM은 소형 양자화 모델에 한정될 것으로 추정(출처 미확보); API 기반 LLM 사용 시 재현성(모델 버전 고정) 문제를 논문에 명시해야 함.
- **T6(자기대결·공진화 red-team)**: RLlib이 "self-play and league-based training"을 지원(KQ1), DEAP가 공진화 지원(KQ3); 단, RLlib Windows는 Beta → WSL2 권장.
- **T7(이종 교차영역 USV+UAV+UUV)**: BenchMARL의 이종 모델 구성(중앙/분산 레이어 조합)과 TorchRL TensorDict가 이종 관측·행동 공간 처리에 적합; HoloOcean은 UUV 음향통신 포함 다중 에이전트 지원(KQ2)으로 검증 단계에 활용 가능.

## 부록 B. 버전·라이선스·Windows 지원 요약표 (2026-10-05 열람 기준)
| 도구 | 버전/날짜 | 라이선스 | Windows 네이티브 | GPU 벡터화 | 비고 |
|---|---|---|---|---|---|
| VMAS | 활발(614 커밋) | GPL-3.0 | 명시 없음 [확인 필요] | PyTorch 텐서 | 30k 병렬 <10 s(논문) |
| BenchMARL | 활발(177 커밋), JMLR 2024 | MIT | 명시 없음 | TorchRL 경유 | GNN 레이어 지원 |
| TorchRL | 0.13, PyTorch 2.1+ | MIT | CUDA 휠 Linux만 [확인 필요] | ParallelEnv | MAPPO/IPPO 손실 |
| JaxMARL | 활발(986 커밋), NeurIPS 2024 D&B | Apache-2.0 | 불가(JAX GPU) → WSL2 | JAX | MPE 10k env 4.0e7 SPS(2080) |
| PettingZoo | NeurIPS 2021 | MIT | 커뮤니티 지원 | 없음 | AEC/Parallel API |
| MAgent2 | Farama 유지 | MIT | 공식 미지원 | 없음 | 대규모 그리드 전투 |
| EPyMARL | Gymnasium 전환 2024-07 | [확인 필요] | 명시 없음 | 없음 | VMAS 연동 |
| MARLlib | 2023-11 이후 정체 | MIT | Linux 전용 | 없음 | Py3.8–3.9, gym 0.20 |
| skrl | JMLR 2023 | MIT | 명시 없음 | PyTorch/JAX/Warp | IPPO/MAPPO |
| RLlib(Ray) | Ray 2.59/2.61 문서, 3.0 dev | Apache-2.0 [확인 필요] | Beta | — | self-play/league |
| Pyquaticus | 82 커밋, Python 3.10 | BSD-3 | 명시 없음(순수 Python) | 없음 | MOOS-IvP 동역학 |
| VRX | 2.3, Gazebo Harmonic/ROS 2 Jazzy | Apache-2.0 | 불가(Ubuntu) | — | OCEANS 2019 |
| HoloOcean | v2.3.0, UE | [확인 필요] | 지원 | — | ICRA 2022, 다중 에이전트 |
| Unity ML-Agents | Release 23 (2025-08-28) | Apache-2.0 | 지원 | — | MA-POCA |
| Stone Soup | Python 3.10+ | MIT | 지원(순수 Python) | — | Dstl 추적 |
| OR-Tools | 9.15 (2026-01-12) | Apache-2.0 | x64 휠 | — | HiGHS 1.12, SCIP 10.0 번들 |
| HiGHS | 1.12(OR-Tools 번들) | MIT | 지원 | — | scipy.optimize.milp |
| SCIP | 10.0.0(OR-Tools 번들) | Apache-2.0 | [확인 필요] | — | PySCIPOpt |
| Cbc | 2.10.10 | EPL-2.0 | 바이너리 제공 | — | python-mip/PuLP |
| Gurobi | 학술 Named-User 1년 | 상용(학술 무료) | 지원 | — | 모델 크기 무제한 |
| pymoo | 0.6.2 (2026-06-27) | [확인 필요, 오픈소스] | 지원 | Joblib/GPU | NSGA-II/III |
| DEAP | [확인 필요] | LGPL-3.0 | 지원 | — | 공진화 |
| PyTorch | 2.14.1 최신, 2.15 예정(CUDA 13.2) | BSD | cu128/cu130 휠 | — | sm_120은 2.7+cu128부터 |
| PyG | 옵션 휠 torch 1.13–2.12 | MIT [확인 필요] | 지원 | — | 순수 PyTorch 모드 가능 |
| DGL | 2.4.0 (2024-09-03) | Apache-2.0 [확인 필요] | — | — | PyTorch ≤2.4, Blackwell 미지원 |
| Triton(Windows 포크) | PyTorch 2.7→3.3 … 2.10→3.6 | MIT [확인 필요] | 지원(포크) | — | sm_120 공식 지원 |
| Hydra | 1.3 안정/1.4 pre | MIT | 지원 | — | hydra-ecosystem 이관 |
| Optuna | v5 (2026-09-07) | MIT | 지원 | — | NSGA-II/MOTPE |
| MLflow | [버전 확인 필요] | Apache-2.0 | 지원 | — | 로컬 추적 |
| W&B(Forge) | 학술 무료 Pro | SaaS | 지원 | — | 200 GB, 학술 이메일 |
| pygame-ce | 2.5.8 | LGPL-2.1 | 지원 | — | 실시간 2-D |
| Arcade | [확인 필요] | MIT | 지원(pyglet) | — | OpenGL 2-D |
| Rerun | [확인 필요] | [확인 필요] | 네이티브·웹 뷰어 | — | 다중모달 로깅 |
| Streamlit | [확인 필요] | Apache-2.0 | 지원 | — | 대시보드 |
