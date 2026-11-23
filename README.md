# A+토벌단: (영화 ‘치이카와: 인어섬의 비밀’ 분석 )
![치이카와 이미지](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQvr6wCKv8G08uzzmr1oxUXxPBOJpjadSC909VEQ0uddw&s=10) 
## 프로젝트 소개
우리 팀은 **영화 ‘치이카와: 인어섬의 비밀’의 등장인물, 주요 사건, 장소, 사물, 문화적 요소 데이터셋**을 대상으로 작품의 서사적·문화적·관계적 특징을 분석하는 지식그래프를 구축합니다.

국경과 문화를 넘어 흥행하게 된 <치이카와>의 요소들을 **서사적 측면, 문화적 측면, 관계적 측면**으로 정리하여 흥행 요인을 탐색하고자 합니다.

Neo4j를 활용하여 등장인물 간 관계, 사건의 인과관계, 일본 문화적 요소와 서사의 연결성을 시각화하고 분석합니다.

## 팀원
- 박민진 (불어불문학과) — 등장인물 및 관계 데이터 수집, 일본 문화 요소 분석, 데이터 입력
- 방민주 (영어영문학과) — 주요 사건 및 서사 구조 분석, Cypher 질의 작성 및 검증
- 석예린 (한문학과) — 장소 및 주요 사물 데이터 수집, 지식그래프 시각화

## 데이터 출처
-  [나무위키 — 극장판 치이카와: 인어 섬의 비밀](https://namu.wiki/w/극장판%20치이카와:%20인어%20섬의%20비밀): 영화의 등장인물, 주요 사건, 줄거리 및 세계관 정보
-  [CGV — 극장판 치이카와: 인어 섬의 비밀](https://cgv.co.kr/cnm/cgvChart/movieChart/30001367): 영화의 공식 소개, 기본 정보 및 작품 개요
## 데이터 편찬작업물: (월) B팀_치이카와
## 그래프 데이터 설계

### 레이블(클래스)/노드
| 레이블 | 노드 예시 | 주요 속성 |
|---|---|---|
| Character | 치이카와, 하치와레, 우사기, 세이렌, 히토하 | id, name, name_kor, type, personality, immortality, skills |
| Event | 전단지수령, 인어섬방문, 세이렌조우, 인어살해, 영생획득 | id, name, type |
| Place | 치이카와의 집, 인어섬 마을, 세이렌의 거처, 해변 | id, name, type |
| Object | 전단지, 토벌봉, 인어 비늘, 인어 조림, 전설의 동물 도감 | id, name, type |
| CulturalElement | 축제, 인어설화, 바다신앙, 생선조림, 오사카사투리 | id, name, type |

**총 5개 레이블, 55개 노드**

### 관계 타입(엣지)
| 출발노드 | 도착노드 | 관계어 |
|---|---|---|
| Character | Character | FRIENDS_OF |
| Character | Character | RIVAL_OF |
| Character | Character | ATTACKS |
| Character | Character | RESCUES |
| Character | Character | KIDNAPS |
| Character | Character | KILLS |
| Character | Event | PARTICIPATES_IN |
| Event | Event | CAUSES |
| Event | Place | OCCURS_AT |
| Character | Place | TRAVELS_TO |
| Character | Place | LIVES_IN |
| Character | Place | OPERATES |
| Character | Object | USES |
| Character | Object | EATS |
| Object | Event | REVEALS |
| Event | CulturalElement | REFLECTS |
| Character | CulturalElement | REFLECTS |
| Object | CulturalElement | ASSOCIATED_WITH |
| Object | Event | CAUSES |

**총 114개 관계**

## 핵심 연구 질문

### 1. 서사적 측면

- 하나의 사건은 어떻게 연쇄적인 갈등과 해결로 이어지는가?
- 겉으로 드러난 갈등과 실제 갈등의 원인은 어떻게 다른가?

### 2. 문화적 측면

- 일본의 전통문화와 설화는 작품 속에서 어떤 서사적 기능을 수행하는가?
- 일본 문화의 고유성을 드러내는 사물과 표현은 무엇이며, 이야기에 어떻게 활용되는가?

### 3. 관계적 측면

- 가장 많은 사건에 관여하는 캐릭터는 누구이며, 어떤 서사적 역할을 수행하는가?
- 등장인물 간 우정·갈등·구조 관계는 어떻게 연결되어 있는가?
