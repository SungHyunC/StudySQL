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

 = : Equal

 > : Greater than

 < : Less than

 >= : Greater than or equal

 <= : Less than or equal
 
 <> : Not equal. Note: In some versions of SQL this operator may be written as !=

BETWEEN : 특정 범위의 사이

LIKE : Search for a pattern

IN : 열에 대해 가능한 값을 여러 개 지정하는 방법

## SQL AND, OR 및 NOT 연산자
AND, OR, NOT WHERE 와 결합할 수 있다.
### AND 구문 and Example
```
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2 AND condition3 ...;
```
"Customers"에서 모든 필드를 선택하며, 국가는 "Germany" 도시는 "Berlin"이다.
```
SELECT * FROM Customers
WHERE Country='Germany' AND City='Berlin';

```

### OR 구문 or Example
```
SELECT column1, column2, ...
FROM table_name
WHERE condition1 OR condition2 OR condition3 ...;
```
도시가 "Berlin" 또는 "München"인 "Customers"에서 모든 필드를 선택한다.
```
SELECT * FROM Customers
WHERE City='Berlin' OR City='München';
```
"Cusomers"에서 국가가 "Germany" 또는 "Spain"인 모든 필드를 선택한다.
```
SELECT * FROM Customers
WHERE Country='Germany' OR Country='Spain';
```
### NOT 구문 or Example
```
SELECT column1, column2, ...
FROM table_name
WHERE NOT condition;
```
국가가 "Germany"이 아닌 "Customers"에서 모든 필드를 선택한다.
```
SELECT * FROM Customers
WHERE NOT Country='Germany';
```

### AND, OR 및 NOT 결합
"Customers"에서 모든 필드를 선택하며, 여기서 국가는 "Germany"이고 도시는 "Berlin"이어야 한다. OR "München"
```
SELECT * FROM Customers
WHERE Country='Germany' AND (City='Berlin' OR City='München');
```
국가가 있는 "Customers"에서 모든 필드를 선택한다. "Germany"도 아니고 "USA"도 아니다.
```
SELECT * FROM Customers
WHERE NOT Country='Germany' AND NOT Country='USA';
```
## SQL ORDER BY KEYWORD
ORDER BY 키워드를 사용하여 결과 집합을 오름차순 또는 내림차순으로 정렬한다.
기본적으로 레코드를 오름차순으로 정렬한다. 레코드를 내림차순으로 정렬하면 DESC 키워드
```
SELECT column1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC|DESC;
```
### ORDER BY 예제
```
SELECT * FROM Customers;
ORDER BY Country;
```
### DESC 예제
```
SELECT * FROM Customers
ORDER BY Country DESC;
```
### 여러 열로 정렬 예제
NO.1
```
SELECT * FROM Customers
ORDER BY Country, CustomerName;
```
NO.2
```
SELECT * FROM Customers
ORDER BY COuntry ASC, CustomerName DESC;
```
## SQL INSERT INTO
INSERT INTO 문장은 표에 새 레코드를 삽입하는 데 사용된다.

예시1
```
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```
예시2
```
INSERT INTO table_name
VALUES (value1, value2, value3, ...);
```
지정된 열에만 데이터 삽입도 가능합니다.
```
INSERT INTO Customers (CustomerName, City, Country)
VALUES ('Cardinal', 'Stavanger', 'Norway');
```

## SQL NULL Values
NULL 값을 가진 필드는 값이 없는 필드다.

예시1 IS NULL Syntax
```
SELECT column_names
FROM table_name
WHERE column_name IS NULL;
```
```
SELECT CustomerName, ContactName, Address
FROM Customers
WHERE Address IS NULL;
```
예시2 IS NOT NULL Syntax
```
SELECT column_names
FROM table_name
WHERE column_name IS NOT NULL;
```
```
SELECT CustomerName, ContactName, Address
FROM Customers
WHERE Address IS NOT NULL;
```
## SQL UPDATE 
UPDATE 문장은 표의 기존 기록을 수정하는 데 사용된다.

UPDATE 구문
```
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```
예시1
```
UPDATE Customers
SET ContactName = 'Alfred Schmidt', City= 'Frankfurt'
WHERE CustomerID = 1;
```
여러 레코드 UPDATE
```
UPDATE Customers
SET ContactName='Juan'
WHERE Country='Mexico';
```
주의 : UPDATE 문을 쓸때는 WHERE를 생략하게 된다면 모든 레코드가 업데이트 됩니다
```
UPDATE Customers
SET ContactName='Juan';
```
## SQL DELETE 
DELETE 문장은 테이블의 기존 레코들르 삭제하는 데 사용된다.
예시
```
DELETE FROM table_name WHERE condition;`
```
예제1 고객 "AAlfreds Futterkiste"를 Customers 에서 삭제
```
DELETE FROM Customers WHERE CustomerName='Alfreds Futterkiste';
```
예제2 모든 레코드 삭제
```
DELETE FROM table_name;
```

## SELECT TOP
많은 데이터들 가운데 특정 개수의 데이터만 출력하고 싶을 때 사용된다.
예시1
```
SELECT TOP 3 * FROM Customers;
```
동등한 예
```
SELECT * FROM Customers
LIMIT 3;
```
예시2 레코드의 처음 50%를 "Customers" 에서
```
SELECT TOP 50 PERCENT * FROM Customers;
```
예시3 WHERE 절 추가
```
SELECT TOP 3 * FROM Customers
WHERE Country='Germany';
```
## SQL MIN() and MAX() Functions

MIN()
```
SELECT MIN(column_name)
FROM table_name
WHERE condition;
```
MAX()
```
SELECT MAX(column_name)
FROM table_name
WHERE condition;
```

Example
```
SELECT MIN(Price) AS SmallestPrice
FROM Products;
```
```
SELECT MAX(Price) AS LargestPrice
FROM Products;
```

## The SQL COUNT(), AVG() and SUM() Functions

COUNT()
```
SELECT COUNT(column_name)
FROM table_name
WHERE condition;
```
AVG()
```
SELECT AVG(column_name)
FROM table_name
WHERE condition;
```
SUM()
```
SELECT SUM(column_name)
FROM table_name
WHERE condition;
```

Example
```
SELECT COUNT(ProductID)
FROM Products;

SELECT AVG(Price)
FROM Products;

SELECT SUM(Quantity)
FROM OrderDetails;

```

The SQL LIKE Operator

LIKE 
```
SELECT column1, column2, ...
FROM table_name
WHERE columnN LIKE pattern;
```

example
```
SELECT * FROM Customers
WHERE CustomerName LIKE 'a%';
```
## SQL IN Operator

```
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1, value2, ...);
```

```
SELECT column_name(s)
FROM table_name
WHERE column_name IN (SELECT STATEMENT);
```

##SQL BETWEEN Operator
```
SELECT column_name(s)
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```

##SQL Between

```
SELECT column_name(s)
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```
example
```
SELECT * FROM Products
WHERE Price BETWEEN 10 AND 20;
```
