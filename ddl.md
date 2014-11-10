# Data Defination Language (DDL) 

`Veri Tanımlama Dili`

## Komutlar

* [**Create Komutu**](#create)
* [**Alter Komutu**](#alter)
* [**DROP Komutu**](#drop)
* [**TRUNCATE Komutu**](#truncate)


## Create

**Veri tabanı üzerinde herşey nesnedir. Nesne oluşturmak için Create 
kullanılır. Database, view, trigger,user, table, function, procedure gibi 
nesneler create deyimi ile oluşturulur.**

```sql

CREATE TABLE TBL_BOLUM
(
BOLUM_ID int identity(1,1) not null,
BOLUM_ADI varchar(200) not null,
SILINDIMI int not null,
CONSTRAINT PK_BOLUM PRIMARY KEY (BOLUM_ID)
)


CREATE TABLE TBL_OGRENCI
(
OGR_ID int identity(1,1) not null,
OGR_ADI varchar(200) not null,
OGR_SOYADI varchar(200) not null,
TC_NO varchar(11) not null,
SILINDIMI int not null,
KAYIT_TARIHI smalldatetime not null,
BOLUM_ID int not null,
CONSTRAINT PK_OGRENCI PRIMARY KEY (OGR_ID),
CONSTRAINT FK_OGRENCI_BOLUM FOREIGN KEY (BOLUM_ID) REFERENCES TBL_BOLUM(BOLUM_ID)
) 

```

## Alter

**Varolan bir nesneyi güncellemek için alter deyimi kullanılır. Default
kullanmadan, Not Null değer ekleyebilmek için ilgili tabloda değer olmamalıdır.**

1. Alter Table kullanarak sütun ekleme işlemi 

`ALTER TABLE <TABLE_NAME> ADD <SÜTUN ADI> OZELLİK`

```sql
ALTER TABLE TBL_OGRENCI
ADD ADRES VARCHAR(1000) NOT NULL
```

2. Alter Table kullanarak sütun silme işlemi 

`ALTER TABLE <TABLE_NAME> DROP COLUMN <SÜTUN ADI>`

```sql
ALTER TABLE TBL_OGRENCI
DROP COLUMN ADRES 
```

3. Alter Table kullaraka sütun güncelleme işlemi 

`ALTER TABLE <TABLE_NAME> ALTER COLUMN <SÜTUN ADI> ÖZELLİK`

```sql
ALTER TABLE TBL_OGRENCI
ALTER COLUMN ADRES VARCHAR(500) NOT NULL
```

## Drop

**Veri tabanı üzerindeki nesneleri silmek için kullanılır. Alter deyimiyle 
kullanılan drop ifadesi nesneye bağlı özelliği silmek için kullanılır.**

```sql
DROP TABLE <TABLE_NAME>
DROP DATABASE <DB_NAME>
```

## TRUNCATE

**Veri tabanı üzerindeki tabloyu değil, tabloya bağlı tüm kayıtları
silmek için kullanılır. Bir diğer tabiriyle delete from <table_name> işlemini
gerçekleştirir. Delete ile yapılan silme işleminde index kaldığı yerden devam
ederken, truncate işleminde ise index başa döner. Transaction Log içerisine
kayıt işlemi yapılmaz. Hızlıdır. Inserted ve Deleted sahte tablolarına kayıt
yazılmaz. Komut çalıştırılırken tabloya bağlı diğer tablolar göz ardı
edilmemelidir (fk durumları).**

```sql
TRUNCATE TABLE <TABLE_NAME>
```


