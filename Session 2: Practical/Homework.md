Create a query builder with following capabilities in the order specified, with a commit per task:

1. **Generate a select query to select all columns from a table.**

*Acceptance Criteria :*

If the table name is `products`, then the assertion should look something like:

`$this->assertEquals('select * from products', $sql->select('products'))`

2. **Generate a select query to select specific columns from a table.**

*Acceptance Criteria :*

If the table name is `products` and the columns required to be fetched are `id` and `name`, then the assertion should look something like:

`$this->assertEquals('select id, name from products', $sql->select('products', ['id', 'name']))`

3. **Generate a select query to select specific columns from a table, with order by on a column**

*Acceptance Criteria :*

If the table name is `products` and the columns required to be fetched are `id` and `name` and sorted as descending by `id`, then the assertion should look something like:

`$this->assertEquals('select id, name from products order by id desc', $sql->select('products', ['id', 'name'], ['id', 'desc']))`

4. **Generate a select query to select specific columns from a table, with order by on a column - with capitalized keywords, and correct spacings.**

*Acceptance Criteria :*

If the table name is `products` and the columns required to be fetched are `id` and `name` and sorted as descending by `id`, then the assertion should look something like:

`$this->assertEquals('SELECT id, name FROM products ORDER BY id DESC', $sql->select('products', ['id', 'name'], ['id', 'desc']))`

5. **Generate a select query to select specific columns from a table, with order by on a column - with appropriate usage of back-ticks.**

*Acceptance Criteria :*

If the table name is `products` and the columns required to be fetched are `id` and `name` and sorted as descending by `id`, then the assertion should look something like:

`$this->assertEquals('SELECT "id", "name" FROM "products" ORDER BY "id" DESC', $sql->select('products', ['id', 'name'], ['id', 'desc']))`

6. **Generate a query with a table joined with other table**

` *Acceptance Criteria :*

If main table is "products" and you want to join "products" table with "categories" table, Your query should look like below.

```$this->assertEquals('select * from products join categories on products.category_id=categories.id', $sql->select('products', 'categories', ['id', 'category_id']))```
`

7. **Generate a query that limits the result from products table to 10.**

*Acceptance Criteria :*

If your table is `products` you want to fetch only 10 results from products table, your query should look like below.

`$this->assertEquals('select * from products limit 10', $sql->select('products', 10))`
