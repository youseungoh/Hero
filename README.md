# Y.SEUNGOH Portfolio — Scrolling Case Study Hero

케이스 스터디 슬라이드가 대각선으로 겹쳐 쌓인 채 위로 무한 루프 스크롤되는 포트폴리오 히어로 섹션입니다.

## 주요 기능

- 15장(6종 x 반복)의 카드가 알아서 회전·오프셋되며 대각선 카스케이드로 쌓이는 레이아웃
- CSS `@keyframes`만으로 구현한 무한 루프 세로 스크롤 (JS 프레임 연산 없음)
- 마우스 오버 시 스크롤 자동 정지 (`:hover` + `animation-play-state`)
- 상/하단 페이드 마스킹으로 카드가 자연스럽게 나타나고 사라짐
- 6개 세션(바이브코딩 이해 → 생성형AI 앱 → Claude Code → 공공데이터 API → GitHub 배포 → 수업 공유) 커리큘럼 콘텐츠 반영
- Lucide 아이콘 CDN 연동 (rocket, bot, terminal, database, github, share-2 등)
- 모바일 반응형: 900px 이하에서 좌우 2단 → 상하 배치로 전환

## 기술 스택

- HTML / CSS / Vanilla JavaScript (프레임워크 없음, `index.html` 단일 파일)
- Google Fonts: `Archivo Black`(큰 숫자·헤드라인), `Space Grotesk`(본문·라벨)
- Lucide Icons (CDN: `unpkg.com/lucide`)
- 별도 빌드 도구 없음 — 브라우저에서 바로 실행

## 실행 방법

1. `hero-section.html` 파일을 더블클릭해서 브라우저로 열거나
2. GitHub Pages에 업로드해서 배포 (파일명을 `index.html`로 지정)

인터넷 연결이 있어야 Google Fonts와 Lucide 아이콘이 정상적으로 로드됩니다.

## 파일 구조

```
hero-section.html
├── <style>        전체 CSS (색상 변수, 레이아웃, 카드 회전/애니메이션)
├── .hero-copy     좌측 헤드라인 · 서브카피 · CTA 버튼 · 통계
├── .stack-viewport 우측 스크롤 카드 영역
└── <script>       카드 데이터(slidesData) → HTML 생성 → Lucide 아이콘 렌더링
```

## 커스터마이징 가이드

### 1. 색상 바꾸기
`:root` 안의 CSS 변수만 수정하면 전체 톤이 바뀝니다.

```css
--bg: #0d0d0d;        /* 배경 */
--orange: #ff4300;    /* 시그니처 컬러 */
--off-white: #f2efe8; /* 밝은 카드 배경 */
```

### 2. 헤드라인 · 통계 문구 수정
`<div class="hero-copy">` 안의 텍스트를 직접 수정하면 됩니다. `<em>` 태그로 감싼 부분만 오렌지색으로 강조됩니다.

### 3. 스크롤 카드 내용 수정
`<script>` 안의 `slidesData` 배열 하나만 편집하면 카드 15장 전체에 반영됩니다.

```js
{v:'v-orange', html:`<div class="slide-eyebrow">...</div>...`}
```

- `v`: 카드 색상 타입 — `v-orange`, `v-process`(다크), `v-white`, `v-metric`, `v-word`
- `html`: 카드 안에 들어갈 실제 내용

카드 장수는 `total` 변수(현재 15)로 조절합니다.

### 4. 스크롤 속도 조절
`.stack-track`의 `animation` 값에서 `34s`를 늘리면 느려지고, 줄이면 빨라집니다.

```css
animation: scrollUp 34s linear infinite;
```

### 5. 버튼 링크 변경
`.btn` 요소의 `href`만 원하는 주소로 바꾸면 됩니다. 현재는 새 탭(`target="_blank"`)으로 열리도록 설정되어 있습니다.

## GitHub Pages 배포 체크리스트

1. GitHub 저장소 생성 (Public)
2. 파일명을 `index.html`로 변경해서 업로드
3. Settings → Pages → Branch: `main` / `/ (root)` 설정 후 Save
4. `https://{username}.github.io/{저장소이름}/` 주소로 확인

## 브라우저 호환성

최신 Chrome, Edge, Safari, Firefox에서 정상 동작합니다. CSS `mask-image`를 지원하지 않는 구형 브라우저에서는 상하단 페이드 효과만 생략되고 나머지 기능은 그대로 동작합니다.

---
© Produced by Y.Seungoh
