## 📌 집계 함수와 산술 함수

</br>

### 1️⃣ COUNT(), MAX(), MIN(), AVG()

COUNT() 안에 컬럼을 넣는다면 NULL 을 COUNT 하지 않기 때문에 유의해야한다.

NULL과 상관없이 COUNT를 하기 위해선 따로 컬럼을 넣지 않고 COUNT(*)로 작성 하면 된다.



**MAX()** 모든 ROW 중 **최대값**, **MIN()** 모든 ROW 중 **최소값**, **AVG()** 안에 컬럼을 넣어 **평균값**을 나타낸다.

</br>

### 2️⃣ SUM 함수 - 합계

```sql
SELECT SUM(age) FROM copang_main.member;
```

</br>

### 3️⃣ STD 함수 - 표준편차

```sql
SELECT STD(age) FROM copang_main.member;
```

산술 함수 중 자주 쓰이는 함수 

**ABS 함수 - 절대값을 구하는 함수**

**SQRT 함수 - 제곱근을 구하는 함수**

**CEIL 함수 - 올림 함수**

</br>

### 4️⃣ FLOOR 함수 - 내림 함수

```sql
SELECT FLOOR(height) FROM copang_main.member;
```

</br>

### 5️⃣ ROUND 함수 - 반올림 함수

```sql
SELECT ROUND(height) FROM copang_main.member;
```

</br>

[다양한 산술 함수 참고 사이트🔎](https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html)

</br>

집계 함수와 산술 함수의 차이점

1. 집계 함수는 특정 컬럼의 여러 row의 값들을 동시에 고려해서 실행되는 함수
2. 산술 함수는 특정 컬럼의 각 row의 값마다 실행되는 함수

MAX 함수를 생각한다면 특정 컬럼의 값 중에서 최댓값을 구하려면 여러 row의 값들을 동시에 고려합니다. 하지만 ABS, ROUND 같은 산술 함수들은 특정 컬럼의 각 row의 값들에 대해 각각 실행된다.

</br>

## 📌 NULL에 관해 알아야하는 사실

</br>

### IS NULL 과 NULL은 다르다

간혹 IS NULL 을 사용해야하는데 NULL을 사용하는 경우가 종종 있다.

이런 실수를 한다면 아무 row도 출력되지 않는다.

</br>

### NULL은 어떤 연산을 하더라도 NULL 이다.

</br>

### 💡값들의 범위를 지정할 때 사용하는 함수

BETWEEN A AND B

A이상 B 이하

</br>

### 💡컬럼 데이터를 조회할 때 사용하는 함수

IS NULL '%'

IS NOT NULL '%'

</br>

## 📌 컬럼끼리 계산하기

alias 를 사용하여 컬럼명을 수정하여 가독성을 위해 변경한다.

Concat 여러컬럼을 하나의 컬럼으로 묶어준다.

</br>

case ~ when ~ then<br>            when ~ then<br>            else<br>end as

</br>

### 💡COALESCE(컬럼명,null 일때 변경할 문구)

MySQL에서 NULL을 다른 값으로 변환 할 수 있는 방법이다.

</br>

### 💡IFNULL(컬럼명, 'N/A') 함수 

IFNULL 함수는 첫번째 인자가 null이면 두번째 인자를 표시하고 NULL이 아니면 해당 값을 그대로 표현합니다.

</br>

### 💡IF(컬럼명 IS NOT NULL , 컬럼명 , 'N/A') 함수 

IF함수는 가장 첫번째 인자에 조건식이 나옵니다. 만약 그 조건식의 결과가 TRUE라면 두번째 인자를 리턴하고 False라면 세번째 인자를 리턴 한다.

</br>

### 💡띄어쓰기(스페이스)가 포험된 alias에는 따옴표를 붙여줘야 합니다.

만약 컬럼에 스페이스가 포함된 alias를 붙이고 싶다면, **작은 따옴표**나 **큰 따옴표**를 붙여서 alias부분을 확실하게 표현해주어야 합니다.

