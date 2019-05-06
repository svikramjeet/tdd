Create a query builder with following capabilities in the order specified, with a commit per task:

1. **Generate a select query to select all columns from a table.**

*Acceptance Criteria :*

If the table name is `products`, then the assertion should look something like:

>$this->assertEquals('select * from products', $sql->select('products'))

2. **Generate a select query to select specific columns from a table.**

*Requirement :*

The table name is `products` and the columns required to be fetched are `id` and `name`.

>$this->assertEquals('select id, name from products', $sql->select('products', ['id', 'name']))

3. **Generate a select query to select specific columns from a table, with order by on a column**

*Requirement :*

The table name is `products` and the columns required to be fetched are `id` and `name` and sorted as descending by `id`.

>$this->assertEquals('select id, name from products order by id desc', $sql->select('products', ['id', 'name'], ['id', 'desc']))

4. **Generate a select query to select all columns from table with order by multiple columns**

*Requirement :*

The table name is `products` and the columns required to be ordered are `name` and `category` and sorted as ascending by `name` and `category`.

5. **Generate a select query to select specific columns from a table, with order by on a column - with capitalized keywords, and correct spacings.**

*Requirement :*

The table name is `products` and the columns required to be fetched are `id` and `name` and sorted as descending by `id` with capitalized keywords like SELECT, FROM, ORDER BY

>$this->assertEquals('SELECT id, name FROM products ORDER BY id DESC', $sql->select('products', ['id', 'name'], ['id', 'desc']))

6. **Generate a query that limits the result from products table to 10.**

*Requirement :*

Your table is `products` you want to fetch only 10 results from products table.

7. **Generate a query that limits the result from products table to 6 and offset is 5.**

*Requirement :*

Your table is `products` you want to fetch only 6 results from products table skipping the first 5 results.

8. **Generate a select query to get all the columns of ta ble with a count column that give the total number of products.**

*Requirement :*

Your table is `products` and you want to fetch all the columns of product along with the toal number of products.

9. **Generate a select query to get the product with maximum cost**

*Requirement :*

Your table is `products` and you want to fetch a product from the table that has maximum cost.

10. **Generate a select query to get the cost of products with group by**

*Requirement :*

Your table is `products` and you want to get the unique values of cost which can be done by group by.

11. **Generate a query to get all the unique products in the table**

*Requirement :*

Your table is `products` and you want to get all the unique products of the table using DISTINCT name.


12. **Generate a query with a table joined with other table**

 *Requirement :*

The main table is `products` and you want to join `products` table with `categories` table.

13. **Generate an insert query to insert a row with name, cost, color**

 *Requirement :*

The main table is `products` and you want to insert a row with values into `name`, `age` and `color`.

14. **Generate an insert query to insert multiple rows of values with column : name, cost and color.**

*Requirement :*

The main table is `products` and you want to insert 3 rows with values into `name`, `age` and `color`.

15. **Generate an insert query to insert a row with name and cost and default color as red.**

*Requirement :*

The main table is `products` and you want to insert a rows with values into `name`, `age` and and default value of `color` as red.

16. **Generate an update query to update a row of products with where condition on the name of product**

*Requirement :*

The main table is `products` and you want to update a row with `name` apple to orange.

17. **Generate an update query to update all the products color to black whose color is red**

*Requirement :*

The main table is `products` and you want to update all the rows of table whose color is red to black.

18. **Generate an update query to update the cost of products to their default value of 100.**

*Requirement :*

The main table is `products` and you want to update all the cost of products to the default cost of 100.

19. **Generate an update query to update all the products color to pink**

*Requirement :*

The main table is `products` and you want to update all the cost of products to the default cost of 100.

20. **Generate a delete query to delete the product whose name is abc**

*Requirement :*

The main table is `products` and you want to delete a product with name abc.

21. **Generate a delete query to delete the products whose cost is greater than 500**

*Requirement :*

The main table is `products` and you want to delete all the products whose cost is greater than 500.

22. **Generate a delete query to delete all the products**

*Requirement :*

The main table is `products` and you want to delete all the products.