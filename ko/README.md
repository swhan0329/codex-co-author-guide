# Codex Co-author 가이드 (한국어)

이 문서는 [`sample-codex-coauthor`](https://github.com/sigridjineth/sample-codex-coauthor)를 실제 레포에 어떻게 붙여 쓰는지 설명합니다.

핵심은 간단합니다.

```text
Co-authored-by: codex <codex@openai.com>
```

이 문장을 `git commit` 할 때마다 자동으로 넣고 싶을 때 쓰는 방식입니다.

## 이게 정확히 뭔가

이건 Codex 자체를 설치하는 도구가 아닙니다.

- Codex app / CLI 설치: 사용자 기준 1회
- co-author 훅 설치: 레포 clone마다 1회

즉 Codex를 이미 쓰고 있고, 특정 레포의 커밋에 Codex를 contributor처럼 남기고 싶을 때 쓰는 레포별 설정입니다.

## 언제 쓰면 되나

아래가 맞으면 쓰면 됩니다.

- Codex app 또는 Codex CLI로 코드 수정 예정
- 내가 직접 `git commit` 할 예정
- GitHub에서 Codex co-author 표시를 남기고 싶음

아래면 굳이 필요 없습니다.

- Codex는 쓰지만 co-author 표시가 필요 없음
- 그냥 평소 커밋 흐름이면 충분함

## 설치하면 뭐가 달라지나

자동화되는 건 딱 하나입니다.

- `git commit -m "..."` 할 때 `Co-authored-by: codex <codex@openai.com>`가 자동으로 붙음

여전히 직접 하는 일:

- `git add`
- `git commit`
- `git push`
- PR 생성
- GitHub merge

## 기본 사용법

레포를 clone한 뒤 한 번만 실행합니다.

```bash
bash scripts/setup-codex-attribution.sh
```

그다음부터는 평소처럼 커밋하면 됩니다.

```bash
git add .
git commit -m "Fix small bug"
```

확인:

```bash
git show -s --format=%B HEAD
```

## 왜 clone마다 다시 해야 하나

이 설정은 로컬 Git 설정인 `.git/config`를 바꾸기 때문입니다.

즉:

- 같은 clone: 한 번만 하면 됨
- 새 clone: 다시 해야 함
- 다른 컴퓨터: 다시 해야 함

## 원본 sample repo에는 skill도 있지 않나

맞습니다. 원본 sample repo는 두 방식으로 쓸 수 있습니다.

### 1. 스크립트 방식

```bash
bash scripts/setup-codex-attribution.sh
```

### 2. Codex skill 방식

원본 repo에는 이런 repo-local skill이 있었습니다.

- `$install-codex-coauthor-hook`
- `$add-ai-coauthor`
- `$show-ai-attribution-status`

즉 Codex에게 이렇게 시킬 수 있는 구조입니다.

- `$install-codex-coauthor-hook` 실행해줘
- `$show-ai-attribution-status`로 상태 확인해줘
- `$add-ai-coauthor`로 co-author 추가해줘

다만 자동 trailer에 꼭 필요한 건 아래 최소 구성입니다.

- `.githooks/prepare-commit-msg`
- `.gitmessage`
- `scripts/setup-codex-attribution.sh`

## 실전 적용에서는 어떻게 하는 게 좋나

초심자 기준으로는 스크립트 방식이 가장 쉽습니다.

- 기본 가이드: 스크립트 방식
- 선택 옵션: skill 방식도 가능

즉 블로그나 LinkedIn에는 이렇게 요약하면 됩니다.

> `sample-codex-coauthor`는 Git hook을 이용해 Codex co-author trailer를 자동 추가하는 방식이다. 원본 sample repo는 스크립트로 직접 설정할 수도 있고, Codex skill을 통해 설치/상태 확인을 할 수도 있다.

## 실제 적용 예시

실제 예시는 [vehicle_speed_estimation 예시](../examples/vehicle_speed_estimation.ko.md)를 보면 됩니다.
