# Todolist App Style Guide

첨부 스크린샷의 스타일은 `밝은 배경 + 얇은 경계선 + 높은 여백 + 둥근 카드 + 부드러운 그림자 + 파스텔 포인트 컬러`가 핵심이다.  
TodoList 앱에는 이 감각을 유지하되, 작업 관리 앱답게 가독성과 상태 구분을 더 명확하게 적용한다.

## 1. 색상 팔레트

### 디자인 원칙

- 기본 배경은 거의 흰색에 가까운 밝은 뉴트럴 톤을 사용한다.
- 카드/패널은 흰색 또는 아주 옅은 회색으로 분리한다.
- Primary는 버튼, 현재 선택 상태, 핵심 강조에만 사용한다.
- Secondary는 보조 액션과 링크형 요소에 사용한다.
- Success/Error는 상태 전달 용도로만 사용한다.
- 태그 칩은 파스텔 배경 + 진한 텍스트 조합으로 시각적 노이즈를 줄인다.

### 권장 컬러 토큰

- `Primary`: `#8B5CF6` / `#7C3AED`
- `Secondary`: `#38BDF8` / `#0EA5E9`
- `Neutral`: `#111827`, `#374151`, `#6B7280`, `#D1D5DB`, `#E5E7EB`, `#F3F4F6`, `#FAFAFA`, `#FFFFFF`
- `Success`: `#22C55E` / `#16A34A`
- `Error`: `#EF4444` / `#DC2626`

### 추가 상태 컬러

- `Accent Pink`: `#EC4899`
- `Accent Amber`: `#F59E0B`
- `Accent Sky`: `#38BDF8`
- `Accent Mint`: `#34D399`

### Tailwind 커스텀 색상 설정

```js
// tailwind.config.js
module.exports = {
  content: ['./src/**/*.{js,ts,jsx,tsx,html}', './docs/**/*.md'],
  theme: {
    extend: {
      colors: {
        brand: {
          50: '#F5F3FF',
          100: '#EDE9FE',
          200: '#DDD6FE',
          300: '#C4B5FD',
          400: '#A78BFA',
          500: '#8B5CF6',
          600: '#7C3AED',
          700: '#6D28D9',
          800: '#5B21B6',
          900: '#4C1D95',
        },
        accent: {
          pink: '#EC4899',
          sky: '#38BDF8',
          amber: '#F59E0B',
          mint: '#34D399',
        },
        neutral: {
          0: '#FFFFFF',
          50: '#FAFAFA',
          100: '#F3F4F6',
          200: '#E5E7EB',
          300: '#D1D5DB',
          400: '#9CA3AF',
          500: '#6B7280',
          600: '#4B5563',
          700: '#374151',
          800: '#1F2937',
          900: '#111827',
        },
        success: {
          50: '#F0FDF4',
          100: '#DCFCE7',
          500: '#22C55E',
          600: '#16A34A',
          700: '#15803D',
        },
        error: {
          50: '#FEF2F2',
          100: '#FEE2E2',
          500: '#EF4444',
          600: '#DC2626',
          700: '#B91C1C',
        },
      },
      boxShadow: {
        card: '0 1px 2px rgba(15, 23, 42, 0.04), 0 8px 24px rgba(15, 23, 42, 0.06)',
        panel: '0 10px 30px rgba(15, 23, 42, 0.08)',
        lift: '0 12px 32px rgba(15, 23, 42, 0.12)',
      },
      borderRadius: {
        xl2: '1.25rem',
        '3xl': '1.5rem',
      },
    },
  },
  plugins: [],
}
```

## 2. 타이포그래피

### 폰트 패밀리

- 기본 폰트: `Inter`, `system-ui`, `sans-serif`
- 숫자/날짜 가독성이 중요하므로 `tabular-nums`를 적극 사용한다.
- 제목과 본문은 같은 산세리프 계열을 유지해 UI 일관성을 확보한다.

### 사이즈 스케일

