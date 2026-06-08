# JNB Logistics - GitHub Pages 배포 가이드

## 정적 사이트 구조

```
_github_pages/          ← 이 폴더 전체를 GitHub에 올림
├── index.html          ← 메인 홈
├── intro/
│   ├── index.html      ← Company / About us
│   └── network/
│       └── index.html  ← Network (11개 지점)
├── service/
│   └── index.html      ← Service Scope
├── performance/
│   └── index.html      ← Performance
├── template/           ← 테마 CSS/JS/이미지 (50MB)
├── css/                ← custom.css 등
└── img/                ← 서브비주얼 이미지
```

---

## STEP 1. GitHub 계정 및 저장소 생성

1. https://github.com 접속 → 로그인 (없으면 회원가입)
2. 우상단 **[+ New repository]** 클릭
3. 설정:
   - Repository name: `jnbgls` (또는 `jnb-website`)
   - Visibility: **Public** (GitHub Pages 무료 이용 조건)
   - Initialize: 체크 없이 생성
4. **[Create repository]** 클릭

---

## STEP 2. 파일 업로드

### 방법 A: GitHub 웹 업로드 (소규모, 추천 아님 - 파일 많음)

### 방법 B: GitHub Desktop 사용 (추천)

1. https://desktop.github.com 다운로드 및 설치
2. 로그인 후 **[Clone a repository]** → 위에서 만든 repo 선택
3. 로컬 경로를 `_github_pages` 폴더로 지정하거나,
   `_github_pages` 폴더 내용을 clone한 폴더에 복사
4. **[Commit to main]** → **[Push origin]**

### 방법 C: Git 명령어 (빠름)

```bash
# _github_pages 폴더로 이동
cd "C:\전산개발\JNB 홈피 소스\www\_github_pages"

# Git 초기화 및 업로드
git init
git add .
git commit -m "Initial static site deploy"
git branch -M main
git remote add origin https://github.com/[계정명]/[저장소명].git
git push -u origin main
```

---

## STEP 3. GitHub Pages 활성화

1. GitHub 저장소 → **Settings** 탭
2. 좌측 메뉴 **Pages** 클릭
3. **Source**: `Deploy from a branch`
4. **Branch**: `main` / `/ (root)` 선택
5. **[Save]** 클릭
6. 약 1~3분 후 `https://[계정명].github.io/[저장소명]/` 으로 접속 가능

---

## STEP 4. 커스텀 도메인 연결 (jnbgls.com)

### GitHub 설정
1. Settings → Pages → **Custom domain**에 `www.jnbgls.com` 입력
2. **[Save]** 클릭
3. `_github_pages` 폴더에 `CNAME` 파일 생성 (내용: `www.jnbgls.com`)

### DNS 설정 (도메인 관리 업체에서)
| 레코드 타입 | 호스트 | 값 |
|------------|--------|-----|
| CNAME | www | [계정명].github.io |
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |

DNS 전파: 최대 24~48시간 소요

### HTTPS 강제 적용
- Settings → Pages → **Enforce HTTPS** 체크 (DNS 연결 완료 후 활성화됨)

---

## STEP 5. 향후 페이지 수정 방법

1. `_github_pages/` 내 HTML 파일 직접 수정
2. GitHub Desktop에서 변경사항 확인 → Commit → Push
3. 1~2분 내 자동 반영

---

## 주요 경로 매핑 (구 JSP → 새 HTML)

| 구 주소 | 새 주소 |
|---------|---------|
| `/index.jsp` | `/` |
| `/intro/index.jsp` | `/intro/` |
| `/intro/network/index.jsp` | `/intro/network/` |
| `/service/index.jsp` | `/service/` |
| `/performance/index.jsp` | `/performance/` |

---

## 비용 요약

| 항목 | 비용 |
|------|------|
| GitHub Pages 호스팅 | **무료** |
| GitHub 저장소 (Public) | **무료** |
| 도메인 (jnbgls.com 유지) | 기존 비용 그대로 |
| SSL (HTTPS) | **무료** (Let's Encrypt 자동) |

---

## 문의
페이지 수정, 추가 요청은 `_github_pages/` 폴더 내 해당 HTML 파일을 수정하면 됩니다.
