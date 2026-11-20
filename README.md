# Portfolio

> 본 프로젝트들은 모두 바이브코딩 기법으로 AI 도구를 활용하여 개발하였습니다.

## 프로젝트 한눈에 보기

| 프로젝트 | 한 줄 소개 | 주요 기술 |
|---|---|---|
| [Company Web](./new_company) | 회사 홈페이지 + 관리자/게시판 시스템 | Next.js 15, React 19, TypeScript, MySQL |
| [CoupleLink](./wedding-matching) | 국제결혼 매칭 플랫폼 (한국어/베트남어) | React 19, Node.js, Express, MySQL |
| [통합 엑셀 분석기](./quarterly-report-graph-generator) | 분기 보고서용 통행량 엑셀 분석·그래프 생성 데스크톱 도구 | Python, PyQt5, pandas, matplotlib |
| [시각 지능 색차 식별 시스템](./vision) | 색차 식별·데이터 관리 데스크톱 앱 | Electron, Node.js, Express |

---

## 1. Company Web — 회사 홈페이지

회사 소개, 사업 영역, 특허, 오시는 길, 게시판을 갖춘 기업 웹사이트입니다. 관리자 로그인과 게시판 글쓰기·이미지 업로드 기능을 직접 구현했습니다.

- **주요 기능**
  - 회사 소개 / 연혁 / 특허 / 사업·서비스 소개 페이지
  - 게시판(공지·일반·크라우드) 목록·상세·작성·수정·삭제, 검색, 페이지네이션
  - 관리자 로그인(세션 인증) 및 대시보드
  - 카카오맵 연동 오시는 길, 지도 기반 지역 선택 UI
  - 스크롤 애니메이션·페이지 전환 효과, SEO(sitemap, robots, OG 이미지)
- **기술 스택**: Next.js 15 (App Router) · React 19 · TypeScript · Tailwind CSS 4 · MySQL · Drizzle ORM · iron-session · Tiptap · Framer Motion · GSAP · Kakao Map
- 👤 **담당 역할**: 프론트엔드 개발

<details>
<summary>📁 폴더 구조 보기</summary>

```
new_company/
├── app/                          # Next.js App Router
│   ├── page.tsx                  # 메인 페이지
│   ├── layout.tsx
│   ├── admin/                    # 관리자 (로그인, 대시보드)
│   ├── api/                      # API Routes
│   │   ├── admin/                # login / logout / session
│   │   ├── board/                # 게시판 CRUD
│   │   ├── images/
│   │   └── upload/
│   ├── board/                    # 게시판 (목록 / 상세 / 작성)
│   ├── business/                 # 사업영역 / 서비스 허브
│   ├── info/                     # 회사소개 / 특허 / 오시는 길
│   ├── reference/                # 서비스 현황
│   ├── agree/                    # 이용약관
│   ├── privacy/                  # 개인정보처리방침
│   ├── error.tsx
│   ├── not-found.tsx
│   ├── robots.ts
│   ├── sitemap.ts
│   └── opengraph-image.tsx
├── components/
│   ├── admin/                    # 관리자 로그인 폼
│   ├── board/                    # 게시판 UI (목록, 상세, 에디터, 검색, 페이지네이션)
│   ├── layout/                   # 헤더, 푸터, 네비게이션, 스크롤/전환 효과
│   ├── sections/                 # 메인 섹션 (Hero, Manifesto, Why, 3D Showcase 등)
│   └── ui/                       # 카카오맵, 지도 선택기, 애니메이션 공통 UI
├── lib/
│   ├── auth/                     # 세션 관리
│   ├── data/                     # 서비스 데이터
│   ├── db/                       # DB 연결, 스키마(Drizzle), 쿼리 모듈
│   │   └── queries/              # board, config, history, installation, menu, patent, service
│   ├── map-utils.ts
│   ├── menu.ts
│   └── utils.ts
├── public/assets/images/         # 이미지 리소스 (소개, 특허, 설치사례, 서비스 등)
├── scripts/                      # 유지보수 스크립트
├── changelog/                    # 단계별 작업 이력
├── docs/                         # 설계·분석 문서
├── middleware.ts                 # 라우트 보호
├── drizzle.config.ts
├── next.config.ts
├── tsconfig.json
├── eslint.config.mjs
├── postcss.config.mjs
├── package.json
├── .env.example
└── README.md
```

</details>

---

## 2. CoupleLink — 국제결혼 매칭 플랫폼

다양한 국적의 회원이 프로필을 등록하고, 매칭 점수 기반으로 상대를 탐색하며, 관심 표시와 매칭 요청으로 연결되는 웹 서비스입니다.

- **주요 기능**
  - 회원가입/로그인(JWT), 관리자 승인제, 비밀번호 재설정, 회원 탈퇴
  - 상세 프로필(기본 정보·생활 습관·MBTI·키워드)과 사진 최대 3장 관리
  - **매칭률 계산(0~100점)**: 관심사·나이 선호도·결혼 계획·직업 항목별 가중치 적용
  - 오늘의 추천, 조건 필터·정렬, 관심 표시, 매칭 요청 수락/거절
  - 인증 서류 제출 및 관리자 심사, 알림 시스템
  - 관리자 페이지(회원 승인, 서류 심사, 이력 조회, 메시지 발송)
  - 한국어 / 베트남어 다국어 지원
- **기술 스택**: React 19 · Vite · Tailwind CSS · Node.js · Express · MySQL · Sequelize · JWT · Multer(파일 매직 바이트 검증)
- 👤 **담당 역할**: 풀스택 개발

