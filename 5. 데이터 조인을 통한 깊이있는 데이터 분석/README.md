## 📌 조인(join)

실무에서 최소 열 개, 수 십, 수백개의 테이블을 다뤄야하는데 테이블 간의 연관 관계를 파악하고 여러 테이블을 하나로 합쳐서 활용 해야한다.<br>여러 테이블을 합쳐서 하나의 테이블인 것처럼 보는 행위를 **조인(join)'**이라고 한다. 실무에서 조인을 잘해야 제대로된 데이터 분석을 할 수 있다.

</br>



'다른 테이블의 특정 row를 식별할 수 있게 해주는 컬럼'을 **Foreign Key**라고 합니다. 

Foreign Key는 우리말로 **외래키**라고도 합니다.

**Foreign Key는 다른 테이블의 특정 row를 식별할 수 있어야 하기 때문에 주로 다른 테이블의 Primary Key를 참조할 때가 많습니다.** 



     , decode(sa.sales_volume, null, '판매량 정보 없음'
                             , sa.sales_volume) as '판매량'
LEFT OUTER JOIN 왼쪽 테이블을 기준으로 해당 값이 있으면 나타내주고
오른쪽 테이블에 연관된 컬럼내용이 있다면 값을 보여주고 없으면 NULL 로 나타낸다.











select substring(it.registration_date, 0, 4) as '등록 연도'
     , count(re.*) as '리뷰 개수'
     , avg(re.star) as '별점 평균값'
  from review re inner join item it on re.item_id = it.id
    inner join member me on re.mem_id = me.id
 where 1=1
   and it.gender = 'u'
 group by substring(it.registration_date, 0, 4)
having count(substring(it.registration_date, 0, 4)) >= 10
 order by avg(re.star)

🌵🔥🌪️🌹🌻🍀🌱💻💡💣💊🎈🧷🔍🔎📌📍🎁🔑🗝️⏱️❓❗⭐

0️⃣1️⃣2️⃣3️⃣4️⃣5️⃣6️⃣7️⃣8️⃣9️⃣🔟🔼🔽➡️⬅️〰️➰➿🎵🎶❌🚫💢