- `text-xs`: 보조 메타, 칩 안 텍스트
- `text-sm`: 필터, 리스트 메타, 보조 설명
- `text-base`: 본문, 입력값
- `text-lg`: 섹션 제목, 카드 제목
- `text-xl`: 화면 제목
- `text-2xl`: 대시보드성 메인 타이틀

### 굵기

- `font-normal`: 일반 본문
- `font-medium`: 버튼, 리스트 제목, 칩 라벨
- `font-semibold`: 화면 제목, 주요 카드 제목
- `font-bold`: 매우 제한적으로 사용

### 줄간격

- 본문: `leading-6`
- 카드 제목: `leading-5` 또는 `leading-6`
- 긴 설명: `leading-7`

### 권장 조합

- 화면 제목: `text-2xl font-semibold tracking-tight text-neutral-900`
- 섹션 제목: `text-lg font-semibold text-neutral-900`
- 카드 제목: `text-base font-medium text-neutral-900`
- 메타 정보: `text-sm text-neutral-500`
- 캡션: `text-xs text-neutral-400`

## 3. 공통 컴포넌트 스타일

### 버튼

#### Primary

- Tailwind 클래스: `inline-flex items-center justify-center rounded-xl bg-brand-600 px-4 py-2.5 text-sm font-medium text-white shadow-sm transition hover:bg-brand-700 active:bg-brand-800 disabled:cursor-not-allowed disabled:bg-neutral-300`
- 용도: 저장, 추가, 주요 실행

#### Secondary

- Tailwind 클래스: `inline-flex items-center justify-center rounded-xl border border-neutral-200 bg-white px-4 py-2.5 text-sm font-medium text-neutral-700 shadow-sm transition hover:bg-neutral-50 hover:border-neutral-300 active:bg-neutral-100`
- 용도: 취소, 필터 초기화, 보조 액션

#### Danger

- Tailwind 클래스: `inline-flex items-center justify-center rounded-xl bg-error-600 px-4 py-2.5 text-sm font-medium text-white shadow-sm transition hover:bg-error-700 active:bg-error-800`
- 용도: 삭제, 위험한 변경

#### 공통 버튼 상태

- 포커스: `focus:outline-none focus:ring-2 focus:ring-brand-500 focus:ring-offset-2`
- 비활성: `disabled:opacity-50 disabled:shadow-none`
- 아이콘 버튼: `h-9 w-9 rounded-lg`

### 입력폼

#### 기본 상태

- 클래스: `w-full rounded-xl border border-neutral-200 bg-white px-3.5 py-2.5 text-sm text-neutral-900 placeholder:text-neutral-400 shadow-sm transition`

#### 포커스 상태

- 클래스: `focus:border-brand-500 focus:outline-none focus:ring-2 focus:ring-brand-500/20`

#### 에러 상태

- 클래스: `border-error-500 bg-error-50 text-error-700 placeholder:text-error-300 focus:border-error-500 focus:ring-error-500/20`

#### 라벨과 도움말

- 라벨: `mb-1 block text-sm font-medium text-neutral-700`
- 도움말: `mt-1 text-xs text-neutral-500`
- 에러 문구: `mt-1 text-xs font-medium text-error-600`

### 카드 / 리스트 아이템

#### 카드

- 클래스: `rounded-2xl border border-neutral-200 bg-white shadow-card`
- 내부 여백: `p-5`
- 카드 헤더: `flex items-start justify-between gap-3`
- 카드 구분선이 필요하면 `border-b border-neutral-100`

#### 리스트 아이템

- 클래스: `rounded-xl border border-neutral-200 bg-white px-4 py-3 transition hover:border-neutral-300 hover:shadow-sm`
- 완료 상태: `opacity-70` + 제목 `line-through text-neutral-400`
- 우선순위 강조: 카드 상단에 `h-1 rounded-t-xl` 또는 왼쪽 보더 컬러 사용

#### 태그 칩

