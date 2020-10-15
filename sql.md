---
title: Sql Server
---


## Order Query

```sql
Select - From - Where - Group By - Having - Order By
```

## Order EXEC Query

```sql
From - Where - Group By - Having - Select - Order By
```

## Window Function

```list
 کار کردن بر روی مجموعه ای از رکورد ها-1
 2-گروه بندی رکورد های یک جدول
```

```sql
window_Function() 
OVER (   
       [ <PARTITION BY clause> ]  
       [ <ORDER BY clause> ]   
       [ <ROW or RANGE clause> ]  
      ) 
```

ORDER BY اجباری است.

```sql
USE AdventureWorks2016
GO

SELECT
ROW_NUMBER() OVER (PARTITION BY S.TerritoryID  ORDER BY S.SalesOrderID) as RowNO,
*
FROM Sales.SalesOrderHeader S
GO

```

```sql
USE AdventureWorks2016
GO
SELECT * FROM
(
SELECT
ROW_NUMBER() OVER (PARTITION BY S.TerritoryID  ORDER BY S.SalesOrderID) as RowNO,
*
FROM Sales.SalesOrderHeader S
) d ORDER BY d.RowNO
GO 
```


```sql
RANK() --با کپ
DENSE_RANK() -- بدون کپ
NTILE(8) --   گروه بندی (به 8 گروه تقسیم  میکند)
```



## Window Aggregates

```sql
USE AdventureWorks2016
GO
SELECT
S.CustomerID,S.SalesOrderID, CAST(S.OrderDate AS date) AS OrderDate,S.SubTotal,
SUM(S.SubTotal) OVER (PARTITION BY S.CustomerID ORDER BY S.SalesOrderID) AS SubTotal
FROM Sales.SalesOrderHeader S
GO
```

## Analytical Function

#### LEAD  استفاده از سطر بعدی برای رکورد جاری

offset چه تعداد سطر در نظر گرفته نشود
default مقدار پیش فرض برای رکوردهای قبلی یا بعدی ای وجود ندارد

```sql
    LEAD (Expression [offset] [default])
    OVER ( [ <PARTITION BY clause> ]  
           [ <ORDER BY clause> ]) 
```
#### LAG  استفاده از سطر قبلی برای رکورد جاری


```sql
    LAG (Expression [offset] [default])
    OVER ( [ <PARTITION BY clause> ]  
           [ <ORDER BY clause> ]) 
```
## window Frame

```list
  محدود کردن ردیف های بیشتر در پارتیشن -1
 2- کار کردن در هر لحظه با تعداد رکورد های خاص
```


## Copy Table 

```sql
  SELECT * INTO NewTable From OldTable

  SELECT * INTO NewTable From OldTable WHERE 1=2     --بدون دیتا

```



## OUTPUT   FOR INSERT - UPDATE - DELETE - MERGE

```sql
-- گرفتن دیتا اضافه شده بلافاصله بعد از اضافه شدن در دیتابیس
  INSERT INTO Customers(CustID,CompanyName,Phone)
  OUTPUT inserted.*
  VALUES(6,'Cust 6', '(666) 666-6666')

  UPDATE Orders SET Country='IRAN'
  OUTPUT deleted.*,inserted.*
  WHERE OrderID = 10

  DELETE Orders 
  OUTPUT deleted.*
  WHERE OrderID = 10

```

## UBDATE BY JOIN

```sql
UPDATE OD SET OD.Discount=0.5
FROM [OrderDetails] OD
INNER JOIN Orders O ON OD.OrderID = O.OrderID
INNER JOIN Customers C ON O.CustomerID = C.CustomerID
WHERE c.Country = 'UK'
```

## DELETE BY JOIN

```sql
DELETE FROM OD 
FROM [OrderDetails] OD
INNER JOIN Orders O ON OD.OrderID = O.OrderID
INNER JOIN Customers C ON O.CustomerID = C.CustomerID
WHERE c.Country = 'UK'
```

## TRUNCATE  

```sql
--برای پاک کردن با سرعت بالا با رعایت شرایط
TRUNCATE FROM Orders 
```

## BULK INSERT  

```sql
BULK INSERT Students
FROM 'C:\Dump\Students.txt'
WITH
(
       KEEPIDENTITY,
       FIRSTROW=1,
       FIELDTERMINATOR=',',
       ROWTERMINATOR='\n'
)
GO
```