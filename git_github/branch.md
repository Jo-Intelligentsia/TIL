# **branch**

## **branch** 란?
- 독립적인 작업흐름을 만들고 관리
---
## 명령어
---
- `$ git branch 브랜치명`
>   - 브랜치 생성
- `$ git checkout(switch) 브랜치명`
>   - 브랜치 이동
- `$ git checkout(switch) -b 브랜치명`
>   - 브랜치 생성 후 이동
- `$ git branch`
>   - 브랜치 목록 확인
- `$ git branch -d 브랜치명`
>   - 브랜치 삭제
---
## **merge**
---
- 작업을 완료한 각 브랜치들을 **병합하기** 위한 명령어
>   - 다른 파일을 수정한 경우
>       - 충돌 없이 자동으로 `merge commit`이 생성
>   - 같은 파일 수정한 경우
>       - 직접 해당 파일을 확인하고 적절하게 수정한 이후에 직접 커밋 실행
---
## **git flow**
---
-  `branch`를 활용하여 협업하는 전략
>   - `master(main)`
>       - 배포 가능한 상태의 코드
>   - `develop(main)`
>       - feature branch로 나뉘어지거나, 발생된 버그 수정 등 개발 진행
>       - 개발 이후 release branch 로 분기
>   - `feature branches(supporting)`
>       - 기능별 개발 브랜치(topic branch)
>       - 기능이 반영되거나 드랍되는 경우 브랜치 삭제
>   - `release branches(supporting)`
>       - 개발 완료 이후 QA/Test 등을 통해 얻어진 다음 배포전 minor bug fix등 반영
>   - `hotfixes(supporting)`
>       - 긴급하게 반영 해야하는 bug fix
>       - release branch는 다음 버전을 위한 것이라면, hotfixes branch는 현재버전을 위한 것
---
## **github flow**
---
- 기본 원칙
>   - `master branch`는 반드시 배포 가능한 상태
>   - `feature branch`는 각 기능의 의도를 알 수 있도록 작성
>   - `commit message`는 매우 중요하며, 명확하게 작성
>   - `pull request`를 통해 협업을 진행
>   - 변경사항을 반영하고 싶다면, `master branch`에 병합
- *`shared repository model`*
>   - 동일한 저장소를 공유하여 활용하는 방식
>       1. 팀원 초대 및 저장소 clone
>           - `collaborator`에 등록 되어야 해당저장소에 대한 `push` 권한 부여
>           - `clone` 이후 작업에 맞춘 작업 환경설정 마무리
>       2. 브랜치에서 작업 및 github push
>           - `collaborator`는 항상 독립적인 `feature branch`에서 진행
>           - commit 후 원격저장소에 push
>       3. `pull request` 생성
>           - github에서 `pull request` 버튼 클릭
>           - `pull request` 설정을 진행한 후 요청을 생성
>       4. review 및 merge
>           - 코드리뷰 진행 후 관리자의 판단아래 병합
>           - 병합 과정에서 충돌이 발생할 경우 해결 후 병합을 진행
>           - master branch로 병합의 경우 코드가 반드시 배포 가능한 상태여야 함
>       5. 병합 후 다음 작업 진행
>           - 병합된 branch 삭제 후 master branch 업데이트
- *`fork & pull model`*
>   - `repository`에 `collaborator` 에 등록되지 않은 상태에서 진행
>   - github 기반의 오픈소스 참여 과정에서 쓰이는 방식
>       1. 원격 저장소를 fork 함
>           - 내 저장소로 복제본을 가져옴으로써 로컬에서 작업 후 원격 저장소로 push 할 수 있게 되는 것.
>       2. clone 을 하고 작업 환경 설정
>           - clone 시 반드시 본인 저장소인지 확인
>       3. 이후 작업은 shared repository model과 동일