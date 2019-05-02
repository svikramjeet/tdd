Create a query builder with following capabilities in the order specified, with a commit per task:

1. **Generate a select query to select all columns from a table.**

*Acceptance Criteria :*

If the table name is `products`, then the assertion should look something like:

>$this->assertEquals('select * from products', $sql->select('products'))

2. **Generate a select query to select specific columns from a table.**

*Requirement :*

The table name is `products` and the columns required to be fetched are `id` and `name`.

3. **Generate a select query to select specific columns from a table, with order by on a column**

*Requirement :*

The table name is `products` and the columns required to be fetched are `id` and `name` and sorted as descending by `id`.

4. **Generate a select query to select specific columns from a table, with order by on a column - with capitalized keywords, and correct spacings.**

*Requirement :*

The table name is `products` and the columns required to be fetched are `id` and `name` and sorted as descending by `id` with capitalized keywords like SELECT, FROM, ORDER BY

5. **Generate a query with a table joined with other table**

 *Requirement :*

The main table is `products` and you want to join `products` table with `categories` table.

6. **Generate a query that limits the result from products table to 10.**

*Requirement :*

Your table is `products` you want to fetch only 10 results from products table.
