<a id="readme-top"></a>
<br />
<div align="center">
    <h3 align="center">SQL SERVER BASIC</h3>
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



<!-- DATABASE -->
### DATABASE

_Northwind Database_

 [See more](https://docs.yugabyte.com/preview/sample-data/northwind/)


## SELECT
<div style="margin-left: 2em;">
* Viết câu lệnh SQL lấy ra tên của tất cả các sản phẩm trong bảng Products

```sh
SELECT [ProductName] FROM [dbo].[Products];
```
* Viết câu lệnh SQL lấy ra tên sản phẩm, giá bán trên mỗi đơn vị, số lượng sản phẩm trên đơn vị
```sh
SELECT [ProductName], [UnitPrice], [QuantityPerUnit]
FROM [dbo].[Products];
```
* Viết câu lệnh SQL lấy ra tên công ty của khách hàng và quốc gia của các khách hàng đó
```sh
SELECT [CompanyName], [Country]
FROM [dbo].[Customers];
```
SELECT CompanyName, Country
FROM dbo.Customers;

* Viết câu lệnh SQL lấy ra tất cả dữ liệu từ bảng Products
```sh
SELECT *
FROM [dbo].[Products];
```
* Viết câu lệnh SQL lấy ra tất cả dữ liệu từ bảng khách hàng  - Customers

```sh
SELECT *
FROM [dbo].[Customers];
```
</div>

<p align="right">(<a href="#readme-top">back to top</a>)</p>