<details>
<summary>📁 폴더 구조 보기</summary>

```
wedding-matching/
├── backend/                      # Node.js 서버
│   ├── server.js
│   ├── config/                   # 상수 설정
│   ├── middleware/               # 인증, 요청 제한, 파일 업로드
│   ├── models/                   # DB 모델 (user, interest, keyword, profileDetail, userImage, verification 등)
│   ├── routes/
│   │   ├── auth.js
│   │   ├── notifications.js
│   │   ├── verification.js
│   │   └── users/                # admin, images, likes, list, profile
│   ├── services/                 # 스케줄러
│   ├── utils/                    # 매칭 점수 계산, 나이 계산, 검증, 로거 등
│   ├── __tests__/                # 단위 테스트
│   ├── package.json
│   └── .env.example
├── src/                          # React (Vite) 프론트엔드
│   ├── main.jsx
│   ├── App.jsx
│   ├── index.css
│   ├── screens/
│   │   ├── LandingScreen.jsx
│   │   ├── HomeScreen.jsx
│   │   ├── AdminScreen.jsx
│   │   ├── admin/                # 회원 / 인증 / 알림 관리 탭
│   │   └── home/                 # 필터바, 카드 컴포넌트 등
│   ├── components/               # 모달(로그인, 가입, 프로필 수정, 인증 등), 카드, 입력 컴포넌트
│   ├── contexts/                 # 인증, 다국어 컨텍스트
│   ├── hooks/
│   ├── services/                 # API 클라이언트, 인증/좋아요/인증서류 서비스
│   ├── utils/
│   ├── lib/                      # 다국어 번역, 정적 데이터
│   └── __tests__/
├── public/                       # 이미지 리소스
├── docs/                         # 기능 명세, 보안, 개선 보고서
├── index.html
├── vite.config.js
├── tailwind.config.js
├── postcss.config.js
├── ecosystem.config.js           # PM2 설정
├── deploy.sh                     # 배포 스크립트
├── apache-vhost.conf.example
├── package.json
└── README.md
```

</details>

---

## 3. 통합 엑셀 분석기 — 분기 보고서 그래프 생성기

분기별로 흩어져 있던 4개의 엑셀 분석 프로젝트를 **하나의 코드베이스로 통합**한 데스크톱 도구입니다. 엑셀 파일을 열면 파일명에서 분기를 자동 감지하고, 해당 분기에 맞는 셀 범위로 통행량 그래프를 생성합니다.

- **주요 기능**
  - 파일명(`2분기`, `Q2`, `2Q` 등)에서 분기 자동 감지
  - 분기·지역별 셀 위치 차이를 **설정 파일(config)로 중앙 관리**
  - 지역별 분석 모듈(구리, 달서, 달성, 장성 등) 분리 구조
  - 상관분석 및 분기별 분석 그래프 출력
- **기술 스택**: Python · PyQt5 · pandas · NumPy · SciPy · matplotlib · openpyxl · PyInstaller
- 👤 **담당 역할**: 풀스택 개발

<details>
<summary>📁 폴더 구조 보기</summary>

```
quarterly-report-graph-generator/
├── main_app.py                   # 메인 실행 파일 (GUI)
├── configs/
│   ├── __init__.py
│   └── quarter_configs.py        # 분기별 설정
├── modules/                      # 지역별 엑셀 분석 모듈
│   ├── __init__.py
│   ├── common_utils.py
│   ├── dalseo.py
│   ├── dalseong_hwawon.py
│   ├── dalseong_nampyeong.py
│   ├── guri_3.py
│   └── jangsung.py
├── ExcelAnalyzer.spec            # PyInstaller 빌드 설정
├── requirements.txt
├── SPECIFICATION.md
├── CELL_POSITION_REFERENCE.md
└── README.md
```

</details>

---

## 4. 시각 지능 색차 식별 시스템

시각 지능을 활용해 색상 차이를 식별하고 분석 데이터를 관리하는 Electron 기반 데스크톱 애플리케이션입니다.

- **주요 기능**
  - 이미지/센서 데이터 기반 색차 식별 및 분석
  - 분석 데이터의 로컬 저장·관리
  - JWT 기반 사용자 인증 및 세션 관리
  - Express 로컬 서버 내장(데이터 처리 및 API)
  - electron-builder로 Windows 설치 파일(.exe) 배포
- **기술 스택**: Electron · Node.js · Express.js · JSON Web Token · electron-builder
- 👤 **담당 역할**: 외부 기기와 api 연동 및 프론트엔드 개발

<details>
<summary>📁 폴더 구조 보기</summary>

```
vision/
├── electron.js                   # Electron 메인 프로세스
├── preload.js
├── static/
│   ├── index.html
│   ├── favicon.ico
│   ├── placeholder_video.png
│   ├── css/
│   │   └── style.css
│   ├── js/
│   │   └── app.js
│   └── sounds/
│       └── alarm.mp3
├── package.json
└── README.md
```

</details>

---

## 기술 스택 요약

| 분야 | 기술 |
|---|---|
| Frontend | React, Next.js, TypeScript, Tailwind CSS, Vite |
| Backend | Node.js, Express |
| Database | MySQL, Sequelize, Drizzle ORM |
| Desktop | Electron, PyQt5 |
| Data / Script | Python, pandas, NumPy, SciPy, matplotlib |
| Auth / Security | JWT, iron-session, bcrypt, Rate Limiting |
| Deploy / Tools | PM2, Apache, electron-builder, PyInstaller, Git |

---
