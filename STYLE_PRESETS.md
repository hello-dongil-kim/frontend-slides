# Style Presets Reference — NAVER Core Context (NCC)

모든 프리셋은 **NAVER Core Context**를 따른다. 개별 프리셋은 서비스 맥락(Basic/Brand 폰트, Light/Dark 모드, 카드 레이아웃, 강조 토큰)에 따라 분기되지만, 단일 디자인 시스템 위에서 동작한다.

**Viewport CSS:** 필수 기반 스타일은 [viewport-base.css](viewport-base.css) 참조. 모든 프레젠테이션에 포함.

---

## NCC 공통 규칙 (모든 프리셋 공통)

| 규칙 | 값 |
|------|-----|
| letter-spacing | **-0.3px (전 크기 공통, 예외 없음)** |
| 폰트 패밀리 | Pretendard(Basic) 또는 NanumSquare Neo(Brand) |
| 카드 radius | 12px (`m`) |
| 버튼·입력 radius | 8px (`s`) |
| Pill/아바타 radius | 999px (`full`) |
| Stroke 설정 | **Inside만 사용** (Center/Outside 금지) |
| 깊이 표현 | **배경색 계층(base→default→raised)** — drop-shadow 금지 |
| 터치 타겟 | 최소 44×44px |
| 레이아웃 | `clamp()` 기반 Fluid — 고정 breakpoint 금지 |
| 다크 모드 | 모든 색상 토큰에 Light/Dark 쌍 필수 |

**CSS 변수 네임스페이스 템플릿:**
```css
:root {
  /* 배경 계층 */
  --bg-base: #F0F0F0;        /* 페이지 기본 */
  --bg-default: #FFFFFF;     /* 카드 */
  --bg-raised: #F8F9FA;      /* 상위 구분 영역 */
  --bg-inverted: #1C1C1C;

  /* 텍스트 계층 */
  --fg-default: #000000;
  --fg-subtle-1: #2E2E2E;
  --fg-subtle-2: #424242;
  --fg-decorative: #A3A3A3;
  --fg-inverted: #FFFFFF;
  --fg-disabled: rgba(0,0,0,0.2);

  /* Primary — NAVER Green */
  --primary-default: #03A94D;       /* UI CTA */
  --primary-decorative: #03C75A;    /* 브랜드 장식 전용 */
  --primary-subtle: #E6F9EE;        /* 뱃지/태그 */

  /* Secondary — Blue (정보/링크) */
  --secondary-default: #3283FD;
  --link-mobile: #0068C3;

  /* 상태 */
  --positive: #03A94D;
  --positive-subtle: #E6F9EE;
  --negative: #F4361E;
  --negative-subtle: #FEEBE8;
  --informative: #3283FD;
  --attention: #D6A323;

  /* 선 */
  --stroke-subtle: rgba(0,0,0,0.10);
  --stroke-divider: rgba(0,0,0,0.08);
  --stroke-focus: #000000;
  --stroke-activated: rgba(0,0,0,0.80);

  /* 상태 레이어 */
  --hover-soft: rgba(0,0,0,0.06);
  --pressed-soft: rgba(0,0,0,0.15);
  --backdrop-1: rgba(0,0,0,0.40);
  --backdrop-2: rgba(0,0,0,0.50);

  /* Radius */
  --r-s: 8px;
  --r-m: 12px;
  --r-l: 16px;
  --r-full: 999px;

  /* Spacing (8px 기본) */
  --sp-sm: 8px;
  --sp-md: 12px;
  --sp-lg: 16px;
  --sp-xl: 20px;
  --sp-2xl: 24px;
  --sp-3xl: 32px;
}

[data-theme="dark"] {
  --bg-base: #131313;
  --bg-default: #1F1F1F;
  --bg-raised: #2D2D2D;
  --bg-inverted: #F8F8F8;
  --fg-default: #FFFFFF;
  --fg-subtle-1: #F1F1F1;
  --fg-subtle-2: #E7E7E7;
  --fg-decorative: #AAAAAA;
  --fg-inverted: #131313;
  --fg-disabled: rgba(255,255,255,0.3);
  --primary-default: #05AC4F;
  --primary-decorative: #03C75A;
  --primary-subtle: #112E1E;
  --secondary-default: #3283FD;
  --link-mobile: #5FA5F8;
  --positive: #03C75A;
  --positive-subtle: #112E1E;
  --negative: #FF5D49;
  --negative-subtle: #431C18;
  --informative: #5196FD;
  --attention: #FCC029;
  --stroke-subtle: rgba(255,255,255,0.10);
  --stroke-divider: rgba(255,255,255,0.08);
  --stroke-focus: #FFFFFF;
  --stroke-activated: rgba(255,255,255,0.90);
  --hover-soft: rgba(255,255,255,0.10);
  --pressed-soft: rgba(255,255,255,0.20);
}

html { font-family: 'Pretendard', system-ui, sans-serif; letter-spacing: -0.3px; }
```

