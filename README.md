# Platform Config Repository

Spring Cloud Config Server를 위한 설정 저장소입니다.

이 저장소는 Spring Cloud Config Server에서 사용하는 설정 파일들을 포함합니다.

## 구조

```
platform-config/
├── config/
│   └── wallet-gateway-api/
│       ├── dev.yaml
│       ├── qa.yaml
│       ├── stg.yaml
│       └── prod.yaml
├── .github/
│   └── pull_request_template.md
├── CODEOWNERS
└── README.md
```

## 서비스

서비스를 위한 환경별 설정 파일:

- `config/${service-name}/dev.yaml` - 개발 환경
- `config/${service-name}/qa.yaml` - QA 환경
- `config/${service-name}/stg.yaml` - 스테이징 환경
- `config/${service-name}/prod.yaml` - 운영 환경

## 주의사항

- 운영 환경의 민감한 정보(비밀번호, API 키 등)는 환경 변수나 Vault를 통해 관리하는 것을 권장합니다.
- JWT Secret, Database Password, Redis Password 등은 환경 변수로 관리해야 합니다.
- 프로덕션 환경에서는 모든 민감한 정보를 환경 변수로 설정해야 합니다.

## Pull Request 가이드

### CODEOWNERS

이 저장소는 CODEOWNERS 파일을 사용하여 자동으로 리뷰어를 지정합니다. 설정 파일을 변경하면 해당 경로에 지정된 팀이나 사용자가 자동으로 리뷰어로 추가됩니다.

CODEOWNERS 파일을 수정하려면:

1. `CODEOWNERS` 파일을 열어 리뷰어를 지정합니다
2. 형식: `<경로> <@username 또는 @team>`
3. 예시: `/config/wallet-gateway-api/ @wallet-team @backend-team`

### PR 템플릿

Pull Request 생성 시 템플릿이 자동으로 적용됩니다. 다음 정보를 포함해주세요:

- 변경된 서비스 및 환경
- 변경 내용 상세 (변경 전/후)
- 변경 사유
- 영향도 분석
- 테스트 방법

PR 템플릿은 `.github/pull_request_template.md`에 위치합니다.
