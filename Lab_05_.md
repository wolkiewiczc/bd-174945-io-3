1.
--- pkt1
```sql
create table infs_wolkiewiczc.client AS select * FROM company_2025.CLIENT;
create table infs_wolkiewiczc.ORDER AS select * FROM company_2025.ORDER;
create table infs_wolkiewiczc.EMPLOYEE AS select * FROM company_2025.EMPLOYEE;
```
--- pkt2
```sql
SELECT * FROM infs_wolkiewiczc.ORDER;
```
--- pkt3
```sql
SELECT * FROM `ORDER` where ORDER_STATUS = 5;
```
--- pkt4
```sql
SELECT ORDER_ID, ORDER_STATUS FROM `ORDER` where ORDER_ID in (1, 3, 5);
```
2.
--- pkt1
```sql
SELECT * FROM `EMPLOYEE` where FIRST_NAME = "Agnieszka" and pensja = 3900;
```
--- pkt2
```sql
SELECT * FROM `EMPLOYEE` where  pensja between 5000 and 7000;
```
--- pkt3
```sql
SELECT * FROM `CLIENT` where IS_COMPANY = 1 and SHORT_NAME like '%eco%' ;
```
3.
--- pkt1
```sql
SELECT * FROM `ORDER` where Month(ORDER_DATE) in (6,7);
```
--- pkt2
```sql
SELECT * FROM CLIENT WHERE TAX_IDENTIFIER is not null ORDER BY SHORT_NAME ASC;
```
--- pkt3
```sql
SELECT * FROM EMPLOYEE ORDER BY BIRTH_DATE DESC Limit 5;
```
4.
--- pkt1
```sql
SELECT distinct(FIRST_NAME) FROM EMPLOYEE;
```
--- pkt2
```sql
SELECT CONCAT(FIRST_NAME,"-",LAST_NAME) AS "imię-nazwisko" FROM EMPLOYEE where LAST_NAME LIKE 'ko%';
```
--- pkt3
```sql
SELECT LAST_NAME,pensja FROM EMPLOYEE where year(DATE_OF_EMPLOYMENT) between 2010 and 2014;
```
5.
--- pkt1
```sql
SELECT pensja,(pensja-pensja/4) AS NETTO , pensja/4 AS podatek FROM EMPLOYEE ;
```
--- pkt2
```sql
SELECT * FROM CLIENT WHERE TAX_IDENTIFIER is null;
```
--- pkt3
```sql
SELECT SHORT_NAME FROM CLIENT WHERE SHORT_NAME like 'K%' or SHORT_NAME like '%ski' order by SHORT_NAME DESC;
```
