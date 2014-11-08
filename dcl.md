# Data Control Language (DCL) 

`Veri Kontrol Dili  `

## Komutlar

* [**GRANT Komutu**](#grant)
* [**DENY Komutu**](#deny)
* [**REVOKE Komutu**](#revoke)


## Grant

**Yetki vermek için kullanılır.**

```sql
GRANT select, crate table
ON TBL_ABC, TBL_CDE TO Guest1433, Guest1434
```

## Deny

**Kullanıcının veritabanı üzerindeki nesneleri kullanmasını kısıtlamak
için kullanılır. Grant ile verilen bir yetki deny ile alınır. Deny işlemi grant
işlemine göre baskındır.**

```sql
DENY CREATE TABLE TO Guest1433, Guest1434
```

## Revoke

**Veritabanı üzerinde kullanıcı üzerinde tanımlanmış tüm
yetkilerin kaldırılmasını sağlar (engellenen ve verilen). Yetki kaldırılırsa
grant ile tekrar yetki verilebilir. Fakat deny ile verilen bir kısıtlama grant
ile aşılamaz.**

```sql
REVOKE SELECT ON TBL_ABC 
FROM Guest1433, Guest1434 
```

