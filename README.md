<a id="readme-top"></a>
<br />
<div align="center">
    <h3 align="center">SQL SERVER BASIC</h3>
</div>

<!-- DATABASE -->
### DATABASE

_Northwind Database_    [>>See more](https://docs.yugabyte.com/preview/sample-data/northwind/)


<div>
    <a href="#" target="_blank"><img src="northwind/northwind.png" width="1200" alt="Northwind database" /></a>
</div>

<!-- MAIN CONTENTS -->
<details>
  <summary>Main contents</summary>
  <ol>
    <li>
      <a href="#select">SELECT</a>
      <ul>
        <li><a href="#select-distinct">SELECT DISTINCT</a></li>
        <li><a href="#select-top">SELECT TOP</a></li>
      </ul>   
    </li>
    <li>
      <a href="#alias">Alias</a>
    </li>
    <li><a href="#min-max">Min Max</a></li>
    <li><a href="#count-sum-avg">Count-Sum-AVG</a></li>
    <li><a href="#order-by">ORDER BY</a></li>
    <li><a href="#math-operations">Math Operations</a></li>
    <li><a href="#where">Where</a></li>
    <li><a href="#and-or-not">And-Or-Not</a></li>
    <li><a href="#between">Between</a></li>
    <li><a href="#like">LIKE</a></li>
    <li><a href="#wildcard">Wildcard</a></li>
    <li><a href="#in-not-in">IN-NOT IN</a></li>
    <li><a href="#is-null-is-not-null">IS NULL - IS NOT NULL</a></li>
    <li><a href="#group-by">GROUP BY</a></li>
    <li><a href="#day-month-year">Day-Month-Year</a></li>
    <li><a href="#having">HAVING</a></li>
    <li><a href="#query-data-from-multiple-tables">Query data from multiple tables</a></li>
    <li><a href="#union">Union</a></li>
    <li><a href="#join">JOIN - LEFT JOIN - RIGHT JOIN - FULL JOIN</a></li>
    <li><a href="#sub-query">Sub query</a></li>
    <li><a href="#sql-statement-execution-order">SQL statement execution order</a></li>
    <li><a href="#common-table-expression">Common Table Expression</a></li>
    <li><a href="#recursive-query">Recursive query</a></li>
    <li><a href="#windows-functions">Windows Functions</a></li>
    <li><a href="#create-database">Create Database</a></li>
    <li><a href="#create-table">Create Table</a></li>
    <li><a href="#insert">INSERT</a></li>
    <li><a href="#select-into">SELECT INTO</a></li>
    <li><a href="#delete">DELETE</a></li>
    <li><a href="#update">UPDATE</a></li>
    <li><a href="#create-index">Create Index</a></li>
    <li><a href="#view">View</a></li>
    <li><a href="#stored-procedures">Stored Procedures</a></li>
    <li><a href="#trigger">Trigger</a></li>
  </ol>
</details>



<ol>
    <li>
      <a id="select">SELECT</a>
<div style="margin-left: 2em;">
      
* Viết câu lệnh SQL lấy ra tên của tất cả các sản phẩm trong bảng Products
```sh
SELECT [ProductName] FROM [dbo].[Products];
```
* Viết câu lệnh SQL lấy ra tên sản phẩm, giá bán trên mỗi đơn vị, số lượng sản phẩm trên đơn vị trong bảng Products
```sh
SELECT [ProductName], [UnitPrice], [QuantityPerUnit]
FROM [dbo].[Products];
```
* Viết câu lệnh SQL lấy ra tên công ty của khách hàng và quốc gia của các khách hàng đó trong bảng Customers
```sh
SELECT [CompanyName], [Country]
FROM [dbo].[Customers];

SELECT CompanyName, Country
FROM dbo.Customers;
```
* Viết câu lệnh SQL lấy ra tất cả dữ liệu từ bảng Products
```sh
SELECT *
FROM [dbo].[Products];
```
* Viết câu lệnh SQL lấy ra tất cả dữ liệu từ bảng Customers
```sh
SELECT *
FROM [dbo].[Customers];
```
</div>
      <ul>
        <li><a id="select-distinct">SELECT DISTINCT</a></li>
<div style="margin-left: 2em;">


* Viết câu lệnh SQL lấy ra tên các quốc gia (Country) khác nhau từ bảng  Customers
```
SELECT DISTINCT [Country] 
FROM [dbo].[Customers];
```
* Viết câu lệnh SQL lấy ra tên các mã số bưu điện (PostalCode) khác nhau từ bảng Nhà cung cấp - Suppliers
```
SELECT DISTINCT PostalCode 
FROM Suppliers;
```
* Viết câu lệnh SQL lấy ra các dữ liệu khác nhau về họ của nhân viên (LastName) và cách gọi danh hiệu lịch sự (TitleOfCourtesy) của nhân viên từ bảng Employees
```
SELECT DISTINCT [LastName], [TitleOfCourtesy]
FROM [dbo].[Employees];

SELECT DISTINCT [TitleOfCourtesy]
FROM [dbo].[Employees];
```
</div>
        <li><a id="select-top">SELECT TOP</a></li>
<div style="margin-left: 2em;">


* Viết câu lệnh SQL lấy ra 05 dòng đầu tiên trong bảng Customers.
```
SELECT TOP 5 *
FROM [dbo].[Customers];
```

* Viết câu lệnh SQL lấy ra 30% nhân viên của công ty hiện tại.
```
SELECT TOP 30 PERCENT *
FROM [dbo].[Employees];
```

* Viết câu lệnh SQL lấy ra các mã khách hàng trong bảng đơn hàng với quy định là mã khách hàng không được trùng lặp, chỉ lấy 5 dòng dữ liệu đầu tiên.
```
SELECT DISTINCT TOP 5 [CustomerID]
FROM [dbo].[Orders];
```
</div>
      </ul>   
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="alias">Alias</a>
<div style="margin-left: 2em;">

* Viết câu lệnh SQL lấy “CompanyName” và đặt tên thay thế là “Công ty”; “PostalCode” và đặt tên thay thế là “Mã bưu điện”
```
SELECT	[CompanyName] AS [Tên công ty],
		[PostalCode] AS "Mã bưu điện",
		[City] "Thành phố"
FROM [dbo].[Customers];
```
* Viết câu lệnh ra “LastName” và đặt tên thay thế là “Họ”; “FirstName” và đặt tên thay thế là “Tên”
```
SELECT [LastName] AS [Họ và chữ lót],  [FirstName] AS [Tên]
FROM [dbo].[Employees];
```
* Viết câu lệnh SQL lấy ra 15 dòng đầu tiên tất cả các cột trong bảng Orders, đặt tên thay thế cho bảng Orders là “o”
```
SELECT TOP 15 [o].*
FROM [dbo].[Orders] AS [o];
```
</div>
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="min-max">Min Max</a>
<div style="margin-left: 2em;">


* Viết câu lệnh SQL tìm giá thấp nhất của các sẩn phẩm trong bảng Products.
```
SELECT MIN([UnitPrice]) AS [MinPrice]
FROM [dbo].[Products];
```
* Viết câu lệnh lấy ra ngày đặt hàng gần đây nhất từ bảng Orders.
```
SELECT MAX([OrderDate]) AS [MaxOrderDate]
FROM [dbo].[Orders];
```

* Viết câu lệnh SQL tìm số lượng hàng trong kho (UnitsInStock) lớn nhất.
```
SELECT MAX([UnitsInStock]) AS [MaxUnitsInStock]
FROM [dbo].[Products];
```
</div>
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="count-sum-avg">Count-Sum-AVG</a>
<div style="margin-left: 2em;">

* Hãy đếm số lượng khách hàng có trong bảng (Customers).
```
SELECT COUNT(*) AS [NumberOfCustomers]
FROM [dbo].[Customers];

SELECT COUNT([CustomerID]) AS [NumberOfCustomers]
FROM [dbo].[Customers];
```
* Tính tổng số tiền vận chuyển (Freight) của tất cả các đơn đặt hàng.
```
SELECT SUM([Freight]) AS [SumFreight]
FROM [dbo].[Orders];
```
* Tính trung bình số lượng đặt hàng (Quantity) của tất cả các sản phẩm trong bảng [Order Details]
```
SELECT AVG([Quantity]) AS [AvgQuantity]
FROM [dbo].[Order Details];
```
* Đếm số lượng, tính tổng số lượng hàng trong kho và trung bình giá của các sản phẩm có trong bảng Product.
```
SELECT	COUNT(*) AS [NumberOfProducts], 
		SUM([UnitsInStock]) AS [TotalUnitsInStock], 
		AVG([UnitPrice]) AS [AvgUnitPrice]
FROM [dbo].[Products];
```
</div>
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="order-by">ORDER BY</a>
<div style="margin-left: 2em;">

* Bạn hãy liệt kê tất cả các nhà cung cấp theo thứ tự tên đơn vị CompanyName Từ A-Z
```
SELECT *
FROM [dbo].[Suppliers]
ORDER BY [CompanyName] ASC; -- ascending

SELECT *
FROM [dbo].[Suppliers]
ORDER BY [CompanyName];
```
* Bạn hãy liệt kê tất cả các sản phẩm theo thứ tự giá giảm dần.
```
SELECT *
FROM [dbo].[Products]
ORDER BY [UnitPrice] DESC; -- descending
```
* Bạn hãy liệt kê tất cả các nhân viên theo thứ tự họ và tên đệm A-Z. Không dùng ASC | DESC
```
SELECT *
FROM [dbo].[Employees]
ORDER BY [LastName] ASC, [FirstName] ASC;

SELECT *
FROM [dbo].[Employees]
ORDER BY [LastName], [FirstName];
```
* Hãy lấy ra một sản phẩm có số lượng bán cao nhất từ bảng [Order Details]. Không được dùng MAX.
```
SELECT *
FROM [dbo].[Order Details]
ORDER BY [Quantity] DESC;

SELECT TOP 1 *
FROM [dbo].[Order Details]
ORDER BY [Quantity] DESC;
```

</div>
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="math-operations">Math Operations</a>
<div style="margin-left: 2em;">

* Tính số lượng sản phẩm còn lại trong kho (UnitsInStock) sau khi bán hết các sản phẩm đã được đặt hàng (UnitsOnOrder). StockRemaining = UnitsInStock - UnitsOnOrder
```
SELECT	[ProductID], 
		[ProductName], 
		[UnitsInStock],
		[UnitsOnOrder],
		([UnitsInStock]-[UnitsOnOrder]) AS [StockRemaining]
FROM [dbo].[Products];
```
* Tính giá trị đơn hàng chi tiết cho tất cả các sản phẩm trong bảng OrderDetails
 OrderDetailValue = UnitPrice x Quantity
```
SELECT	*,
		([UnitPrice]*[Quantity]) AS [OrderDetailValue]
FROM [dbo].[Order Details];
```

* Tính tỷ lệ giá vận chuyển đơn đặt hàng (Freight) trung bình của các đơn hàng trong bảng Orders so với giá trị vận chuyển của đơn hàng lớn nhất (MaxFreight). FreightRatio = AVG(Freight)/ MAX(Freight) 
```
SELECT  AVG([Freight])/MAX([Freight]) AS [FreightRatio]
FROM [dbo].[Orders]
```
</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="where">Where</a>
<div style="margin-left: 2em;">

* Bạn hãy liệt kê tất cả các nhân viên đến từ thành phố London.
```
SELECT *
FROM [dbo].[Employees]
WHERE [City]='London';
```
* Bạn hãy liệt kê tất cả các nhân viên đến từ thành phố London. Sap xep ket qua theo LastName A->Z
```
SELECT *
FROM [dbo].[Employees]
WHERE [City]='London'
ORDER BY [LastName] ASC;
```
* Bạn hãy liệt kê tất các đơn hàng bị giao muộn, biết rằng ngày cần phải giao hàng là RequiredDate, ngày giao hàng thực tế là ShippedDate.
```
SELECT [OrderID], [RequiredDate], [ShippedDate]
FROM [dbo].[Orders]
WHERE [ShippedDate]>[RequiredDate];


SELECT COUNT(*) AS [So don giao hang muon]
FROM [dbo].[Orders]
WHERE [ShippedDate]>[RequiredDate];
```
* Lấy ra tất cả các đơn hàng chi tiết được giảm giá nhiều hơn 10%. (Discount > 0.1)
```
SELECT * 
FROM [dbo].[Order Details]
WHERE [Discount]>0.1;
```
</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="and-or-not">And-Or-Not</a>
<div style="margin-left: 2em;">

* Bạn hãy liệt kê tất cả các sản phẩm có số lượng trong kho (UnitsInStock) nhỏ hơn 50 hoặc lớn hơn 100.
```
SELECT *
FROM [dbo].[Products]
WHERE [UnitsInStock]<50 OR [UnitsInStock]>100;
```
* Bạn hãy liệt kê tất các đơn hàng được giao đến Brazil, đã bị giao muộn, biết rằng ngày cần phải giao hàng là RequiredDate, ngày giao hàng thực tế là ShippedDate.
```
SELECT *
FROM [dbo].[Orders]
WHERE [ShipCountry]='Brazil' AND [RequiredDate]<[ShippedDate];
```
* Lấy ra tất cả các sản phẩm có giá dưới 100$ và mã thể loại khác 1. Lưu ý: dùng NOT
```
SELECT *
FROM [dbo].[Products]
WHERE [UnitPrice]>=100 OR [CategoryID]=1;

SELECT *
FROM [dbo].[Products]
WHERE NOT([UnitPrice]>=100 OR [CategoryID]=1);
```
</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="between">Between</a>
<div style="margin-left: 2em;">

* Lấy danh sách các sản phẩm có giá bán trong khoảng từ 10 đến 20 đô la.
```
SELECT *
FROM [dbo].[Products]
WHERE [UnitPrice] BETWEEN 10 AND 20;

SELECT *
FROM [dbo].[Products]
WHERE [UnitPrice]>=10 AND [UnitPrice]<=20;
```
* Lấy danh sách các đơn đặt hàng được đặt trong khoảng thời gian từ ngày 1996-07-01 đến ngày 1996-07-31:
```
SELECT *
FROM [dbo].[Orders]
WHERE [OrderDate] BETWEEN '1996-07-01' AND '1996-07-31';
```
* Tính tổng số tiền vận chuyển (Freight) của các đơn đặt hàng được đặt trong khoảng thời gian từ ngày 1996-07-01 đến ngày 1996-07-31:
```
SELECT SUM([Freight]) AS [TotalJulyFreight]
FROM [dbo].[Orders]
WHERE [OrderDate] BETWEEN '1996-07-01' AND '1996-07-31';
```
</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="like">LIKE</a>
<div style="margin-left: 2em;">

* Hãy lọc ra tất cả các khách hàng đến từ các quốc gia (Country) bắt đầu bằng chữ ‘A’
```
SELECT *
FROM [dbo].[Customers]
WHERE [Country] LIKE 'A%';
```
* Lấy danh sách các đơn đặt được gửi đến các thành phố có chứa chữ ‘a’.

```SELECT *
FROM [dbo].[Orders]
WHERE [ShipCity] LIKE '%a%';
```
* Hãy lọc ra tất cả các đơn hàng với điều kiện:<br>
    ShipCountry  LIKE ‘U_’<br>
    ShipCountry LIKE ‘U%’
```
SELECT *
FROM [dbo].[Orders]
WHERE [ShipCountry] LIKE 'U_';

SELECT *
FROM [dbo].[Orders]
WHERE [ShipCountry] LIKE 'U%';
```
</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="wildcard">Wildcard</a>
<div style="margin-left: 2em;">

* Hãy lọc ra tất cả các khách hàng có tên liên hệ bắt đầu bằng chữ ‘A’
```
SELECT *
FROM [dbo].[Customers]
WHERE [ContactName] LIKE 'A%';
```
* Hãy lọc ra tất cả các khách hàng có tên liên hệ bắt đầu bằng chữ ‘H’, và có chữ thứ 2 là bất kỳ ký tự nào.
```
SELECT *
FROM [dbo].[Customers]
WHERE [ContactName] LIKE 'H_%';
```
* Hãy lọc ra tất cả các đơn hàng được gửi đến thành phố có chữ cái bắt đầu là L, chữ cái thứ hai là u hoặc o.
```
SELECT [OrderID], [ShipCity]
FROM [dbo].[Orders]
WHERE [ShipCity] LIKE 'L[u,o]%';
```
* Hãy lọc ra tất cả các đơn hàng được gửi đến thành phố có chữ cái bắt đầu là L, chữ cái thứ hai khong là u hoặc o.
```
SELECT [OrderID], [ShipCity]
FROM [dbo].[Orders]
WHERE [ShipCity] LIKE 'L[^u,o]%';
```
* Hãy lọc ra tất cả các đơn hang được gửi đến thành phố có chữ cái bắt đầu là L, chữ cái thứ hai là các ký tự từ a đến e.
```
SELECT [OrderID], [ShipCity]
FROM [dbo].[Orders]
WHERE [ShipCity] LIKE 'L[a-e]%';
```
</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="in-not-in">IN-NOT IN</a>
<div style="margin-left: 2em;">


</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="is-null-is-not-null">IS NULL - IS NOT NULL</a>
<div style="margin-left: 2em;">


</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="group-by">GROUP BY</a>
<div style="margin-left: 2em;">


</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="day-month-year">Day-Month-Year</a>
<div style="margin-left: 2em;">


</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="having">HAVING</a>
<div style="margin-left: 2em;">


</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="query-data-from-multiple-tables">Query data from multiple tables</a>
<div style="margin-left: 2em;">


</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="union">Union</a>
<div style="margin-left: 2em;">


</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="join">JOIN - LEFT JOIN - RIGHT JOIN - FULL JOIN</a>
<div style="margin-left: 2em;">


</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="sub-query">Sub query</a>
<div style="margin-left: 2em;">


</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="sql-statement-execution-order">SQL statement execution order</a>
<div style="margin-left: 2em;">


</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="common-table-expression">Common Table Expression</a>
<div style="margin-left: 2em;">


</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="recursive-query">Recursive query</a>
<div style="margin-left: 2em;">


</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="windows-functions">Windows Functions</a>
<div style="margin-left: 2em;">


</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="create-database">Create Database</a>
<div style="margin-left: 2em;">


</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="create-table">Create Table</a>
<div style="margin-left: 2em;">


</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="insert">INSERT</a>
<div style="margin-left: 2em;">


</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="select-into">SELECT INTO</a>
<div style="margin-left: 2em;">


</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="delete">DELETE</a>
<div style="margin-left: 2em;">


</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="update">UPDATE</a>
<div style="margin-left: 2em;">


</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="create-index">Create Index</a>
<div style="margin-left: 2em;">


</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="view">View</a>
<div style="margin-left: 2em;">


</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="stored-procedures">Stored Procedures</a>
<div style="margin-left: 2em;">


</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
    <li><a id="trigger">Trigger</a>
<div style="margin-left: 2em;">


</div>    
    </li>
    <p align="right">[<a href="#readme-top">back to top</a>]</p>
</ol> 