---

## Light Themes — Pretendard (Basic)

### 1. NCC Base Card

**Vibe:** 기본형, 친근, 균형, 네이버 서비스 표준

**Layout:** `bg-base` 페이지 위에 `bg-default` 카드 1개. 카드 내 헤딩 상단, 본문 중앙, CTA 하단.

**Typography:**
- Display: Pretendard 700 (`display.medium` 32px / `display.small` 28px)
- Heading: Pretendard 600 (`heading.large` 22px)
- Body: Pretendard 400 (`paragraph.medium` 16px, line-height 25px)

**Colors:**
- 배경: `var(--bg-base)` → 카드 `var(--bg-default)` → 내부 구분 `var(--bg-raised)`
- 텍스트: `var(--fg-default)` / 보조 `var(--fg-subtle-2)`
- CTA: `var(--primary-default)` 배경, `#FFFFFF` 텍스트

**Signature Elements:**
- 카드 radius 12px, stroke 1px inside `var(--stroke-subtle)`
- Primary CTA 높이 48px, radius 8px
- 구분선 1px `var(--stroke-divider)` — 섹션 분할

---

### 2. NCC Minimal

**Vibe:** 절제, 여백, 읽기 중심

**Layout:** 카드 없이 `bg-base` 배경 직접 사용. 중앙 정렬 텍스트 블록. 좌우 `clamp(0px, calc(-240px + 53.333vw), 80px)` 패딩.

**Typography:**
- Display: Pretendard 700 `display.large` 40px, line-height 48px
- Body: Pretendard 400 `paragraph.medium` 16px

**Colors:**
- 배경: `var(--bg-base)` 단일
- 텍스트: `var(--fg-default)` 헤딩 / `var(--fg-subtle-1)` 본문

**Signature Elements:**
- 그림자·보더 전무 — 텍스트만으로 리듬
- 섹션 구분은 `var(--stroke-divider)` 1px 수평선만
- 인라인 링크는 `var(--primary-default)` 색상 (밑줄 없음)

---

### 3. NCC Editorial

**Vibe:** 에디토리얼, 구조적, 정보 중심

**Layout:** 2단 그리드. 좌측 `var(--bg-raised)` 썸네일/이미지(radius 12px, inset 이미지 radius 4px), 우측 `var(--bg-default)` 텍스트 블록.

**Typography:**
- Display: Pretendard 700 `display.small` 28px
- Heading: Pretendard 600 `heading.medium` 20px
- Body: Pretendard 400 `paragraph.small` 15px, line-height 24px
- Caption: Pretendard 600 `label.xSmall` 14px, `var(--fg-decorative)`

**Colors:**
- 페이지 `var(--bg-base)` → 콘텐츠 컨테이너 `var(--bg-default)` → 이미지 박스 `var(--bg-raised)`
- 태그/뱃지: `var(--primary-subtle)` 배경, `var(--primary-default)` 텍스트

**Signature Elements:**
- Inset Radius Formula 엄격 적용 (이미지 내부 4px)
- 메타 정보 라인 (날짜·저자·카테고리) — `detail.medium` 12px, `var(--fg-decorative)`
- Pill 카테고리 태그 (radius 999px, `var(--primary-subtle)`)

---

### 4. NCC Info Highlight

**Vibe:** 정보성, 안내, 링크 중심

**Layout:** 카드 상단에 Secondary Blue 배지, 하단에 정보성 CTA.

**Typography:**
- Heading: Pretendard 600 `heading.large` 22px
- Body: Pretendard 400 `paragraph.medium` 16px
- Link: Pretendard 600 `label.medium` 16px, `var(--link-mobile)`

**Colors:**
- 카드: `var(--bg-default)`
- 강조 배지: `var(--secondary-default)` 배경 (`#3283FD`), `#FFFFFF` 텍스트
- 링크 텍스트: `var(--link-mobile)` (`#0068C3`)
- 정보성 CTA: `var(--secondary-default)` 배경

