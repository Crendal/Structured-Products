# 배포 안내 (Windows CMD)

1. ZIP 압축을 해제한 후 `Structured-Products-Final` 폴더를 열고 탐색기 주소창에 `cmd`를 입력합니다.
2. Git과 GitHub CLI를 설치했다면 다음을 실행합니다.

```bat
gh auth login
git init -b main
git add .
git commit -m "Initial Structured Products site"
gh repo create Structured-Products --public --source=. --remote=origin --push
```

3. GitHub에서 `Settings → Pages → Build and deployment → Deploy from a branch`로 이동합니다. `main`과 `/(root)`를 선택하여 저장합니다.
4. `https://아이디.github.io/Structured-Products/`로 접속합니다.

## 구조

- `/` : 메인 페이지
- `/els-comparison/` : 업로드한 최종 ELS Map / 증권사 및 상품 비교
- `/pricing/` : 향후 프라이싱 개발 공간 (실제 계산 기능 없음)

## 데이터 교체

현재 비교 HTML에는 데이터가 내장되어 있고 일반 방문자용 파일 업로드 UI는 숨겨져 있습니다. 방문자 전체의 데이터를 바꾸려면 **업데이트된 데이터를 포함하는 최종 HTML을 생성한 후** `els-comparison/index.html` 파일을 교체하고 Commit하세요. 단순히 `data` 폴더에 파일만 추가해도 사이트에 자동 반영되지는 않습니다.

## 주의

Public 저장소는 코드와 내장 데이터가 공개됩니다. 게시 전 외부 공개가 가능한 데이터인지 확인하세요.
