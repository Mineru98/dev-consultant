# Dev Consultant Plugin

모호한 고객 요구사항을 상세한 애플리케이션 명세서로 변환하는 Claude Code 플러그인입니다.

## Overview

**13개의 전문화된 에이전트**와 **4개의 스킬**이 구조화된 워크플로우를 통해 초기 컨셉부터 QA 리포트까지 포괄적인 문서를 생성합니다.

### 지원 플랫폼

| 스킬 | 기술 스택 | 용도 |
|------|----------|------|
| `webapp-consultant` | HTML + Tailwind + Vanilla JS | 클라이언트 전용 웹앱 |
| `tauri-app-consultant` | React + TypeScript + Rust | 크로스플랫폼 데스크톱/모바일 앱 |
| `mobile-web-consultant` | HTML + Tailwind + PWA | 모바일 친화적 웹앱 |
| `chrome-extension-consultant` | Manifest V3 + Tailwind | Chrome 확장 프로그램 |

## What's New in v2.0.0

### 새로운 스킬 (3개 추가)
- **tauri-app-consultant**: Tauri v2 기반 데스크톱/모바일 앱
- **mobile-web-consultant**: PWA 및 모바일 친화적 웹앱
- **chrome-extension-consultant**: Chrome Extension (Manifest V3)

### 인터뷰어 모드 분리
- **Standard Mode**: 빠른 요구사항 수집 (2-3 질문, ~5분)
- **Hell Interviewer**: 극도로 상세한 요구사항 추출 (20-45분)

### 새로운 에이전트 (5개 추가)
- `hell-interviewer`: 상세 요구사항 추출
- `tauri-architect`: Rust 백엔드 + Tauri 아키텍처
- `mobile-ui-sketcher`: 모바일 우선 와이어프레임
- `mobile-interaction-designer`: 터치 인터랙션 전문가
- `extension-architect`: Manifest V3 아키텍처

## Project Structure

```
dev-consultant/
├── agents/                              # 13개 에이전트
│   ├── interviewer/AGENT.md             # 요구사항 추출 (기본 모드)
│   ├── hell-interviewer/AGENT.md        # 요구사항 추출 (상세 모드) [NEW]
│   ├── ui-sketcher/AGENT.md             # ASCII 와이어프레임
│   ├── mobile-ui-sketcher/AGENT.md      # 모바일 와이어프레임 [NEW]
│   ├── ux-spec-writer/AGENT.md          # UX 명세서
│   ├── client-tech-architect/AGENT.md   # 웹앱 기술 아키텍처
│   ├── tauri-architect/AGENT.md         # Tauri 아키텍처 [NEW]
│   ├── extension-architect/AGENT.md     # 확장 아키텍처 [NEW]
│   ├── mermaid-designer/AGENT.md        # 플로우 다이어그램
│   ├── interactive-designer/AGENT.md    # 웹 애니메이션
│   ├── mobile-interaction-designer/AGENT.md # 터치 인터랙션 [NEW]
│   ├── planner/AGENT.md                 # 프로젝트 계획
│   └── browser-qa/AGENT.md              # 브라우저 QA
├── skills/
│   ├── webapp-consultant/               # 웹앱 컨설턴트
│   ├── tauri-app-consultant/            # Tauri 앱 컨설턴트 [NEW]
│   ├── mobile-web-consultant/           # 모바일 웹 컨설턴트 [NEW]
│   └── chrome-extension-consultant/     # 확장 프로그램 컨설턴트 [NEW]
└── .claude-plugin/
    └── plugin.json
```

## 13 Specialized Agents

### Core Agents (모든 스킬에서 사용)

| Agent | Output | Purpose |
|-------|--------|---------|
| **Interviewer** | `01-requirements.md` | 빠른 요구사항 추출 (2-3 질문) |
| **Hell Interviewer** | `01-requirements-deep.md` | 상세 요구사항 추출 (20-45분) |
| **UX Spec Writer** | `03-ux-specification.md` | UX 철학 (Norman/Nielsen) 통합 |
| **Mermaid Designer** | `05-flow-diagrams.md` | 사용자 플로우 다이어그램 |
| **Planner** | `07-roadmap.md` | MoSCoW/RICE 우선순위 |
| **Browser QA** | `08-qa-report.md` | Chrome 자동화 QA |

