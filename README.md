## 내용
스프링부트로 게시판 만들어보기

## 개발환경
- IntelliJ IDEA Community Edition 2023.3.3
- Amazon Corretto 21
- mysql community server 8.0
- spring boot 3.1.8
- mybatis framework
- thymeleaf

## dependencies
- Spring Web
    - MVC 패턴 구현을 위한
- Lombok
- Spring Boot DevTools
    - 코드 수정시 자동으로 서버 재시작

DB 연동시(뒷부분에서 추가 예정)
- MyBatis Framework
- MySQL Driver

## 강의 구성
0. 소개 
1. 프로젝트 세팅
2. 시작페이지 출력, devtools 적용
3. service, repository, DTO class 작성, lombok 설치
4. 게시글 작성 화면 구현
5. 게시글 작성 데이터 컨트롤러에 가져오기
6. mybatis 세팅하기
7. 게시글 작성 데이터 DB에 저장하기
8. 목록 출력 메서드 구현
9. 목록 출력 화면 구현
10. 게시글 조회(조회수 처리하기) 메서드 구현
11. 게시글 조회 화면 구현
12. 게시글 수정 메서드 구현
13. 게시글 수정 화면 구현
14. 게시글 삭제하기
15. 파일첨부 메서드 구현
16. 파일조회 메서드 구현
17. 파일첨부 화면 구현, WebConfig 클래스 정의
18. 다중 파일첨부 메서드 구현
19. 다중 파일첨부 화면 구현

## table 정의
```sql
-- board_table
 drop table if exists board_table;
 create table board_table
 (
	id bigint primary key auto_increment,
    boardTitle varchar(50),
    boardWriter varchar(20),
    boardPass varchar(20),
    boardContents varchar(500),
    boardHits int default 0,
    createdAt datetime default now(), 
    fileAttached int default 0
);
-- board_file_table
drop table if exists board_file_table;
create table board_file_table
(
    id	bigint auto_increment primary key,
    originalFileName varchar(100),
    storedFileName varchar(100),
    boardId bigint,
    constraint fk_board_file foreign key(boardId) references board_table(id) on delete cascade
);
```