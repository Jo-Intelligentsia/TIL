# Workbench

- Workbench 란?
    - MySQL 서버 및 데이터베이스 작업을 위한 그래픽 도구 (GUI)
- Workbench 기능
    - SQL 개발
        - 데이터베이스 서버에 대한 연결을 생성하고 관리
        - 연결 매개변수를 구성할 수 있음
        - 내장 SQL 편집기를 사용하여 데이터베이스 연결에서 SQL 쿼리를 실행할 수 있는 기능을 제공
    - 데이터 모델링(디자인)
        - 데이터베이스 스키마의 모델을 그래픽으로 생성
        - 스키마와 라이브 데이터베이스 간에 리버스 및 포워드 엔지니어링을 수행
        - 포괄적인 테이블 편집기를 사용하여 데이터베이스의 모든 측면을 편집
        - 테이블 편집기
            - 테이블, 열, 인덱스, 트리거, 파티셔닝, 옵션, 삽입 및 권한, 루틴 및 뷰를 편집할때 쉬운 기능을 제공
    - 서버 관리
        - 사용자 관리
        - 백업 및 복구 수행
        - 감사 데이터 검사
        - 데이터베이스 상태 확인
        - MySQL 서버 성능 머니터링을 통해 MySQL 서버 인스턴스를 관리할 수 있음
    - 데이터 마이그레이션 
        - 다른 RDBMS 테이블, 개체 및 데이터에서 MySQL 로 마이그레이션을 할 수 있음
    - MySQL 엔터프라이즈 지원
        - MySQL 엔터프라이즈 백업
        - MySQL 방화벽 및 MySQL 감사와 같은 엔터프라이즈 지원


# Workbench 활용 & MySQL 접속 방법

- MySQL Workbench 파일 실행

    - MySQL 서버 연결
        - MySQL Workbench 실행 후  `MySQL Connections` 에 있는 `Rescan servers` 를 클릭

    - MySQL 접속
        1.  `MySQL Connections` 아래에 있는 Local instance `MySQL 80` 을 클릭
        2. password 창이 뜨면 password 입력

    - 실습 데이터베이스 연결
        1. 왼쪽편 아래쪽에 있는 `Administration` 클릭
        2. `Data Import/Restore` 클릭
        3. `Import from Self-Contained File` 체크
        4. `...` 클릭 후 다운로드 받은 sample_db.sql 선택
        5. `Start Import` 클릭
        6. `Import Completed` 확인이 되면 연결 완료

# 실습 데이터베이스에 대한 쿼리(Query)문 작성 및 쿼리문 실행방법

- 실습 데이터베이스 확인
    - 왼쪽 하단에 있는 `Schemas` 클릭
    - `SCHEMAS` 옆에 `새로고침` 버튼 클릭
    - `classicmodels` 생성 확인

- 쿼리 (Query) 실행 테스트
    - `classicmodels` 데이터베이스 선택
    - `Query` 에디터 클릭
    - 쿼리문 입력
        ```SQL
            SELECT * FROM customers;
        ```
    - `Query` 실행 (번개모양)
    - 출력 확인

    
# 한글 입력 설정 및 폰트 설정
- 한글 입력 설정
    - 데이터베이스 옆 도구 모양 클릭
    - utf8 과 utf8_bin 으로 변경
    - 아래쪽 Apply 클릭
- 폰트 설정
    - 왼쪽 위 `Edit` 클릭 후 `Preferences` 클릭
    - 왼쪽 `Fonts & colors`
    - `SQL Editor` 에 다운받은 폰트로 수정  