### Platform-Specific Agents

| Agent | Platform | Purpose |
|-------|----------|---------|
| **UI Sketcher** | Web | ASCII 와이어프레임 + Tailwind |
| **Mobile UI Sketcher** | Mobile | 모바일 우선 와이어프레임 |
| **Client Tech Architect** | Web/PWA | IndexedDB + Repository 패턴 |
| **Tauri Architect** | Tauri | Rust 백엔드 + SQLite |
| **Extension Architect** | Chrome | Manifest V3 + Message Passing |
| **Interactive Designer** | Web | Tailwind 애니메이션 |
| **Mobile Interaction Designer** | Mobile | 터치 제스처 + 햅틱 |

## Workflow

모든 스킬은 동일한 8단계 워크플로우를 따릅니다:

```
┌────────────────────────────────────────────────────────────────┐
│                      고객 요청 (모호)                            │
└───────────────────────────┬────────────────────────────────────┘
                            ↓
┌────────────────────────────────────────────────────────────────┐
│  인터뷰어 모드 선택                                              │
│  • Standard (2-3 질문, ~5분)                                    │
│  • Hell Interviewer (상세, 20-45분)                             │
└───────────────────────────┬────────────────────────────────────┘
                            ↓
┌────────────────────────────────────────────────────────────────┐
│  Phase 1: Discovery (순차)                                      │
│  Interviewer → UI Sketcher → UX Spec Writer                    │
└───────────────────────────┬────────────────────────────────────┘
                            ↓
┌────────────────────────────────────────────────────────────────┐
│  Phase 2: Specification (병렬)                                  │
│  Tech Architect + Mermaid Designer + Interaction Designer      │
└───────────────────────────┬────────────────────────────────────┘
                            ↓
┌────────────────────────────────────────────────────────────────┐
│  Phase 3: Final (순차)                                          │
│  Planner → Browser QA                                          │
└───────────────────────────┬────────────────────────────────────┘
                            ↓
┌────────────────────────────────────────────────────────────────┐
│            최종 출력: .shared/ 폴더에 8개 문서                    │
└────────────────────────────────────────────────────────────────┘
```

## Installation

```bash
# Claude Code 마켓플레이스에서 설치
/plugin marketplace add Mineru98/dev-consultant
/plugin install dev-consultant
```

## Usage

### 1. 스킬 선택 및 실행

```bash
# 웹앱 개발
/webapp-consultant

# Tauri 데스크톱/모바일 앱
/tauri-app-consultant

# 모바일 친화적 PWA
/mobile-web-consultant

# Chrome 확장 프로그램
/chrome-extension-consultant
```

### 2. 인터뷰어 모드 선택

스킬 실행 시 인터뷰어 모드를 선택합니다:

```
"인터뷰어 모드를 선택하세요:"
• Standard (빠른 요구사항 수집, 2-3 질문, ~5분)
• Hell Interviewer (상세 탐색, 20-45분)
```

### 3. 개별 에이전트 사용

```javascript
// 기본 인터뷰어
Task({
  subagent_type: "interviewer",
  prompt: "개인 재무 추적기 요구사항 추출",
  description: "요구사항 수집"
})

// Hell Interviewer (상세)
Task({
  subagent_type: "hell-interviewer",
  prompt: "기업용 프로젝트 관리 시스템 요구사항",
  description: "상세 요구사항 수집"
})
```

## Skill Comparison

| 스킬 | 프론트엔드 | 백엔드 | 저장소 | 특화 |
|------|-----------|--------|--------|------|
| webapp | HTML + Tailwind + JS | 없음 | IndexedDB | 클라이언트 전용 |
| tauri-app | React + TS | Rust | SQLite | 네이티브 성능 |
| mobile-web | HTML + Tailwind + JS | 없음 | IndexedDB + PWA | 오프라인 지원 |
| chrome-ext | HTML + Tailwind + JS | Service Worker | chrome.storage | 브라우저 통합 |

