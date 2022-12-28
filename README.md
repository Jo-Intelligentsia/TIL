# git
- CLI(Command Line Interface)
    - 명령 기반의 인터페이스
    - 프롬포트 기본 인터페이스
        - 컴퓨터정보, 디렉토리, $
- 분산버전관리시스템으로 코드의 버전을 관리하는 도구
    - 분산버전관리시스템(DVCS)
        - 중앙집중식버전관리시스템은 중앙에서 버전을 관리하고 파일을 받아서 사용
        - 원격 저장소를 통하여 협업하고, 모든 히스토리를 클라이언트들이 공유
- 2005년 리눅스 커널을 위한 도구로 리누스 토르발스가 개발
- 컴퓨터 파일의 변경사항을 추적하고 여려명의 사용자들 간에 해당 파일들의 작업을 조율

## CLI 디렉토리(폴더) 관리

- pwd (print working directory)
    - 현재 디렉토리(폴더) 출력
- cd 디렉토리(폴더)이름 (change directory)
    - 디렉토리(폴더) 이동
        - . : 현재디렉토리
        - .. : 상위 디렉토리
        - ~/Desktop/TIL -> TIL 파일로 한번에 이동
- ls (list) 
    - 목록
- mkdir (make directory)
    - 디렉토리(폴더) 생성
- touch 파일명
    - 파일 생성
- rm 파일명 (remove)
    - 파일 삭제하기
- rm -r 폴더명
    - 폴더 삭제하기


## git 저장소
- 기본 흐름
    1. 파일 작업
    2. 변경된 파일 모으기 (add)
    3. 버전으로 남기기 (commit)

    - Working Directory (파일의 변경사항)
        - 파일명(untracked/modified) - $ git add 파일명
    - Staging Area(버전으로 기록하기 위한 파일 변경사항의 목록)
        - 파일명(staged) - $ git commit -m '커밋메세지'
    - Repository (커밋들이 기록되는 곳)
        - 파일명(commited)


- $ git init (git 사용시 필수)
    - 특정 폴더를 git 저장소를 만들어 git으로 관리
        - .git 폴더가 생성 (숨김으로 표시)
        - git bash 에서는 (master) 표기 확인 가능

- $ git add 파일명
    - Working Directory상의 변경된 내용을 Staging Area 에 추가
        - untracked 상태의 파일을 staged 로 변경 (New file)
        - modified 상태의 파일을 staged 로 변경

- $ git commit -m '커밋메세지'
    - staged 상태의 파일들을 커밋을 통해 버전으로 기록
    - 커밋 메세지는 변경사항을 나타낼수 있도록 명확히 작성

- commited 파일
    - commited 된 파일을 스냅샷으로 관리하고 매우 크기가 작음
    - 파일이 변경되지 않으면 새로 저장하지 않음
    
- $ git status
    - Working Directory, Staging Area 에 있는 파일 상태 확인
    - Changes not staged for commit
        - 커밋된적 있는 파일을 수정한 상태
    - Changes to be committed
        - 수정한 파일을 add 한 상태

- $ git log 
    - Repository 에 기록된 커밋을 조회
    - $ git log -1
        - 최근 1개
    - $ git log --oneline
        - 한 줄로
    - $ git log -2 --oneline
        - 최근 2개를 한 줄로
