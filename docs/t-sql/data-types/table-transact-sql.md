---
title: 表 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 7/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|data-types
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- table data type [SQL Server]
- table variables [SQL Server]
ms.assetid: 1ef0b60e-a64c-4e97-847b-67930e3973ef
caps.latest.revision: 48
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 1751c6c9b6a05cd4337bd376108ef8d7e3d84ea4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="table-transact-sql"></a>表 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

一种特殊的数据类型，可用于存储结果集以进行后续处理。 table 主要用于临时存储一组作为表值函数的结果集返回的行。 可将函数和变量声明为 table 类型。 table 变量可用于函数、存储过程和批处理中。 若要声明 table 类型的变量，请使用 [DECLARE @local_variable](../../t-sql/language-elements/declare-local-variable-transact-sql.md)。
  

**适用范围**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] （[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 到 [当前版本](http://go.microsoft.com/fwlink/p/?LinkId=299658)）、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。
  
![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>语法  
  
```sql
table_type_definition ::=   
    TABLE ( { <column_definition> | <table_constraint> } [ ,...n ] )   
  
<column_definition> ::=   
    column_name scalar_data_type   
    [ COLLATE <collation_definition> ]   
    [ [ DEFAULT constant_expression ] | IDENTITY [ ( seed , increment ) ] ]   
    [ ROWGUIDCOL ]   
    [ column_constraint ] [ ...n ]   
  
 <column_constraint> ::=   
    { [ NULL | NOT NULL ]   
    | [ PRIMARY KEY | UNIQUE ]   
    | CHECK ( logical_expression )   
    }   
  
<table_constraint> ::=   
     { { PRIMARY KEY | UNIQUE } ( column_name [ ,...n ] )  
     | CHECK ( logical_expression )   
     }   
```  
  
## <a name="arguments"></a>参数  
table_type_definition  
与在 CREATE TABLE 中定义表时所用的信息子集相同的信息子集。 表声明包括列定义、名称、数据类型和约束。 允许的约束类型仅为 PRIMARY KEY、UNIQUE KEY 和 NULL。  
有关语法的详细信息，请参阅 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)、[CREATE FUNCTION (Transact-SQL)](../../t-sql/statements/create-function-transact-sql.md) 和 [DECLARE @local_variable (Transact-SQL)](../../t-sql/language-elements/declare-local-variable-transact-sql.md)。
  
collation_definition  
由 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 区域设置和比较样式、Windows 区域设置和二进制表示法或 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 排序规则组成的列的排序规则。 如果未指定 collation_definition，则此列将继承当前数据库的排序规则。 另外，如果将此列定义为公共语言运行时 (CLR) 用户定义类型，则它将继承用户定义类型的排序规则。
  
## <a name="remarks"></a>Remarks  
可以在批处理的 FROM 子句中按名称引用 table 变量，如下例所示：
  
```sql
SELECT Employee_ID, Department_ID FROM @MyTableVar;  
```  
  
在 FROM 子句外，必须使用别名来引用 table 变量，如下例所示：
  
```sql
SELECT EmployeeID, DepartmentID   
FROM @MyTableVar m  
JOIN Employee on (m.EmployeeID =Employee.EmployeeID AND  
   m.DepartmentID = Employee.DepartmentID);  
```  
  
对于具有不更改的查询计划的小规模查询以及在主要考虑重新编译时，table 变量提供以下好处：
-   table 变量的行为类似于局部变量。 有明确定义的作用域。 这就是在其中声明该变量的函数、存储过程或批处理。  
     在其作用域内，table 变量可像常规表那样使用。 该变量可应用于 SELECT、INSERT、UPDATE 和 DELETE 语句中用到表或表的表达式的任何地方。 但是，table 不能用于以下语句中：  
  
```sql
SELECT select_list INTO table_variable;
```
  
在定义 table 变量的函数、存储过程或批处理结束时，会自动清除此变量。
  
-   在存储过程中使用 table 变量与使用临时表相比，减少了存储过程的重新编译量，并且没有影响性能的基于成本的选择。  
-   涉及 table 变量的事务只在 table 变量更新期间存在。 因此，table 变量需要较少的锁定和记录资源。  
  
## <a name="limitations-and-restrictions"></a>限制和局限
Table 变量没有分发统计信息，不会触发重新编译。 因此，在许多情况下，优化器会在假定 table 变量没有行的前提下生成查询计划。 出于这一原因，如果您预计会存在大量行（超过 100 行），那么在使用 table 变量时应小心谨慎。 这种情况下，使用临时表可能是更好的解决方案。 或者，如果查询联接 table 变量和其他表，则可使用 RECOMPILE 提示，这使优化器会对 table 变量使用正确的基数。
  
在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 优化器基于成本的原因模型中，不支持 table 变量。 因此，在需要基于成本的选择来实现高效的查询计划时，不应使用这些变量。 在需要基于成本的选择时，临时表是首选。 这通常包含具有联接、并行度决策和索引选择选项的查询。
  
修改 table 变量的查询不会生成并行查询执行计划。 修改特大型 table 变量或复杂查询中的 table 变量时，可能会影响性能。 在这种情况下，请考虑改用临时表。 有关详细信息，请参阅 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)。 还可以并行执行读取 table 变量而不对变量进行修改的查询。
  
不能显式创建 table 变量的索引，也不保留 table 变量的任何统计信息。 在某些情况下，可以通过改用支持索引和统计信息的临时表来改善性能。 有关临时表的详细信息，请参阅 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)。
  