## .shared Collaboration System

모든 에이전트는 `.shared/` 폴더에 결과물을 저장합니다:

```
[target-repository]/.shared/
├── 01-requirements.md        ← Interviewer
├── 02-wireframes.md          ← UI Sketcher
├── 03-ux-specification.md    ← UX Spec Writer
├── 04-tech-architecture.md   ← Tech Architect
├── 05-flow-diagrams.md       ← Mermaid Designer
├── 06-animations.md          ← Interaction Designer
├── 07-roadmap.md             ← Planner
└── 08-qa-report.md           ← Browser QA
```

## When to Use Each Skill

### webapp-consultant
✅ 클라이언트 전용 웹앱
✅ HTML + Tailwind + Vanilla JS
✅ 백엔드 없는 프로젝트
❌ 서버 사이드 필요 시

### tauri-app-consultant
✅ 크로스플랫폼 데스크톱 앱
✅ 네이티브 성능 필요
✅ 시스템 통합 (파일, 알림 등)
❌ 웹 전용 프로젝트

### mobile-web-consultant
✅ 모바일 우선 PWA
✅ 오프라인 지원 필요
✅ 터치 인터랙션 중심
❌ 데스크톱 우선 프로젝트

### chrome-extension-consultant
✅ 브라우저 기능 확장
✅ 웹페이지 수정/향상
✅ 크로스사이트 기능
❌ 독립 실행 앱

## Final Output

각 스킬은 8개의 포괄적인 Markdown 문서를 생성합니다:

1. **01-requirements.md** - 문제 정의, 사용자 페르소나, 기능 분류
2. **02-wireframes.md** - ASCII 와이어프레임 + 스타일 힌트
3. **03-ux-specification.md** - 사용자 스토리, UX 분석
4. **04-tech-architecture.md** - 데이터 모델, 아키텍처 설계
5. **05-flow-diagrams.md** - Mermaid 사용자 플로우
6. **06-animations.md** - 인터랙션 및 애니메이션 명세
7. **07-roadmap.md** - MoSCoW 우선순위, 개발 로드맵
8. **08-qa-report.md** - QA 테스트 결과

## References by Skill

### webapp-consultant
| Reference | Description |
|-----------|-------------|
| workflow.md | 전체 프로세스 |
| localbase-guide.md | IndexedDB API |
| tailwind-animations.md | 애니메이션 패턴 |

### tauri-app-consultant
| Reference | Description |
|-----------|-------------|
| tauri-architecture.md | Tauri 패턴 |
| rust-patterns.md | Rust 베스트 프랙티스 |
| tauri-commands.md | 커맨드 가이드 |

### mobile-web-consultant
| Reference | Description |
|-----------|-------------|
| mobile-ux-patterns.md | 모바일 UX 패턴 |
| pwa-guide.md | PWA 구현 가이드 |
| touch-interactions.md | 터치 제스처 |

### chrome-extension-consultant
| Reference | Description |
|-----------|-------------|
| manifest-v3-guide.md | MV3 가이드 |
| extension-architecture.md | 아키텍처 패턴 |
| chrome-storage-patterns.md | 스토리지 패턴 |

## Credits

- Norman, Don. "The Design of Everyday Things"
- Nielsen, Jakob. "Usability Heuristics"
- ai-diagrams-toolkit (Mermaid patterns)
- localbase (IndexedDB wrapper)
- Tauri (Cross-platform framework)

## License

GPL-3.0 - See [LICENSE](LICENSE) file

## Version

Current version: **2.0.0**

### Changelog

#### v2.0.0
- 새로운 스킬 3개 추가 (tauri-app, mobile-web, chrome-extension)
- 인터뷰어 모드 분리 (Standard / Hell Interviewer)
- 새로운 에이전트 5개 추가
- 플랫폼별 레퍼런스 파일 추가

#### v1.1.0
- 초기 릴리스
- webapp-consultant 스킬
- 8개 에이전트
