# 예시: `vehicle_speed_estimation`

레포:
- <https://github.com/swhan0329/vehicle_speed_estimation>

이 문서는 `vehicle_speed_estimation`을 실제로 clone한 뒤,  
Codex co-author trailer가 자동으로 붙게 만드는 가장 현실적인 흐름을 설명합니다.

핵심 목표는 아래 문장이 커밋에 자동으로 들어가게 하는 것입니다.

```text
Co-authored-by: codex <codex@openai.com>
```

## 누구에게 필요한가

아래가 맞으면 이 예시를 따르면 됩니다.

- `vehicle_speed_estimation`을 직접 clone해서 작업할 예정
- Codex app 또는 Codex CLI로 코드 수정을 도와받을 예정
- 이후 내가 직접 `git commit`, `git push`, PR, merge를 할 예정

## 실제 따라 하기

### 1. 레포를 clone 한다

```bash
git clone https://github.com/swhan0329/vehicle_speed_estimation.git
cd vehicle_speed_estimation
```

### 2. co-author 자동 추가를 켠다

이 레포에는 이미 필요한 파일이 들어 있으므로, 아래만 실행하면 됩니다.

```bash
bash scripts/setup-codex-attribution.sh
```

이 명령은 로컬 Git 설정에 아래를 넣습니다.

```bash
core.hooksPath=.githooks
commit.template=.gitmessage
ai.coauthor=codex <codex@openai.com>
```

중요:

- 같은 clone에서는 한 번만 하면 됩니다
- 새로 clone 받으면 다시 해야 합니다

### 3. Codex로 레포를 연다

둘 중 하나면 됩니다.

- Codex app: `vehicle_speed_estimation` 폴더를 연다
- Codex CLI: 레포 폴더에서 `codex`를 실행한다

예시 프롬프트:

```text
이 레포에서 작은 개선점 하나를 찾아 수정하고 테스트까지 돌려줘.
```

### 4. 테스트를 돌린다

이 레포는 둘 다 됩니다.

```bash
pytest -q
```

또는

```bash
python -m unittest discover -s tests
```

### 5. 평소처럼 커밋한다

```bash
git add .
git commit -m "Fix small issue in vehicle_speed_estimation"
```

이때 `Co-authored-by: codex <codex@openai.com>`를 직접 적을 필요는 없습니다.  
훅이 자동으로 붙입니다.

### 6. 실제로 붙었는지 확인한다

```bash
git show -s --format=%B HEAD
```

정상이라면 아래처럼 보입니다.

```text
Fix small issue in vehicle_speed_estimation

Co-authored-by: codex <codex@openai.com>
```

### 7. 원격으로 push 한다

```bash
git push origin <브랜치명>
```

### 8. GitHub에서 PR을 열고 merge 한다

여기부터는 평소 GitHub 흐름과 같습니다.

## 가장 많이 헷갈리는 점

### Codex app/CLI를 설치하면 자동으로 되는가?

아니요.

- Codex 설치/로그인: 사용자 기준 준비
- 이 레포에서 co-author 훅 켜기: 레포 clone 기준 준비

둘은 별개입니다.

### 왜 새 clone에서는 다시 해야 하나?

`bash scripts/setup-codex-attribution.sh`는 레포 파일이 아니라  
로컬 Git 설정 `.git/config`를 바꾸기 때문입니다.

즉:

- 같은 clone: 한 번만
- 새 clone: 다시 실행

## 한 줄 요약

`vehicle_speed_estimation`에서는 아래만 기억하면 됩니다.

1. clone 한다
2. `bash scripts/setup-codex-attribution.sh` 한 번 실행
3. Codex로 수정
4. 테스트
5. 평소처럼 `git commit`
6. 평소처럼 `git push`

그러면 이후 커밋마다 아래가 자동으로 붙습니다.

```text
Co-authored-by: codex <codex@openai.com>
```
