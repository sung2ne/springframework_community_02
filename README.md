# 데이터베이스 설정

1. 테이블 생성하기

```sql
CREATE TABLE TB_BOARD (
    SEQ NUMBER(38,0) NOT NULL,       -- 게시글 고유 식별자
    TITLE VARCHAR2(256) NOT NULL,    -- 게시글 제목
    CONTENT NCLOB NOT NULL,          -- 게시글 내용 (NCLOB: 대용량 문자 데이터)
    CREATED_AT DATE DEFAULT SYSDATE NOT NULL,  -- 게시글 생성 날짜 (기본값: 현재 날짜)
    CONSTRAINT TB_BLOG_PK PRIMARY KEY (SEQ)    -- SEQ 컬럼을 기본 키로 설정
)
TABLESPACE USERS;  -- 테이블이 저장될 테이블스페이스
```

```sql
CREATE SEQUENCE BLOG_SEQ 
INCREMENT BY 1            -- 1씩 증가
MINVALUE 1                -- 최소값 1
MAXVALUE 9999999999999999999999999999  -- 최대값
NOCYCLE NOCACHE NOORDER;  -- 재사용 불가, 캐시 사용 안함, 순서 지정 없음
```

2. pom.xml에 데이터베이스 관련 라이브러 추가
3. db-context.xml|03.db-context.xml
4. web.xml에 db-context 관련 내용 추가
5. BoardVO.java