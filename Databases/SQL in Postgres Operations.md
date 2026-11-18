# SQL in Postgres Operations

## Views

### Overview

Views allow you to execute a complex query using a name for this query.
Views are stored within a particular schema can be reused among many clients.
Since views are reused, your applications might not need to store complex SQL statements.

See "Just Use Postgres" book for examples.

### Types of views

There are plain views and materialized views:
plain views are always executed, whereas materialized ones executed only once.
Materialized views are materialized during creation and can be refreshed when needed.

## Common table expressions

### Overview

CTEs are defined on a per-query basis, whereas views are per-schema global.
Recursive queries can be applied to CTEs.

See "Just Use Postgres" book for examples.

## pg_typeof

`pg_typeof` allows one to see the column type:

      SELECT pg_typeof(creation_time) FROM orders;

## NULL caveats

Understand: `COUNT(*)` counts all rows, whereas `COUNT(column_name)` counts only non-null rows.
When you do `ORDER BY` remember about `NULLS LAST`, `NULLS FIRST` options, which are useful.

`!=` operator behaviour is tricky for `NULL`.
Use `IS NULL` or `IS NOT NULL` for `NULL` comparison:
https://lab.karpov.courses/learning/152/module/1762/lesson/18485/53202/251025/

## COALESCE

`COALESCE` returns a first non-null value:

      SELECT COALESCE(NULL, 'I am not NULL' , 'The last non-null.')
      -- The first string is returned.

## CASE

Here is an example of a `CASE` statement:

      SELECT name,
            CASE
            WHEN name='pork' OR name='mutton' THEN 'meat'
            WHEN name='catfish' OR name='salmon' THEN 'fish'
            ELSE 'something else'
            END AS сategory
      FROM table

Understand: if `ELSE` clause is not specified and no `WHEN` case is matched,
`NULL` is returned.

## DATE comparison

When you compare dates, they are interpreted as 12 a.m.
So, these two queries are equivalent:

      SELECT column_1
      FROM table
      WHERE column_2 <= '2022-12-31'


      SELECT column_1
      FROM table
      WHERE column_2 <= '2022-12-31 00:00:00'

Be careful when you write the following query:

      SELECT column_1, column_2, column_3
      FROM table
      WHERE column_3 BETWEEN '2022-11-20' AND '2022-12-31'

The date `'2022-12-31'` is interpreted as `'2022-12-31 00:00:00'`, which is 12 a.m..
Because of this, the last day of the interval is almost excluded from your sample.
So, to include the last day, specify the date as follows:

      '2022-12-31 23:59:59'

https://lab.karpov.courses/learning/152/module/1762/lesson/18485/53202/288782/
https://lab.karpov.courses/learning/152/module/1762/lesson/18485/53202/251024/

## DATE_PART function

The following example contains a various usage of `DATE_PART` function:

      SELECT
        user_id,
        order_id,
        action,
        time
      FROM user_actions WHERE
        action = 'cancel_order'
        and date_part('dow', time) = 3
        and date_part('month', time) = 8
        and date_part('hour', time) between 12 and 15
        and date_part('year', time) = 2022
      ORDER BY order_id desc

## LIKE and ILIKE

The following queries will return `TRUE`.

      SELECT 'SQL' ILIKE '%q%'
      SELECT 'SQL' ILIKE '_q_';
      SELECT 'SQL' NOT LIKE '% %'; -- SQL is just one word. No space.

## Aggregate Functions

The most popular aggregate functions are:

* COUNT;
* SUM;
* AVG;
* MAX;
* MIN.

https://www.postgresql.org/docs/18/functions-aggregate.html

## SELECT DISTINCT

To select all distinct values within a given column:

      SELECT DISTINCT user_id FROM user_actions ORDER BY user_id;

## SELECT DISTINCT pairs

To select all distinct pairs of values:

      SELECT DISTINCT courier_id, order_id
      FROM courier_actions ORDER BY courier_id, order_id;

## Aggregate Functions and DISTINCT

`DISTINCT` can be used within `SUM`, `AVG`, `COUNT`:

      SELECT
          COUNT(user_id) AS users,
          COUNT(DISTINCT user_id) AS unique_users
      FROM user_actions;

## MIN, MAX with dates

`MIN` and `MAX` can be applied to dates to find the first and the last date:

      SELECT
      MIN(time) AS first_delivery, MAX(time) AS last_delivery
      FROM courier_actions
      WHERE action = 'deliver_order';

## AGE function

`AGE` computes the time which has elapsed between the two dates:

      SELECT age(max(birth_date))::VARCHAR as min_age
      FROM   couriers
      WHERE  sex = 'male';

## Aggregate functions and CASE

`CASE` can be used within an aggregate function:

      SELECT sum(case when name = 'chips' then price * 3
                      when name = 'fish' then price * 2
                      when name = 'energy drink' then price
                      else 0 end) as order_price
      FROM   products

## / operator on INT

Understand: `/` operator will return an `INT` if it's invoked on an `INT`.
If you want a true division to be performed, first cast `INT` to a `DECIMAL`:

      SELECT
          COUNT(DISTINCT user_id) AS unique_users,
          COUNT(DISTINCT order_id) AS unique_orders,
          ROUND(COUNT(DISTINCT order_id)::DECIMAL / COUNT(DISTINCT user_id)::DECIMAL, 2)
          AS orders_per_user
      FROM user_actions;

https://lab.karpov.courses/learning/152/module/1762/lesson/17926/53322/251386/
https://stackoverflow.com/questions/34504497/division-not-giving-my-answer-in-postgresql

## FILTER operator

`FILTER` allows you to apply an aggregate function only to specific rows.

      SELECT
          COUNT(DISTINCT order_id) AS orders,
          COUNT(DISTINCT order_id) FILTER(WHERE ARRAY_LENGTH(product_ids, 1) >= 5) AS large_orders,
          ROUND((COUNT(DISTINCT order_id) FILTER(WHERE ARRAY_LENGTH(product_ids, 1) >= 5)::DECIMAL
          / COUNT(DISTINCT order_id)::DECIMAL), 2) AS large_orders_share
      FROM orders;

https://lab.karpov.courses/learning/152/module/1762/lesson/17926/53322/289238/
