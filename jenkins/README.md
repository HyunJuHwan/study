# 개요

CI/CD 역할을 할 Jenkins를 설치합니다.
Jenkins를 설치하고, agent를 추가하여 작업 실행자를 등록합니다.

# 작업

## Jenkins 설치
```shell
sh docker-build.sh
```

## Jenkins agent 추가

- 에이전트 추가 시 나오는 가이드대로 agent.jar를 다운로드 받습니다.(agent 실행 서버)
- 실행 스크립트를 실행파일로 만듭니다.
- 실행 후 정상 연결 여부를 점검합니다.
- 프록시 설정을 추가합니다.
- 자동화 할 앱들을 하나씩 추가하여 테스트합니다.

## 스크립트 예시
- build
  
```
export PATH=/home/chungnam/apps/maven/bin:$PATH
docker login {이미지저장소} -u {저장소ID} -p {저장소pwd}
make build docker tag push
```

- deploy (docker swarm 기준)
```
docker stack deploy -c {연결한 git 디렉토리의 docker-compose-swarm.yml 파일 위치} {배포할 스텍 명}
```
```
swarm 모드가 아닐 시 docker compose -f {파일경로} up -d 명령어로 실행
```
