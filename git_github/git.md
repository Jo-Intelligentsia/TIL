# **git**

## **git 저장소**
---
- 기본 흐름
>   - 파일 작업
>   - 변경된 파일 모으기 (add)
>   - 버전으로 남기기 (commit)


>    - `Working Directory` (파일의 변경사항)
>        - 파일명(untracked/modified) - $ git add 파일명
>    - `Staging Area`(버전으로 기록하기 위한 파일 변경사항의 목록)
>        - 파일명(staged) - $ git commit -m '커밋메세지'
>    - `Repository` (커밋들이 기록되는 곳)
>        - 파일명(commited)
>    - `commited`
>        - commited 된 파일을 스냅샷으로 관리하고 매우 크기가 작음
>        - 파일이 변경되지 않으면 새로 저장하지 않음
---
## **git 설정 파일(config)**
---
- 사용자 정보(commit author) : 커밋을 하기 위해 반드시 필요
> - git config --global user.name `"username"`
>   - `GitHub`에서 설정한 `username`으로 설정
> - git config --global user.email `"my@email.com"`
>   - `GitHub`에서 설정한 `email`로 설정

- 설정확인
> - git config -l
> - git config --global -l
> - git config user.name
---
## **git 명령어**
---
- `$ git init` (git 사용시 필수)
>   - 특정 폴더를 git 저장소를 만들어 git으로 관리
>   - .git 폴더가 생성 (숨김으로 표시)
>   - git bash 에서는 (master) 표기 확인 가능

- `$ git add 파일명`
>    - `Working Directory`상의 변경된 내용을 `Staging Area` 에 추가
>    - `untracked` 상태의 파일을 `staged` 로 변경 (New file)
>    - `modified` 상태의 파일을 `staged` 로 변경

- `$ git commit -m '커밋메세지'`
>    - `staged` 상태의 파일들을 커밋을 통해 버전으로 기록
>    - 커밋 메세지는 변경사항을 나타낼수 있도록 명확히 작성
- `$ git status`
>    - `Working Directory, Staging Area` 에 있는 파일 상태 확인
>    - `Changes not staged for commit`
>        - 커밋된적 있는 파일을 수정한 상태
>    - `Changes to be committed`
>        - 수정한 파일을 add 한 상태

- `$ git log` 
>  - Repository 에 기록된 커밋을 조회
>        - 최근 1개
>   - `$ git log --oneline`
>      - 한 줄로
> - `$ git log -2 --oneline`
>    - 최근 2개를 한 줄로
