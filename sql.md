---
title: Sql Server
---


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
