Zadanie 1
```sql
Create table lab10(ORDER_NUMBER VARCHAR(45), CHANGE_DATE TIMESTAMP, NEW_STATUS_NAME VARCHAR(100))

delimiter //
create trigger lab10 after update on `ORDER` for each row
begin 
declare statusname varchar(100);
SELECT STATUS_NAME INTO statusname FROM ORDER_STATUS WHERE STATUS_ID = old.ORDER_STATUS;
	INSERT INTO lab10 VALUES(OLD.ORDER_NUMBER,
    current_date(), 
    statusname);
end //
```
Zadanie 2
```sql
DELIMITER $$
create trigger check_amount BEFORE INSERT ON company_2025.order_position for each row 
begin
declare stock_amount decimal(7,2)
SELECT AMOUNT into stock_amount FROM INVENTORY where PRODUCT_ID = new.PRODUCT_ID limit 1;
IF stock_amount is null then signal sqlstate '4500' set message_text = 'Produkt nie istnieje w magazynie'
END IF;
IF stock_amount < new.amount then signal sqlstate '4500' set message_text = ' ZA MAŁO '
end if;
END $$
DELIMITER ;
```
Zadanie 3
```sql

```
Zadanie 4
```sql

```
Zadanie 5
```sql

```
