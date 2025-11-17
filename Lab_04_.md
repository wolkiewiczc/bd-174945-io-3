# Zadanie 1
-- pkt 1
```sql
alter table zadanie drop foreign key zadanie_ibfk_1;
alter table projekt drop foreign key projekt_ibfk_1;
```
-- pkt 2
```sql
alter table pracownik change id_pracownika id_pracownika int;
alter table pracownik drop primary key;
```
-- pkt 3
```sql
alter table pracownik add primary key (id_pracownika);
```
-- pkt 4
```sql
alter table zadanie add foreign key (pracownik) references pracownik(id_pracownika) on delete set null;
alter table projekt add foreign key (menadzer_projektu) references pracownik(id_pracownika);
```
# Zadanie 2
-- pkt 1
```sql
alter table zadanie add column godziny_szacowane INTEGER default 8;
```
--pkt 2
```sql
update zadanie set godziny_szacowane = 4 where id_zadania = 1;
update zadanie set godziny_szacowane = 12 where id_zadania = 2;
```
-- pkt 3
```sql
alter table zadanie change godziny_szacowane godziny_szacowane INTEGER default 6;
```
-- pkt 4
```sql
INSERT INTO zadanie values(4, "praca domowa", "normalny","matma", null, null,null,default);
delete from zadanie where id_zadania = 4;
```

# Zadanie 3
-- pkt 1
```sql
alter table projekt add column opis_projektu varchar(50);
```
-- pkt 2
```sql
alter table projekt modify opis_projektu varchar(200);
```
-- pkt 3
```sql
update projekt set opis_projektu = ("MVP") where id_projektu = 1;
update projekt set opis_projektu = ("XD") where id_projektu = 2;
```
-- pkt 4
```sql
alter table projekt drop column opis_projektu;
```

# Zadanie 4
-- pkt 1
```sql
alter table zadanie drop foreign key zadanie_ibfk_2;
```
-- pkt 2
```sql
alter table zadanie add foreign key (projekt) references projekt(id_projektu) ON DELETE SET NULL;
```
-- pkt 3
```sql
delete from projekt where id_projektu = 2;
```
-- pkt 4
```sql
select * from zadanie;
```
