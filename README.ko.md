# Work to Blog Publisher

> Claude Code 세션에서 작업한 내용을 GitHub 저장소로 배포하고 블로그에 공유하는 통합 워크플로우 스킬

## 왜 만들었나?

### 문제점

개발 작업을 완료한 후 공유하려면 여러 단계를 거쳐야 합니다:

1. README 문서 작성
2. Git 초기화 및 커밋
3. GitHub 저장소 생성 및 push
4. 블로그 포스트 작성
5. 블로그 발행

**이 과정이 번거로워서 좋은 작업물도 공유하지 않고 넘어가는 경우가 많습니다.**

### 해결책

`work-to-blog-publisher`는 이 모든 과정을 **하나의 명령으로 자동화**합니다:

```
"작업 결과 배포해줘" → README 작성 → GitHub push → 블로그 발행
```

## 주요 기능

| 기능 | 설명 |
|-----|------|
| **세션 분석** | 현재 작업 내용을 자동으로 분석하여 문서화 |
| **README 생성** | 프로젝트 목적, 기능, 사용법을 포함한 README 자동 작성 |
| **GitHub 배포** | 저장소 생성, 커밋, push까지 한 번에 처리 |
| **블로그 발행** | 프로젝트 필요성을 강조한 블로그 포스트 자동 생성 |

## 빠른 시작

### 1. 사전 요구사항

```bash
# GitHub CLI 인증 확인
gh auth status

# WordPress 환경변수 설정 (블로그 발행 시)
export WP_SITE_URL="https://your-site.com"
export WP_USERNAME="your-username"
export WP_APP_PASSWORD="xxxx xxxx xxxx xxxx xxxx xxxx"
```

### 2. 스킬 설치

```bash
# 스킬 디렉토리에 복사
cp -r work-to-blog-publisher ~/.claude/skills/
```

### 3. 사용하기

Claude Code에서 다음과 같이 요청:

```
# 슬래시 커맨드
/work-to-blog-publisher

# 또는 자연어로
"현재 작업한 내용을 GitHub에 배포하고 블로그로 공유해줘"
"작업 결과 배포해줘"
"README 작성하고 GitHub에 올려줘"
```

## 워크플로우

```
┌─────────────────┐
│  Phase 1        │
│  README 작성    │
│  - 세션 분석    │
│  - 문서 생성    │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Phase 2        │
│  GitHub 배포    │
│  - 저장소 URL   │
│    입력받기     │
│  - commit/push  │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Phase 3        │
│  블로그 발행    │
│  - 콘텐츠 작성  │
│  - WordPress    │
│    발행         │
└─────────────────┘
```

## 사용 예시

### 예시 1: 전체 워크플로우

```
사용자: 오늘 만든 CLI 도구를 GitHub에 공개하고 블로그에도 올려줘

Claude: work-to-blog-publisher 스킬을 사용하겠습니다.

[Phase 1] README 작성 중...
- 프로젝트: my-cli-tool
- 목적: 파일 변환 자동화
- 기능: JSON/YAML/TOML 상호 변환

README.md 생성 완료

[Phase 2] GitHub 배포
GitHub 저장소 URL을 입력해주세요.
예: https://github.com/username/my-cli-tool

사용자: my-cli-tool

Claude: 저장소 생성 및 push 완료
https://github.com/username/my-cli-tool

[Phase 3] 블로그 발행
포스트 작성 완료 (draft)
https://your-blog.com/?p=123
```

### 예시 2: README만 작성

```
사용자: README만 작성해줘

Claude: [Phase 1만 실행]
README.md 생성 완료
```

### 예시 3: GitHub 배포만

```
사용자: GitHub에만 올려줘

Claude: [Phase 2만 실행]
GitHub 저장소 URL을 입력해주세요.
```

## 트리거 키워드

스킬이 자동으로 활성화되는 키워드:

| 한국어 | 영어 |
|-------|------|
| 작업 공개 | publish work |
| GitHub에 배포 | release project |
| 블로그로 공유 | share as blog |
| 오픈소스로 배포 | - |
| 작업 결과 배포 | - |
| README 작성하고 배포 | - |

## 생성되는 문서 구조

### README.md

```markdown
# 프로젝트명

간단한 한 줄 설명

## 왜 만들었나? (Why)
## 주요 기능 (Features)
## 빠른 시작 (Quick Start)
## 설정 (Configuration)
## 예시 (Examples)
## 라이선스 (License)
```

### 블로그 포스트

```markdown
# [프로젝트명]: [한 줄 설명]

## TL;DR
## 왜 만들었나? (Problem)
## 어떻게 해결했나? (Solution)
## 사용 방법 (How to Use)
## 구현 과정에서 배운 것
## 마무리
```

## 설정

### WordPress 환경변수

`~/.zshrc` 또는 `~/.bashrc`에 추가:

```bash
export WP_SITE_URL="https://your-wordpress-site.com"
export WP_USERNAME="your-username"
export WP_APP_PASSWORD="xxxx xxxx xxxx xxxx xxxx xxxx"
```

**Application Password 생성 방법:**
1. WordPress 관리자 → 사용자 → 프로필
2. "애플리케이션 비밀번호" 섹션에서 새 비밀번호 생성

### GitHub CLI

```bash
# 설치 (macOS)
brew install gh

# 인증
gh auth login
```

## 관련 스킬

| 스킬 | 용도 |
|-----|------|
| `github-init` | Git 저장소 초기화 전문 |
| `wp-blog-post` | WordPress 블로그 발행 전문 |

## 파일 구조

```
work-to-blog-publisher/
├── SKILL.md      # 스킬 정의 및 워크플로우
└── README.md     # 이 문서
```

## 라이선스

MIT License

---

Built with [Claude Code](https://claude.ai/claude-code)
