## 📌 데이터 조회의 핵심, SELECT 와 WHERE

### 🔎 SELECT 테이블의 데이터를 조회할 때 사용하는 구문

#### 💡 SELECT * FROM copang_main.member;

> ' * ' asterisk 모든 컬럼을 조회한다.

#### 💡 SELECT email, age, address FROM copang_main.member;

> 이렇게 하면 보고 싶은 컬럼만 조회 할 수 있다.

#### 💡 FROM 뒤에는 어떤 테이블에 어떤것을 조회할 지 선택해준다.

#### 💡 SELECT * FROM copang_main.member WHERE email = 'codeit@naver.com;

> WHERE 뒤에는 특정 조건을 설정한다.

</br>

-----

</br>

## 📌 SQL 작성 형식

### 1️⃣  SQL 문에는 항상 세미콜론을 사용해야한다. ❗❗

> 하나의 SQL문 끝에 세미콜론을 써줘야한다. SQL문법 상 세미콜론이 **하나의 SQL 문을 종결하는 단위**이기 때문이다.

</br>

### 2️⃣ SQL 문 안에는 공백이나 개행 등을 자유롭게 넣을 수 있다.

> 어떤 방식으로 쓰든 구분되어야할 키워드들이 최소한 하나 이상의 공백으로 구분되어 있고, 세미콜론으로 마무리되어 있으면 실행에는 문제가 없다. 이런 점을 이용해 **길이가 긴 SQL 문을 쓸 때는 개행(줄바꿈), 탭 등을 적절하게 활용하여 가독성을 높인다.**

```sql
SELECT * FROM copang_main.member	WHERE email = 'codeit@naver.com';

SELECT * FROM copang_main.member
		WHERE email = 'codeit@naver.com';
```

</br>

### 3️⃣ SQL 문의 대소문자 구분 문자

```sql
SELECT * FROM copang_main.member WHERE email = 'codeit@naver.com';
```

> 대문자로 작성된 내용은 MySQL에서 원래부터 존재하는 **예약어**이며 그 외에 내용은 **사용자가 지정한 부분**입니다.
>
> MySQL의 예약어는 대문자로 적는 것이 관례이고, 가독성에 좋습니다. 단, 소문자로 바꿔서 실행해도 문제되지 않습니다.
>
> 나머지 사용자가 지정한 부분에 데이터베이스 이름, 테이블 이름, 컬럼 이름 등은 대소문자를 가리지 않고, 실제로 존재하는 것의 이름을 작성하면 된다.

## </br>

### 4️⃣ 데이터베이스 이름과 테이블 이름

> 데이터베이스 이름 뒤에 점(.)을 붙이고 그 다음에 테이블 이름을 작성했습니다. 이렇게 쓰면 해당 데이터베이스 안의 테이블을 가리키는 것인데 실무에서는 서로 다른 데이터베이스에, 같은 이름 테이블이 존재할 수도 있기 때문에 이렇게 사용하는게 좋습니다.
>
> 하지만 항상 그럴 필요는 없습니다.

```sql
SELECT * FROM member;

USE copang_main;
SELECT * FROM member;
```

> 위 내용 처럼 USE copang_main; 은 copang_main 이라는 데이터베이스를 사용하겠다고 확실히 선언하는 것입니다. 그리고 그 뒤로는 그냥 테이블 이름만 써도 괜찮습니다.

</br>

-----

</br>

## 📌 조건 표현식

### 1️⃣ 범위 조회 BETWEEN a AND b (a부터 b까지)

> 에를 들어 나이가 20살에서 30살을 조회하려면 **BETWEEN a AND b** 를 사용합니다.
>
> 반대로 20살에서 30살을 제외하려면 **NOT**을 추가하여 **NOT BETWEEN a AND b** 로 사용하면 됩니다.

```sql
SELECT * FROM copang_main.member
        WHERE age BETWEEN 20 AND 30;
        
SELECT * FROM copang_main.member
        WHERE age NOT BETWEEN 20 AND 30;
```

</br>

### 2️⃣ 같지 않음(!=, <>)

> '같음'을 나타내는 **등호(=)**, '같지 않음'은 **!= OR <>**

```sql
SELECT * FROM copang_main.member WHERE gender != 'm';
SELECT * FROM copang_main.member WHERE gender <> 'm';
```

</br>

### 3️⃣ 이 중에 있는 ~ (IN)