table 类型声明中的 CHECK 约束、DEFAULT 值和计算列不能调用用户定义函数。
  
不支持在 table 变量之间进行赋值操作。
  
由于 table 变量作用域有限，并且不是持久数据库的一部分，因而不受事务回滚的影响。
  
表变量在创建后就无法更改。
  
## <a name="examples"></a>示例  
  
### <a name="a-declaring-a-variable-of-type-table"></a>A. 声明一个表类型的变量  
下例将创建一个 `table` 变量，用于储存 UPDATE 语句的 OUTPUT 子句中指定的值。 在它后面的两个 `SELECT` 语句返回 `@MyTableVar` 中的值以及 `Employee` 表中更新操作的结果。 请注意，`INSERTED.ModifiedDate` 列中的结果与 `Employee` 表的 `ModifiedDate` 列中的值不同。 这是因为对 `AFTER UPDATE` 表定义了 `ModifiedDate` 触发器，该触发器可以将 `Employee` 的值更新为当前日期。 不过，从 `OUTPUT` 返回的列可反映触发器激发之前的数据。 有关详细信息，请参阅 [OUTPUT 子句 (Transact-SQL)](../../t-sql/queries/output-clause-transact-sql.md)。
  
```sql
USE AdventureWorks2012;  
GO  
DECLARE @MyTableVar table(  
    EmpID int NOT NULL,  
    OldVacationHours int,  
    NewVacationHours int,  
    ModifiedDate datetime);  
UPDATE TOP (10) HumanResources.Employee  
SET VacationHours = VacationHours * 1.25   
OUTPUT INSERTED.BusinessEntityID,  
       DELETED.VacationHours,  
       INSERTED.VacationHours,  
       INSERTED.ModifiedDate  
INTO @MyTableVar;  
--Display the result set of the table variable.  
SELECT EmpID, OldVacationHours, NewVacationHours, ModifiedDate  
FROM @MyTableVar;  
GO  
--Display the result set of the table.  
--Note that ModifiedDate reflects the value generated by an  
--AFTER UPDATE trigger.  
SELECT TOP (10) BusinessEntityID, VacationHours, ModifiedDate  
FROM HumanResources.Employee;  
GO  
```  
  
### <a name="b-creating-an-inline-table-valued-function"></a>B. 创建内联表值函数  
下面的示例将返回内联表值函数。 对于销售给商店的每个产品，该函数返回三列，分别为 `ProductID`、`Name` 以及各个商店年初至今总数的累计 `YTD Total`。
  
```sql
USE AdventureWorks2012;  
GO  
IF OBJECT_ID (N'Sales.ufn_SalesByStore', N'IF') IS NOT NULL  
    DROP FUNCTION Sales.ufn_SalesByStore;  
GO  
CREATE FUNCTION Sales.ufn_SalesByStore (@storeid int)  
RETURNS TABLE  
AS  
RETURN   
(  
    SELECT P.ProductID, P.Name, SUM(SD.LineTotal) AS 'Total'  
    FROM Production.Product AS P   
    JOIN Sales.SalesOrderDetail AS SD ON SD.ProductID = P.ProductID  
    JOIN Sales.SalesOrderHeader AS SH ON SH.SalesOrderID = SD.SalesOrderID  
    JOIN Sales.Customer AS C ON SH.CustomerID = C.CustomerID  
    WHERE C.StoreID = @storeid  
    GROUP BY P.ProductID, P.Name  
);  
GO  
```  
  
若要调用该函数，请运行此查询。
  
```sql
SELECT * FROM Sales.ufn_SalesByStore (602);  
```  
  
## <a name="see-also"></a>另请参阅
[COLLATE (Transact-SQL)](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)  
[CREATE FUNCTION (Transact-SQL)](../../t-sql/statements/create-function-transact-sql.md)  
[用户定义函数](../../relational-databases/user-defined-functions/user-defined-functions.md)  
[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
[DECLARE @local_variable (Transact-SQL)](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[使用表值参数（数据库引擎）](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)  
[查询提示 (Transact-SQL)](../../t-sql/queries/hints-transact-sql-query.md)
  
  
