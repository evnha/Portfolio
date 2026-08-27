# Handoff: 한은하 백엔드 개발자 포트폴리오

## Overview

한은하(Backend Engineer, 경력 4년 4개월)의 개인 포트폴리오 웹사이트입니다. 메가존클라우드에서 수행한 12개 프로젝트를 PAAR(Problem–Analyze–Action–Result) 구조로 소개하며, **핵심 성과 지표**·**문제 해결 스토리**·**실제 산출물(아키텍처 다이어그램, 화면설계서, 통합 가이드 등)**을 중심으로 구성되었습니다.

한 페이지 스크롤 구조이며, 상단 스티키 nav로 About / Achievements / Experience / Projects / Skills / Contact 섹션을 이동합니다. 이미지 산출물은 lightbox로 확대 가능합니다.

---

## About the Design Files

이 번들의 파일은 **HTML로 제작된 디자인 레퍼런스**입니다. 최종 픽셀·색상·타이포·인터랙션 의도를 시각화한 프로토타입이며, **그대로 배포하기 위한 프로덕션 코드가 아닙니다**.

작업의 목표는 이 HTML 디자인을 **대상 코드베이스의 기존 환경**(예: Next.js, React, Vue, Astro 등)에서 그 프로젝트의 관례·라이브러리를 활용해 **재구현**하는 것입니다. 아직 프론트엔드 환경이 없다면:

- **Next.js (App Router) + Tailwind CSS** — 정적 페이지 최적화, SEO 유리
- **Astro** — 개인 포트폴리오에 이상적 (거의 순수 정적 HTML 출력)

---

## Fidelity

**High-fidelity (hifi)** — 최종 색상·타이포·간격·인터랙션이 확정된 픽셀 퍼펙트 목업입니다. 아래 문서화된 정확한 hex 값·폰트·간격을 준수하여 재현하세요.

---

## Screens / Views

이 포트폴리오는 단일 페이지(Single Page)로, 6개 스크롤 섹션 + 상단 nav + 하단 footer + 전역 lightbox 오버레이로 구성됩니다.

### 0. Top Navigation (sticky)