> 범위가 아닌 정확하게 20살, 30살을 조건으로 조회하려면 **IN()** 을 사용합니다.

```sql
SELECT * FROM copang_main.member WHERE age IN(20, 30);
```

#### </br>

### 4️⃣ ' '안에 내용을 포함하는 조회하는 방법 LIKE ' ';

> LIKE '서울%' : 서울~ 
>
> LIKE '%고양시%' : ~고양시~ 

```sql
SELECT * FROM copang_main.member 
        WHERE address LIKE '서울%'
          AND address LIKE '%고양시%';
```

#### </br>

### 5️⃣ 한 글자를 나타내는 _

> 문자열 패턴 매칭 조건 LIKE 뒤의 '%' 는 임의의 길이를 가진 문자열(0자도 포함)을 나타낸다.
>
> %말고 언더바(_) 하나 기호도 있는데 LIKE 뒤의 언더바 하나의 문자 하나를 나타낸다.
>
> member 테이블에서 이메일 주소가 c로 시작하고 그 뒤에 여섯글자가 있는 row를 조회하는 쿼리를 작성합니다.

```sql
SELECT * FROM copang_main.member WHERE email LIKE 'c_____@%';
```

</br>

----

</br>

## 📌 DATE 데이터 타입 관련 함수

### DATE 타입의 값에서 연도(year)만, 혹은 월(month)만, 혹은 일(day)만 추출할 수 있습니다.

### 1️⃣ 연도, 월, 일 추출하기

```sql
SELECT * FROM copang_main.member WHERE YEAR(birthday) = '1992';
SELECT * FROM copang_main.member WHERE MONTH(sign_up_day) IN (6, 7, 8);
SELECT * FROM copang_main.member WHERE DAYOFMONTH(sign_up_day) BETWEEN 15 AND 31;
```

> **YEAR 함수**를 사용하면 날짜 값에서 연도만 뽑아낼 수 있습니다.
>
> **MONTH 함수**를 사용하면 날짜 값에서 월만 뽑아낼 수 있습니다.
>
> **DAYOFMONTH 함수**를 사용하면 날짜 값에서 일만 뽑아낼 수 있습니다.

</br>

### 2️⃣ 날짜 간의 차이 구하기

```sql
SELECT * FROM copang_main.member WHERE MONTH(sign_up_day) IN (6, 7, 8);
```

> **DAYEDIFF 함수** 날짜 간의 차이를 구하는 함수
>
> **DATEDIFF(날짜 a, 날짜 b)**를 사용하면 **'날짜 a - 날짜 b'**를 해서 그 차이 일수를 알려준다.
>
> **CURDATE()** 오늘 날짜를 구하는 함수

</br>

### 3️⃣ 날짜 더하기 빼기

```sql
SELECT email, sign_up_day, DATE_ADD(sign_up_day, INTERVAL 300 DAY)
  FROM copang_main.member;
  
SELECT email, sign_up_day, DATE_SUB(sign_up_day, INTERVAL 250 DAY)
  FROM copang_main.member;
```

> 더하는 함수 **DATE_ADD()**, 빼는 함수 **DATE_SUB()**
>
> 각각 INTERVAL 300 DAY ,INTERVAL 250 DAY 300일을 더하고 빼는 함수를 예를 들었습니다.

</br>

### 4️⃣ UNIX Timestamp 값

```sql
SELECT email, sign_up_day, UNIX_TUMESTAMP(sign_up_day)
  FROM copang_main.member;
  
SELECT email, sign_up_day, FROM_UNIXTIME(UNIX_TUMESTAMP(sign_up_day))
  FROM copang_main.member;
```

> 시간까지 포함하는 컬럼이라면 DATETIME이라는 데이터 타입을 사용해야한다.
>
> DATETIME 타입의 컬럼에는 보통 '2021-03-10 20:26:59'이런식으로 값들이 저장되어 있다.
>
> 하지만 1553526000 이런 식으로 상당히 큰 숫자값이 적혀있는 경우들이 많은데 이런 형식의 날짜시간 값을 UNIX Timestamp라고 합니다. UXIT Timestamp는 특정 날짜의 특정 시간을, 1970년 1월 1일 기준으로 총 몇초가 지났는지로 나타낸 값입니다.
>
> 날짜 형태로 바꾸려면 **FROM_UNIXTIME 함수**를 사용하면 됩니다.

