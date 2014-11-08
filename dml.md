# (Data Manipulation Language (DDL) 

`Veri İşleme Dili `

## Komutlar

* [**SELECT Komutu**](#select)
* [**INSERT Komutu**](#ınsert)
* [**UPDATE Komutu**](#update)
* [**DELETE Komutu**](#delete)


## Select

**Listeleme, seçme işlemi gerçekleştirir.**

1. Sorgulanacak tabloların her sütunu yazdırılabilir.
2. Birden fazla tablo üzerinde işlem yapılabilir.
3. Matematiksel, mantıksal ifadeler kullanılabilir.
4. Genel manada sorgulama da esneklik sağlar. (Sıralama, koşul belirtme ...)

`SELECT DISTINCT <SÜTUN_ADI , ...> as ... FROM <TABLE_NAME>, ... 
WHERE <KOŞUL_İFADESI> `

```sql
SELECT DISTINCT KAPASITE FROM SINIFLAR WHERE KAPASITE >40

```

## Insert

**Veri tabanı üzerindeki herhangi bir tabloya bir veya select ile
kullanıldığında toplu olarak kayıt ekler. Insert into ifadesinden sonra gelen table
name üzerindeki kolon sıralaması varsa, values ifadesi içerisindeki sıralama için
önemlidir. NOT NULL değerler kayıt ekleme sırasında göz ardı edilemez. Select
ifadesi ile birden fazla kayıt aynı anda eklenebilir.**

`INSERT INTO <TABLE_NAME> (<KOLON_1>,<KOLON_2> , ... ) 
VALUES (<KOLON_1_DEGER>,<KOLON_2_DEGER> , ...)
`

````sql
INSERT INTO TBL_BOLUM (BOLUM_ADI,SILINDIMI)
VALUES ('Bilgisayar Programciligi UE',0)

```


## Update

**Tablo üzerinde yer alan kayıtlar üzerinde güncelleme işlemi yapar.
Koşul ifadesi olarak kullanılan where ifadesi sayesinde istenilen kayıt veya
kayıtlar güncellenir. Where ifadesinden sonra koşul yazılmaz ise ilgili tablo
üzerindeki her kayıt güncellemeden etkilenir. Doğru bir güncelleme işlemi
için koşul ifadesi mantıksal ve karşılaştırma operatörlerinden faydalanılarak
yazılmalıdır. (<, >, <=, >=, <>, or, and, not, in/not in, between, Like, ...
Vb.)
**

`UPDATE <TABLE_NAME> 
SET <SÜTUN_ADI=DEGER_1>, ...
WHERE <Koşul_İfadesi>`

```sql
UPDATE TBL_OGRENCI
SET OGR_ADI = 'MEHMET'
WHERE OGR_ID=1
```

## Delete

**Tablo üzerinde kayıtları koşullu veya koşulsuz olarak silmek için
kullanılır. Silinmek istenen kayıt veya kayıtlar where ifadesi ile sınırlandırılır.
Where ifadesi kullanılmaz ise tabloadaki tüm kayıtlar silinir. Transaction log
ile kayıt altına alınır. Delete işlemi sonrası otomatik index numarası
tanımlanmış ise kaldığı yerden devam eder (Identity, Sequence ...).**

`DELETE FROM <TABLE_NAME>
WHERE <Koşul_İfadesi>
`

```sql
DELETE FROM TBL_OGRENCI
WHERE OGR_ID=2
```

