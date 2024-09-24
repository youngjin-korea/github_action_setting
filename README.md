## 경로는 항상 프로젝트 최상단 .github > workflows > **.yml
.github
      > workflows
          > deploy.yml




```
# workflows 안에 yml파일은 하나의 작업 흐름 workflow라고 부름
# name은 workflow의 이름이다
name: github action deploy ci/cd

# Event로 main 브랜치에 push 됐을 때 workflow 실행
on:
  push:
    branches:
      - main

# 하나의 workflow는 여러 job을 가지고 job들은 병렬로 실행된다
jobs:
#  job식별하기 위한 고유 식별자
  My-deploy-job:
#    운영체제 고르는 기능
    runs-on: ubuntu-latest
#   job은 여러 스텝들을 갖는다
    steps:
#      name으로 스텝의 이름을 적고 run으로 리눅스 코드를 짠다
      - name: Hello World 찍기
        run: echo "Hello World"

      - name: 여러 명령어를 쓰려면
        run: |
          echo "many"
          echo "once with"

#          깃허브에 이미 있는 변수 각각 commit id, repository id
      - name: githubAction 내에 있는 변수
        run: |
          echo $GITHUB_SHA
          echo $GITHUB_REPOSITORY

      - name: 노출되면 안되는 값
        run: |
          echo ${{ secrets.MY_KEY }}
          # settings > secrets and variables > action 
```
