# 🤖 n8n 리서치봇

채팅으로 주제를 입력하면 인터넷 리서치 → AI 요약 → HTML 리포트 생성 → Google Drive 저장까지 전 과정을 자동화하는 리서치 봇입니다.

## 📋 프로젝트 개요

반복적인 조사·정리 업무를 자동화해 리서치 소요 시간과 정리 비용을 크게 줄이는 것이 목적입니다. 비전문가도 일관된 품질의 리포트 결과물을 확보할 수 있습니다.

### 데모
- **Chat URL**: [https://imjoeyu.app.n8n.cloud/webhook/39780bb0-c4c4-4015-86b4-475c62d16eff/chat](https://imjoeyu.app.n8n.cloud/webhook/39780bb0-c4c4-4015-86b4-475c62d16eff/chat)
- **생성된 리포트 예시**: `research-report-반도체_산업에_대해_알려줘-2026-01-30.html` (screenshots 폴더 참조)

## 🛠 사용 기술 스택

- **Workflow Automation**: n8n
- **LLM**: GPT 모델 (리포트 생성)
- **Search API**: SerpAPI (구글 검색)
- **Storage**: Google Drive
- **Output Format**: HTML 리포트

## 🔄 동작 흐름 (Workflow)

### 1. Chat Trigger
- 사용자가 채팅으로 리서치 주제 입력
- 예: "최근 K-뷰티 트렌드에 대해 알려줘"

### 2. Query Generator
- 입력 문장에서 핵심 키워드 추출
- 다양한 관점의 검색 쿼리 생성

### 3. Search (SerpAPI)
- 최신 뉴스 / 공식 문서 기반 검색
- 검색 결과 수집 및 정리

### 4. Aggregate & Normalize
- 검색 결과를 하나의 item으로 통합
- 리포트 생성에 필요한 데이터 구조 표준화

### 5. Report Generator (LLM)
- 고정된 HTML 레이아웃 기반 리포트 생성
- 주제 이탈 방지 규칙 적용
- 섹션 구조: 개요 / 동향 / 과제 / 사례 / 전망

### 6. HTML → File 변환
- HTML 문자열을 Binary 파일로 변환
- 파일명 자동 생성

### 7. Google Drive Upload
- HTML 리포트를 Drive에 자동 저장

## ✨ 주요 기능 포인트

### ✅ 주제 고정 로직
- 리포트 생성 시 입력 주제를 단일 source로 고정
- 동문서답/주제 이탈 문제 해결

### ✅ 레이아웃 표준화
- 항상 동일한 리포트 구조와 디자인 유지
- 발표/공유 가능한 형태의 결과물 생성

### ✅ 완전 자동화
- 사람 개입 없이 리서치 → 정리 → 저장까지 완료

### ✅ 확장 가능성
- PDF 변환
- Slack / Notion 연동
- 리포트 템플릿 다중화 가능

## 📊 기대 효과

- 리서치 정리 시간 대폭 절감
- 비전문가도 일관된 리포트 결과물 확보
- 반복 리서치 업무의 자동화
- 개인/팀 단위 지식 아카이빙에 활용 가능

## 🚀 설치 및 사용 방법

### 사전 준비

1. **n8n 설치**
   - Self-hosted: [n8n 설치 가이드](https://docs.n8n.io/hosting/)
   - Cloud: [n8n.cloud](https://n8n.cloud/) 가입

2. **필요한 API 키**
   - OpenAI API Key (GPT 모델 사용)
   - SerpAPI Key (Google 검색)
   - Google Cloud Service Account (Drive 업로드)

### 워크플로우 Import

1. n8n 대시보드에서 "Add workflow" 클릭
2. "Import from File" 선택
3. `workflows/research-bot.json` 파일 업로드
4. Credentials 설정
   - OpenAI Account
   - SerpAPI Account
   - Google Drive Account

### 환경 변수 설정

`.env` 파일을 생성하고 다음 정보를 입력하세요:

```env
OPENAI_API_KEY=your_openai_api_key
SERPAPI_KEY=your_serpapi_key
GOOGLE_DRIVE_SERVICE_ACCOUNT_EMAIL=your_service_account_email
```

### 실행

1. n8n에서 워크플로우 활성화
2. Chat URL로 접속
3. 리서치 주제 입력
4. 생성된 리포트를 Google Drive에서 확인

## 📁 프로젝트 구조

```
n8n-research-bot/
├── workflows/
│   └── research-bot.json         # n8n 워크플로우 파일
├── docs/
│   └── setup-guide.md            # 상세 설정 가이드
├── screenshots/
│   ├── workflow-overview.png     # 워크플로우 전체 구조
│   └── report-sample.html        # 생성된 리포트 샘플
├── .env.example                   # 환경 변수 템플릿
├── .gitignore
└── README.md
```

## 🔒 보안 주의사항

- API 키는 절대 GitHub에 업로드하지 마세요
- `.env` 파일은 `.gitignore`에 포함되어 있습니다
- Service Account JSON 파일도 반드시 제외하세요

## 🤝 기여하기

이슈 제보나 개선 제안은 언제든 환영합니다!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 라이선스

이 프로젝트는 MIT 라이선스를 따릅니다.

## 📧 문의

프로젝트에 대한 문의사항이 있으시면 이슈를 등록해주세요.

---

**Built with n8n** 🚀