- **Position**: `position: sticky; top: 0; z-index: 50`
- **Background**: `rgba(245, 241, 234, 0.85)` + `backdrop-filter: saturate(140%) blur(12px)`
- **Padding**: `18px 48px`
- **Border**: 스크롤 20px 이상일 때 `border-bottom: 1px solid var(--rule)` 활성화 (JS 클래스 `.scrolled`)
- **좌측 브랜드**: "한은하." — Noto Serif KR 600 / 17px / letter-spacing -0.01em. 마침표는 accent(#8B3A2E)
- **우측 링크** (gap 28px): About / Achievements / Experience / Projects / Skills / Contact
  - 12.5px, color var(--muted)
  - hover 시 var(--ink)
  - **active 상태** (스크롤 스파이): 하단 1px accent 언더라인
- **반응형** (≤900px): 상위 3개 링크만 노출

### 1. Hero

- **Padding**: `80px 0 100px`
- **Layout**: 2-column grid `1fr 340px`, gap 80px, `align-items: end`

**좌측(lede)**
- Eyebrow row: `─── BACKEND ENGINEER · 2021–2025` (40px 라인 + 대문자 스페이싱 캡션 11px)
- **H1 "한은하."**: Noto Serif KR 500 / `clamp(72px, 11vw, 148px)` / lh 0.94 / ls -0.035em. 마침표는 accent + italic 400
- **Subtitle**: "복잡한 도메인을 *확장 가능한 아키텍처*로<br />풀어내는 백엔드 개발자입니다." — Serif 300 / `clamp(20px, 2.4vw, 28px)` / lh 1.4. `em`은 italic + accent
- **Contact row** (상단 border 1px rule):
  - Email: heh970708@gmail.com (mono 13.5px, mailto 링크)
  - Focus: "SaaS · MSA · Event-Driven"

**우측(side, 좌측 rule 구분)**
- Quick facts 5개 (label/value flex-between, gap 24px):
  - Experience — 4년 4개월
  - Company — 메가존클라우드
  - Projects — 12+
  - SaaS Integrated — 118 services
  - Events / Day — 200K events
- 값은 Serif 500 / 22px

### 2. About (§ 01)

- **Padding**: `120px 0`, `border-top: 1px solid var(--rule)`
- **Header (sec-head)**: 2-column `200px 1fr`
  - 좌: "§ 01 — ABOUT" mono 캡션 + 40px 검정 rule
  - 우: H2 "문제를 정의하고,<br /><em>구조로 답합니다.</em>" — Serif 500 / clamp(40px, 5vw, 60px)
- **Body**: 2-column `200px 1fr` grid
  - **Lede 문단** (드롭캡): 첫 글자를 float-left Serif 500 / 78px / accent. 본문 Serif 400 / 22px / lh 1.55
    > 400개 이상의 SaaS를 다루는 통합 관리 플랫폼과 AWS 기반 분석 환경 플랫폼을 구축하며, MSA 환경에서의 서비스 설계, 이벤트 기반 비동기 처리, 대규모 데이터 처리 및 SaaS 연동 아키텍처를 설계·개발해 왔습니다. 또한 MVC 기반 웹 서비스부터 MSA 환경까지 다양한 시스템 구조를 경험하며, **문제의 본질**과 **측정 가능한 결과**를 먼저 정의하고, 이를 바탕으로 시스템을 설계하고 개선합니다.
  - **3 Principles grid** (repeat(3, 1fr), gap 32px, 상단 rule):
    1. "문제부터 정의합니다"
    2. "확장 가능한 구조를 선택합니다"
    3. "결과를 숫자로 증명합니다"

### 3. Achievements (§ 02)

- **Header**: "숫자로 남긴 *흔적*들" + 설명문
- **Stats grid**: 4×2, 위/아래 `border: 1px solid var(--ink)`, 셀 간 rule 구분
- 큰 숫자: Serif 500 / 56px / ls -0.03em
- unit(`개`, `%`, `/일`)은 Serif 400 / 24px / accent
- 8개 지표 (SSO 118 / Integration 40+ / Event 200K/일 / History 100% / Delivery 5일→4h / Operation 80% / License 10K+ / Infra 100%)

### 4. Experience (§ 03)

- **Header**: "경력 *요약*"
- **Body** (200px | 1fr grid):
  - **Company card**: 메가존클라우드 + role + dates
  - **Era grid** (2 columns, gap 48px):
    - 2022.10–2025.06 · SaaS 통합 관리 플랫폼(Megazone PoPs) 구축
    - 2021.02–2022.09 · AWS 기반 DDM 구축
  - **Infrastructure block** (Era 아래, 상단 rule로 구분):
    - **Grid**: `240px 1fr`, gap 40px, `margin-top: 40px`, `padding-top: 28px`
    - 좌: eyebrow "Infrastructure" (mono 10px muted uppercase) + 제목 "Megazone PoPs *네트워크 구성*" (Serif 500 / 18px) + 짧은 설명 "AWS EKS·Aurora·API Gateway 기반의 3-AZ 서비스 인프라입니다." (12.5px muted)
    - 우: `.infra-figure` — 크림톤 배경 카드 (paper-2 배경, 1px rule border, padding 12px), 내부에 네트워크 구성도 이미지, hover 시 "확대 ↗" mono 캡션이 우상단 페이드인
    - **클릭 시 lightbox**로 `assets/네트워크구성도.png` 원본 크기 확대

### 5. Projects (§ 04) — 타임라인

12개 프로젝트를 최신순으로 세로 타임라인에 정렬.

- **Timeline container**: `padding-left: 240px`, 왼쪽에 세로 rule `left: 200px` (1px var(--rule))
- **Project card**:
  - `padding: 0 0 72px 48px`
  - **Dot** (::before): `left: -46px`, `top: 12px`, 9×9px + 1.5px border ink
  - **Highlight dot** (`.highlight`): 배경/border accent, `box-shadow: 0 0 0 4px var(--paper), 0 0 0 5px var(--accent)`
  - **Dateline** (절대 위치): `left: -240px`, width 170px, text-align right (range 12px mono ink 500 + duration 11px muted-2)
  - **제목**: Serif 500 / 26px / lh 1.3, `em`은 italic accent
  - **Results 블록**: 상하 rule, `grid-template-columns: repeat(auto-fit, minmax(160px, 1fr))`
    - 큰 숫자: Serif 500 / 34px / ls -0.025em
    - Unit/plus: Serif 400 / 18px / accent
  - **Problem 문단**: Serif 400 / 15.5px / lh 1.7 / ink-2. 앞에 인라인 "문제" 태그 (Sans 10.5px 500 accent uppercase)
  - **Tech tags**: mono 10.5px, 배경 paper-2, padding 4px 10px, radius 2px
  - **Artifacts 블록** (선택, `p.artifacts` 있을 때만 렌더):
    - 상단 `1px dashed var(--rule)` 구분선
    - 헤더: `◆ Artifacts · 산출물` (mono 10.5px accent uppercase, ls 0.14em)
    - **Grid**: `repeat(auto-fit, minmax(220px, 1fr))`, gap 16px
    - **`.arti-card`**: paper-2 배경 + 1px rule border + padding 12px 12px 14px
      - `.arti-thumb`: aspect-ratio 4/3, 배경 #FAF6EE (또는 dark 클래스는 #12100E), 이미지 object-fit contain
      - hover 시 border → accent, 배경 → paper, translateY(-1px)
      - hover 시 "확대 ↗" mono 캡션 페이드인
    - `.arti-title`: Serif 500 / 14px
    - `.arti-cap`: mono 10px muted uppercase
    - 클릭 시 `openLightbox(pi, ai)` 호출
  - **"자세히 보기" 토글 버튼**: 12px muted, pill(999px), hover 시 ink + paper-2 배경. 우측 `↓` arrow (open 시 180° 회전)
  - **접힘 상세** (`.prj-detail`): max-height 0 → 3000px, transition 0.5s ease
    - 2-column grid (gap 40px): **Analyze — 대안 검토** / **Action — 실행**
    - 각 헤더: mono 10.5px accent uppercase + 하단 1px rule
    - list: `counter(item, decimal-leading-zero)` (01, 02…), Sans 13.5px

**12개 프로젝트** (최신순 정렬, 실제 데이터는 `PROJECTS` 배열 참조):

| # | 기간 | 제목 | Highlight | Artifacts |
|---|---|---|---|---|
| 1 | 2025.04–06 | 앱 인스턴스 할당·회수 이력 관리 시스템 구축 | ✓ | — |
| 2 | 2023.07–2025.04 | SaaS 통합 서비스 구축 및 유지보수 | ✓ | 클래스 다이어그램(dark) + M365 통합 가이드 |
| 3 | 2022.10–2025.04 | SaaS 비용·구독·라이선스 통합 관리 | ✓ | — |
| 4 | 2025.03 | App Discovery 및 Shadow IT 탐지 고도화 | | — |
| 5 | 2023.10–2025.05 | SaaS 운영 통합 대시보드 구축 | | — |
| 6 | 2024.08–09 | 워크스페이스 관리자 역할·권한 개선 | | — |
| 7 | 2024.08–09 | SaaS 통합 서비스 야놀자 PoC | | — |
| 8 | 2024.05–08 | Workflow Automation 시스템 구축 | ✓ | — |
| 9 | 2023.06–2024.08 | SaaS SSO 기반 통합 인증 | ✓ | — |
| 10 | 2023.05–2024.04 | 로그인 장애 분석 및 대응 | | — |
| 11 | 2023.02–03 | Browser Extension SaaS 자동 로그인 | | — |
| 12 | 2021.02–2022.09 | AWS 기반 DDM 구축 | ✓ | 화면설계서 로그인 + 대시보드 |

### 6. Skills (§ 05)

- **Grid**: 2 columns, 각 skill-group `padding: 32px 32px 32px 0`, 상단 1px rule
- 오른쪽 열: `padding-left: 32px`, `border-left: 1px solid var(--rule)`
- **각 skill-group** (140px | 1fr grid):
  - 좌: 카테고리 Serif 500 / 20px + 하단 mono 10px muted-2 uppercase 서브라벨
  - 우: `<span>` 배지들, gap 6px 8px
    - 기본: mono 12px ink-2, 배경 paper-2, padding 5px 10px, radius 2px
    - **`.primary`**: 배경 var(--ink), 텍스트 var(--paper)

**9개 카테고리**:
1. **Language / Backend**: `Java 11*`, `Kotlin 1.9.25*`, Java 8
2. **Framework / Server**: `Spring Boot 2.3.4*`, `Spring Boot 3.3.5*`, Spring Security, JPA/Hibernate, MyBatis, JSP
3. **Frontend / Client**: JavaScript, jQuery, HTML
4. **Database / Storage**: `MySQL 8.0.40*`, `PostgreSQL 16.4*`, MariaDB
5. **Cloud · Infra / AWS**: `AWS SQS*`, `AWS Lambda*`, `EventBridge*`, EC2, VPC, IAM, S3, Redshift, Athena, SageMaker, `Terraform*`
6. **Auth · Protocol / Identity**: `OAuth 2.0*`, `OIDC*`, `SAML 2.0*`, SCIM, Bearer Token, API Key
7. **Monitoring · Ops / Observability**: Datadog, ArgoCD, Slack, Confluence
8. **Architecture / Design**: `MSA*`, `Clean Architecture*`, `Event-Driven*`, Template Method, RBAC
9. **Concurrency / Performance**: ExecutorService, Fixed Thread Pool, ShedLock, SQL 최적화

(* = primary 배지)

### 7. Contact (§ 06)

- **Padding**: `140px 0 100px`, 상단 rule, text-align center
- **Eyebrow**: "§ 06 — CONTACT"
- **H2**: "함께 *이야기*해요." — Serif 400 / clamp(48px, 7vw, 92px)
- **Mail link**: heh970708@gmail.com — Serif 400 / clamp(24px, 3vw, 36px), 하단 1px ink border, hover 시 accent
- **Sub**: "보통 24시간 이내에 회신드립니다." — Serif italic 14px muted

### 8. Footer

- Padding 32px 0, 상단 rule, flex-between
- 좌: "© 2026 · HAN EUN HA" (mono 11.5px muted-2)
- 우: "DESIGNED WITH INTENT"

### 9. Lightbox (전역)

`.lightbox#lightbox` — fixed inset:0, z-index 100

- **Backdrop**: `rgba(20, 16, 14, 0.92)`
- **표시 방식**: 초기 `display: none`, `.open` 클래스 시 `display: flex + opacity 1` (transition 0.25s)
- **이미지**: `max-width: 100%`, `max-height: calc(100vh - 120px)`, `box-shadow: 0 40px 100px rgba(0,0,0,0.5)`, background paper
- **Caption** (하단 24px, 중앙): Serif 15px paper, `<small>`은 mono 10.5px muted-2 uppercase
- **Close 버튼** (우상단 24/32): Serif 28px paper, 1px paper/30% border, hover 시 border/background 강조
- **닫기 트리거**: 이미지 외부 클릭 / ESC 키 / X 버튼

---

## Interactions & Behavior

### Scroll Spy Navigation
- `window.scrollY > 20`일 때 nav에 `.scrolled` 클래스 추가 (하단 border 활성화)
- `y + window.innerHeight * 0.35` 지점에 가장 가까운 섹션의 nav 링크에 `.active` 클래스
- 클릭 시 `scroll-behavior: smooth`로 부드러운 스크롤

### Project Detail Toggle
- 각 카드 "자세히 보기" 버튼 클릭 시 `.project`에 `.open` 토글
- `.prj-detail`: `max-height 0 → 3000px`, transition 0.5s ease
- 화살표: `rotate(180deg)` transition 0.3s
- 라벨 텍스트: "대안·행동 자세히 보기" ↔ "접기"

### Artifact Lightbox
- **개별 카드**: `openLightbox(pi, ai)` — 프로젝트 index + artifact index
  - `PROJECTS[pi].artifacts[ai]`에서 `src`, `title`, `cap`, `alt` 조회
  - `body.style.overflow = 'hidden'` 처리 (스크롤 잠금)
- **인프라 다이어그램**: `openInfraLightbox()` — 하드코딩된 네트워크구성도 표시
- **공통 닫기**: `closeLightbox()` — 클래스 제거, body overflow 복원, ESC 키 리스너

### Reveal on Scroll
- `IntersectionObserver` (threshold 0.08, rootMargin `0px 0px -40px 0px`)
- 대상: `.stat, .project, .principle, .era-card, .skill-group`
- 초기: `opacity: 0`, `transform: translateY(16px)`
- `.in`: `opacity: 1`, `transform: none`, transition 0.8s ease

### Responsive (≤900px)
- wrap padding 48px → 24px
- Nav의 Experience/Projects/Skills/Contact 링크 숨김
- Hero grid 단일 컬럼, side는 상단 rule 구분
- Stats 4→2 컬럼
- Timeline: `padding-left: 32px`, dot `left: -20px`, dateline은 static으로 재배치 (flex row)
- Skill grid 단일 컬럼
- **Infra block**: 단일 컬럼, gap 20px, padding 축소
- **Arti-grid**: 단일 컬럼, gap 12px
- **Lightbox**: padding 20px, close 버튼 크기 축소
- Section padding 120px → 72px

---

## State Management

프론트엔드 상태는 최소:
- **nav.scrolled** — window scroll 파생
- **nav a.active** — window scroll 파생 (섹션별 offsetTop 비교)
- **project.open** — 각 프로젝트별 독립 토글
- **element.in** — IntersectionObserver 콜백
- **lightbox.open** + **현재 표시 이미지** — 클릭 시 활성화, body overflow 잠금

React/Vue 등에서 구현 시:
```tsx
const [scrolled, setScrolled] = useState(false);
const [activeSection, setActiveSection] = useState<string>('about');
const [openProjects, setOpenProjects] = useState<Set<number>>(new Set());
const [lightbox, setLightbox] = useState<{src: string, title: string, cap: string} | null>(null);
```

데이터 페칭 없음 — 모든 콘텐츠 정적. `PROJECTS` 배열을 별도 `projects.ts`로 분리 권장.

---

## Design Tokens

### Colors
```css
--paper:    #F5F1EA;  /* main background (warm cream) */
--paper-2:  #EEE8DD;  /* tag/artifact/infra card background */
--paper-3:  #E4DCCC;  /* (reserved) */
--ink:      #1A1614;  /* primary text, thick rules */
--ink-2:    #3D342C;  /* secondary text */
--muted:    #6B5F52;  /* meta text */
--muted-2:  #8F8375;  /* faintest text */
--rule:     #D6CCBB;  /* hairline dividers */
--rule-2:   #C4B8A3;  /* (reserved) */
--accent:       #8B3A2E;  /* deep burgundy — em, unit, dot highlight, artifact accent */
--accent-soft:  #A85040;  /* (reserved) */
--good:         #4A6B3A;  /* (reserved) */
```

### Typography
- **Serif** (제목, 큰 숫자, 리드): `"Noto Serif KR", "Nanum Myeongjo", serif`, weights 300/400/500/600/700/900
- **Sans** (본문): `"Pretendard Variable", Pretendard, -apple-system, sans-serif`
- **Mono** (태그, 수치, 캡션, artifact 캡션): `"JetBrains Mono", ui-monospace, "SF Mono", Menlo, monospace` — `font-variant-numeric: tabular-nums`

**Type Scale**:
- H1 Hero: `clamp(72px, 11vw, 148px)` / 500 / lh 0.94 / ls -0.035em
- H2 Section: `clamp(40px, 5vw, 60px)` / 500 / lh 1 / ls -0.02em
- H2 Contact: `clamp(48px, 7vw, 92px)` / 400 / lh 1.1 / ls -0.025em
- H3 Company: 36px / 500 / ls -0.02em
- Project title: 26px / 500 / lh 1.3 / ls -0.01em
- Era title: 22px / 500 / lh 1.3
- Infra title: 18px / 500 / lh 1.3 / ls -0.01em
- Artifact title: 14px / 500 / lh 1.35
- Achievements big num: 56px / 500 / ls -0.03em
- Project result big num: 34px / 500 / ls -0.025em
- Lightbox caption: 15px serif
- Body: 15px / 400 / lh 1.6
- Small body: 13.5px / lh 1.7
- Caption: 12–12.5px
- Eyebrow / mono tag: 10–11px / 500 / uppercase / ls 0.06–0.14em

### Spacing
- Section padding: `120px 0` (mobile 72px)
- Wrap: max-width 1120px, padding 0 48px (mobile 24px)
- Section header bottom margin: 72px (mobile 48px)
- Hero padding: `80px 0 100px`
- Contact padding: `140px 0 100px`
- Project card bottom padding: 72px
- Artifact grid gap: 16px (mobile 12px)
- Infra block: margin-top 40px, padding-top 28px, gap 40px

### Borders & Rules
- **Hairline**: `1px solid var(--rule)` (#D6CCBB)
- **Dashed**: `1px dashed var(--rule)` (artifacts 상단 구분)
- **Thick**: `1px solid var(--ink)` (섹션 rule)
- **Accent (nav active)**: `1px solid var(--accent)`
- Border radius: 대부분 2px (tags/badges) / 999px (pill toggle)

### Shadows / Effects
- Nav backdrop: `backdrop-filter: saturate(140%) blur(12px)`
- Highlight dot ring: `box-shadow: 0 0 0 4px var(--paper), 0 0 0 5px var(--accent)`
- Lightbox image: `box-shadow: 0 40px 100px rgba(0,0,0,0.5)`

### Motion
- Nav border: 0.2s
- Toggle/hover: 0.2s
- Reveal: opacity/transform 0.8s ease
- Detail expand: max-height 0.5s ease
- Arrow rotate: transform 0.3s
- Lightbox: opacity 0.25s

---

## Assets

**외부 리소스 (CDN)**:
- Google Fonts — Noto Serif KR + JetBrains Mono
  `https://fonts.googleapis.com/css2?family=Noto+Serif+KR:wght@300;400;500;600;700;900&family=JetBrains+Mono:wght@400;500&display=swap`
- Pretendard variable CSS — `https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/variable/pretendardvariable.min.css`

**로컬 이미지 & 문서 자산** (`design_handoff_portfolio/assets/`):

| 파일 | 용도 | 출처 | 사이즈 |
|---|---|---|---|
| `네트워크구성도.png` | Experience 인프라 블록 + lightbox | 원본 PDF 1페이지 → 180dpi 렌더 | 2880×2160 |
| `네트워크구성도.pdf` | 원본 참고자료 | Megazone PoPs 인프라 문서 | 949KB |
| `클래스다이어그램_saas통합.png` | SaaS 통합 서비스 카드 artifact (dark 썸네일) | 원본 PNG (다크 배경) | 973×1024 |
| `가이드_m365_p1.png` | SaaS 통합 서비스 카드 artifact | Microsoft 365 통합 가이드 docx → PDF 1페이지 → 150dpi | 1241×1754 |
| `Microsoft365_User_API_통합.docx` | 원본 가이드 문서 | Confluence 통합 가이드 | 611KB |
| `화면설계서_로그인.png` | DDM 프로젝트 카드 artifact | 화면설계서 pptx 슬라이드 2 → 140dpi | 1867×1050 |
| `화면설계서_대시보드.png` | DDM 프로젝트 카드 artifact | 화면설계서 pptx 슬라이드 4 → 140dpi | 1867×1050 |
| `화면설계서_v0.4.pptx` | 원본 화면설계서 | 롯데면세점 DDM v0.4 | 856KB |

**아이콘 세트 없음** — 모든 UI 요소는 순수 CSS 텍스트/도형/rule/유니코드(✕, ↓, ↗, ◆). 프로필 사진, 로고, 아이콘 세트 추가 불필요.

---

## Files

이 번들에 포함된 디자인 참조 파일:

- **`Portfolio.html`** — 전체 포트폴리오 (HTML + CSS + JS + 프로젝트 데이터 인라인)
  - `<head>`의 `<style>` 블록에 모든 스타일
  - `<body>` 마지막 `<script>` 블록에 `PROJECTS` 배열(12개), `renderProjects()`, `toggleProject()`, `openLightbox()`, `closeLightbox()`, `openInfraLightbox()`, scroll spy, IntersectionObserver
- **`assets/`** — 이미지·원본 문서 (위 표 참고)

**구현 시 참고**:
- `PROJECTS` 배열을 별도 `projects.ts` 또는 `projects.json`으로 분리 권장. 각 항목은 다음 필드를 가집니다:
  ```ts
  interface Project {
    range: string;           // "2025.04 — 2025.06"
    dur: string;             // "2개월"
    highlight?: boolean;
    title: string;           // HTML — <em>...</em> 강조 포함
    problem: string;         // 평문 (P)
    results: Array<{
      big: string;           // "100", "5일", "10K"
      unit?: string;         // "%", "→ 4h"
      plus?: boolean;        // '+' 표시
      lbl: string;           // 캡션
    }>;
    tags: string[];          // ["Java 11", "Spring Boot 2.3.4", ...]
    artifacts?: Array<{      // 산출물 (선택)
      title: string;
      cap: string;           // "Class Diagram · Template Method Pattern"
      src: string;           // "assets/..."
      dark?: boolean;        // 다크 배경 썸네일
      alt?: string;
    }>;
    analyze: string[];       // HTML — <strong> 강조 포함 (A)
    action: string[];        // HTML — <strong> 강조 포함 (A)
  }
  ```
- 각 섹션(`Hero`, `About`, `Achievements`, `Experience`, `Projects`, `Skills`, `Contact`, `Lightbox`)을 독립 컴포넌트로 분리 권장
- 스크롤 스파이는 라이브러리 대신 `IntersectionObserver` 그대로 사용 가능
- 프로젝트 카드의 `max-height` transition은 CSS Grid `grid-template-rows: 0fr → 1fr` 방식으로 대체 고려 가능 (더 부드러움)
- **이미지 최적화**: Next.js/Astro의 Image 컴포넌트로 `네트워크구성도.png`(2.9K wide) 를 responsive srcset로 처리하면 초기 로드 개선

---

## Implementation Checklist

- [ ] 3개 폰트 로드 (Noto Serif KR, Pretendard, JetBrains Mono)
- [ ] CSS 변수 12개 정의
- [ ] Sticky nav + scroll spy
- [ ] Hero (2-column, 반응형)
- [ ] About (드롭캡, 3-column principles)
- [ ] Achievements 4×2 stats grid
- [ ] Experience 2 era cards + **Infrastructure block** + lightbox 연결
- [ ] Projects 타임라인 (12 items, 6 highlight, 세로 rule + 도트 정렬)
- [ ] **Project artifacts 블록** (조건부 렌더, 2개 프로젝트만 표시)
- [ ] Project detail 접힘/펼침 + Analyze/Action 2-column
- [ ] Skills 9 카테고리 (2-column grid)
- [ ] Contact 큰 세리프 이메일 링크
- [ ] Footer
- [ ] **Lightbox 오버레이** (ESC 닫기, backdrop 클릭 닫기, body 스크롤 잠금)
- [ ] IntersectionObserver 기반 fade-in reveal
- [ ] ≤900px 반응형 (모바일 nav 축소, 타임라인 재배치, artifact grid 단일 컬럼)
