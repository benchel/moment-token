# moment-token

# @vanchall/moment-token

Moment 프로젝트에서 사용하는 디자인 토큰 패키지입니다. 색상, 간격, 모서리 반지름, 타이포그래피 토큰을 관리하며 CSS Variables, SCSS Variables, Tailwind CSS v4 테마 형식으로 제공합니다.

## 설치

```bash
npm install @vanchall/moment-token
```

## 사용법

### CSS

생성된 CSS 파일을 애플리케이션의 전역 스타일에 포함합니다.

```css
@import "@vanchall/moment-token/css";
```

CSS 변수는 `:root`에 정의됩니다.

```css
.card {
  color: var(--color-text-primary);
  background-color: var(--color-surface-default);
  border-radius: var(--radius-md);
  padding: var(--spacing-4);
}
```

### SCSS

```scss
@use "@vanchall/moment-token/scss" as token;

.card {
  color: token.$color-text-primary;
  background-color: token.$color-surface-default;
  border-radius: token.$radius-md;
  padding: token.$spacing-4;
}
```

### Tailwind CSS v4

Tailwind CSS의 전역 CSS 파일에서 테마를 불러옵니다.

```css
@import "tailwindcss";
@import "@vanchall/moment-token/tailwind";
```

토큰은 `@theme` 블록으로 제공되므로 Tailwind 유틸리티 클래스에서 사용할 수 있습니다.

```html
<article class="rounded-md bg-surface-default p-4 text-text-primary">
  Content
</article>
```

## 제공 토큰

### 색상

- 원시 색상: `white`, `sand`, `espresso`, `gray-warm`, `moss`, `clay`, `charcoal`
- 의미 색상: `brand`, `surface`, `text`, `border`, `badge`

CSS 변수 예시:

```css
:root {
  --color-brand-primary: var(--color-espresso-900);
  --color-text-primary: var(--color-charcoal-950);
  --color-surface-subtle: var(--color-sand-100);
  --color-badge-new-bg: var(--color-moss-600);
}
```

### 간격

`--spacing-1`부터 `--spacing-10`까지 제공하며 값은 `4px`부터 `128px`까지의 간격 체계를 사용합니다.

### 모서리 반지름

`sm`, `md`, `lg`, `xl`, `full` 토큰을 제공합니다.

```css
border-radius: var(--radius-lg);
```

### 타이포그래피

- 글자 크기: `display`, `h1`, `h2`, `h3`, `body-lg`, `body`, `body-md`, `body-sm`
- 행간: `tight`, `tight-m`, `normal`
- 자간: `tight`, `normal`, `wide`
- 글꼴: `primary`, `display`

```css
.heading {
  font-family: var(--font-display);
  font-size: var(--font-size-h1);
  line-height: var(--leading-tight);
  letter-spacing: var(--tracking-tight);
}
```

## 프로젝트 구조

```text
tokens/                 # 디자인 토큰 원본 JSON
  color-primitives.json
  color-semantic.json
  radius.json
  spacing.json
  typography.json
dist/
  css/variables.css     # CSS Variables
  scss/_variables.scss  # SCSS Variables
  tailwind/theme.css    # Tailwind CSS v4 @theme
build-tokens.mjs        # Style Dictionary 빌드 스크립트
```

`dist` 아래 파일은 토큰 원본에서 자동 생성됩니다. 생성된 파일을 직접 수정하지 말고 `tokens` 아래 JSON을 수정한 뒤 다시 빌드하세요.

## 로컬 개발

의존성을 설치합니다.

```bash
npm install
```

토큰 산출물을 생성합니다.

```bash
npm run build
```

`npm publish` 실행 전에도 `prepublishOnly` 스크립트에 의해 자동으로 빌드됩니다.

## 패키지 Export

| 경로 | 내용 |
| --- | --- |
| `@vanchall/moment-token/css` | CSS Variables |
| `@vanchall/moment-token/scss` | SCSS Variables |
| `@vanchall/moment-token/tailwind` | Tailwind CSS v4 테마 |
| `@vanchall/moment-token/tokens/*` | 원본 토큰 JSON |

## 라이선스

MIT