- 공통: `inline-flex items-center rounded-full px-2.5 py-1 text-xs font-medium`
- 예시:
  - 업무: `bg-brand-100 text-brand-700`
  - 개인: `bg-accent-sky/15 text-sky-700`
  - 학습: `bg-accent-amber/15 text-amber-700`
  - 완료: `bg-success-100 text-success-700`

### 헤더 / 네비게이션

#### 상단 헤더

- 클래스: `sticky top-0 z-20 border-b border-neutral-200 bg-white/90 backdrop-blur`
- 내부: `mx-auto flex h-16 max-w-7xl items-center justify-between px-4 sm:px-6 lg:px-8`

#### 네비게이션

- 목적: 화면 전환보다 상태 전환 중심
- 탭/세그먼트가 있다면 `inline-flex rounded-xl bg-neutral-100 p-1`
- 선택 상태: `bg-white shadow-sm text-neutral-900`

## 4. 반응형 브레이크포인트 적용 기준

### Tailwind 브레이크포인트

- `sm`: `640px`
- `md`: `768px`
- `lg`: `1024px`

### 적용 기준

- `sm`
  - 빠른 추가 입력을 세로 스택으로 전환
  - 필터 칩을 두 줄로 감싸기
  - 카드 패딩 축소: `p-4`
- `md`
  - 검색/필터를 2열 배치
  - 목록 카드의 메타 정보를 한 줄 더 노출
  - 모달 폭을 넓혀 편집 효율 향상
- `lg`
  - 좌측 목록, 우측 상세/편집 패널 분할
  - 상단 툴바 고정
  - 목록과 폼을 동시에 보는 작업 흐름 지원

### 권장 사용 예

- 모바일 기본: `grid grid-cols-1 gap-4`
- 태블릿: `md:grid-cols-2`
- 데스크톱: `lg:grid-cols-[minmax(0,1.6fr)_minmax(360px,1fr)]`

## 5. 다크모드 지원 여부 및 기준 색상

### 권장 판단

- 기본은 `라이트 모드 우선`으로 간다.
- 이 프로젝트의 핵심 스타일은 밝은 카드와 얕은 그림자이므로, 캡처의 UI 톤과도 맞는다.
- 초기 버전에서는 다크모드를 필수로 넣지 않아도 된다.
- 다만 Tailwind의 `dark:` 변형을 남겨두면 추후 확장하기 쉽다.

### 다크모드 기준 색상

- 배경: `#0F172A`
- 카드 배경: `#111827`
- 보조 표면: `#1F2937`
- 경계선: `#374151`
- 기본 텍스트: `#F9FAFB`
- 보조 텍스트: `#D1D5DB`
- 비활성 텍스트: `#9CA3AF`
- Primary: `#A78BFA`
- Secondary: `#38BDF8`
- Success: `#4ADE80`
- Error: `#F87171`

### 다크모드 Tailwind 예시

```js
module.exports = {
  darkMode: 'class',
}
```

### 다크모드 컴포넌트 예시

- 카드: `dark:bg-neutral-800 dark:border-neutral-700`
- 본문: `dark:text-neutral-100`
- 보조 텍스트: `dark:text-neutral-400`
- 입력폼: `dark:bg-neutral-900 dark:border-neutral-700 dark:text-neutral-100 dark:placeholder:text-neutral-500`

## 6. 화면 적용 예시

### 할 일 카드

- `rounded-2xl border border-neutral-200 bg-white shadow-card`
- 상단에 `h-1 rounded-t-2xl bg-accent-pink` 또는 상태 컬러를 둔다.
- 제목은 `text-base font-semibold text-neutral-900`
- 메타는 `text-sm text-neutral-500`

### 검색 바

- `rounded-2xl border border-neutral-200 bg-neutral-50 px-4 py-3`
- 입력값은 `bg-transparent outline-none`

### 필터 칩

- `rounded-full border border-neutral-200 bg-white px-3 py-1.5 text-sm text-neutral-600`
- 활성 상태: `border-brand-200 bg-brand-50 text-brand-700`

### 빈 상태 카드

- `rounded-3xl border border-dashed border-neutral-200 bg-neutral-50 px-6 py-10 text-center`

