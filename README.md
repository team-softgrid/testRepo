# testRepo
깃허브 플로우를 실습하기 위한 저장소

## GitHub Flow 절차

1. **메인 브랜치 생성**
   - `main` 브랜치는 항상 배포 가능한 상태를 유지합니다.
   - 모든 작업은 `main` 브랜치에서 새로운 브랜치를 생성하여 진행합니다.

2. **기능 브랜치 생성**
   - 새로운 기능 개발이나 버그 수정을 위해 `main` 브랜치에서 새 브랜치를 생성합니다.
   - 브랜치 이름은 작업 내용을 명확하게 설명하도록 작성합니다.
   - 예: `feature/login-page`, `bugfix/header-layout`

3. **커밋 작성**
   - 작업 내용을 적절한 단위로 나누어 커밋합니다.
   - 커밋 메시지는 명확하고 상세하게 작성합니다.
   - 예: "로그인 페이지 UI 구현", "헤더 레이아웃 버그 수정"

4. **Pull Request 생성**
   - 작업이 완료되면 GitHub에서 Pull Request를 생성합니다.
   - PR 설명에는 변경사항과 관련된 상세 내용을 기록합니다.
   - 리뷰어를 지정하고 코드 리뷰를 요청합니다.

5. **리뷰 및 논의**
   - 지정된 리뷰어가 코드를 검토합니다.
   - 필요한 경우 토론을 진행하고 코드를 수정합니다.
   - 모든 리뷰어가 승인하면 다음 단계로 진행합니다.

6. **main 브랜치로 병합**
   - 모든 검토가 완료되면 `main` 브랜치로 병합합니다.
   - 병합 후에는 작업 브랜치를 삭제합니다.

7. **배포**
   - `main` 브랜치에 병합된 변경사항은 자동으로 또는 수동으로 배포됩니다.
   - 배포 후 문제가 없는지 확인합니다.

## 깃 푸쉬 코멘트 규칙
- 푸쉬 코멘트는 작업 내용을 간결하게 요약합니다.
- 커밋 메시지와 동일하거나 관련된 내용을 포함해야 합니다.
- 예:
  - "feature/login-page 브랜치 초기 작업 푸쉬"
  - "bugfix/header-layout 수정사항 반영"
  - "최종 리뷰 반영 후 main 브랜치 병합 준비"

## GitHub Flow 실제 사용 예시

### 1. 새로운 기능 개발 시나리오

#### 1.1 브랜치 생성
```bash
# main 브랜치에서 시작
git checkout main
git pull origin main

# 새 기능 브랜치 생성
git checkout -b feature/user-profile
```

#### 1.2 작업 및 커밋
```bash
# 파일 수정 후 스테이징
git add UserProfile.js
git add UserProfile.css

# 의미 있는 단위로 커밋
git commit -m "사용자 프로필 페이지 레이아웃 구현"

# 추가 수정 작업
git add UserProfile.js
git commit -m "프로필 이미지 업로드 기능 추가"
```

#### 1.3 원격 저장소에 푸시
```bash
git push origin feature/user-profile
```

### 2. 버그 수정 시나리오

#### 2.1 버그 수정 브랜치 생성
```bash
git checkout main
git checkout -b bugfix/login-error
```

#### 2.2 수정 및 테스트
```bash
# 버그 수정 후 커밋
git add LoginComponent.js
git commit -m "로그인 실패 시 에러 메시지 표시 버그 수정"

# 테스트 코드 추가
git add LoginComponent.test.js
git commit -m "로그인 에러 처리 테스트 케이스 추가"
```

### 3. Pull Request 생성 후 작업

#### 3.1 리뷰 반영
```bash
# 리뷰어의 피드백을 반영한 수정
git add LoginComponent.js
git commit -m "코드 리뷰 피드백 반영: 에러 처리 로직 개선"
git push origin bugfix/login-error
```

#### 3.2 main 브랜치 병합 준비
```bash
# main 브랜치의 최신 변경사항 동기화
git checkout main
git pull origin main
git checkout bugfix/login-error
git merge main

# 충돌 해결 후 푸시
git push origin bugfix/login-error
```

### 4. 배포 후 확인

#### 4.1 배포 후 모니터링
- 로그 모니터링
- 에러 추적
- 성능 메트릭 확인
- 사용자 피드백 수집

#### 4.2 문제 발생 시 빠른 대응
```bash
# 긴급 수정이 필요한 경우
git checkout -b hotfix/urgent-fix
# 수정 작업 진행
git commit -m "긴급: 서비스 중단 문제 해결"
git push origin hotfix/urgent-fix
```