**Signature Elements:**
- 좌측 4px 수직 액센트 바 `var(--secondary-default)` — 정보 섹션 마커
- 링크는 `underline` 기본, hover 시 색상 변화 없이 밑줄만 진해짐
- "i" 아이콘 원형 뱃지 — 18×18px, `var(--informative)`

---

### 5. NCC Status Grid

**Vibe:** 대시보드, 상태 요약, 기능성

**Layout:** 3×2 또는 2×2 카드 그리드. `auto-fill, minmax(min(33%, 160px), 1fr)`.

**Typography:**
- Heading: Pretendard 600 `heading.small` 19px
- Metric: Pretendard 700 `display.xSmall` 24px
- Label: Pretendard 600 `label.xSmall` 14px

**Colors (상태별 서브틀 활용):**
- 긍정 카드: `var(--positive-subtle)` 배경, `var(--positive)` 텍스트
- 부정 카드: `var(--negative-subtle)` 배경, `var(--negative)` 텍스트
- 정보 카드: 서브틀 블루(`rgba(50,131,253,0.10)`) 배경, `var(--informative)` 텍스트
- 주의 카드: 서브틀 옐로(`rgba(214,163,35,0.12)`) 배경, `var(--attention)` 텍스트

**Signature Elements:**
- 각 카드 상단 좌측에 상태 아이콘 (24×24px)
- 카드 radius 12px, stroke 없이 subtle 배경색만으로 구분
- 메트릭 숫자 + 델타 (예: `+12%` `var(--positive)`)

---

### 6. NCC Divider

**Vibe:** 섹션 분할, 문서형, 구조 명확

**Layout:** 수직 스택. 각 섹션 상단에 섹션 번호(`01` `02`), 중앙에 헤딩과 본문, 섹션 간 1px `var(--stroke-divider)`.

**Typography:**
- Section Number: Pretendard 600 `label.medium` 16px, `var(--fg-decorative)`
- Heading: Pretendard 700 `display.xSmall` 24px
- Body: Pretendard 400 `paragraph.medium` 16px

**Colors:**
- 배경: `var(--bg-default)` 단일
- 구분선: `var(--stroke-divider)`

**Signature Elements:**
- 섹션 번호는 모노스페이스 느낌 (Pretendard의 `tnum` feature 활용)
- 하단 페이지 번호 `var(--fg-decorative)` — Safe Area 하단 패딩 포함
- 인라인 강조 키워드는 `var(--primary-default)` 색상만 (bold 추가 금지)

---

## Dark Themes — Pretendard (Basic)

### 7. NCC Dark Base

**Vibe:** 다크 기본, 야간 가독성

**Layout:** `bg-base` (`#131313`) → `bg-default` (`#1F1F1F`) 카드 → `bg-raised` (`#2D2D2D`) 내부 구분.

**Typography:** NCC Base Card와 동일 (Pretendard 700/600/400)

**Colors:**
- 텍스트: `#FFFFFF` / `#F1F1F1` / `#E7E7E7`
- CTA: `#05AC4F` (dark primary) 배경
- 구분선: `rgba(255,255,255,0.08)`

**Signature Elements:**
- Stroke `rgba(255,255,255,0.10)` inside
- Hover 상태 레이어 `rgba(255,255,255,0.10)`
- Pressed `rgba(255,255,255,0.20)`

---

### 8. NCC Dark Hero

**Vibe:** 임팩트, 발표 오프닝, 제품 히어로

**Layout:** 풀블리드 `bg-base` 다크 배경, 중앙 단일 `display.large` 헤드라인, 하단에 Decorative Green 액센트 바 또는 CTA.

**Typography:**
- Display: Pretendard 700 `display.large` 40px, line-height 48px
- Subtitle: Pretendard 400 `paragraph.medium` 16px, `var(--fg-subtle-1)`

**Colors:**
- 배경: `#131313` 단일 (그라디언트 금지 — NCC 배경 계층 원칙)
- 헤드라인: `#FFFFFF`
- 액센트: `var(--primary-decorative)` (`#03C75A`) — 브랜드 모멘트에만

**Signature Elements:**
- 상단 상태 바 영역 Safe Area 처리 (`env(safe-area-inset-top)`)
- 좌측 하단 네이버 브랜드 심볼 위치 (발표 일관성)
- 배경은 **단색** — 비네트/그라디언트/파티클 금지

