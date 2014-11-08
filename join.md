# Join Çeşitleri

## İnner join

**tablo birleştirir sonuçları ekrana gösterir**

```sql
SELECT 
* 
FROM 
BOLUM INNER JOIN PROGRAM 
ON (BOLUM .BOLUM_ID=PROGRAM .BOLUM_ID) 
```


## Outer join

**tablo birleştirir ve null değerine sahip alanlarıda listeler**

```sql
SELECT 
* 
FROM 
BOLUM LEFT OUTER JOIN PROGRAM 
ON (BOLUM .BOLUM_ID=PROGRAM .BOLUM_ID)
```

## Left && Right outer join

**tablo birleştirir tablo yönünü belirlemeyi sağlar**

```sql
SELECT 
* 
FROM 
PROGRAM RIGHT OUTER JOIN BOLUM
ON (BOLUM .BOLUM_ID=PROGRAM .BOLUM_ID)
```

## Full join

**Left ve right outer joinlerin birleşik olarak kullanılmasını sağlar. Left ve right
işlemlerinin birleşimidir. Karşılıklı null olan kayıtlar listelenir.**

```sql
SELECT 
* 
FROM 
PROGRAM FULL OUTER JOIN BOLUM 
ON (BOLUM .BOLUM_ID=PROGRAM .BOLUM_ID)
```

## Semi join

**Join tekniği kullanılarak yazılmış bir sorguda kullanılan karşılıklı tablolardan
sadece birine göre listeleme yapılacaksa semi join kullanılır. Yani sadece bir
varlığa sahip kolonlar listelenir**


```sql
SELECT B.* FROM 
BOLUM B FULL OUTER JOIN PROGRAM P ON(B.BOLUM_ID=P.BOLUM_ID)
```

## Anti Join

**Semi join gibi kullanılır fakat ilişkide ortak olmayan satırların
listelenmesini sağlar.**

```sql
SELECT * from BOLUM 
where BOLUM_ID not in (
SELECT 
PROGRAM .BOLUM_ID 
FROM 
PROGRAM inner JOIN BOLUM 
ON (BOLUM .BOLUM_ID=PROGRAM .BOLUM_ID)
)
```

## Naturel Join

**Aynı isimde ve tiple olan sütünlara göre otomatik birleşirir. İlişkili
kolonların birleştirilmesidir. Ortak sütun tek hale getirilerek sorgu
listelenir. Her iki ilişkide ortak sütun üzerinden görünmez bir join
oluşturulur. Equi joindeki aynı isim ve nitelikleri tekrar yazmamak için
kullanılır. Eğer sütun isimleri farklıysa önce rename yapılır.**

```sql
SELECT * from BOLUM 
where BOLUM_ID not in (
SELECT 
PROGRAM .BOLUM_ID 
FROM 
PROGRAM inner JOIN BOLUM 
ON (BOLUM .BOLUM_ID=PROGRAM .BOLUM_ID)
)
```
