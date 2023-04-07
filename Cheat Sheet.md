The <b>SELECT</b> clause

This statement will do a query of all tables and columns in a specified table. Adding an asterisk (*) in the SELECT statement to return all the records within the table.

```sql
SELECT * FROM
```


Selects all the records in the table. Adding DISTINCT selects only the distinct values.:

```sql
SELECT DISTINCT * FROM KCC.dbo.Customers
```



To show only a specific number of data, add TOP(n) where n is the number of data you want to return:
```sql 
SELECT TOP (3) * FROM KCC.dbo.Customers
```

Filtering with <b>WHERE</b>

To only look for specific data in a specific column:

```sql
SELECT * FROM KCC.dbo.Customers WHERE State ='WA'
```

To look for data that is not equal to that value:

```sql
SELECT * FROM KCC.dbo.Customers WHERE State <>'WA'
```

`<>` is the not equal sign. Alternatively, `!=` can be used.

Selects two values with `OR`:

```sql
SELECT * FROM KCC.dbo.Customers WHERE State = 'WA' OR State = 'NY'
```
<b>IN</b> & <b>NOT IN</b>

This makes the code look cleaner and more efficient. The `IN` operator shows the data in the specified values. It is a shorthand for multiple `OR` conditions:

```sql
SELECT * FROM KCC.dbo.Customers WHERE State IN('WA', 'NY', 'UT')
```

The opposite of the `IN` operator where it doesn’t show the values specified in the query is `NOT IN`:

```sql
SELECT * FROM KCC.dbo.Customers WHERE State NOT IN('WA', 'NY', 'UT')
```

The use of `ADD` shows the two values for two conditions such as `CustomerName` and `Country`:

```sql
SELECT * FROM KCC.dbo.Customers WHERE CustomerName = 'Tres Delicious' AND Country = 'United States'
```

Adding `OR` to the statement shows a record if the condition is true:

```sql
SELECT * FROM KCC.dbo.Customers WHERE CustomerName = 'Tres Delicious' AND Country = 'United States' OR Country = 'France'
```

Adding parentheses makes it so that it is not confusing how the query is going to run. To make it clear, we can use parentheses:

```sql
SELECT * FROM KCC.dbo.Customers WHERE CustomerName = 'Tres Delicious' AND (Country = 'United States' OR Country = 'France')
```


<b>LIKE</b>

Using `LIKE` searches for a specified pattern in a column:

```sql
SELECT * FROM KCC.dbo.Customers WHERE CustomerName LIKE 'A%' AND (Country = 'United States' OR Country = 'France')
```

`NOT LIKE` does the opposite:

```sql
SELECT * FROM KCC.dbo.Customers WHERE CustomerName NOT LIKE 'A%' AND (Country = 'United States' OR Country = 'France')
```

Filtering with <b>NUMBER</b>

The use of the `>` sign displays values in the column with values exceeding 1000. We can also use other operators such as `<=` or `>=`:

```sql
SELECT TOP (1000) [OrderID], [OrderDate], [CustomerID], [OrderTotal] FROM [KCC].[dbo].[Orders] WHERE OrderTotal > 1000
```

The use of BETWEEN in the statement displays the specified range of values:


```sql
SELECT TOP (1000) [OrderID], [OrderDate], [CustomerID], [OrderTotal] FROM [KCC].[dbo].[Orders] WHERE OrderTotal BETWEEN 1000 AND 2000

```
