# Database 기본
- [sqlite 설치](#설치)
- [DDL](#ddl)
- [DML](#dml)
- [DCL](#dcl)


## 설치

### 필요한 파일 다운로드
https://www.sqlite.org/download.html

2개의 파일 설치
![image](https://user-images.githubusercontent.com/63838039/193729337-f0dbe79b-61b7-404e-8ca8-3155bab74e6c.png)

### 환경변수 설정
![image](https://user-images.githubusercontent.com/63838039/193729466-39aee6ae-70df-4838-be46-458fe671f5ce.png)


### Git bash 설정
![image](https://user-images.githubusercontent.com/63838039/193729508-89b0b805-f4f2-4df4-9c9b-ec49a167de26.png)

~/.bashrc 파일에 alias 등록
```
alias sqlite3="winpty sqlite3"
```

## sqlite3 명령어

### sqlite3 실행
```
winpty sqlite3
```

### 원하는 db 선택
```
.open db이름
.open mydb.sqlite3
```
- sqlite3 실행하면서 db 선택
```
winpty sqlite3 mydb.sqlite3
```

- 데이터베이스 확인
```
.database
```

- 테이블 확인
```
.tables
```


## DDL
- 테이블을 생성, 삭제, 변경하는 명령어
### CREATE

```
CREATE TABLE table_name(
  column_name type constraints
)
```

### ALTER
```
ALTER TABLE table_name RENAME TO new_table_name;

ALTER TABLE table_name RENAME COLUMN column_name TO new_column_name;

ALTER TABLE table_name ADD COLUMN column_definition constraints;

ALTER TABLE table_name DROP COLUMN column_name;
```

### DROP
```
DROP TABLE table_name;
```

## DML
- 데이터를 조작 하는 언어(추가, 조회, 변경, 삭제)

### SELECT
```
SELECT column1, column2 FROM table_name;

SELECT select_list 
FROM table_name
ORDER BY column_1 ASC, column_2 DESC;

SELECT DISTINCT select_list FROM table_name;

SELECT column_list FROM table_name
WHERE column_1 = 10

WHERE column_2 LIKE 'Ko%'           --대소문자 구분 x
                                    -- % 0개 이상의 문자, _ 단일(1개) 문자가 있음
WHERE column_3 IN (1, 2)

WHERE column_4 BETWEEN 10 AND 20    -- 10이상 20이하

SELECT column_list FROM table_name
LIMIT 10;                           --  row 행의 수를 제한

SELECT column_list FROM table_name
LIMIT 10 OFFSET 10;                 -- 10번째 데이터 이후로 10개의 데이터 출력 11~20

SELECT column_list, COUNT(*) AS number_of_name FROM table_name
GROUP BY column1                    -- 그룹별로 포함되는 데이터의 수를 구함
```

- Aggregate function
```
AVG, COUNT, MAX, MIN, SUM
```

### INSERT

```
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...),
VALUES (value1, value2, ...),
VALUES (value1, value2, ...),
;
```

### UPDATE

```
UPDATE table_name
SET column_1 = new_value_1,
    column_1 = new_value_1
WHERE search_condition;
```

### DELETE

```
DELETE FROM table_name
WHERE search_condition;

DELETE FROM table_name            -- 모든 데이터 삭제
```


## DCL
- 권한에 대한 명령어




## 기타
### csv import 하는 방법
```
sqllite3

.mode csv
.import csv_file_name table_name
```

### sqlite READ 정리된 상태로 보기
```
.mode column
```

### column명 보이게 하기
```
.header on
```

