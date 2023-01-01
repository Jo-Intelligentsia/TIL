# **git hub**

## **git hub 명령어**
---
- `$ git remote(원격저장소) add(추가) origin(원격저장소 기본이름) https://github.com/github usename/저장소이름`
>   - github 에 저장소를 추가

- `$ git remote -v`
>    - 설정값 확인
- `$ git push origin(원격저장소) master(브랜치)`
>   - 로컬 저장소의 버전을 원격저장소로 보냄
>    - 커밋한 버전을 github에 보냄
- `$ git pull origin(원격저장소) master(브랜치)`
>   - 원격저장소의 버전을 로컬 저장소로 가져옴
>    - 다른사람이 github 에서 커밋한 버전을 가져옴
- `$ git clone url (원격저장소 주소)`
>   - 원격저장소를 복제하여 가져옴
>    - 다른사람의 git hub 의 커밋한 오픈소르를 복제
- `.gitignore 파일 생성`
>    - 버전 관리를 별도로 하지 않는 파일/디렉토리를 관리
>   - .gitignore 에 등록
