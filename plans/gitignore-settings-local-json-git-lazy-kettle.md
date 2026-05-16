# Context

`.claude/settings.local.json`을 git 추적에서 제외하려 했으나 여전히 추적되고 있음.
두 가지 복합적인 문제가 원인임.

---

## 근본 원인

### 문제 1: 잘못된 `.gitignore` 위치와 패턴

| 항목 | 내용 |
|---|---|
| `.gitignore` 위치 | `.claude/.gitignore` |
| 현재 패턴 | `.claude/settings.local.json` |
| 실제 매칭 경로 | `.claude/.claude/settings.local.json` (존재하지 않음) |
| 의도한 경로 | `.claude/settings.local.json` |

`.gitignore`의 패턴은 **해당 파일이 있는 디렉토리 기준**으로 해석됨.
따라서 `.claude/.gitignore` 안에서 `.claude/settings.local.json`은 존재하지 않는 경로를 가리킴.

### 문제 2: 파일이 이미 git index에 추적 중

`.gitignore`를 고쳐도, 이미 git이 추적하고 있는 파일은 자동으로 무시되지 않음.
`git rm --cached`로 index에서 명시적으로 제거해야 함.

---

## 해결 방안 (권장)

### Step 1: 루트에 `.gitignore` 생성 또는 수정

프로젝트 루트(`D:\workspace\my-profile-site\.gitignore`)에 아래 내용 추가:

```
.claude/settings.local.json
```

> `.claude/.gitignore`의 기존 잘못된 패턴은 삭제하거나 `settings.local.json`으로 수정.

### Step 2: git index에서 파일 제거

```powershell
git rm --cached .claude/settings.local.json
```

이 명령은 **파일 자체는 삭제하지 않고**, git이 추적하는 목록에서만 제거함.

### Step 3: 변경사항 커밋

```powershell
git add .gitignore
git commit -m "chore: gitignore에 settings.local.json 추가"
```

---

## 검증 방법

```powershell
# 무시 규칙이 적용되는지 확인
git check-ignore -v .claude/settings.local.json
# → 출력이 있으면 정상적으로 무시됨

# git status에서 더 이상 보이지 않아야 함
git status
```

---

## 관련 파일

- `.claude/.gitignore` — 잘못된 패턴 수정 필요
- `.gitignore` (루트) — 새로 생성 또는 패턴 추가 필요