'''sql select name as '상품 이름', price from item;

이렇게 하지 않으면 **스페이스를 기준으로 구문 해석이 이루어지는 SQL특성상 에러가 발생**하니까 주의 해야한다.

</br>

## 📌 고유값만 보기

DISTINCT 중복된 값을 삭제하고 조회한다.

SUBSTRING(컬럼,시작점,끝점) 컬럼 내용에 특정 부분만 잘라 사용할때 쓰는 함수 입니다.

LENGTH(문자열)함수 : 문자열 길이 구해준다

UPPER, LOWER 함수

- UPPER(문자열) 문자열을 모두 **대문자**로 바꿔서 보여준다.
- LOWER(문자열) 문자열을 모두 **소문자**로 바꿔서 보여준다.

LPAD, RPAD 함수

- LPAD(컬럼명, 총 길이, 남은 공간에 채울 내용) : 총 길이만큼 원래 컬럼 값을 넣고 남은 **왼쪽**에 채운다.
- RPAD(컬럼명, 총 길이, 남은 공간에 채울 내용) : 총 길이만큼 원래 컬럼 값을 넣고 남은 **오른쪽**에 채운다.

TRIM, LTRIM, RTRIM 함수

- TRIM(컬럼명) : 왼쪽, 오른쪽 양쪽 다 공백 삭제
- LTRIM(컬럼명) : 왼쪽 공백 삭제
- RTRIM(컬럼명) : 오른쪽 공백 삭제

</br>

## 📌 그루핑

Group by 여러 컬럼을 기준으로 그루핑을 할수 있다.

**Aggregate function(집계함수)**

MAX(컬럼명)함수 : 해당 테이블에 모든 row의 컬럼중 가장 큰 값<br>MIN(컬럼명)함수 : 해당 테이블에 모든 row의 컬럼중 가장 작은 값<br>COUNT(컬럼명)함수 : 해당 테이블에 컬럼의 null값을 제외한 갯수<br>AVG(컬럼명)함수 : 해당 테이블에 모든 row의 컬럼 평균값

HAVING함수 : GROUP BY 를 한 후 WHERE 처럼 조건을 설정 할 수 있다.

### 💡 group by 를 사용했을때 select 문에 조회하고자 하는 내용중 집계함수를 사용한 컬럼은 group by를 하지않는다. 반대로 group by를 사용했을때 집계함수를 사용하지 않은 컬럼명이 있다면 무조건 group by를 해야한다. 그렇지 않으면 에러가 난다.❗

</br>

### 💡SELECT 문에 마지막 순서 정리와 각 절들의 대한 설명

1. FROM : 어느 테이블을 대상으로 할 것인지를 먼저 결정합니다. 
2. WHERE : 해당 테이블에서 특정 조건(들)을 만족하는 row들만 선별합니다. 
3. GROUP BY : row들을 그루핑 기준대로 그루핑합니다. 하나의 그룹은 하나의 row로 표현됩니다.
4. HAVING : 그루핑 작업 후 생성된 여러 그룹들 중에서, 특정 조건(들)을 만족하는 그룹들만 선별합니다.  (~~을 가지고 있는)
5. SELECT : 모든 컬럼 또는 특정 컬럼들을 조회합니다. SELECT 절에서 컬럼 이름에 alias를 붙인 게 있다면, 이 이후 단계(ORDER BY, LIMIT)부터는 해당 alias를 사용할 수 있습니다.
6. ORDER BY : 각 row를 특정 기준에 따라서 정렬합니다. 
7. LIMIT : 이전 단계까지 조회된 row들 중 일부 row들만을 추립니다. 

</br>

WITH ROLLUP : GROUP BY를 한 다음 사용하며 부분 합계를 내준다.

GROUPING 함수 : 원래 값이 null인지 부분합계를 나타낸 null인지 구분하기 위해 GROUPING 함수를 사용한다.<br>                                      원래 값이 NULL이라면 0 이고, 부분합계를 위해 값이 NULL이라면 1로 값이 나타난다.
