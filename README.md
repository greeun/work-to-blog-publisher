# Work to Blog Publisher

> An integrated workflow skill that deploys work done in a Claude Code session to a GitHub repository and shares it on a blog

## Why was this built?

### The Problem

After finishing development work, sharing it requires several steps:

1. Write a README document
2. Initialize Git and commit
3. Create a GitHub repository and push
4. Write a blog post
5. Publish the blog post

**This process is cumbersome, so good work often goes unshared.**

### The Solution

`work-to-blog-publisher` **automates this whole process with a single command**:

```
"Deploy the work results" → Write README → GitHub push → Publish blog
```

## Key Features

| Feature | Description |
|-----|------|
| **Session analysis** | Automatically analyzes the current work and documents it |
| **README generation** | Automatically writes a README including the project's purpose, features, and usage |
| **GitHub deployment** | Handles repository creation, commit, and push in one go |
| **Blog publishing** | Automatically generates a blog post that emphasizes why the project is needed |

## Quick Start

### 1. Prerequisites

```bash
# Check GitHub CLI authentication
gh auth status

# Set WordPress environment variables (for blog publishing)
export WP_SITE_URL="https://your-site.com"
export WP_USERNAME="your-username"
export WP_APP_PASSWORD="xxxx xxxx xxxx xxxx xxxx xxxx"
```

### 2. Install the Skill

```bash
# Copy to the skills directory
cp -r work-to-blog-publisher ~/.claude/skills/
```

### 3. Usage

Make a request in Claude Code like:

```
# Slash command
/work-to-blog-publisher

# Or in natural language
"현재 작업한 내용을 GitHub에 배포하고 블로그로 공유해줘"
"작업 결과 배포해줘"
"README 작성하고 GitHub에 올려줘"
```

## Workflow

```
┌─────────────────┐
│  Phase 1        │
│  Write README   │
│  - Session      │
│    analysis     │
│  - Doc generate │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Phase 2        │
│  GitHub deploy  │
│  - Enter repo   │
│    URL          │
│  - commit/push  │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Phase 3        │
│  Blog publish   │
│  - Write content│
│  - WordPress    │
│    publish      │
└─────────────────┘
```

## Usage Examples

### Example 1: Full Workflow

```
User: Publish the CLI tool I built today to GitHub and post it on the blog too

Claude: I'll use the work-to-blog-publisher skill.

[Phase 1] Writing README...
- Project: my-cli-tool
- Purpose: Automate file conversion
- Features: JSON/YAML/TOML interconversion

README.md generated

[Phase 2] GitHub deployment
Please enter the GitHub repository URL.
e.g.: https://github.com/username/my-cli-tool

User: my-cli-tool

Claude: Repository created and pushed
https://github.com/username/my-cli-tool

[Phase 3] Blog publishing
Post written (draft)
https://your-blog.com/?p=123
```

### Example 2: Write README Only

```
User: Just write the README

Claude: [Run Phase 1 only]
README.md generated
```

### Example 3: GitHub Deployment Only

```
User: Just push it to GitHub

Claude: [Run Phase 2 only]
Please enter the GitHub repository URL.
```

## Trigger Keywords

Keywords that automatically activate the skill:

| Korean | English |
|-------|------|
| 작업 공개 | publish work |
| GitHub에 배포 | release project |
| 블로그로 공유 | share as blog |
| 오픈소스로 배포 | - |
| 작업 결과 배포 | - |
| README 작성하고 배포 | - |

## Generated Document Structure

### README.md

```markdown
# Project Name

A brief one-line description

## Why was this built? (Why)
## Key Features (Features)
## Quick Start
## Configuration
## Examples
## License
```

### Blog Post

```markdown
# [Project Name]: [One-line description]

## TL;DR
## Why was this built? (Problem)
## How was it solved? (Solution)
## How to Use
## What I learned during implementation
## Wrap-up
```

## Configuration

### WordPress Environment Variables

Add to `~/.zshrc` or `~/.bashrc`:

```bash
export WP_SITE_URL="https://your-wordpress-site.com"
export WP_USERNAME="your-username"
export WP_APP_PASSWORD="xxxx xxxx xxxx xxxx xxxx xxxx"
```

**How to create an Application Password:**
1. WordPress admin → Users → Profile
2. Generate a new password in the "Application Passwords" section

### GitHub CLI

```bash
# Install (macOS)
brew install gh

# Authenticate
gh auth login
```

## Related Skills

| Skill | Purpose |
|-----|------|
| `github-init` | Specialized in Git repository initialization |
| `wp-blog-post` | Specialized in WordPress blog publishing |

## File Structure

```
work-to-blog-publisher/
├── SKILL.md      # Skill definition and workflow
└── README.md     # This document
```

## License

MIT License

---

Built with [Claude Code](https://claude.ai/claude-code)
