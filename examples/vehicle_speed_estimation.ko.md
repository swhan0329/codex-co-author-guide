# 예시: `vehicle_speed_estimation`

레포:
- <https://github.com/swhan0329/vehicle_speed_estimation>

이 문서는 `sample-codex-coauthor` 방식을 실제 기존 레포에 적용한 예시를 설명합니다.

## 무엇을 남겼나

실전 적용에서는 아래 최소 구성만 남겼습니다.

- `.githooks/prepare-commit-msg`
- `.gitmessage`
- `scripts/setup-codex-attribution.sh`

## 무엇을 뺐나

원본 sample repo에는 `.agents/skills` 아래의 repo-local Codex skill 파일도 있었습니다.

하지만 실제 적용 레포에서는 핵심 Git hook 흐름에 꼭 필요하지 않았기 때문에 제거했습니다.

## 왜 이 예시가 중요한가

이 예시는 아래 차이를 보여줍니다.

- 원본 sample repo: 스크립트 방식 + skill 방식 둘 다 시연
- 실제 적용 레포: 최소 구성만 남겨서 간결하게 유지

## 실제로 테스트한 흐름

직접 확인한 흐름은 아래와 같습니다.

1. `vehicle_speed_estimation`에서 작은 코드 변경 수행
2. 테스트 통과 확인
3. Codex co-author attribution 활성화
4. 커밋 생성
5. 커밋 본문에 아래가 들어가는지 확인

```text
Co-authored-by: codex <codex@openai.com>
```

6. GitHub 원격 브랜치로 push

## 실전 문서화 팁

문서에는 두 층을 같이 보여주는 게 좋습니다.

- 원본 sample repo 소개:
  - script로도 가능
  - skill로도 가능
- 실제 적용 예시:
  - 최소 구성만 남기는 방식도 충분히 실용적임

이렇게 정리하면 독자는 "전체 기능"과 "가장 쉬운 도입 경로"를 같이 이해할 수 있습니다.
