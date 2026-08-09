# flowwork-apis

[flowwork](https://github.com/geeshow/flowwork)에서 사용하는 사내 API 명세를 **Bruno** 컬렉션 형태로 모아둔 저장소입니다.

## 구성

```
bruno.json              # Bruno 컬렉션 매니페스트
environments/           # 환경 변수 (Bruno 환경)
  core.bru              #   coreBaseUrl
  payments.bru          #   baseUrl, authToken(vault:// 참조)
core/                   # 코어 도메인 (약정/사용자/계좌/메타코드)
customer/               # 고객 정보
payments/               # 정산
```

각 `.bru` 파일이 하나의 API 요청입니다. 폴더 = 분류입니다.

## 커스텀: 응답 필드(`output`)

각 요청의 `docs` 블록에 `output:` 줄로 응답(output) 필드를 적어둡니다. flowwork는 이를 읽어
결과 표의 컬럼 후보 / 의존 조회의 값 필드로 사용합니다.

```
docs {
  output: app_user_id, sec_user_id, CIF, name, phone, email
}
```

## 사용

[Bruno](https://www.usebruno.com/) 앱에서 이 폴더를 컬렉션으로 열면 됩니다.

## 참고

- `authToken` 값의 `vault://...` 는 실제 시크릿이 아니라 **참조 문자열**입니다. 실제 시크릿
  치환은 flowwork 프록시가 호출 직전에 수행합니다.
- 기본 URL은 데모용 목 업스트림(`http://localhost:9100`)을 가리킵니다.
