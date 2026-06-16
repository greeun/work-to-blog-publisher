---
name: work-to-blog-publisher
description: |
  Use when session work needs to be published as open source project with documentation.
  Triggers: "작업 공개", "GitHub에 배포", "블로그로 공유", "오픈소스로 배포", "publish work",
  "share as blog", "release project", "작업 결과 배포", "README 작성하고 배포"
---

# Work Blog Publisher

세션에서 작업한 내용을 GitHub 저장소로 배포하고 블로그에 공유하는 통합 워크플로우.

## Workflow

```
1. README 작성 → 2. GitHub 저장소 생성/push → 3. 블로그 포스트 작성/발행
```

## When to Use

- 세션에서 완료한 프로젝트/기능을 오픈소스로 공개할 때
- 작업 내용을 문서화하여 GitHub에 배포하고 블로그로 홍보할 때
- "작업 공개해줘", "GitHub에 올려줘", "블로그로 공유해줘" 요청 시

## Prerequisites

### GitHub CLI
```bash
gh auth status  # 인증 상태 확인
```

### WordPress (블로그 발행 시)
```bash
# ~/.zshrc 또는 ~/.bashrc에 설정
export WP_SITE_URL="https://your-site.com"
export WP_USERNAME="your-username"
export WP_APP_PASSWORD="xxxx xxxx xxxx xxxx xxxx xxxx"
```

---

## Phase 1: README 작성

### 1.1 세션 분석

현재 세션에서 작업한 내용을 분석:

| 분석 항목 | 추출 내용 |
|----------|----------|
| **프로젝트명** | 작업한 기능/도구의 이름 |
| **목적** | 왜 만들었는지, 어떤 문제를 해결하는지 |
| **주요 기능** | 핵심 기능 목록 |
| **기술 스택** | 사용된 언어, 프레임워크, 라이브러리 |
| **사용법** | 설치 및 실행 방법 |

### 1.2 README 템플릿

```markdown
# 프로젝트명

간단한 한 줄 설명

## 왜 만들었나? (Why)

이 프로젝트가 해결하는 문제와 필요성 설명

## 주요 기능 (Features)

- 기능 1: 설명
- 기능 2: 설명
- 기능 3: 설명

## 빠른 시작 (Quick Start)

### 설치

\```bash
# 설치 명령어
\```

### 사용법

\```bash
# 기본 사용 예시
\```

## 설정 (Configuration)

필요한 환경변수나 설정 파일 설명

## 예시 (Examples)

구체적인 사용 예시

## 라이선스 (License)

MIT License

---

Built with [Claude Code](https://claude.ai/claude-code)
```

### 1.3 README 작성 가이드라인

- **명확한 목적**: 첫 문장에서 무엇을 하는 도구인지 알 수 있어야 함
- **즉시 사용 가능**: Quick Start로 5분 내 실행 가능해야 함
- **예시 포함**: 실제 사용 예시 필수
- **필요성 강조**: "왜 만들었나" 섹션에서 문제점과 해결책 명시

---

## Phase 2: GitHub 저장소 생성 및 Push

### 2.1 저장소 URL 입력받기

사용자에게 GitHub 저장소 URL 또는 저장소 이름 입력 요청:

```
GitHub 저장소 URL을 입력해주세요.
예: https://github.com/greeun/project-name
또는 저장소 이름만 입력: project-name
```

### 2.2 Git 초기화 및 Push

```bash
# 현재 디렉토리가 git repo가 아닌 경우
git init

# .gitignore 생성 (프로젝트 타입에 맞게)
# Node.js, Python, Go 등

# 초기 커밋
git add .
git commit -m "Initial commit: [프로젝트 설명]

- Add README with documentation
- Add core functionality
- Add configuration

Co-Authored-By: Claude Opus 4.5 <noreply@anthropic.com>"

# GitHub 저장소 생성 및 push
gh repo create [repo-name] --source=. --push --public --description "[설명]"

# 또는 기존 저장소에 push
git remote add origin https://github.com/[username]/[repo-name].git
git branch -M main
git push -u origin main
```

### 2.3 저장소 설정

```bash
# 토픽 추가
gh repo edit --add-topic "claude-code" --add-topic "[관련-기술]"

# About 설정
gh repo edit --description "[프로젝트 설명]"
```

---

## Phase 3: 블로그 포스트 작성

### 3.1 블로그 콘텐츠 구조

**필수 강조점: 이 스킬/도구의 필요성**

```markdown
# [프로젝트명]: [한 줄 설명]

## TL;DR
- 핵심 포인트 3-5개

## 왜 만들었나? (Problem)

### 기존의 문제점
- 문제점 1: 구체적 설명
- 문제점 2: 구체적 설명

### 해결하고 싶었던 것
- 목표 1
- 목표 2

## 어떻게 해결했나? (Solution)

### 핵심 아이디어
[핵심 접근 방식 설명]

### 주요 기능
1. **기능 1**: 설명
2. **기능 2**: 설명

## 사용 방법 (How to Use)

### 설치
\```bash
# 설치 명령어
\```

### 기본 사용법
\```bash
# 사용 예시
\```

## 구현 과정에서 배운 것

### 기술적 인사이트
- 배운 점 1
- 배운 점 2

### 개선할 점
- 향후 계획

## 마무리

[프로젝트 요약 및 GitHub 링크]

**GitHub**: [저장소 URL]

---

*이 프로젝트는 [Claude Code](https://claude.ai/claude-code)와 함께 개발되었습니다.*
```

