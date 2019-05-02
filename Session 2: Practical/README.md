# TDD Session 2
In this session, we are going to discuss few things at beginner level like why we need to write UNIT Test? How to configure/write unit test with popular testing framework along with the introduction of TDD.



### Focus Points
- Introduction, Benefits of writing unit test case on your project.
- Famous TDD FWs.
- General setup.
- Basic configurations
- Guidelines.
- Example of **UNIT TESTING**

<hr/>

### Introduction of TDD, Unit Test and benefits of unit Test.

**TDD** : **T**est **D**riven **D**evelopment is an innovative software development approach/process where tests are written, before writing the minimum of code required for the test to be fulfilled. 

**UNIT TESTING** : Unit Testing is a level of software testing where individual units/components of a software are tested through testing framework.

#### Benefits of Unit Testing
- Quality of Code
- Finds Software Bugs Early
- Refactor Code
- Provides Documentation
- More confident when you refactor

<hr/>

### Famous TDD FWs.
- **Phpunit :** Because it is basic and starting from basic is easy. It is mature and very popular and that’s why good documentation, lot of tutorials and lot of threads on Q&A boards and on forums.

<p>&nbsp; &nbsp; Official website: https://phpunit.de/ </p>


- **CodeCeption :** BDD-style PHP testing framework, it was more than basic, but can be used for different sort of testing.

<p>&nbsp; &nbsp; Official website: https://codeception.com/</p>

<hr/>


### Setup of PhpUnit.
- 
```wget https://phar.phpunit.de/phpunit-6.0.phar
chmod +x phpunit-6.0.phar
sudo mv phpunit-6.0.phar /usr/local/bin/phpunit
phpunit --version


```
- composer require --dev phpunit/phpunit ^6.0


<hr/>

### Configuration

```
<?xml version="1.0" encoding="UTF-8"?>
<phpunit colors="true" stopOnFailure="false">
    <testsuites>
        <testsuite name="Application Test Suite">
            <directory suffix="Test.php">./tests</directory>
        </testsuite>
    </testsuites>
    <filter>
        <whitelist processUncoveredFilesFromWhitelist="true">
            <directory suffix=".php">./app</directory>
        </whitelist>
    </filter>
    <php>
        <env name="APP_ENV" value="testing"/>
        <env name="DB_CONNECTION" value="sqlite_testing"/>
        <env name="DB_DATABASE" value=":memory:"/>
        <env name="CACHE_DRIVER" value="array"/>
        <env name="SESSION_DRIVER" value="array"/>
        <env name="QUEUE_DRIVER" value="sync"/>
    </php>
</phpunit>

```

### General assertions in TDD

- assertTrue($param)

- assertFalse($param)

- assertEqual($expected,$actual)

### Guidelines

- No if condition in test case
- Never write code before unit test
- Test should be independent
- No DB transaction
- Do not write negative case only

### My first test

```

<?php
namespace Tests\Unit;
use Tests\ParentTestClass;

class SampleTest extends ParentTestClass
{
	public function testHelloWorld() {
		$this->assertTrue(true);
		$this->assertFalse(false);
		$this->assertEquals(10, 10);
	}
}
```

Have a look into below image how unit test should work on your production code.

![alt text](https://github.com/narayansharma91/node_tdd_sessions/blob/master/Session%202:%20Practical/images/unit_test.png)


<hr/>


### Homework
Create a query builder with following capabilities in the order specified, with a commit per task:

1. **Generate a select query to select all columns from a table.**

*Acceptance Criteria*

If the table name is `products`, then the assertion should look something like:

`$this->assertEquals('select * from products', $sql->select('products'))`

2. **Generate a select query to select specific columns from a table.**

*Acceptance Criteria*

If the table name is `products` and the columns required to be fetched are `id` and `name`, then the assertion should look something like:

`$this->assertEquals('select id, name from products', $sql->select('products', ['id', 'name']))`

3. **Generate a select query to select specific columns from a table, with order by on a column**

*Acceptance Criteria*

If the table name is `products` and the columns required to be fetched are `id` and `name` and sorted as descending by `id`, then the assertion should look something like:

`$this->assertEquals('select id, name from products order by id desc', $sql->select('products', ['id', 'name'], ['id', 'desc']))`

4. **Generate a select query to select specific columns from a table, with order by on a column - with capitalized keywords, and correct spacings.**

*Acceptance Criteria*

If the table name is `products` and the columns required to be fetched are `id` and `name` and sorted as descending by `id`, then the assertion should look something like:

`$this->assertEquals('SELECT id, name FROM products ORDER BY id DESC', $sql->select('products', ['id', 'name'], ['id', 'desc']))`

5. **Generate a select query to select specific columns from a table, with order by on a column - with appropriate usage of back-ticks.**

*Acceptance Criteria*

If the table name is `products` and the columns required to be fetched are `id` and `name` and sorted as descending by `id`, then the assertion should look something like:

`$this->assertEquals('SELECT "id", "name" FROM "products" ORDER BY "id" DESC', $sql->select('products', ['id', 'name'], ['id', 'desc']))`

6. **Generate a query with a table joined with other table**

*Acceptance Criteria*

If main table is `products` and you want to join `products` table with `categories` table, Your query should look like below.

`$this->assertEquals('select * from products join categories on products.category_id=categories.id', $sql->select('products', 'categories', ['id', 'category_id']))`

7. **Generate a query that limits the result from products table to 10.**

*Acceptance Criteria*

If your table is `products` you want to fetch only 10 results from products table, your query should look like below.

`$this->assertEquals('select * from products limit 10', $sql->select('products', 10))`

