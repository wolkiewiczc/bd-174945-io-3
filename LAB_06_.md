1.
--- pkt1
```sql
Select AVG(pensja) FROM EMPLOYEE;
```
--- pkt2
```sql
Select AVG(pensja),count(JOB_POSITION_ID) FROM EMPLOYEE group by(JOB_POSITION_ID);
```
--- pkt3
```sql
Select DEPARTMENT_ID,AVG(2025-year(BIRTH_DATE)) FROM EMPLOYEE group by(DEPARTMENT_ID);
```
2.
--- pkt1
```sql
Select DEPARTMENT_ID,sum(pensja) FROM EMPLOYEE group by(DEPARTMENT_ID) order by sum(pensja) desc;
```
--- pkt2
```sql
Select JOB_POSITION_ID,AVG(pensja) FROM EMPLOYEE group by(JOB_POSITION_ID) having count(JOB_POSITION_ID)>=3 and avg(pensja)>3000;
```
--- pkt3
```sql
Select DEPARTMENT_ID,count(distinct(pensja)) AS liczba_różnych_pensji FROM EMPLOYEE
group by DEPARTMENT_ID having count(DEPARTMENT_ID)>4 order by count(distinct(pensja));
```
3.
--- pkt1
```sql
create table infs_wolkiewiczc.JOB_POSITION AS select * from company_2025.JOB_POSITION;
create table infs_wolkiewiczc.DEPARTMENT AS select * from company_2025.DEPARTMENT;
```
--- pkt2
```sql
SELECT d.DEPARTMENT_NAME, count(e.EMPLOYEE_NAME)
FROM DEPARTMENT d LEFT JOIN EMPLOYEE e ON d.DEPARTMENT_ID = e.DEPARTMENT_ID
group by d.DEPARTMENT_NAME;
```
--- pkt3
```sql
SELECT d.DEPARTMENT_NAME, concat(FIRST_NAME,"-",LAST_NAME)
FROM DEPARTMENT d LEFT JOIN EMPLOYEE e ON d.DEPARTMENT_ID = e.DEPARTMENT_ID;
```
4.
--- pkt1
```sql
SELECT e.LAST_NAME,j.POSITION_NAME
FROM EMPLOYEE e natural join JOB_POSITION j
where year(BIRTH_DATE) between 1990 and 1999;
```
--- pkt2
```sql
SELECT e.LAST_NAME,e.FIRST_NAME,j.POSITION_NAME
FROM EMPLOYEE e natural join JOB_POSITION j
where j.POSITION_NAME = "magazynier" order by BIRTH_DATE desc limit 5;
```
--- pkt3
```sql
SELECT concat(a.CLIENT_ID,"-",b.CLIENT_ID),concat(a.SHORT_NAME,"-",b.SHORT_NAME)
FROM CLIENT a JOIN CLIENT b on (a.CLIENT_ID+5) = b.CLIENT_ID
order by a.CLIENT_ID;
```
5.
--- pkt1
```sql
Select j.POSITION_NAME, avg(pensja)
FROM EMPLOYEE e
JOIN JOB_POSITION j ON j.JOB_POSITION_ID=e.JOB_POSITION_ID
JOIN DEPARTMENT d ON d.DEPARTMENT_ID=e.DEPARTMENT_ID
where d.DEPARTMENT_NAME not in ("HR","IT")
GROUP BY j.POSITION_NAME
having count(e.DEPARTMENT_ID)>3; 
```
--- pkt2
#########
Select j.JOB_POSITION_ID,MAX(e1.BIRTH_DATE),Min(e2.BIRTH_DATE)
FROM EMPLOYEE e1 ,(Select MAX(k.BIRTH_DATE),Min(k.BIRTH_DATE) FROM EMPLOYEE k) e2
JOIN JOB_POSITION j ON j.JOB_POSITION_ID=e.JOB_POSITION_ID
JOIN DEPARTMENT d ON d.DEPARTMENT_ID=e.DEPARTMENT_ID
;

(Select MAX(BIRTH_DATE),Min(BIRTH_DATE)
FROM EMPLOYEE)

select * from EMPLOYEE, DEPARTMENT;
#########