### 3.2 Infographic visualization (REQUIRED)

**Maximize infographics so the post structure and every explanation are graspable at a glance.**
Treat visuals as the primary delivery vehicle: if content can be shown, render it as an image
even when prose would work. Target one visual per major section (minimum 2 per post) and
**diversify the types**.

| Section | Recommended infographic |
|---------|-------------------------|
| Post scope / "what this covers" | **Mind map** (Mermaid `mindmap`) |
| Why I built it (Problem) | Problem→solution **webtoon/illustrated panel**, before/after schematic |
| How it's solved (Solution) | **Architecture diagram**, data-flow schematic |
| How it works / usage flow | **Flowchart**, sequence diagram |
| Performance / metrics | **Chart/graph** (Mermaid `xychart-beta`, `pie`) |
| Version / migration | **Timeline** (Mermaid `timeline`) |
| Comparison / selection | Comparison table, **quadrant chart** |
| Anything beyond the above | **Open-ended creative visualization** (cards, journey strip, labeled map, custom infographic) — list is not exhaustive |

**Rules**:
- Do not repeat one type — mix at least 2 (mind map, flowchart, chart, architecture, webtoon…).
- Judge by "Can the post be understood by skimming the images alone?"
- **Plugin-independent images only**: render every infographic to a self-contained static image
  file (PNG/JPG/SVG) and embed it via the core `wp:image` block. Never use inline Mermaid
  (`<pre class="mermaid">`), chart/diagram shortcodes, plugin-specific blocks, or JS chart
  libraries — the post must render on any WordPress install with zero plugins.
- Production follows `wp-blog-post` skill's `Visual Elements Guidelines → Infographic-First
  Principle`: Mermaid via `mmdc` → PNG; webtoon/custom infographics via image-gen → upload with
  `upload_media.py`. Specific alt text required on every image.

```bash
# Mermaid → PNG (mmdc also renders mindmap, xychart-beta, pie, timeline besides flowcharts)
mmdc -i /tmp/diagram.mmd -o /tmp/diagram.png -w 900 --backgroundColor white
python ~/.claude/skills/wp-blog-post/scripts/upload_media.py \
  --file /tmp/diagram.png --alt-text "Diagram description"
```

### 3.3 블로그 발행

**REQUIRED SUB-SKILL**: `wp-blog-post` 스킬 사용

```bash
# 카테고리 자동 선택, 태그 자동 생성
python ~/.claude/skills/wp-blog-post/scripts/publish_post.py \
  --title "[프로젝트명]: [부제]" \
  --content-file /tmp/post_content.html \
  --status draft \
  --categories "Development,Open Source" \
  --tags "[관련-태그들]"
```

### 3.4 블로그 콘텐츠 강조점

| 섹션 | 강조 내용 |
|-----|---------|
| **왜 만들었나** | 기존 문제점, 불편함, 필요성 |
| **어떻게 해결** | 핵심 아이디어, 차별화 포인트 |
| **사용 방법** | 즉시 따라할 수 있는 예시 |
| **배운 것** | 기술적 인사이트, 공유할 가치 |

---

## Execution Checklist

사용자 요청 시 다음 순서로 실행:

### Step 1: 세션 분석
- [ ] 현재 세션에서 작업한 내용 파악
- [ ] 프로젝트 목적, 기능, 기술 스택 정리

### Step 2: README 작성
- [ ] 프로젝트 디렉토리에 README.md 생성
- [ ] 필요성, 기능, 사용법 포함
- [ ] 예시 코드 추가

### Step 3: GitHub 배포
- [ ] 사용자에게 저장소 URL/이름 입력 요청
- [ ] git init 및 .gitignore 생성
- [ ] 초기 커밋 생성
- [ ] GitHub 저장소 생성 및 push
- [ ] 토픽 및 설명 설정

### Step 4: 블로그 발행
- [ ] 블로그 콘텐츠 작성 (필요성 중심)
- [ ] Infographic visualization (one per section target, min 2, diverse types — mind map/flowchart/chart/architecture/webtoon; plugin-independent static images via `wp:image`)
- [ ] HTML 변환
- [ ] wp-blog-post 스킬로 발행
- [ ] 발행된 URL 사용자에게 전달

---

## Quick Example

```bash
# 전체 워크플로우 예시

# 1. README 확인
cat README.md

# 2. GitHub 배포
git init
git add .
git commit -m "Initial commit: Add project with documentation"
gh repo create my-project --source=. --push --public

# 3. 블로그 발행
python ~/.claude/skills/wp-blog-post/scripts/publish_post.py \
  --title "My Project: Solving X Problem" \
  --content-file /tmp/post_content.html \
  --status draft
```

## Related Skills

- **github-init**: Git 저장소 초기화 전문
- **wp-blog-post**: WordPress 블로그 발행 전문