---

### 9. NCC Dark Split

**Vibe:** 대비, 비교, Before/After

**Layout:** 수직 50:50 스플릿. 좌측 `bg-inverted.1` (`#F8F8F8`, 다크모드에선 밝은 패널), 우측 `bg-base` (`#131313`).

**Typography:**
- Heading: Pretendard 600 `heading.large` 22px (양 패널 동일)
- Body: Pretendard 400 `paragraph.small` 15px

**Colors:**
- 좌측 패널: 밝은 배경 + 다크 텍스트 (`#131313`)
- 우측 패널: 다크 배경 + 밝은 텍스트 (`#FFFFFF`)

**Signature Elements:**
- 패널 사이 구분선 없음 — 색상 대비만으로 분할
- 각 패널 상단에 라벨 (`LIGHT` / `DARK`, `label.xSmall` 14px, `var(--fg-decorative)`)
- 중앙에 선택적 미니 배지 "vs" (radius 999px)

---

### 10. NCC Dark Info

**Vibe:** 다크 정보성, 야간 안내

**Layout:** NCC Info Highlight 다크 변형. Secondary Blue 액센트 유지.

**Typography:** Pretendard 600/400

**Colors:**
- 카드: `#1F1F1F`
- 링크: `#5FA5F8` (다크 모바일 링크)
- 배지: `#3283FD` 배경, `#FFFFFF` 텍스트
- 정보 아이콘: `var(--informative)` (`#5196FD`)

**Signature Elements:**
- 좌측 4px 수직 액센트 바 `#5196FD`
- 인포 박스는 `rgba(81,150,253,0.12)` 서브틀 배경

---

## Brand Themes — NanumSquare Neo

### 11. NCC Brand Hero

**Vibe:** 브랜드 선언, 행사 타이틀, 공식 발표

**Layout:** 풀 히어로. 중앙 NanumSquare Neo 800 헤드라인, Decorative Green 액센트.

**Typography:**
- Display: **NanumSquare Neo 800** `display.large` 40px — NCC의 "Brand 폰트 히어로는 800 기본" 규칙 적용
- Subtitle: NanumSquare Neo 400 `paragraph.medium` 16px

**Colors:**
- 배경: `var(--bg-default)` (`#FFFFFF` L / `#1F1F1F` D)
- 헤드라인: `var(--fg-default)`
- 액센트 키워드: `var(--primary-decorative)` (`#03C75A`) — 브랜드 장식 전용
- 선택적 브랜드 그린 배경 블록: `var(--primary-decorative)` + 흰 텍스트

**Signature Elements:**
- 브랜드 폰트 전용 — Pretendard와 혼용 금지
- 자간 유지 -0.3px (브랜드 폰트에도 동일 적용)
- 네이버 브랜드 심볼 또는 로고 영역 (좌측 상단 또는 우측 하단)

---

### 12. NCC Brand Event

**Vibe:** 이벤트, 프로모션, 축제성

**Layout:** `primary-decorative` (`#03C75A`) 풀 배경 + 흰 텍스트 히어로 슬라이드 / 또는 `bg-default` + 그린 박스 콤비네이션.

**Typography:**
- Event Title: **NanumSquare Neo 800** 40px
- Sub Headline: NanumSquare Neo 700 `display.xSmall` 24px
- Body: NanumSquare Neo 400 `paragraph.medium` 16px

**Colors:**
- 히어로 배경: `#03C75A` (Decorative Green 풀블리드)
- 히어로 텍스트: `#FFFFFF`
- 카드 섹션: `var(--bg-default)` + `var(--stroke-subtle)` inside

**Signature Elements:**
- 날짜·장소 메타 박스 — 흰 카드 radius 12px, 그린 배경 위에 떠 있는 구조
- CTA는 **인버트 처리**: 흰 배경 + 그린 텍스트 (브랜드 맥락에서 CTA 강조)
- Pill 카테고리 태그 활용 (라이브/온라인/오프라인 등)

---

## 폰트 패밀리 빠른 참조

