# 개요

CI/CD 역할을 할 Jenkins를 설치합니다.
Jenkins를 설치하고, agent를 추가하여 작업 실행자를 등록합니다.

# 작업

## Jenkins 설치
```shell
sh docker-build.sh
```

## Jenkins 초기 설정

## Jenkins agent 추가

- 에이전트 추가 시 나오는 가이드대로 agent.jar를 다운로드 받습니다.(agent 실행 서버)
- 실행 스크립트를 실행파일로 만듭니다.
- 실행 후 정상 연결 여부를 점검합니다.
- 프록시 설정을 추가합니다.
- 자동화 할 앱들을 하나씩 추가하여 테스트합니다.
