## 📌 집계 함수와 산술 함수

</br>

### 1️⃣ COUNT(), MAX(), MIN(), AVG()

COUNT() 안에 컬럼을 넣는다면 NULL 을 COUNT 하지 않기 때문에 유의해야한다.

NULL과 상관없이 COUNT를 하기 위해선 따로 컬럼을 넣지 않고 COUNT(*)로 작성 하면 된다.



**MAX()** 모든 ROW 중 **최대값**, **MIN()** 모든 ROW 중 **최소값**, **AVG()** 안에 컬럼을 넣어 **평균값**을 나타낸다.

</br>

### 2️⃣ SUM 함수 - 합계



</br>

### 3️⃣ STD 함수 - 표준편차



</br>

### 4️⃣ FLOOR 함수 - 내림 함수



</br>

### 5️⃣ ROUND 함수 - 반올림 함수



</br>

[다양한 산술 함수 참고 사이트🔎](https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html)

</br>

집계 함수와 산술 함수의 차이점

1. 집계 함수는 특정 컬럼의 여러 row의 값들을 동시에 고려해서 실행되는 함수
2. 산술 함수는 특정 컬럼의 각 row의 값마다 실행되는 함수

MAX 함수를 생각한다면 특정 컬럼의 값 중에서 최댓값을 구하려면 여러 row의 값들을 동시에 고려합니다. 하지만 ABS, ROUND 같은 산술 함수들은 특정 컬럼의 각 row의 값들에 대해 각각 실행된다.

</br>

## 📌 NULL에 관해 알아야하는 사실



### IS NULL 과 NULL은 다르다

간혹 IS NULL 을 사용해야하는데 NULL을 사용하는 경우가 종종 있다.

이런 실수를 한다면 아무 row도 출력되지 않는다.



### NULL은 어떤 연산을 하더라도 NULL 이다.







IS NULL

IS NOT NULL

COALESCE(컬럼명,null 일때 변경할 문구)



</br>

BETWEEN AND

NOT LIKE '%%'

</br>

## 📌 컬럼끼리 계산하기

alias 를 사용하여 컬럼명을 수정하여 가독성을 위해 변경한다.

Concat 여러컬럼을 하나의 컬럼으로 묶어준다.



case ~ when ~ then<br>            when ~ then<br>            else<br>end as



</br>

## 📌 고유값만 보기



DISTINCT 중복된 값을 삭제하고 조회한다.











🌵🔥🌪️🌹🌻🍀🌱💻💡💣💊🎈🧷🔍🔎📌📍🎁🔑🗝️⏱️❓❗⭐

0️⃣1️⃣2️⃣3️⃣4️⃣5️⃣6️⃣7️⃣8️⃣9️⃣🔟🔼🔽➡️⬅️〰️➰➿🎵🎶❌🚫💢






