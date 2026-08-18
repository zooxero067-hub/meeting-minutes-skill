# 미팅기록 자동 정리 스킬 (meeting-minutes)

정제되지 않은 미팅 기록(음성 전사 텍스트, 메모 등)을 Claude Code가 회사 공유용 공식 문서로 자동 정리해주는 스킬입니다.

**산출물 (항상 2개):**
- `미팅기록.md` — 노션에 그대로 붙여넣을 수 있는 마크다운
- `미팅기록.html` — 브라우저에서 보기 좋은 시각화 문서 (카드 레이아웃, 인쇄 지원)

## 설치 방법

Claude Code가 설치되어 있어야 합니다.

### 방법 1: 개인 전역 설치 (모든 프로젝트에서 사용)

```bash
git clone https://github.com/zooxero067-hub/meeting-minutes-skill.git
mkdir -p ~/.claude/skills
cp -r meeting-minutes-skill/meeting-minutes ~/.claude/skills/
```

### 방법 2: 특정 프로젝트에만 설치 (팀 공유용)

프로젝트 루트에서:

```bash
git clone https://github.com/zooxero067-hub/meeting-minutes-skill.git /tmp/mm-skill
mkdir -p .claude/skills
cp -r /tmp/mm-skill/meeting-minutes .claude/skills/
```

`.claude/skills/`를 git에 커밋하면 팀원 전체가 같은 스킬을 공유합니다.

## 사용 방법

Claude Code 세션에서 자연어로 요청하면 됩니다:

```
미팅 기록 정리해줘: /path/to/회의녹취.txt
```

```
회의록 만들어줘
참석자: 대표님, 김팀장, 이매니저
[미팅 내용 붙여넣기]
```

파일 경로 + 보조 메모를 함께 전달해도 됩니다. 음성 전사(STT) 텍스트의 타임스탬프·추임새는 자동으로 제거됩니다.

## 정리 기준

- 미팅 개요(일시/장소/참석자), 아젠다, 논의 내용, 결정 사항, 액션 아이템(담당자/기한/상태), 슬랙·노션 공유용 요약 포함
- 논의 내용은 발언자 나열이 아닌, 참석하지 않은 사람도 읽고 이해할 수 있는 서술형으로 정리
- 원본에 없는 내용은 추가하지 않음

## 폴더 구조

```
meeting-minutes-skill/
└── meeting-minutes/
    └── SKILL.md   ← 스킬 본체
```
