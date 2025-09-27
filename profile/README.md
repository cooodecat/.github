# Otto - GitHub과 AWS를 연결하는 CI/CD 자동화 플랫폼

## 프로젝트 소개

Otto는 AI 시대에 누구나 쉽게 배포할 수 있도록 지원하는 CI/CD 자동화 플랫폼입니다.

최근 AI의 발전으로 누구나 손쉽게 코드를 작성할 수 있게 되었지만, 작성된 코드를 실제 서비스로 배포하는 과정은 여전히 높은 진입 장벽으로 남아 있습니다. Otto는 이러한 배포의 문턱을 낮추어, 바이브 코더들도 복잡한 AWS 설정 없이 GitHub 코드를 실제 서비스로 쉽게 배포할 수 있도록 만들었습니다.

### 핵심 가치

- **접근성**: 비개발자도 드래그앤드롭으로 CI/CD 파이프라인 구성 가능
- **자동화**: GitHub 푸시만으로 AWS 빌드와 배포가 자동 실행
- **투명성**: 실시간 로그로 배포 과정을 학습하며 이해도 향상
- **통합성**: GitHub과 AWS 서비스를 원스톱으로 연결

### 배포 URL

- Frontend: [https://codecat-otto.shop](https://codecat-otto.shop)
- Backend: [https://api.codecat-otto.shop](https://api.codecat-otto.shop)

## 팀원

| [<img src="https://github.com/GigaGukBab.png" width="200px" alt=""/>](https://github.com/GigaGukBab) | [<img src="https://github.com/kokominji.png" width="200px">](https://github.com/kokominji) | [<img src="https://github.com/kimkimkimbo.png" width="200px">](https://github.com/kimkimkimbo) | [<img src="https://github.com/52galuser.png" width="200px">](https://github.com/52galuser) | [<img src="https://github.com/jeeyuni.png" width="200px">](https://github.com/jeeyuni) | [<img src="https://github.com/roarjang.png" width="200px">](https://github.com/roarjang) |
| :--------------------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------: | :------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------: |
|                            [👑 **한진우**](https://github.com/GigaGukBab)                            |                         [**고민지**](https://github.com/kokominji)                         |                          [**김보아**](https://github.com/kimkimkimbo)                          |                         [**유호준**](https://github.com/52galuser)                         |                        [**이지윤**](https://github.com/jeeyuni)                        |                        [**장준영**](https://github.com/roarjang)                         |

## 주요 기능

### 1. 시각적 파이프라인 빌더

- 드래그앤드롭으로 CI/CD 파이프라인 구성
- 15개 이상의 사전 정의된 노드 타입
- 병렬 실행 및 조건부 분기 지원
- 실시간 파이프라인 실행 상태 시각화

### 2. 실시간 모니터링

- WebSocket 기반 빌드 로그 스트리밍
- Phase별 로그 그룹화 및 필터링
- 빌드 진행률 및 소요 시간 추적
- ANSI 색상 코드 지원

### 3. GitHub 통합

- GitHub OAuth 인증
- GitHub App을 통한 자동 웹훅 등록
- 리포지토리별 빌드 트리거 설정
- Pull Request 상태 자동 업데이트

### 4. AWS 자동화

- CodeBuild 프로젝트 자동 생성/관리
- ECS 서비스 및 태스크 정의 자동 구성
- ECR 리포지토리 자동 생성
- IAM 역할 및 정책 자동 설정

## 기술 스택

### Frontend

- **Framework**: SvelteKit 2.22.0, Svelte 5.0
- **UI**: XYFlow, Tailwind CSS 4.0
- **Real-time**: Socket.io Client
- **Type Safety**: TypeScript, Nestia SDK

### Backend

- **Framework**: NestJS 11.x, Fastify
- **Database**: PostgreSQL, Redis
- **Type Safety**: Nestia, Typia
- **AWS SDK**: CodeBuild, ECS, ECR, EventBridge

### Infrastructure

- **CI/CD**: AWS CodeBuild
- **Container**: Docker, AWS ECR
- **Orchestration**: AWS ECS Fargate
- **Monitoring**: CloudWatch, EventBridge
- **Serverless**: AWS Lambda

## 시스템 아키텍처

<img width="3136" height="1856" alt="otto-architecture" src="https://github.com/user-attachments/assets/2a14e898-34af-4436-a812-474d508261ee" />


### 아키텍처 구성 요소

1. **Frontend (SvelteKit)**
   - Vercel 배포
   - 시각적 파이프라인 빌더
   - 실시간 로그 뷰어

2. **Backend (NestJS)**
   - ECS Fargate 배포
   - API 서버 및 WebSocket
   - AWS 서비스 오케스트레이션

3. **AWS Services**
   - CodeBuild: 소스 코드 빌드
   - ECS: 컨테이너 배포
   - ECR: Docker 이미지 저장
   - EventBridge: 이벤트 라우팅
   - Lambda: 이벤트 처리
   - CloudWatch: 로그 수집

### 데이터 플로우

1. **빌드 실행 플로우**

   ```
   User → Frontend → Backend API → CodeBuild → ECR → ECS
   ```

2. **실시간 로그 플로우**

   ```
   CodeBuild → CloudWatch → EventBridge → Lambda → Backend → WebSocket → Frontend
   ```

3. **GitHub 웹훅 플로우**
   ```
   GitHub → Webhook → Backend → CodeBuild → Auto Deploy
   ```

## 프로젝트 구조

```
otto/
├── otto-front/             # Frontend 프로젝트
│   └── src/
│       ├── lib/            # 라이브러리 및 컴포넌트
│       └── routes/         # SvelteKit 라우팅
│
└── otto-handler/           # Backend 프로젝트
    ├── src/
    │   ├── auth/           # 인증 모듈
    │   ├── project/        # 프로젝트 관리
    │   ├── pipeline/       # 파이프라인 관리
    │   ├── aws/            # AWS 서비스
    │   └── logs/           # 로그 시스템
    └── lambda/             # Lambda 함수
```


**Otto** - 누구나 쉽게 배포할 수 있는 세상을 만들다
