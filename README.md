# KPI 퍼포먼스 시뮬레이터
> Meta Ads 집행 전 KPI를 사전 시뮬레이션하는 퍼포먼스 마케팅 도구

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-4BAF9F?style=flat)](https://ahynn8.github.io/KPI-simulator/)

---

## 프로젝트 소개

광고 집행 전에 예산·CPM·CTR·CVR 조합별 KPI를 미리 계산해보는 시뮬레이터입니다.  
가상 캠페인 기획서 작성을 위해 KPI 수치가 실제로 손익분기를 달성하는지 검증하기 위해 직접 구현했습니다.

```
"성장 키워드에 어떤 KPI 목표를 설정하고, 어떤 요소를 개선해야 하는지 설계"
```

---

## 주요 기능

### 실시간 KPI 계산
- 6개 변수 입력 → 노출·클릭·전환·ROAS·CPA 자동 산출
- 예산 규모별 CPM 상승 효과 자동 반영
- 손익분기(BEP) 달성 여부 즉시 판정

### 시나리오 비교

| 시나리오 | 내용 |
|---|---|
| 현재 | 현재 입력값 기준 |
| 소재 A/B테스트 | CTR × 1.3 (소재 교체 효과 반영) |
| 타겟 최적화 | CTR × 1.2, CVR × 1.1 |

### 예산 스케일링
- 예산 ×0.25 ~ ×5 범위에서 ROAS 변화 시각화
- CPM 상승 효과 반영한 현실적 스케일링 시뮬레이션

### CSV 업로드
- 캠페인별 KPI 파일 업로드 → 슬라이더 자동 세팅

---

## 실제 검증 결과

| 캠페인 | 예산 | CTR | CVR | ROAS | BEP |
|---|---|---|---|---|---|
| 뷰티 브랜드 캠페인 기획서 | 900만원 | 3.9% | 2.5% | 200.2% | 200% 달성 |
| 패션 브랜드 캠페인 기획서 | 300만원 | 2.6% | 2.0% | 271% | 250% 초과 달성 |

---

## 계산 로직

```
실제 CPM  = 예산 < 100만원 → 기본 CPM
           예산 ≥ 100만원 → 기본 CPM × (1 + 0.05 × ⌊(예산-100만원)/100만원 + 1⌋)
노출수    = 예산 ÷ 실제 CPM × 1,000
클릭수    = 노출수 × CTR
전환수    = 클릭수 × CVR
ROAS     = (전환수 × AOV ÷ 예산) × 100
손익분기  = (1 ÷ 마진율) × 100
```

> CPM 상승 로직은 예산 확대 시 경쟁 입찰 증가로 CPM이 오르는 실무 현상을 반영한 자체 설계값입니다. 실제 플랫폼 데이터 기반이 아닌 시뮬레이션 목적임을 명시합니다.

---

## KPI 기준값 출처

| 카테고리 | 지표 | 수치 | 출처 |
|---|---|---|---|
| 패션 | CTR 평균 | 2.84% | Lebesgue 2026 |
| 패션 | Instagram Reels CTR | 3.1% | MHI Growth Engine 2026 |
| 패션 | Instagram Feed CVR | 3.4% | MHI Growth Engine 2026 |
| 패션 | ROAS 중앙값 | 218% | AdAmigo.ai 2026 |
| 뷰티 | Instagram Stories CTR | 3.1% | MHI Growth Engine 2026 |
| 뷰티·패션 | CVR 범위 | 2~3% | Triple Whale 2025 |

> 시뮬레이터 기준값은 업계 평균 대비 보수적으로 설정되었습니다.

---

## 기술 스택

| 항목 | 내용 |
|---|---|
| Language | HTML · CSS · JavaScript |
| 배포 | GitHub Pages |

---

## 포트폴리오 연결

- [검색 트렌드 대시보드](https://trend-dashboard-tap.streamlit.app) — 이 시뮬레이터의 KPI 수치 도출 근거 데이터 분석
- [뷰티 브랜드 캠페인 기획서](https://drive.google.com/file/d/1ycQZGCR2f9fJDtghe0IE1xCbBHAoQhCR/view?usp=sharing) — Meta Ads KPI 시뮬레이션 포함
- [패션 브랜드 캠페인 기획서](https://drive.google.com/file/d/1kFHbhB6amNispbV4QTFM8f2e1Lov_-hU/view?usp=sharing) — Meta Ads KPI 시뮬레이션 포함