| Preset | Display Font | Body Font | 폰트 구분 | 모드 |
|--------|--------------|-----------|----------|------|
| 1. NCC Base Card | Pretendard 700 | Pretendard 400 | Basic | Light |
| 2. NCC Minimal | Pretendard 700 | Pretendard 400 | Basic | Light |
| 3. NCC Editorial | Pretendard 700 | Pretendard 400 | Basic | Light |
| 4. NCC Info Highlight | Pretendard 700 | Pretendard 400 | Basic | Light |
| 5. NCC Status Grid | Pretendard 700 | Pretendard 400 | Basic | Light |
| 6. NCC Divider | Pretendard 700 | Pretendard 400 | Basic | Light |
| 7. NCC Dark Base | Pretendard 700 | Pretendard 400 | Basic | Dark |
| 8. NCC Dark Hero | Pretendard 700 | Pretendard 400 | Basic | Dark |
| 9. NCC Dark Split | Pretendard 700 | Pretendard 400 | Basic | Dark↔Light |
| 10. NCC Dark Info | Pretendard 700 | Pretendard 400 | Basic | Dark |
| 11. NCC Brand Hero | NanumSquare Neo 800 | NanumSquare Neo 400 | Brand | Light/Dark |
| 12. NCC Brand Event | NanumSquare Neo 800 | NanumSquare Neo 400 | Brand | Brand Green |

**폰트 로드 예시:**
```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/static/pretendard.css">
<link rel="stylesheet" href="https://hangeul.pstatic.net/hangeul_static/css/nanum-square-neo.css">
```

---

## 빠른 컬러 레퍼런스

| 역할 | Light | Dark |
|------|-------|------|
| 페이지 배경 (base) | `#F0F0F0` | `#131313` |
| 카드 배경 (default) | `#FFFFFF` | `#1F1F1F` |
| 상위 구분 (raised.1) | `#F8F9FA` | `#2D2D2D` |
| 기본 텍스트 | `#000000` | `#FFFFFF` |
| 보조 텍스트 | `#2E2E2E` | `#F1F1F1` |
| 비활성 텍스트 | `#A3A3A3` | `#AAAAAA` |
| Primary CTA (UI Green) | `#03A94D` | `#05AC4F` |
| Decorative Green (브랜드) | `#03C75A` | `#03C75A` |
| Secondary Blue | `#3283FD` | `#3283FD` |
| Link (Mobile) | `#0068C3` | `#5FA5F8` |
| 에러 (Negative) | `#F4361E` | `#FF5D49` |
| 주의 (Attention) | `#D6A323` | `#FCC029` |
| 카드 보더 | `rgba(0,0,0,0.10)` | `rgba(255,255,255,0.10)` |
| 구분선 | `rgba(0,0,0,0.08)` | `rgba(255,255,255,0.08)` |
| Hover 오버레이 | `rgba(0,0,0,0.06)` | `rgba(255,255,255,0.10)` |
| Pressed 오버레이 | `rgba(0,0,0,0.15)` | `rgba(255,255,255,0.20)` |

---

## DO NOT USE (NCC 위반 패턴)

**컬러 hex 직접 사용 금지** — 반드시 토큰 또는 CSS 변수로 참조 (`var(--primary-default)`)

**UI Green과 Decorative Green 혼용 금지**
- UI Green `#03A94D` → Primary CTA 전용
- Decorative Green `#03C75A` → 브랜드 장식 전용

**다른 포인트 컬러 추가 금지** — 보라/핑크/오렌지 액센트 추가 불가. 상태 표현은 NCC 상태 토큰(positive/negative/informative/attention)만 사용.

**그림자 사용 금지** — drop-shadow, box-shadow로 elevation 표현 금지. 배경 계층(base→default→raised)만으로 깊이 표현.

**Stroke Center/Outside 금지** — Inside만 사용. 레이아웃 충돌 발생.

**weight 800 남용 금지** — Brand 폰트 히어로 영역에만 사용. 일반 본문 불가.

**Label과 Paragraph 혼용 금지** — 버튼 텍스트에 Paragraph 사용 불가. UI 요소=Label, 읽기 흐름=Paragraph.

**margin을 컴포넌트에 사용 금지** — 여백은 `padding`과 `gap`으로만 처리.

**letter-spacing 변경 금지** — 전 크기 공통 -0.3px. 예외 없음.

**고정 breakpoint 계단식 반응형 금지** — `clamp()` 기반 Fluid 레이아웃만 허용.

**Inset Radius Formula 미적용 금지** — 카드(12px) 내 이미지는 `12 - (padding/2)` 공식 적용. 예: padding 16px → 이미지 radius 4px.

---

## CSS Gotchas

