# StudySQL
www.w3schools.com/sql 공부 중


## SQL명령어 일부
SELECT - 데이터베이스에서 데이터 추출

UPDATE - 데이터베이스의 데이터 업데이트

DELETE - 데이터베이스에서 데이터 삭제

INSERT INTO - 데이터베이스에 새 데이터 사입

CREATE DATABASE - 새 데이터베이스 작성

ALTER DATABASE - 데이터베이스 수정

CREATE TABLE - 새 테이블 작성

ALTER TABLE - 테이블 수정

DROP TABLE - 테이블 삭제

CREATE INDEX - 인덱스 생성(검색 키)

DROP INDEX - 인덱스 삭제

## SQL 구문
Example
```
SELECT * FROM Customers;
```
SQL 키워드는 대소문자를 구분하지 않음 : select = SELECT

SQL문 뒤에는 세미콜론이 필요하다.

## SQL SELECT 문
SELECT 명령문은 데이터베이스에서 데이터를 선택하는 데 사용된다.
반환된 데이터는 결과 집합이라고 하는 결과 테이블에 저장된다.

```
SELECT column1, column2, ...
FROM table_name;
```
column1,column2 는 테이블의 필드 이름이다.

```
SELECT * FROM table_name;
```
모든 필드를 선택하려면 위의 구문을 사용한다.

## SQL Select Differently
SQL SELECT DIRECT 문
SELECT DISTINCT 문장은 오직 구별되는 것만 반환하는 데 사용된다.

```
SELECT DISTINCT column1, column2, ...
FROM table_name;
```

```
SELECT COUNT(DISTINCT Country) FROM Customers;
```
## SQl WHERE 절
지정된 기록을 충족하는 기록만 추출하는 데 사용된다.
WHERE 구문
```
SLECT column1, column2, ...
FROM table_name
WHERE condition;
```
Example
```
SELECT * FROM Customers
WHERE Country = 'Mexico';
```
Text Fields vs. Numberic Fields
SQL에는 텍스트 값 주위에 작은 따옴표가 필요함(대부분의 데이터베이스 시스템은 또한 큰따옴표도 허용한다.)
그러나 숫자 필드는 따옴표로 묶으면 안 된다.

```
SELECT * FROM Customers
WHERE CustomerID=1;
```
WHERE 절의 연산자
= Equal
> Greater than
< Less than
>= Greater than or equal
<= Less than or equal
<> Not equal. Note: In some versions of SQL this operator may be written as !=
BETWEEN 특정 범위의 사이
LIKE Search for a pattern
IN 열에 대해 가능한 값을 여러 개 지정하는 방법
