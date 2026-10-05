# 09. 전투용 군집 USV 무장할당의 운용적 동인(2022–2026)과 공개출처 기반 현실성 파라미터

조사 방법 메모: 본 세션의 WebSearch 예산이 소진된 상태에서 시작했으므로, 모든 자료는 URL을 직접 열어(WebFetch, korea.kr 보도자료 PDF는 curl+pdftotext) 확인한 것만 인용했다. Naval News·The War Zone·Wikipedia·CRS(everycrsreport 미러)·CNAS·War on the Rocks·korea.kr은 열렸고, USNI News·CSIS·Hudson·RAND·IISS·RUSI(검색결과 비표시)·Breaking Defense/Defense News(검색 비표시)·국방일보 검색·연합뉴스 영문·일본 방위성 예산 페이지는 403/404/빈 결과로 열지 못했다. 열지 못한 출처의 주장은 인용하지 않았고, 2차 출처(Wikipedia)에 의존한 수치는 [확인 필요]로 표시했다. 국내 사업(해검·해령·Navy Sea GHOST·국기연 490억 패키지 과제)은 03_korea_domestic_research.md에 이미 정리되어 있으므로 여기서는 중복 조사하지 않고 2026–2027 예산선과 외부 비교 맥락만 보강했다.

## KQ1. 흑해·홍해 USV 공격에 대해 공개 보고된 교전 데이터(속도·사거리·공격당 USV 수·탐지거리·반응시간·성공/손실률)는 무엇이며 누가 보고했는가?

### Takeaway
공개된 것은 플랫폼 제원(Magura V5 최고 78 km/h·순항 41 km/h·800 km·300 kg·$273k, Sea Baby 90 km/h·≥1,000→1,500 km·850→2,000 kg)과 사건별 투입 수(Kerch 교량 2척, Su-30 격추 작전 3척 투입·2척 교전, Magic Seas 공격에 USV 4척+고속정 8척)이며, 탐지거리·방어측 반응시간·전체 성공/손실률은 어느 1차 출처도 수치로 공개하지 않았다. 러시아 대응은 2023년 물리적 차단물·헬기/전투기 기총·EW에서 2024년 FPV 드론·Lancet, 2026년 요격 USV로 진화했고, 우크라이나는 대공미사일·RWS·요격드론 모함(MV11)으로 응수하여 "USV 대 USV·USV 대 항공기" 교전이 현실화되었다.