### 💡 MySQL 공식 메뉴얼 참조

> 날짜, 시간 관련 데이터 타입 : https://dev.mysql.com/doc/refman/8.0/en/date-and-time-types.html
>
> 날짜, 시간 관련 함수 : https://dev.mysql.com/doc/refman/8.0/en/date-and-time-functions.html

</br>

----

</br>

## 📌 여러 조건을 걸 때 주의할 점

</br>

### 1️⃣ OR를 사용할 때의 주의사항

```sql
SELECT * FROM copang_main.member WHERE id = 1 OR id = 2;
```

> OR 함수를 사용할 때 **WHERE id = 1 OR 2**로 적는 실수를 하는데
>
> 즉, WHERE id = 1 OR 2의 값은 **WHERE id = 1 OR TRUE** 입니다.

</br>

### 2️⃣ AND와 OR 간의 우선순위

> 1) 성별이 여자이거나(OR) 나이가 30세 미만 '이면서'(AND)
>
> 2) 키는 180 이상인 회원들을 조회하려고 합니다.
>
> AND가 OR보다 우선순위가 더 높기 때문에 AND가 OR보다 먼저 실행된다.

```sql
SELECT * FROM copang_main.member
        WHERE gender = 'f' OR age < 30 AND height > 180;
```

> 1) 성별이 여자이거나(OR)
>
> 2) 나이가 30세 미만이면서(AND) 키가 180 이상인 회원들을 조회하는 것을 조회한다.
>
> 우선 순위를 생각을 하는데 신경쓰는 것 보다 '먼저 실행되기를 원하는 조건'을 괄호로 씌워주는게 좋다. 괄호는 AND보다도 우선순위가 높기때문이다.

```sql
SELECT * FROM copang_main.member
        WHERE (gender = 'f' OR age < 30) AND height > 180;
```

> 이렇게 한다면 원하는 조건을 쉽게 작성할 수 있습니다.

### </br>

----

</br>

## 📌 문자열 패턴 매칭 조건을 사용할 때 주의할 점

### 🔎 정렬  : row들을 특정 컬럼을 기준으로 순서대로 출력











🌵🔥🌪️🌹🌻🍀🌱💻💡💣💊🎈🧷🔍🔎📌📍🎁🔑🗝️⏱️❓❗⭐

0️⃣1️⃣2️⃣3️⃣4️⃣5️⃣6️⃣7️⃣8️⃣9️⃣🔟🔼🔽➡️⬅️〰️➰➿🎵🎶❌🚫💢







</br>

---

</br>

## 📌 데이터 정렬해서 보기

### 🔎 정렬  : row들을 특정 컬럼을 기준으로 순서대로 출력

</br>

```sql
SELECT * FROM copang_main.member
ORDER BY height ASC;
```

#### 💡기본으로 **ASC** (ascending) 오름차순 

#### 💡**DESC**(descending) 내림차순

</br>

```sql
SELECT * FROM copang_main.member
ORDER BY YEAR(sign_up_day) DESC, email ASC;
```

> 정렬이 차례대로 YEAR(sign_up_day)이 먼저 내림차순, email이 오름차순 순으로 정렬 된다.

</br>

### 💡 각 절의 작성 순서를 꼭 지켜야 실행했을 때 에러가 발생하지 않는다.❗

#### 🔎 MySQL에서 SELECT 문 내의 각 절들 간의 작성 순서 [링크](https://dev.mysql.com/doc/refman/8.0/en/select.html)

</br>

-----

</br>

## 📌 정렬할 때 주의할 점

### 

🌵🔥🌪️🌹🌻🍀🌱💻💡💣💊🎈🧷🔍🔎📌📍🎁🔑🗝️⏱️❓❗⭐

0️⃣1️⃣2️⃣3️⃣4️⃣5️⃣6️⃣7️⃣8️⃣9️⃣🔟🔼🔽➡️⬅️〰️➰➿🎵🎶❌🚫💢



</br>

----

</br>

## 📌 데이터 일부만 추려보기

### 🔎 LIMIT  제한, 한도

```sql
SELECT * FROM copang_main.member
ORDER BY sign_up_day DESC
LIMIT 10;
LIMIT 8, 2;
```

> LIMIT n은 row 0 부터 n까지, LIMIT n, m 은 row n부터 m개를 추려서 확인

## 💡row는 0 부터 시작한다는 것을 명심해야한다.❗❗