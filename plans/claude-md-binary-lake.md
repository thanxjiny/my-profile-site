# README.md / CLAUDE.md 개선 플랜

## Context

현재 프로젝트 문서 파일 두 개가 사실상 비어있습니다.

- `README.md`: 한 줄 메모 수준 — 기술 스택, 실행 방법, 구조 정보 없음
- `CLAUDE.md`: `＠README.md 파일을 참고해` 한 줄 — 전각 `＠`(U+FF20)를 사용해 Claude Code의 파일 참조 기능이 실제로 동작하지 않음

두 파일을 보강하면 프로젝트 복귀 시 빠른 컨텍스트 파악과 Claude Code 작업 정확도가 높아집니다.

---

## 프로젝트 현황 (탐색 결과)

| 항목 | 내용 |
|------|------|
| 프로젝트명 | LITTLE KOSTO - Data Scientist Portfolio |
| 언어 | HTML5, Vanilla JavaScript |
| CSS | Tailwind CSS (CDN 방식) |
| 기타 라이브러리 | SmoothScroll 1.4.10 (CDN) |
| 빌드 도구 | 없음 (package.json 없음) |
| 소스 파일 | `index.html` 단일 파일 (302줄) |

---

## 수정 대상 파일

- `D:\workspace\my-profile-site\README.md`
- `D:\workspace\my-profile-site\CLAUDE.md`

---

## 수정안

### README.md

```markdown
# LITTLE KOSTO — Data Scientist Portfolio

데이터 사이언티스트 포트폴리오 웹사이트입니다.

## 기술 스택

- HTML5, Vanilla JavaScript
- Tailwind CSS (CDN)
- SmoothScroll 1.4.10 (CDN)

## 실행 방법

빌드 없이 브라우저에서 바로 열 수 있습니다.

```bash
# 방법 1: 파일 직접 열기
index.html을 브라우저에 드래그

# 방법 2: 로컬 서버 (선택)
npx serve .
```

## 페이지 구조

| 섹션 | 내용 |
|------|------|
| Hero | 이름, 직함, 소개 문구 |
| About | 자기소개 및 관심사 |
| Skills | 기술 스택 카드 6개 |
| Projects | 프로젝트 카드 4개 |
| Contact | 이메일, SNS 링크 |

## 배포

정적 파일 배포 (GitHub Pages, Netlify, Vercel 등)
```

---

### CLAUDE.md

```markdown
@README.md

## 프로젝트 구조

- 소스 파일: `index.html` 단 하나 (모든 섹션 포함)
- 빌드 시스템 없음 — package.json, node_modules 없음

## 작업 시 주의사항

- CSS는 Tailwind CDN 클래스 기반 — 별도 CSS 파일 없음
- 외부 라이브러리는 모두 CDN으로 로드 (npm 설치 불필요)
- 섹션 ID: `#about`, `#skills`, `#projects`, `#contact`
```

---

## 변경 요약

| 파일 | 기존 | 수정 |
|------|------|------|
| `README.md` | 한 줄 메모 | 기술스택·실행방법·구조 추가 |
| `CLAUDE.md` | 전각 `＠` 참조 (동작 안 함) | 반각 `@` 수정 + 작업 컨텍스트 추가 |

---

## 검증 방법

1. README.md — GitHub 또는 VSCode Preview에서 렌더링 확인
2. CLAUDE.md — 새 대화에서 `@CLAUDE.md`를 Claude에 전달 시 컨텍스트가 정상 포함되는지 확인