### Cited Findings
**우크라이나 USV 제원(2차 출처, 세부 수치 [확인 필요])**
- MAGURA V5: 길이 5.5 m, 질량 <1,000 kg, 최고 78 km/h(약 42 kt), 순항 41 km/h(약 22 kt), 작전반경 800 km, 탑재 300 kg, 체공 60 h, 단가 $273,000, 항법 GNSS·관성·시각; 무장은 300 kg 폭약 또는 R-73. MAGURA V7: 7.2 m, <1,300 kg, 최고 72 km/h, 순항 43 km/h, 1,000 km, 650 kg, 48 h(발전기 사용 시 7일), AIM-9 2발 또는 기관총, 270 hp 디젤. MAGURA V11: 개방해역 7일 작전, Sting 요격기 18발 — [Wikipedia MAGURA V5](https://en.wikipedia.org/wiki/MAGURA_V5)
- Sea Baby: 길이 6 m·폭 2 m·수면상 높이 0.6 m, 최고 90 km/h, 작전반경 ≥1,000 km, 단가 850만 흐리브냐(약 $245k, 2025), 탑재 초기 108 kg → 2023년 말 850 kg, 2024.01 공개된 RPV-16 열압력 발사기 6기 탑재형, "Starlink 의존을 피하기 위한 이중화 통신" — [Wikipedia Sea Baby](https://en.wikipedia.org/wiki/Sea_Baby)
- Sea Baby 2025년 개량형: 사거리 1,500 km 초과(기존 약 1,000 km), 탑재 2,000 kg(기존의 2배), 122 mm Grad형 10연장 로켓, 자이로안정화 12.7 mm RWS — [Naval News, T. Ozberk, 2025-10-28](https://www.navalnews.com/naval-news/2025/10/ukraine-unveils-sea-baby-usv-armed-with-rockets-and-machine-gun/)
- Magura MV11: 탑재 4,850 lb(2,200 kg), 최대 1주 작전, 수직발사 Sting 요격기 18발(각 약 9 lb, 고도 약 23,000 ft, 사거리 약 23 mi, 단가 약 $2,100), Sting은 최대 2,000 km 떨어진 곳에서 노트북으로 원격운용 가능, 위성통신 단말·마스트 카메라 — [The War Zone, J. Trevithick, 2026-08-25](https://www.twz.com/sea/ukraines-newest-usv-is-a-super-sized-mothership-packed-with-anti-drone-interceptors)
- 2026.08 우크라이나 무인체계 열병식: Magura V7(Sea Dragon·AA-11), MV11, Sargan/Seawolf(Sea Dragon·AIM-9M형, 쿼드콥터 격납고 4개형, Grad 122 mm 4발+EW형), Sea Baby(램 폭약·RWS·Grad·Sea Dragon 변형)가 "시제가 아닌 실전 운용체계"로 전시 — [Naval News, H I Sutton, 2026-08-25](https://www.navalnews.com/naval-news/2026/08/worlds-first-military-drone-parade-what-we-saw-on-the-water/)

**사건별 투입 수·결과**
- 2023-07-17 Kerch 교량: Sea Baby 2척, 교각·상판 부분 손상; 2023-09-14 Samum, 2023-10 Pavel Derzhavin, 2023-12 Vladimir Kozitsky 피격; 2024-06 기뢰부설로 러 함정 ≥4척 손상(주장); 2025-11-28 셰도우플릿 유조선 Kairos·Virat(터키 연안 28–52 nm); 2025-12 Sub Sea Baby로 Kilo급 B-271 Kolpino 타격(주장) — [Wikipedia Sea Baby](https://en.wikipedia.org/wiki/Sea_Baby)
- 2024-02-01 코르벳 Ivanovets 격침(Magura V5 "수 척"), 2024-02-14 상륙함 Tsezar Kunikov 격침, 2024-03-05 초계함 Sergey Kotov 격침, 2024-05-30 KS-701 Tunets 2척, 2024-08-10 KS-701 1척(Magura 1척 투입), 2024-12-31 Mi-8 격추(R-73 탑재 V5), 2025-05-02 Su-30SM 2기 격추(Magura V7 약 3척, AIM-9, Novorossiysk 서쪽 50 km) — [Wikipedia MAGURA V5](https://en.wikipedia.org/wiki/MAGURA_V5)
- Su-30 격추 작전 세부: Magura-7 3척 투입, 2척이 실제 공격; AIM-9 적외선 유도; Novorossiysk 서쪽 약 50 km; 1기 승무원 생존(민간선 구조), 1기 승무원 사망 보도; Budanov "Magura-7에 몇 종의 미사일을 쓰지만 AIM-9 결과가 가장 좋다" — [The War Zone, H. Altman, 2025-05-03](https://www.twz.com/news-features/two-russian-su-30-flankers-downed-by-aim-9s-fired-from-drone-boats-ukrainian-intel-boss)
- 동일 사건의 Sutton 분석: 러시아는 "약 2년간" Flanker를 저고도로 투입해 기총·무유도로켓으로 USV를 요격해 왔고, 2024-12-31 Mi-8 2기 피격 이후 전투기 의존이 커졌을 가능성 — [Naval News, H I Sutton, 2025-05-03](https://www.navalnews.com/naval-news/2025/05/world-first-ukrainian-maritime-drone-shoots-down-russian-flanker-jet/). Wikipedia는 Mi-8 "1기 격추·1기 손상"으로 기술하므로 격추 수는 1–2기로 상충 [확인 필요].
- Sergey Kotov는 2023-09-14 해상드론 공격으로 손상된 뒤 2024-03-05 격침; Olenegorsky Gornyak 2023-08-04 해상드론 피격; 우크라이나가 전쟁 중 투입한 공격/정찰 USV를 "16–24척"으로 기술(출처·시점 불명) [확인 필요] — [Wikipedia, List of ship losses during the Russo-Ukrainian War](https://en.wikipedia.org/wiki/List_of_ship_losses_during_the_Russo-Ukrainian_War)
- 유조선 Kairos는 터키 연안 28 nm에서 폭발·화재로 기동불능, Virat는 기관실 부근 피격; 두 선박 모두 공선 상태로 Novorossiysk행; 투입 척수·항속거리 미공개; "셰도우플릿을 표적으로 하는 새 국면" — [Naval News, F. Van Lokeren, 2025-12-01](https://www.navalnews.com/naval-news/2025/12/ukraine-strikes-russian-shadow-fleet-tankers-in-black-sea/)
- Sub Sea Baby는 잠항 상태로 공격하는 UUV형 파생체계로 웨이포인트 항법·자체 표적획득 가능; Novorossiysk 입구의 부유 폰툰은 USV 대응용이어서 UUV에는 부적합; 흑해 러 잠수함 가동 전력이 6척 중 2척으로 감소(기사 주장); 발사 후 완전자율인지 실시간 유도가 가능한지 불명 — [Naval News, F. Van Lokeren, 2025-12-16](https://www.navalnews.com/naval-news/2025/12/ukraine-strikes-russian-submarine-with-sub-sea-baby-drone/)
- 세계 최초 USV 대 USV 교전(2026.09): 우크라 HUR의 Sargan-3000/SeaWolf(Nordex 제작, Kongsberg Protector RWS·12.7 mm)가 러시아 소형 공격 USV(개량형 Orcan/Zephyr, 제트스키형 워터젯, 램 폭약 운반용)를 격침; 교전 해역은 Odesa–Crimea 사이 북서 흑해로 추정; 탐지거리·교전 절차 미공개; "양측 전술의 진화를 촉발할 것" — [Naval News, H I Sutton, 2026-09-12](https://www.navalnews.com/naval-news/2026/09/worlds-first-naval-drone-duel-results-in-ukrainian-success/)

**러시아 대응책과 우크라이나 손실**
- 2023년 말 러시아 대응: Sevastopol 항 그물·부유 붐·바지 체인, Kerch 교량 추가 차단물, 기관총·초병함; Be-12 비행정 레이더로 USV 식별; Mi-8·Ka-27 헬기의 무유도로켓·기관총 교전, Flanker 기총 소사 사례; 함정·육상 EW 재밍은 "중간 정도 효과"; 고가치 선박(Ursa Major·Sparta-IV·유조선) 호송, AIS 차단; 초계정 발진 FPV(시연 단계), KMZ Dandelion 대USV 플랫폼 시험 예정 — [Naval News, H I Sutton, 2023-12-21](https://www.navalnews.com/naval-news/2023/12/russia-forced-to-adapt-to-ukraines-maritime-drone-warfare-in-black-sea/)
- 2024-05 러 FPV 드론이 정지 상태의 Magura V를 타격하는 영상(13초) 최초 공개; Budanov: "두 달 전부터 시작된 공격에서 이미 다수의 USV를 FPV에 잃었다"(수량 비공개); 러시아 측 대응수단: 고정익·회전익 항공, 소화기, Lancet, 통신연장용 고소 안테나·공중 중계; FPV는 사거리가 짧고 가시선 통신이 필요하나 연안방어용 "추격 가능한 정밀유도탄"으로 유효 — [The War Zone, H. Altman, 2024-05-30](https://www.twz.com/news-features/russian-fpv-drone-seen-attacking-ukrainian-uncrewed-surface-vessel-for-the-first-time)
- 2024.01 로켓 무장 Sea Baby: RPV-16(무유도, 사거리 약 1,000 m) 추정, 2·4·6연장 변형; 크림 항구에서 출동한 러 보트가 드론 파괴를 시도하자 Sea Baby가 "회두하여 응사"했다는 우크라 보도 — [Naval News, T. Ozberk, 2024-02-01](https://www.navalnews.com/naval-news/2024/01/ukraine-arms-sea-baby-usvs-with-rockets-or-missiles/)
- 2025-09 터키 해안에서 우크라 통제지역으로부터 약 900마일 떨어진 곳에서 폭약 탑재 Magura V5 표류체 발견; 선체 상부 평판 위성안테나 2기+리저 1기(분석가: "Starlink Gen II 단말 2기 이중화"); 통제 상실 원인은 미확인이며 "위성통신 의존 대비 자율 복귀(fail-safe) 메커니즘 부족"이 함의 — [The War Zone, H. Altman, 2025-09-30](https://www.twz.com/news-features/explosive-packed-ukrainian-drone-boat-found-900-miles-away-in-turkey)
- 2026-06-05 루마니아 Constanța 항에서 러시아 EW에 통제를 잃은 Magura V5가 폭발(Wikipedia가 Digi24 인용) [확인 필요] — [Wikipedia MAGURA V5](https://en.wikipedia.org/wiki/MAGURA_V5)

**분석가의 정량 평가**
- Tallis(CNA): 러시아 대형 플랫폼 8척 손실 중 5척은 미사일 공격; 홍해 6개월간 선박 피격 20건 중 14건 미사일·2건 드론; 요격탄은 공격탄의 "대략 2배 가격"; 우크라 USV 성공은 순항미사일로 러 함대를 Novorossiysk로 몰아넣은 뒤의 2차 효과 — [War on the Rocks, J. Tallis, 2024-07-31](https://warontherocks.com/the-calm-before-the-swarm-drone-warfare-at-sea-in-the-age-of-the-missile/)
- Pettyjohn(CNAS): 소셜미디어 타격 영상은 "성공 사례만 보여주는 비대표 표본"이어서 명중률 추정 불가; EW가 "드론을 막는 가장 효과적인 방법"; 러·우 드론은 "인간이 조종하며 광범위하게 네트워크화되지 않음"; AI 명중률 향상 주장은 "제한적일 가능성" — [CNAS, Evolution Not Revolution, 2024-02-08](https://www.cnas.org/publications/reports/evolution-not-revolution)

**홍해(후티)**
- 2024-01-04 후티 최초의 일방향 공격 USV: 국제 항로로 약 15마일 진출 후 선박에서 "수 마일" 떨어진 곳에서 폭발; Cooper 제독 "새 능력의 도입은 우려 사항"; 2023-11-18~2024-01-04 미 함정이 UAV·순항미사일·ASBM 61기 격추, 2023-12-18 OPG 개시 후 UAV 11·CM 2·ASBM 6 격추 및 소형보트 3척 격침 — [Naval News, L. Willett, 2024-01-09](https://www.navalnews.com/naval-news/2024/01/red-sea-crisis-houthis-demonstrate-increased-capability-coalition-demonstrates-increased-presence/); 동일 사건을 "선박에서 1 nm 넘게 떨어져 폭발"로 기술 — [Wikipedia, Timeline of the Red Sea crisis](https://en.wikipedia.org/wiki/Timeline_of_the_Red_Sea_crisis)
- 2024-06-12 MV Tutor: 백색 5–7 m USV가 좌현 후미로 접근, 승무원은 소형 어선으로 오인, 마네킹 2구 탑재로 기만, 선미·기관실 충돌 폭발, 1명 사망, 이후 대함미사일 추가 피격, 06-18 침몰 — [Wikipedia MV Tutor](https://en.wikipedia.org/wiki/MV_Tutor)
- 2025-07-06 Magic Seas(Al Hudaydah 남서 약 51 nm): 무장 고속정 8척, RPG형 로켓 12발 이상, USV 4척, 미사일, 승선 후 폭약 설치·침몰; 2025-07-07 Eternity C: 해상드론·고속정·RPG, 필리핀 선원 3명 사망 등 — [Naval News, T. Ozberk, 2025-07-10](https://www.navalnews.com/naval-news/2025/07/houthis-sunk-two-merchant-ships-in-red-sea-in-a-week/); Eternity C는 07-07 오후·07-08 야간 2차 공격, 07-09 침몰, 승선 25명(선원 22+경비 3), 사망 3 확인·1 추정, 11명 억류 후 12-03 석방 — [Wikipedia MV Eternity C](https://en.wikipedia.org/wiki/MV_Eternity_C)
- 2024-03-21 독일 호위함 Hessen의 Sea Lynx Mk88A가 도어 마운트 12.7 mm로 예인선단을 공격하던 후티 USV 파괴(탐지·교전거리 미공개) — [Naval News, A. Luck, 2024-03-21](https://www.navalnews.com/naval-news/2024/03/german-navy-helicopter-destroys-houthi-drone/)
- EU Aspides 집계(2025-02-12 기준): UAV 18·USV 2·탄도미사일 4 요격; 2024-08-22 프랑스 Chevalier Paul이 구조작전 중 20 mm로 폭발보트(USV) 1척 파괴 — [Wikipedia Operation Aspides](https://en.wikipedia.org/wiki/Operation_Aspides)
- 미군 선제타격(Poseidon Archer): 2024-02-08/09/10 "발사 준비 중인 USV·대함순항미사일"에 7·7·5회 타격; 2024-06-15 홍해에서 USV 2척 파괴; 07-11 USV 5척·UAV 2기 파괴; 07-14 USV 1척 파괴 — [Wikipedia Operation Poseidon Archer](https://en.wikipedia.org/wiki/Operation_Poseidon_Archer)
- USS Carney: 2023-10-19 9시간에 걸쳐 순항미사일 4·드론 15 요격, 2024-05 귀항 시 "후티 교전 51회"; 반응시간(초) 수치는 기사에 없음 — [Wikipedia USS Carney (DDG-64)](https://en.wikipedia.org/wiki/USS_Carney_(DDG-64))
- (연대적 앵커, 2021) 2017.01–2021.06 후티 해상드론 공격 24건(성공·시도 포함); 실험연구상 "접근 선박의 적대 의도를 인간이 정확히 탐지하는 능력은 제한적, 특히 의도를 은폐할 때"; 무장경비·음향장치 등 기존 대해적 수단은 "무인 적대 선박에는 무용" — [War on the Rocks, H. Haugstvedt, 2021-09-03](https://warontherocks.com/red-sea-drones-how-to-counter-houthi-maritime-tactics/)

### Inferences
- 시뮬레이션 시나리오에 쓸 수 있는 "공개출처 근거 파라미터"는 다음 범위로 방어 가능하다. 공격 USV: 최고 35–49 kt(Magura V5 42 kt, Sea Baby 49 kt, 대만 Kuaiqi 43 kt, ULAQ 35 kt), 순항 22–26 kt, 작전반경 400–1,500 km, 탑재 300–2,000 kg(폭약) 또는 유도로켓·AAM 2–4발, 단가 $0.25–0.3M(우크라). 공격 단위: 공개된 "1회 작전 투입"은 1–4척(교량 2, Su-30 작전 3, Magic Seas 4)이며 80척급 집단 공격은 공개 사례가 없다. 따라서 요청 연구자 (b)의 80 vs 80 시나리오는 "미래 포화공격 가정"으로 명시하고, 2–8척 소집단 실증 사례와 20–400척 확장 실험을 분리 보고하는 것이 심사 방어에 유리하다.
- 탐지·반응시간은 어느 출처도 수치화하지 않았으므로, 모델에서는 레이더 수평선·RCS 기반 가정(예: 저RCS 6 m 선체의 함정 레이더 탐지 수 km 내)과 홍해 사례의 "어선 오인·마네킹 기만"을 식별 불확실성(T2) 파라미터로 변환하고, 민감도 분석으로 처리해야 한다.
- 통신 거부 모델(T1)의 실증 근거: Starlink 이중화 단말에도 900마일 표류(통제 상실), EW로 인한 Constanța 폭발(2차 출처), 러 EW "중간 효과", FPV·Lancet·헬기·전투기에 의한 소모. 즉 "통신 두절 시 안전한 자율 행동(abort/loiter/return)과 국지 관측만으로의 교전 결정"은 운용 요구로 정당화된다.
- 2024–2026년의 핵심 변화는 USV가 '소모성 자폭체'에서 '대공·대USV·요격드론 모함·로켓 플랫폼'으로 역할이 분화된 것이다. 이는 WTA 문제를 "USV→함정 할당"에서 "이종 무장(폭약·유도로켓·AAM·요격드론·EW)×이종 표적(함정·헬기·전투기·적 USV·FPV)"의 다층 할당으로 재정의할 근거가 되며, T3·T7의 '왜 지금' 서술에 직접 쓸 수 있다.

### Gaps
- 공격당 투입 USV 수의 전체 분포, 작전별 손실률(발사 대비 명중), 러시아 측 요격 성공률은 어느 1차 출처도 공개하지 않았다(Budanov도 FPV 손실 수량 비공개).
- 함정 레이더/EO의 USV 탐지거리, 승조원 반응시간(초)은 공개 데이터가 없다(USS Carney 기사에 수치 없음).
- 러시아 측 USV(Orcan/Zephyr 등) 제원과 2025–2026 러시아 요격 USV·요격드론 체계의 공개 제원은 확보하지 못했다.
- Wikipedia의 "16–24척 투입", Mi-8 격추 수(1 vs 2), Constanța 폭발 원인은 1차 출처로 재확인이 필요하다.

## KQ2. 미 해군(Replicator·TF-59·hellscape·PEO USC/MASC), 일본, 대만, 터키, 한국 해군/방사청은 전투용 USV의 군집 규모·자율 수준·통신 복원력·결심 지연에 대해 무엇을 말하는가?

### Takeaway
공식 문서가 '수치'로 말하는 것은 규모(Replicator "수천 대"를 2025년 8월까지, hellscape "수만 대", 대만 2028년 5,000대·향후 50,000대, GARC 월 32척 생산 목표)와 선박급 USV의 성능 요구(MASC: ≥2,500 nm·≥25 kt·통신 두절 시 자율 운항·COLREGS 준수)이며, 자율 수준은 "최종 교전 승인 전까지 자동화"(한국 전투용 USV), "협업·치명효과 생성용 소프트웨어"(Replicator)처럼 서술적으로만 제시된다. 결심 지연(초 단위) 요구를 수치로 공개한 국가는 없다.

### Cited Findings
**미국**
- Paparo(INDOPACOM): "대만해협을 다수의 비밀 능력을 사용한 무인 지옥도(unmanned hellscape)로 바꿔 한 달간 그들의 삶을 철저히 비참하게 만들고, 그 시간이 나머지 모든 것을 위한 시간을 벌어준다"; 구상 체계는 Muskie M18 공격 USV·LRUSV, MQ-4C, Switchblade 600, Hero-120, 잠수함·함정 발진 UUV, PB3 PowerBuoy(충전·데이터 중계); 규모 "수만 대"; 네트워크 중추는 Project Overmatch — [Naval News, C. Johnston, 2024-06-16](https://www.navalnews.com/naval-news/2024/06/breaking-down-the-u-s-navys-hellscape-in-detail/)
- Replicator(CRS, 2026-01-21 갱신): 목표 "2025년 8월까지 수천 대의 무인체계"(ADA2: attritable autonomous all-domain); 명시 체계 Switchblade 600, Anduril Altius-600·Ghost-X·Dive-LD, PDW C-100, Fortem DroneHunter F700, 각종 USV/UAV; 예산 FY2023 $300M(재배정 요청), FY2024 $200M(세출), FY2025 $500M(요청); 7개사가 "치명효과 생성을 위한 체계 협업 소프트웨어"와 C2 통합 제공; Replicator 2는 소형 UAS 대응, 2025.08 JIATF-401 설치; 의회 우려: 정보 부족, 총비용, 기술·일정 위험, AI 원칙과의 윤리적 일관성, 인력·전력구조 — [CRS IF12611 (everycrsreport)](https://www.everycrsreport.com/reports/IF12611.html). 04_frontier_trends 노트의 "FY2024 약 $500M 확보"(DefenseScoop)와 CRS의 "FY2024 $200M 세출"은 상충한다(재배정 포함 여부) [확인 필요].
- LUSV·MUSV→MASC 통합(2025): 2025.07 해군 제안요청 기준 Standard MASC는 40 ft 컨테이너 2개(각 36.3 t) 이상·≥2,500 nm·≥25 kt, High-Capacity는 4개 이상, Single Payload는 20 ft 1개(24 t); "해상 위험을 자율적·안전하게 회피"하고 "통신 상실 시 독립 운용"하며 "COLREGS 준수"; C2 스테이션은 육상 또는 타 함정 탑재; 전력구조상 "수십 척(several dozen)"; 과거 LUSV/MUSV 의회 우려는 추진기관 신뢰성과 "자율 운용 기술의 성숙도"; 신규 우려로 "해상 오판·확전" — [CRS R45757 (everycrsreport), 2026-01-16 갱신](https://www.everycrsreport.com/reports/R45757.html)
- GARC: 16 ft, Maritime Applied Physics Corp. 개발, 정찰·감시·차단·전력보호 임무; 해군 목표 월 32척 생산, 사업에 $160M 이상 집행; USVRON-3·USVRON-7 운용(Wikipedia는 USVRON-3 설립을 2025.01로 기술) — [Wikipedia Unmanned surface vehicle](https://en.wikipedia.org/wiki/Unmanned_surface_vehicle); 1차 출처는 USVRON 3이 2024-05-17 NAB Coronado에서 창설(지휘관 Capt. Derek Rader), 임무는 소형 USV 운용·지속지원 교리 수립 — [Naval News, 2024-05-18](https://www.navalnews.com/naval-news/2024/05/u-s-navy-establishes-unmanned-surface-vessel-squadron-three/) → 설립일은 Naval News(2024.05) 우선.
- 2026.05 NATO Arctic Sentry 2026에서 BlackSea Technologies GARC가 USVRON-3과 북극권 운용 시연("동적·경합 해양환경에서 효과적 운용") — [Naval News, 2026-05-16](https://www.navalnews.com/naval-news/2026/05/blacksea-technologies-demonstrates-garc-usv-capabilities-in-norway/)
- Task Force 59: 2021.09 창설된 해군 최초 무인·AI 태스크포스, 23종 이상의 무인체계 운용; 2024-01-03 TG 59.1 창설; T-38 Devil Ray USV 실탄 사격 훈련에서 "매번 명중"; 한 장교 기준 34회 작전·연습에서 60,000 무인 운용시간 — [Naval News, X. Vavasseur, 2024-01-25](https://www.navalnews.com/naval-news/2024/01/us-navy-launches-new-unmanned-task-group-59-1/)
- 2025-12-16 TF 59가 LCS USS Santa Barbara에서 LUCAS 일방향 공격드론을 아라비아만에서 최초 함상 발사(Renshaw 중장: "저비용·효과적 무인능력의 신속 전달") — [Naval News, 2025-12-19](https://www.navalnews.com/naval-news/2025/12/u-s-navy-in-middle-east-employs-attack-drone-at-sea-for-first-time/)
- CNAS "Swarms over the Strait"(2024-06-20, Pettyjohn·Dennis·Campbell): 현재 중국이 미·대만보다 드론 활용에 유리; 제안 체계 대부분이 "원격조종 또는 반자율"이어서 "다수의 드론 조종사"와 훈련이 필요; 대만은 드론과 지상 화력을 통합하는 "전투관리 소프트웨어"와 "공격받는 중에도 정보 공유" 체계가 필요; 규모는 "수천 대"로만 표현 — [CNAS](https://www.cnas.org/publications/reports/swarms-over-the-strait)

**일본**
- 2025-06-15 FFM Mogami가 Iwo-To 근해에서 USV(JMU 제작, 함미 진회수, EMD 처분폭약 탑재)로 최초 실기뢰 처분 훈련; 탐지는 선체 OQQ-11 소나와 OZZ-5 UUV(Thales/NEC SAS) — [Naval News, Y. Inaba, 2025-06-28](https://www.navalnews.com/naval-news/2025/06/mogami-class-frigate-leads-jmsdfs-first-ever-mine-disposal-drill-using-usv/); 해당 USV는 OZZ-5 소나 데이터를 음향으로 받아 무선으로 FFM에 중계하고 소해구 견인·EMD 운용, FY2022 예산부터 조달 — [Naval News, Y. Inaba, 2021-08-31](https://www.navalnews.com/naval-news/2021/08/new-usv-for-japans-mogami-class-ffm-frigate-breaks-cover/)
- FY2027 방위예산 요구 8.9조 엔($55.5B): MQ-9B 17기 2,922억 엔, Sakura급 OPV는 V-BAT·RHIB·USV 운용 설계, "탐색·공격·수중 네트워킹 기능의 UUV 모듈" 연구 항목, 방위성 "무인자산 확대는 인명 손실 감소와 비용 우위가 목적" — [Naval News, K. Takahashi, 2026-08-31](https://www.navalnews.com/naval-news/2026/08/japan-record-fy2027-defense-budget-new-ffm-submarines/)

**대만**
- 공개된 공격 USV: Kuaiqi(저피탐 선체, 43 kt, Cox 디젤 선외기, Kymeta 위성통신, 램 폭약, 쿼드로터 격납고, Jing Feng형 배회탄 6발사관), Endeavour Manta(삼동선 8.6 m×3.7 m, 선택적 유인, 35 kt, Honda 선외기 2기), Sea Shark 800, Piranha 9(9 m, RAM 코팅, 워터젯, 배회탄 격납고); 표적은 "침공 바지"로 초기 상륙 파도를 교란·약화 — [Naval News, H I Sutton, 2025-08-13](https://www.navalnews.com/naval-news/2025/08/taiwans-new-naval-drones-could-strike-any-chinese-invasion/)
- NCSIST Kuai Chi(小型快速無人艇): "소형·고속·저피탐·기동·치명·저비용", 고속 램 공격, "군집 공격 가능", Mighty Hornet I 배회탄(8 km, 15분) 탑재 — [Naval News, T.-J. Hsu, 2025-09-25](https://www.navalnews.com/naval-news/2025/09/taiwan-showcases-new-kaui-chi-attack-usv-at-tadte-2025/)
- 2025 국방보고서: 무인체계 보유 1,600대 → 2028년 5,000대(13종), 추가로 50,000대 확충 발표; Thunder Tiger Sea Shark USV·Altius-600M 조달; 2026년 연안전투지휘부 확대, Harpoon 400기(2029) — [Naval News, A.-M. Lariosa, 2025-11-23](https://www.navalnews.com/naval-news/2025/11/taiwan-defense-report-highlights-area-denial-progress/)
- 2026.07 Pingtung에서 Shield AI Hivemind를 탑재한 Thunder Tiger SeaShark 600·800 2척이 레이더·영상·AIS 융합, 자율 웨이포인트 계획·구역 탐색, 표적 선박 탐지 후 2척 협동 호송을 시연(USV-UAV 팀잉·통신거부 조건은 미언급) — [Naval News, 2026-07-31](https://www.navalnews.com/naval-news/2026/07/shield-ai-and-thunder-tiger-complete-maritime-teaming-demo-in-taiwan/)
- (앵커) 2023 TADTE: SEASHARK 400 USV 43 kt, "우크라이나전 이후 카미카제 임무 고려 가능" — [Naval News, T.-J. Hsu, 2023-10-03](https://www.navalnews.com/naval-news/2023/10/naval-unmanned-systems-showcased-at-taiwans-defense-show/)

**터키**
- ULAQ: 11 m, 35 kt, 216 nm, 탑재 2,000 kg, Sea State 5, Cirit 4발/L-UMTAS/ATMACA 4발형/12.7 mm/ORKA 경어뢰, 이동차량·지휘소·부양플랫폼에서 원격통제, 국산 암호통신, 주야간 EO, 대GPS재밍 장치·EW 내성; 2021-02-12 진수, 2021-05-25 Cirit 첫 사격; 운용국 터키 해군·카타르 — [Wikipedia ULAQ](https://en.wikipedia.org/wiki/ULAQ)
- ULAQ 연표(Naval News 검색결과): 2022-12-28 SSB 조달계약, 2023-07 자폭형 ULAQ KAMA, 2023-10 NATO 해양안보연습 운용평가, 2024-02 ÇAKIR 순항미사일 탑재형, 2024-10-31 카타르 첫 수출, 2025-12 카타르 인도·2026-01 DIMDEX 전시 — [Naval News 검색 'ULAQ'](https://www.navalnews.com/?s=ULAQ)
- MARLIN(Sefine+Aselsan, SSB 주관): "터키 최초 운용 USV", 모듈형 페이로드, 2026.08 MALAMAN 스마트 바닥기뢰 원격·자율 부설 시험, ASuW/ASW/EW·Kuzgun 미사일 발사 실적 — [Naval News, T. Ozberk, 2026-08-21](https://www.navalnews.com/naval-news/2026/08/turkiyes-marlin-usv-demonstrates-mine-laying-capability-with-malaman/)

**한국**
- 해군 전투용 USV 개념설계(DSK 2025): 확대형은 20 mm RCWS·2.75" 비궁·130 mm 유도로켓·해성 대함미사일·자폭드론 군집 발사체계의 5종 무장, Batch-I은 약 100톤급에 20 mm RCWS+130 mm 유도로켓; 센서는 소형 AESA MFR·EO/IR·EOTS·LiDAR·360° 카메라·MASS형 소프트킬; 워터젯 3기; 해군은 "항법·추적·표적지정을 최종 교전 승인 단계 직전까지 자동화"할 계획; 800톤급 OPV와의 유무인 복합운용, PKMR 대체 가능성; 설계 2024년 말 완료 — [Naval News, E. Cha, 2025-04-03](https://www.navalnews.com/naval-news/2025/03/new-combat-usv-design-breaks-cover-at-drone-show-in-south-korea/)
- 정찰용 USV: LIG넥스원 우선협상대상자(2024.09), 12 m급 2척, 2027년 개발 완료, 비궁 발사기 호환(RIMPAC 2024 100% 명중), 저궤도 상용위성 연동으로 운용범위 확장 계획; "유무인 복합전투체계의 첫걸음" — [Naval News, 2024-09-11](https://www.navalnews.com/naval-news/2024/09/south-koreas-lig-nex1-to-design-reconnaissance-usv-for-rok-navy/)
- 2027년 국방예산 정부안(2026-09-03): AI·유무인복합체계 예산 4,968억→7,727억 원(+55.5%), "전투용무인수상정(연구개발)"을 방위사업청 무인전투함사업팀 소관으로 명시, 목적은 "유·무인 복합전투체계를 구성하여 감시·정찰 및 전투 임무 수행, 전방 해역 인명피해 최소화·미래 전장 우위"; 군집드론 연구개발 착수("적 전략 표적 자동 탐지·인지·정밀 타격") — [korea.kr 보도자료 PDF](https://www.korea.kr/common/download.do?fileId=198545121&tblKey=GMN) (상세는 KQ5)

### Inferences
- 자율 수준에 관한 각국 공식 서술은 수렴한다: "최종 교전 승인은 인간, 그 이전(항법·추적·표적지정·협업)은 자동화"(한국), "통신 상실 시 독립 운용·COLREGS"(미 MASC), "협업으로 치명효과 생성하는 소프트웨어"(Replicator). 이는 T5(지휘관 의도→제약 컴파일+human-on-the-loop 거부권)와 T1(통신 두절 시 국지 결정)이 운용 요구와 정합한다는 근거다.
- 군집 규모의 공식 수치(수천~수만, 대만 5,000→50,000)는 요청 연구자 (b)의 80척 시나리오를 넘어서는 20→400척 확장(T4)의 정당성을 제공하되, 실전 공개 사례는 1–4척이므로 "소집단 실증·대집단 일반화" 2단계 평가가 필요하다.
- 결심 지연 요구가 공개되지 않았으므로, 연구에서는 요구치를 "자체 가정"이 아니라 물리적 교전 기하(예: 42 kt USV가 CIWS 유효사거리 1.5 km를 통과하는 데 약 70초, Mk 38 2.5 km 통과에 약 115초)에서 유도해 제시하는 것이 방어 가능하다(계산은 KQ3 참조).

### Gaps
- 미 해군 PEO USC의 소형 USV(GARC) 총 조달 수량·단가, Replicator 1차·2차 해양 체계의 실제 인도 수량은 열람 가능 출처에서 확인하지 못했다(USNI·Breaking Defense 접근 불가).
- 일본 방위성의 USV 군집·무장 USV 계획과 FY2026/2027 USV 예산 세목(방위성 예산 페이지 403)은 미확인.
- 대만의 USV 조달 수량(예: 200척 보도)과 NT$ 금액은 열람한 기사에 없다.
- 터키 해군의 ULAQ/MARLIN 보유 수량과 군집 시연 데이터는 미확인.

## KQ3. 공개된 대USV 방어체계의 교전 능력(탄수·발사율·사거리·탄창·반응시간)과 포화공격 제약은 무엇인가?

### Takeaway
공개 제원으로 함정 근접방어층을 재구성하면 Phalanx(20 mm, 4,500 rpm, 1,550발, 유효 약 1.5 km, Block 1B FLIR 대수상 모드), Mk 38 Mod 2/3(25 mm, 최대 180 rpm, 유효 2.5 km) 및 Mod 4(30 mm Mk44), Bofors 40 Mk4(4–5 km, 300 rpm, 즉응탄 100발, 3P 근접신관), 헬기 12.7 mm/20 mm 및 APKWS(1.1–5 km, $22k), 그리고 EW·요격드론이다. 반응시간은 공개 수치가 없고, 포화공격 제약은 "탄창 심도·재장전·요격탄 가격이 공격탄의 약 2배"라는 분석가 진술로만 뒷받침된다.

### Cited Findings
- Phalanx CIWS: Block 1A 이후 4,500 rpm(75 rps), 탄창 1,550발, 최대 유효사거리 1,625 yd(1,486 m)·최대 6,000 yd, 약 1 nm에서 교전하며 발사탄을 추적해 표적에 "걸어 올림(walks onto)"; Block 1B는 FLIR 추가로 "연안의 소형 선박 위협·부유체" 대응; 2024-01-30 USS Gravely가 후티 미사일을 CIWS로 최초 격추(USV 교전 기록은 없음) — [Wikipedia Phalanx CIWS](https://en.wikipedia.org/wiki/Phalanx_CIWS)
- Mk 38: Mod 2/3 25×137 mm, 최대 180 rpm(3 rps), 유효 2,500 m·최대 6,800 m, 원격 EO/IR·레이저거리측정·자동추적·완전안정화, Mod 3 330° 감시; Mod 4는 30 mm Mk44 Bushmaster II; 목적은 USS Cole 사건 이후 "소형 고속 수상 위협"; 즉응탄수·홍해 사용 기록은 기사에 없음 — [Wikipedia Mark 38 25 mm machine gun system](https://en.wikipedia.org/wiki/Mark_38_25_mm_machine_gun_system)
- 팰릿형 CIWS(2025.04): 홍해에서 "SM-2·SM-6 등 중·장거리 대공미사일을 대량 소모"한 것이 단거리 방어 보강의 계기; Bofors 40 Mk 4(TRIDON Mk2): 교전거리 4–5 km, 300 rpm, 드럼 70발+포 30발=100발, 3P 근접신관탄(텅스텐 구 1,100개), "20 mm의 4배 사거리"; 해군 측 "층상 방어가 핵심, 중·단거리 함포 교전은 필수"; 수 시간 내 비침습 설치 — [Naval News, C. Johnston, 2025-04-17](https://www.navalnews.com/event-news/sea-air-space-2025/2025/04/u-s-navy-pursuing-palletized-ciws-systems-as-threats-evolve/)
- APKWS: 사거리 1,100–5,000 m(회전익)/2–11 km(고정익), 킷 단가 $22,000, 반능동 레이저 CEP <0.5 m, Hydra 70 탄두; 2013.04 UH-1Y가 APKWS 10발로 정지·이동 소형보트 표적에 "단일·복수 표적 100% 명중"; 2021.06 근접신관형이 Class 2 UAS 파괴 — [Wikipedia APKWS](https://en.wikipedia.org/wiki/Advanced_Precision_Kill_Weapon_System)
- 실전 대USV 교전 수단: 헬기 도어건 12.7 mm(독일 Sea Lynx, 2024-03-21), 함포 20 mm(프랑스 Chevalier Paul, 2024-08-22), 미군 선제 공습(발사 전 USV 파괴, 2024.02·06·07) — 출처는 KQ1의 Aspides·Poseidon Archer·Naval News 항목 참조.
- 러시아의 대USV 수단: 항구 붐·그물·바지 체인, Be-12 레이더, Mi-8/Ka-27·Flanker 기총과 무유도로켓, 함정·육상 EW(중간 효과), 호송·AIS 차단 — [Naval News, H I Sutton, 2023-12-21](https://www.navalnews.com/naval-news/2023/12/russia-forced-to-adapt-to-ukraines-maritime-drone-warfare-in-black-sea/); 2024.05부터 FPV 드론, Lancet, 고소 안테나·공중 중계 — [The War Zone, 2024-05-30](https://www.twz.com/news-features/russian-fpv-drone-seen-attacking-ukrainian-uncrewed-surface-vessel-for-the-first-time); 2026.09 요격형 USV 상호 교전 — [Naval News, 2026-09-12](https://www.navalnews.com/naval-news/2026/09/worlds-first-naval-drone-duel-results-in-ukrainian-success/)
- 우크라이나의 대공·대드론 USV 무장: R-73/AIM-9(헬기·전투기 격추), 12.7 mm RWS, Sting 요격기 18발 모함(MV11) — KQ1의 Wikipedia MAGURA V5·TWZ 2026-08-25 항목 참조.
- 포화 제약에 대한 분석: 함정은 "지속적 소모전에 충분한 탄약 밀도를 탑재할 수 없고", 재장전은 전선에서 공격력을 빼내며, "요격탄은 보통 공격탄의 약 2배 가격"; 자율 유도에는 "정교한 결심을 요하는 표적 식별"이 남은 문제 — [War on the Rocks, J. Tallis, 2024-07-31](https://warontherocks.com/the-calm-before-the-swarm-drone-warfare-at-sea-in-the-age-of-the-missile/)
- 인간 식별의 한계: 접근 선박의 적대 의도 탐지는 "특히 의도를 은폐할 때" 제한적(2021 앵커) — [War on the Rocks, H. Haugstvedt, 2021-09-03](https://warontherocks.com/red-sea-drones-how-to-counter-houthi-maritime-tactics/); 홍해 Tutor 사례의 어선 오인·마네킹 기만 — [Wikipedia MV Tutor](https://en.wikipedia.org/wiki/MV_Tutor)
- 대드론 함정체계 신제품: MBDA Sea Warden(Euronaval 2024, 센서·무장 통합 대무인 위협체계) — 제목·요지만 확인 [Naval News 검색 'counter-usv'](https://www.navalnews.com/?s=counter-usv)

### Inferences
- 공개 제원만으로 구성한 "방어층 교전창" 계산: 42 kt(21.6 m/s) USV가 Bofors 40 유효 4.5 km에서 Phalanx 유효 1.5 km까지 약 139초, Phalanx 1.5 km에서 충돌까지 약 69초, Mk 38 2.5 km에서 충돌까지 약 116초를 소요한다. 즉 단일 함정의 근접층은 USV 1척당 약 1–2.5분의 교전창을 가지며, 포화공격 측(T3)의 동시도착(time-on-target) 최적화는 이 창을 공격 USV 수로 나눈 "단위 표적당 교전 가용시간"을 최소화하는 문제로 정식화할 수 있다.
- 탄창 제약: Bofors 40은 즉응탄 100발(3P 근접신관으로 연사 수 발/표적), Phalanx 1,550발(고속 연사로 1표적당 수백 발 소모 가능), Mk 38은 즉응탄 미공개. 방어측의 "동시 처리 가능 표적 수"는 포신 수·조준 전환시간에 의해 제한되므로, 시뮬레이터에서는 포대별 단일 표적 교전·전환 지연(공개 수치 없음 → 민감도 변수)으로 모델링해야 한다.
- 다층 방어의 "바깥층"은 헬기(12.7 mm, APKWS 1.1–5 km)·FPV/Lancet·요격 USV이며, 이는 공격 군집 입장에서 "교전 전 소모(attrition before engagement)"의 확률 과정으로 넣을 수 있다(T2의 Pk·생존 확률 불확실성).
- 식별 불확실성(어선 오인·마네킹·AIS 차단)은 T2의 식별·기만 불확실성 모델에 직접 대응하는 실증 사례다.

### Gaps
- 반응시간(탐지→사격 결심→초탄)과 Mk 38/Phalanx의 대USV 실전 명중률·탄 소모량은 공개 수치가 없다.
- Phalanx Block 1B의 대수상 교전 절차·사거리와 Goalkeeper·Millennium 35 mm 등 타 CIWS 제원은 이번 조사에서 열람하지 못했다.
- 러시아 요격 USV·요격드론의 제원과 대USV EW의 효과 범위(거리·주파수)는 공개 데이터가 없다.

## KQ4. RUSI·CSIS·CNAS·Hudson·RAND·IISS·USNI·Naval News·The War Zone·국방일보·디펜스타임즈 분석가들은 USV 군집 운용의 핵심 미해결 문제(표적할당·통신·자율·군수)로 무엇을 지목하는가?

### Takeaway
열람 가능한 분석(CNAS Pettyjohn, CNA Tallis, Naval News Sutton·Özyurt, CRS, WOTR Haugstvedt)은 "표적할당 알고리즘"을 명시적으로 미해결 문제로 꼽지는 않는다. 대신 (1) 재밍 환경의 통신 복원력, (2) 인간 조종·비네트워크 상태에서 벗어난 진정한 자율과 군집 효과, (3) 자율 유도 시의 표적 식별·오판 위험, (4) 탄창·재장전·대량생산의 군수, (5) 공격측 비대칭 우위의 "짧은 수명"(대응책 진화)을 지목한다. 이는 '학습형 분산 WTA가 왜 필요한가'를 뒷받침하지만, 연구자는 "분석가들이 WTA를 지목했다"고 쓰면 안 되고 "분석가들이 지목한 통신·자율·식별 문제의 교차점이 WTA다"로 써야 한다.

### Cited Findings
- Tallis(CNA, 2024): 무인체계는 장거리 대함미사일에 "부가적" 역할; 미해결 과제는 (a) 재장전 시 전선 공격력 공백, (b) 데이터율 높은 위성링크의 재밍 내성 유지, (c) "정교한 결심을 요하는" 자율 유도의 표적 식별, (d) 함정의 탄약 밀도 한계; "저가 기술의 신속 반복은 진입 장벽을 낮췄지만 전략효과의 상한을 올리지는 않았다" — [War on the Rocks, 2024-07-31](https://warontherocks.com/the-calm-before-the-swarm-drone-warfare-at-sea-in-the-age-of-the-missile/)
- Pettyjohn(CNAS, 2024.02): 러·우 드론은 "인간이 조종하며 광범위하게 네트워크화되지 않음"; EW가 가장 효과적인 대응; 대량생산 조정, 재밍 내성, 진정한 자율 운용, 결정적 군집 효과 달성이 양측 모두 미성숙 — [CNAS, Evolution Not Revolution](https://www.cnas.org/publications/reports/evolution-not-revolution)
- Pettyjohn 외(CNAS, 2024.06): 제안 체계 대부분이 원격조종·반자율이어서 다수의 조종사와 훈련 프로그램이 필요; 대만에 "드론과 지상 화력부대를 통합하는 전투관리 소프트웨어"와 "공격받는 중의 정보 공유" 권고; 인도태평양 지리상 장거리·장기체공 드론이 필요해 우크라식 저가 드론보다 비쌀 수밖에 없음 — [CNAS, Swarms over the Strait](https://www.cnas.org/publications/reports/swarms-over-the-strait)
- CRS(2026.01): 의회는 LUSV/MUSV에 대해 "자율 운용 기술의 성숙도"와 추진기관 신뢰성을 우려했고, MASC에 대해 "해상 오판·확전" 가능성을 신규 쟁점으로 제기 — [CRS R45757](https://www.everycrsreport.com/reports/R45757.html); Replicator에 대해 "국제 AI 원칙과의 윤리적 일관성", 총비용·일정 위험, 인력·전력구조 함의 — [CRS IF12611](https://www.everycrsreport.com/reports/IF12611.html)
- Sutton(Naval News): 러시아의 대응이 차단물→항공 기총→EW→FPV→요격 USV로 적응해 왔고, 2026.09 USV 대 USV 교전은 "양측 전술의 진화"를 촉발; 개별 드론 손실은 소모성 설계상 작전적으로 미미 — [2023-12-21](https://www.navalnews.com/naval-news/2023/12/russia-forced-to-adapt-to-ukraines-maritime-drone-warfare-in-black-sea/), [2026-09-12](https://www.navalnews.com/naval-news/2026/09/worlds-first-naval-drone-duel-results-in-ukrainian-success/)
- Özyurt(예비역 소장, Meteksan, 2024.08): USV는 "game changer이자 game extender"로 위험 완화·지휘관 선택지 확대·확전 압력 완화에 기여하나, 비대칭 우위는 "수명이 제한적"이며 기술 접근성이 높아지면 방어 능력이 발전할 것 — [Naval News, 2024-08-10](https://www.navalnews.com/naval-news/2024/10/unmanned-surface-vehicles-usvs-as-both-game-changers-and-game-extenders/)
- Haugstvedt(2021 앵커): 인간의 적대 의도 식별 한계 때문에 "인간 식별에만 의존하는 것은 불충분"; 대응수단으로 고정밀 소총, 보트 네트(추진기 무력화), 물대포, 재밍·스푸핑, 레이저·고출력 마이크로파 — [War on the Rocks, 2021-09-03](https://warontherocks.com/red-sea-drones-how-to-counter-houthi-maritime-tactics/)
- TWZ(2025.09): Starlink 이중화 단말에도 통제 상실·900마일 표류 → "위성통신 의존 대비 자율 복귀 메커니즘 부족" — [The War Zone, 2025-09-30](https://www.twz.com/news-features/explosive-packed-ukrainian-drone-boat-found-900-miles-away-in-turkey)
- 미 해군 자체 진단(간접): 홍해에서 SM-2/SM-6 대량 소모 → 단거리 함포층 보강 필요(탄창·비용 교환비 문제) — [Naval News, 2025-04-17](https://www.navalnews.com/event-news/sea-air-space-2025/2025/04/u-s-navy-pursuing-palletized-ciws-systems-as-threats-evolve/)
- CIMSEC 검색결과(제목만 확인): "Hormuz and the Era of Asymmetry: Sea Mines, Unmanned Systems..."(2026-06-23), "Designing Maritime Campaigns with Unmanned Systems: Overcoming the Innovation Paradox"(J. Wirtz, 2023-11-15), "Unmanned Ships: A Fleet to Do What?"(J. Panter, 2023-10-17) — 본문 미열람 [CIMSEC 검색](https://cimsec.org/?s=unmanned+surface+vessel+swarm)

### Inferences
- 분석가들이 공통으로 짚는 "재밍 내성 통신 + 비네트워크 인간조종의 한계 + 자율 표적식별의 결심 난도 + 탄창/군수"는 정확히 분산 WTA의 입력(국지 관측·불완전 통신)·출력(누가 무엇을 언제 치는가)·제약(탄수·시간창)에 해당한다. 따라서 후속연구의 서론은 "WTA가 미해결이라고 분석가가 말했다"가 아니라 "분석가가 지목한 네 문제가 교차하는 결심이 WTA이며, 기존 WTA 연구는 이 네 조건을 가정에서 제거해 왔다"로 구성해야 표절·과장 논란이 없다.
- T1(통신 거부 분산 WTA)과 T2(식별·기만 불확실성)의 운용적 정당성이 가장 강하고, T6(적응적 적대자 self-play)는 Sutton·Özyurt의 "대응책 진화·우위의 짧은 수명" 서술과 정합한다. T3(동시도착 포화)는 Tallis의 탄창·요격탄 비용 논지와 미 해군의 함포층 보강 움직임에 근거를 둔다.
- 국내 분석가(국방일보·디펜스타임즈)의 공개 논평은 열람하지 못했으므로, 국내 '왜 지금' 근거는 KQ5의 예산·사업 문서(1차 출처)로 대체하는 것이 안전하다.

### Gaps
- RUSI·CSIS·Hudson·RAND·IISS·USNI Proceedings의 USV 군집·hellscape·표적할당 관련 보고서는 접근 불가(403/검색 비표시)로 내용을 확인하지 못했다. 이들 기관의 "표적할당·C2가 핵심"이라는 진술이 존재하는지 여부 자체를 확인할 수 없다.
- 국방일보·디펜스타임즈·월간 국방의 USV 군집 논평은 검색 실패(국방일보 검색 0건 반환)로 미확인.
- 러시아·중국 측 분석(러 군사평론가의 "정찰 UAV+Lancet" 제안은 TWZ 2차 인용)은 1차 출처 미확인.

## KQ5. 2025–2027년 한국의 어느 사업·예산선이 군집 USV AI 무장할당 능력의 자연스러운 스폰서·사용자인가?

### Takeaway
2027년 국방예산 정부안(73조 2,777억 원, +8.2%)은 "AI·유무인복합체계" 항목을 4,968억→7,727억 원(+55.5%)으로 늘리면서 '전투용무인수상정(연구개발)'을 방위사업청 무인전투함사업팀 소관 사업으로 명시하고, 별도로 "군집드론 연구개발 착수"(자동 탐지·인지·정밀타격), 국방인공지능 1,600억→3,610억 원(+125.6%), 2028년까지 GPU 1,137장 확보를 담았다. 따라서 가장 직접적인 스폰서 후보는 (1) 방사청 무인전투함사업팀의 전투용 USV R&D(Batch-I/II), (2) 국기연-LIG넥스원의 '전투용 USV 통합제어·자율임무' 패키지 과제(2025.12–2030.12, 약 490억 원; 03 노트 참조), (3) 국방부 국방인공지능정책과의 국방 소버린 AI·국방AX 거점(해군·해병대 부산)이며, 사용자는 Navy Sea GHOST 로드맵(2028년 3단계)을 추진하는 해군이다.

### Cited Findings
- 2027년 국방예산 정부안(2026-09-03 배포, 국방부·방위사업청): 총 73조 2,777억 원(+8.2%, "최근 20년 내 최대"), 전력운영 50조 416억 원(+5.9%), 방위력개선 22조 7,112억 원(+13.8%, "역대 최대폭 약 2.8조 원 증가"), 병무행정 5,249억 원; 5대 중점 중 "AI·유무인체계로 전환"과 "드론·대드론 역량 강화" — [korea.kr 보도자료 페이지](https://www.korea.kr/briefing/pressReleaseView.do?newsId=156780057), [첨부 PDF](https://www.korea.kr/common/download.do?fileId=198545121&tblKey=GMN)
- 동 PDF: "AI·유무인 복합체계 예산 55.5% 증가 ('26) 4,968억 원 → ('27) 7,727억 원"; "피지컬 AI 실증 신설(신규 430억 원)"; "폭발물 탐지·제거 로봇, 수중자율기뢰탐색체를 차질 없이 전력화하고, 전투용 무인수상정(연구개발), 다족보행로봇 등 장병을 대신해 위험한 임무를 수행할 수 있는 무인전력을 지속 확충"; 세부 항목 "(전투용무인수상정) 유·무인 복합전투체계를 구성하여 감시·정찰 및 전투 임무를 수행하는 전투용무인수상정을 연구개발 — 전방 해역에서 인명피해를 최소화하고, 미래 전장 우위를 확보"; 담당 "방위사업청 무인전투함사업팀 전투용무인수상정 김재성 팀장(02-2079-5590)"; "(수중자율기뢰탐색체) 해군 기뢰전 능력 보강을 위해 수중 자율주행으로 기뢰를 탐색하는 로봇을 양산" — 동일 PDF
- 동 PDF 드론 부문: "드론/대드론 역량강화 예산 18.8% 증가 ('26) 6,788억 원 → ('27) 8,061억 원"; "군집드론 연구개발에 착수"하며 군집드론은 "적 전략 표적에 대한 자동 탐지·인지 및 정밀 타격이 가능"(방위사업청 공격드론사업팀); 중거리 자폭드론("원거리 이동 표적 추적·조준"), 분대급 소형 대인 자폭드론; 접적지역 대드론 통합체계, 레이저대공무기 Block-I 확대·Block-II 이동형 신규 착수; 교육용 드론 11,377대(’26)→17,320대(’27); 휴대용 통합형 대드론건 등 8종 신규(291억 원); "50만 드론전사" 교육훈련 296억→771억 원 — 동일 PDF
- 동 PDF AI 부문: "국방인공지능" 1,600억→3,610억 원(+125.6%); 국방 소버린 AI를 위한 국방AI 데이터 활용기반·AI 인프라("'28년까지 GPU 1,137장 확보"), 고가치 AI학습데이터 구축 244억 원, 전군 공동활용 AI개발 플랫폼 214억 원, 국방AX 거점 5→6개소("'26년 합참(용산), 육군(판교·대전), 해군·해병대(부산), 공군(양재)"), 피지컬 AI 다족로봇 200대 등 시범도입 430억 원, 분야별 월드모델 구축 54억 원(담당 국방부 국방인공지능정책과) — 동일 PDF
- 동 PDF 기술자립: "(유·무인복합체계 기술 자립) 공군 협업무인전투기, 해군 해상전투 무인항공기 등 유·무인 복합체계 구현을 위한 추진체계 기술 자립"("'25년 장기관리대상전력 선정, '26년 통합소요 검토 진행 중"), 첨단항공엔진 미래도전국방기술 신규 +70억 원 — 동일 PDF
- 2025-12-01 방위사업청 보도자료 "전투용무인수상정 시험평가 협력 맞손": 방사청·국방과학연구소·한국해양과학기술원 간 해양 무인체계 시험평가 발전 MOU(첨부 PDF "251126 [방사청 보도자료] 방사청·국과연·한국해양과학기술원 해양 무인체계 발전 MOU"; 본문 세부는 미열람) — [korea.kr](https://www.korea.kr/briefing/pressReleaseView.do?newsId=156732351)
- korea.kr '무인수상정' 검색(2025.10–2026.10, 12건)의 관련 제목: 2026-08-14 방사청 해군 지원함 EO/IR 감시장비 보강(현대전의 무인 선박 등 비대칭 위협 대응), 2026-07-24 산업부 한미 조선협력센터(무인수상정 공동개발 포함), 2026-04-29 3,600톤급 호위함 제주함(FFG-832) 취역("AI 기반 유·무인 복합전투 능력" 강조) — 제목·요지만 확인 [korea.kr 검색](https://www.korea.kr/briefing/pressReleaseList.do?srchWord=%EB%AC%B4%EC%9D%B8%EC%88%98%EC%83%81%EC%A0%95)
- 2026년 예산 관련 korea.kr 검색: 국방부 2026-06-04 "국민주권정부 출범 1년… 국방부의 국정성과"에 3축체계 예산 8.8조 원(+21.3% 대비 2025) 언급; 2026년 국방예산 본안의 무인·AI 세목은 검색 결과 요지에서 확인 불가 — [korea.kr 검색 '2026년 국방예산'](https://www.korea.kr/briefing/pressReleaseList.do?srchWord=2026%EB%85%84+%EA%B5%AD%EB%B0%A9%EC%98%88%EC%82%B0)
- 해군 전투용 USV 개념(Batch-I 약 100톤급, 20 mm RCWS+130 mm 유도로켓; 확대형 5종 무장·자폭드론 군집 발사체계; "최종 교전 승인 단계 전까지 자동화"; 800톤급 OPV와 MUM-T) — [Naval News, 2025-04-03](https://www.navalnews.com/naval-news/2025/03/new-combat-usv-design-breaks-cover-at-drone-show-in-south-korea/); 정찰용 USV 12 m 2척·2027 완료·LEO 위성연동 — [Naval News, 2024-09-11](https://www.navalnews.com/naval-news/2024/09/south-koreas-lig-nex1-to-design-reconnaissance-usv-for-rok-navy/); HD현대중공업–Anduril USV 공동개발(2025-04-09) — 제목·요지 [Naval News 검색](https://www.navalnews.com/?s=south+korea+unmanned+surface)
- 비교 참조(해외 스폰서 구조): 미 Replicator의 "협업·치명효과 소프트웨어" 7개사 선정과 C2 통합 — [CRS IF12611](https://www.everycrsreport.com/reports/IF12611.html); 대만의 Shield AI Hivemind 기반 USV 협동 시연(2026.07) — [Naval News](https://www.navalnews.com/naval-news/2026/07/shield-ai-and-thunder-tiger-complete-maritime-teaming-demo-in-taiwan/)

### Inferences
- 후속연구의 "스폰서 적합성" 서술은 세 층으로 쓸 수 있다: (i) 무기체계 층 — 방사청 무인전투함사업팀의 전투용 USV R&D(2027 예산 명시)와 국기연-LIG 패키지 과제의 '무장 운용·발사통제 체계'(20 mm RCWS·비궁·자폭드론; 03 노트)는 바로 WTA 알고리즘이 들어갈 자리다; (ii) 기반 층 — 국방 소버린 AI·GPU 1,137장·해군 부산 국방AX 거점·월드모델 구축은 대규모 MARL 학습과 시뮬레이터 기반 평가의 인프라 명분이다; (iii) 교차 층 — "군집드론 R&D 착수(자동 탐지·인지·정밀타격)"는 USV 발진 자폭드론 군집까지 포함하는 이종 할당(T7)의 국내 예산 근거다.
- 2026년 대비 2027년 AI·유무인복합 +55.5%, 국방AI +125.6%라는 증가율 자체가 '왜 지금'의 국내 근거이며, 요청 연구자의 2025 KNST 논문(운용개념 서술)과 중복되지 않는 신규 사실이다.
- 사용자 측 요구("최종 교전 승인 전까지 자동화")는 T5의 human-on-the-loop 거부권 설계와 정합하므로, 평가지표에 "승인 대기 중 결심 지연·거부 후 재할당 시간"을 넣으면 해군 소요와 직접 연결된다.

### Gaps
- 2026년 국방예산 본안(2025.12 국회 통과)의 AI·유무인복합·전투용 USV 세목 금액은 열람하지 못했다(2027 PDF의 '26 기준액 4,968억·6,788억·1,600억 원만 확인).
- 전투용 USV Batch-I/II의 연도별 R&D 예산액·수량·전력화 연도는 2027 PDF에 금액이 적시되지 않았고, 방사청 MOU 보도자료 본문(PDF)은 미열람.
- 국기연 패키지 과제의 과제 코드·공고 원문, ADD의 군집 USV 자율임무 과제, 국방일보·디펜스타임즈의 관련 기사는 미확인(03 노트와 동일한 공백).
