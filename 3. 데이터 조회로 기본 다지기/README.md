## 📌 데이터 조회의 핵심, SELECT 와 WHERE

### 🔎 SELECT 테이블의 데이터를 조회할 때 사용하는 구문

#### 💡 SELECT * FROM copang_main.member;

> ' * ' asterisk 모든 컬럼을 조회한다.

#### 💡 SELECT email, age, address FROM copang_main.member;

> 이렇게 하면 보고 싶은 컬럼만 조회 할 수 있다.

#### 💡 FROM 뒤에는 어떤 테이블에 어떤것을 조회할 지 선택해준다.

#### 💡 SELECT * FROM copang_main.member WHERE email = 'codeit@naver.com;

> WHERE 뒤에는 특정 조건을 설정한다.



-----



## 📌 SQL 작성 형식

### 1️⃣  SQL 문에는 항상 세미콜론을 사용해야한다. ❗❗

> 하나의 SQL문 끝에 세미콜론을 써줘야한다. SQL문법 상 세미콜론이 **하나의 SQL 문을 종결하는 단위**이기 때문이다.



### 2️⃣ SQL 문 안에는 공백이나 개행 등을 자유롭게 넣을 수 있다.

> 어떤 방식으로 쓰든 구분되어야할 키워드들이 최소한 하나 이상의 공백으로 구분되어 있고, 세미콜론으로 마무리되어 있으면 실행에는 문제가 없다. 이런 점을 이용해 **길이가 긴 SQL 문을 쓸 때는 개행(줄바꿈), 탭 등을 적절하게 활용하여 가독성을 높인다.**

```sql
SELECT * FROM copang_main.member	WHERE email = 'codeit@naver.com';

SELECT * FROM copang_main.member
		WHERE email = 'codeit@naver.com';
```



### 3️⃣ SQL 문의 대소문자 구분 문자

```sql
SELECT * FROM copang_main.member WHERE email = 'codeit@naver.com';

```

> 대문자로 작성된 내용은 MySQL에서 원래부터 존재하는 **예약어**이며 그 외에 내용은 **사용자가 지정한 부분**입니다.
>
> MySQL의 예약어는 대문자로 적는 것이 관례이고, 가독성에 좋습니다. 단, 소문자로 바꿔서 실행해도 문제되지 않습니다.
>
> 나머지 사용자가 지정한 부분에 데이터베이스 이름, 테이블 이름, 컬럼 이름 등은 대소문자를 가리지 않고, 실제로 존재하는 것의 이름을 작성하면 된다.

## 

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



-----











🌵🔥🌪️🌹🌻🍀🌱💻💡💣💊🎈🧷🔍🔎📌📍🎁🔑🗝️⏱️❓❗⭐

0️⃣1️⃣2️⃣3️⃣4️⃣5️⃣6️⃣7️⃣8️⃣9️⃣🔟🔼🔽➡️⬅️〰️➰➿🎵🎶❌🚫💢









---



## 📌 데이터 정렬해서 보기

### 🔎 정렬  : row들을 특정 컬럼을 기준으로 순서대로 출력



```sql
SELECT * FROM copang_main.member
ORDER BY height ASC;
```

#### 💡기본으로 **ASC** (ascending) 오름차순 

#### 💡**DESC**(descending) 내림차순



```sql
SELECT * FROM copang_main.member
ORDER BY YEAR(sign_up_day) DESC, email ASC;
```

> 정렬이 차례대로 YEAR(sign_up_day)이 먼저 내림차순, email이 오름차순 순으로 정렬 된다.

#### 

-----



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



---