### CSS 함수 음수 처리

**WRONG — 브라우저가 조용히 무시 (콘솔 에러 없음):**
```css
right: -clamp(28px, 3.5vw, 44px);   /* 무시됨 */
margin-left: -min(10vw, 100px);      /* 무시됨 */
```

**CORRECT — `calc(-1 * ...)` 래핑:**
```css
right: calc(-1 * clamp(28px, 3.5vw, 44px));  /* 정상 */
margin-left: calc(-1 * min(10vw, 100px));     /* 정상 */
```

CSS는 함수명 앞 `-`를 허용하지 않는다. 브라우저는 선언 전체를 버리고 에러도 안 띄운다. **항상 `calc(-1 * ...)` 사용.**

### Inset Radius 공식

중첩된 요소의 안쪽 반경 계산:
```
Outer R = Inner R + (Horizontal Padding / 2)
```

예: 카드 radius 12px, padding 16px → 내부 이미지 radius = 12 - (16/2) = **4px**

### 다크 모드 전환

`[data-theme="dark"]` 속성만으로 모든 토큰 전환. 별도 컴포넌트 작성 금지.

```html
<html data-theme="dark">
```

또는 시스템 선호 기반:
```css
@media (prefers-color-scheme: dark) {
  :root { /* dark tokens */ }
}
```

---

## AI 에이전트 프롬프트 예시

- "NCC Base Card 스타일로 소개 슬라이드. 배경 `#F0F0F0`, 중앙 카드 `#FFFFFF` radius 12px 1px stroke inside `rgba(0,0,0,0.10)`. 헤딩 Pretendard 700 32px, 본문 Pretendard 400 16px line-height 25px, letter-spacing -0.3px. 하단 CTA 높이 48px, 배경 `#03A94D`, 텍스트 `#FFFFFF`, radius 8px."

- "NCC Status Grid로 Q2 성과 4개 카드. 긍정(매출 +12%) `#E6F9EE` 배경 `#03A94D` 텍스트, 부정(이탈률 +3%) `#FEEBE8` 배경 `#F4361E` 텍스트, 정보(DAU) `rgba(50,131,253,0.10)` 배경 `#3283FD` 텍스트, 주의(리스크) `rgba(214,163,35,0.12)` 배경 `#D6A323` 텍스트. 각 카드 radius 12px, padding 20px, 헤딩 Pretendard 600 19px, 메트릭 Pretendard 700 24px, letter-spacing -0.3px."

- "NCC Brand Hero로 2026 네이버 컨퍼런스 오프닝. 배경 `#FFFFFF`, 중앙 헤드라인 NanumSquare Neo 800 40px '네이버다움의 확장', 서브타이틀 NanumSquare Neo 400 16px, 키워드 '경험' 색상 `#03C75A`, letter-spacing -0.3px. 좌측 상단 네이버 심볼, 하단 날짜/장소 메타 label.xSmall 14px `#A3A3A3`."

- "NCC Dark Base 카드 슬라이드. 배경 `#131313`, 카드 `#1F1F1F` radius 12px 1px stroke `rgba(255,255,255,0.10)` inside. 헤딩 Pretendard 700 28px `#FFFFFF`, 본문 Pretendard 400 16px `#F1F1F1` line-height 25px, letter-spacing -0.3px. CTA 배경 `#05AC4F` 텍스트 `#FFFFFF`."

---

## 반복 가이드 (매 슬라이드 체크)

1. **letter-spacing -0.3px** — 전 텍스트 예외 없이 적용
2. **배경 계층** — base → default → raised 순서로만 elevation 표현, 그림자 금지
3. **그린 분리** — UI Green(`#03A94D`) CTA만, Decorative Green(`#03C75A`) 브랜드만
4. **Radius** — 카드 12px, 버튼 8px, 아바타·필 999px
5. **Stroke** — Inside만, 1px `--stroke-subtle` 또는 2px `--stroke-focus`
6. **상태 레이어** — Hover 6%, Pressed 15% (Light 기준)
7. **다크 모드** — 모든 색상 토큰에 Light/Dark 쌍
8. **폰트 구분** — Basic(Pretendard)과 Brand(NanumSquare Neo) 동일 화면 혼용 금지
9. **Inset Radius** — 중첩 이미지/박스는 공식 `Outer - padding/2` 적용
10. **터치 타겟 44×44px** — 슬라이드 내 인터랙션 요소 포함 시 준수