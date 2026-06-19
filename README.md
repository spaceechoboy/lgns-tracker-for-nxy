# Origin LGNS — Tracker (Legacy)

Legacy 듀얼체인 트래커. 헤더 탭으로 **시세 · 자산 · 가계부 · 이율**을 전환하는 설치형(PWA) 단일 페이지.

라이브: https://spaceechoboy.github.io/lgns-tracker/

## 탭
- **시세** — Polygon·Anubis LGNS/USD 가격·DexTools 차트·프리미엄·매도세·환율·김프·메이저 코인·리베이스 카운트다운.
- **자산** — 지갑 주소 입력 → 온체인으로 체인별 **유동 LGNS + sLGNS + 장기 락업(360/600)** 자동 합산.
  평가는 합계×체인가격, 평균매수가는 수동(손익). 주소 없으면 수동 입력.
- **가계부** — 월별 자산 정리. 수동 거래행(수입/지출/매수/매도) → 이번달 수입·지출·순액 집계. 스테이킹 추적 카드 포함.
- **이율** — 듀얼체인 스테이킹 3종 이율(`rates.html`을 `?embed`로 임베드, 스크립트 격리).

## 온체인 read (자산 탭)
공개 RPC로 read-only. selectors: `balanceOf`·`getUserStakesCount`·`stakes`·`balanceForGons`·`extraInterest`.
Polygon 장기=balanceForGons 현재가치, Anubis 장기=원금+extraInterest. 키·서명·트랜잭션 없음.

## 구조
```
index.html      트래커 (4탭 SPA)
rates.html      이율 (이율 탭에 ?embed 임베드)
dashboard.html  (기존 16:9 시세 대시보드 — 유지)
assets/  shell.css · symbol.png      icons/  (PWA·파비콘)
manifest.json · sw.js · .nojekyll
```
빌드·번들 없음(vanilla). 디자인 ANUBIS NEON. 계산기는 별도 레포로 분리 예정.

---
SpaceEchoBoy
