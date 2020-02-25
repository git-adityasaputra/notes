## CATATAN DATABASE


### Menampilkan seluruh Database

*mysql> show databases;*

| Database   |
| ----- | --- |
| information_schema | 
| dbSchool |
| mysql | 23 |
| performance_schema |
| sys |


#### Membuat database baru
*mysql> CREATE DATABASE db_item;*  
>Query OK, 1 row affected (0.00 sec)

mysql> use db_item;
Database changed
mysql> CREATE TABLE db_item (id INT(11) UNSIGNED KEY, name VARCHAR (30) NOT NULL);

Query OK, 0 rows affected (0.00 sec)


mysql> desc db_item;
| Field | Type             | Null | Key | Default | Extra |
|-------|------------------|------|-----|---------|-------|
| id    | int(11) unsigned | NO   | PRI | NULL    |    auto_increment    |
| name  | varchar(30)      | NO   |     | NULL    |       |
2 rows in set (0.00 sec)


mysql> INSERT INTO db_item (id, name) VALUES (1, "I Want Matcha Latte");
Query OK, 1 row affected (0.00 sec)

mysql> SELECT * FROM db_item;
| id | name                |
|----|---------------------|
|  1 | I Want Matcha Latte |
1 row in set (0.01 sec)

mysql> INSERT INTO db_item (id, name) VALUES (2, "Matcha Latte With Avocado");
Query OK, 1 row affected (0.00 sec)

mysql> SELECT * FROM db_item;
| id | name                      |
|----|---------------------------|
|  1 | I Want Matcha Latte       |
|  2 | Matcha Latte With Avocado |
2 rows in set (0.00 sec)

mysql> SELECT * FROM db_item WHERE id > 1;
| id | name                      |
|----|---------------------------|
|  2 | Matcha Latte With Avocado |
1 row in set (0.00 sec)

mysql> INSERT INTO db_item (id, name) VALUES (3, "Coffe With MIlk");
Query OK, 1 row affected (0.00 sec)


mysql> SELECT * FROM db_item WHERE id > 1 AND id < 3;
| id | name                      |
|----|---------------------------|
|  2 | Matcha Latte With Avocado |
1 row in set (0.00 sec)

mysql> UPDATE db_item SET name = "Matcha Latte" WHERE id = 1;
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> SELECT * FROM db_item;
| id | name                      |
|----|---------------------------|
|  1 | Matcha Latte              |
|  2 | Matcha Latte With Avocado |
|  3 | Coffe With MIlk           |
3 rows in set (0.00 sec)

mysql> SELECT * FROM db_item WHERE name Like '%A%';
| id | name                      |
|----|---------------------------|
|  1 | Matcha Latte              |
|  2 | Matcha Latte With Avocado |
2 rows in set (0.00 sec)

mysql> SELECT * FROM db_item;
| id | name                      |
|----|---------------------------|
|  1 | Matcha Latte              |
|  2 | Matcha Latte With Avocado |
|  3 | Coffe With MIlk           |
3 rows in set (0.00 sec)


mysql> SELECT * FROM db_item LIMIT 2;
| id | name                      |
|----|---------------------------|
|  1 | Matcha Latte              |
|  2 | Matcha Latte With Avocado |
2 rows in set (0.00 sec)


mysql> SELECT * FROM db_item ORDER BY id DESC;
| id | name                      |
|----|---------------------------|
|  3 | Coffe With MIlk           |
|  2 | Matcha Latte With Avocado |
|  1 | Matcha Latte              |
3 rows in set (0.00 sec)

mysql> SELECT * FROM db_item ORDER BY id ASC;
| id | name                      |
|----|---------------------------|
|  1 | Matcha Latte              |
|  2 | Matcha Latte With Avocado |
|  3 | Coffe With MIlk           |
3 rows in set (0.00 sec)

mysql> SELECT * FROM db_item ORDER BY name ASC;
| id | name                      |
|----|---------------------------|
|  3 | Coffe With MIlk           |
|  1 | Matcha Latte              |
|  2 | Matcha Latte With Avocado |
3 rows in set (0.00 sec)


mysql> CREATE TABLE db_stock (id INT (11) UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY, item_id INT (11) UNSIGNED NOT NULL,  quantity INT NOT NULL, unit VARCHAR(20) NOT NULL);
Query OK, 0 rows affected (0.01 sec)

mysql> desc db_stock;
| Field    | Type             | Null | Key | Default | Extra          |
|----------|------------------|------|-----|---------|----------------|
| id       | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| item_id  | int(11) unsigned | NO   |     | NULL    |                |
| quantity | int(11)          | NO   |     | NULL    |                |
| unit     | varchar(20)      | NO   |     | NULL    |                |
4 rows in set (0.00 sec)


mysql> SELECT * FROM db_item;
| id | name                      |
|----|---------------------------|
|  1 | Matcha Latte              |
|  2 | Matcha Latte With Avocado |
|  3 | Coffe With MIlk           |
3 rows in set (0.00 sec)


mysql> SELECT * FROM db_stock;
| id | item_id | quantity | unit |
|----|---------|----------|------|
|  1 |       1 |      500 | g    |
1 row in set (0.00 sec)

mysql> INSERT INTO db_stock (item_id, quantity,unit) VALUES (2, 1000, 'kg');
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO db_stock (item_id, quantity,unit) VALUES (3, 1000, 'g');
Query OK, 1 row affected (0.00 sec)

mysql> SELECT * FROM db_stock;
| id | item_id | quantity | unit |
|----|---------|----------|------|
|  1 |       1 |      500 | g    |
|  2 |       2 |     1000 | kg   |
|  3 |       3 |     1000 | g    |
3 rows in set (0.00 sec)

mysql> SELECT * FROM db_item, db_stock WHERE db_item.id = db_stock.id;
| id | name                      | id | item_id | quantity | unit |
|----|---------------------------|----|---------|----------|------|
|  1 | Matcha Latte              |  1 |       1 |      500 | g    |
|  2 | Matcha Latte With Avocado |  2 |       2 |     1000 | kg   |
|  3 | Coffe With MIlk           |  3 |       3 |     1000 | g    |
3 rows in set (0.00 sec)


mysql> SELECT * FROM db_item, db_stock WHERE db_item.id = db_stock.item_id;
| id | name                      | id | item_id | quantity | unit |
|----|---------------------------|----|---------|----------|------|
|  1 | Matcha Latte              |  1 |       1 |      500 | g    |
|  2 | Matcha Latte With Avocado |  2 |       2 |     1000 | kg   |
|  3 | Coffe With MIlk           |  3 |       3 |     1000 | g    |
3 rows in set (0.00 sec)


mysql> SELECT * FROM db_item INNER JOIN db_stock ON db_item.id = db_stock.id;
| id | name                      | id | item_id | quantity | unit |
|----|---------------------------|----|---------|----------|------|
|  1 | Matcha Latte              |  1 |       1 |      500 | g    |
|  2 | Matcha Latte With Avocado |  2 |       2 |     1000 | kg   |
|  3 | Coffe With MIlk           |  3 |       3 |     1000 | g    |
3 rows in set (0.00 sec)

mysql> SELECT * FROM db_item CROSS JOIN db_stock ON db_item.id = db_stock.id;
| id | name                      | id | item_id | quantity | unit |
|----|---------------------------|----|---------|----------|------|
|  1 | Matcha Latte              |  1 |       1 |      500 | g    |
|  2 | Matcha Latte With Avocado |  2 |       2 |     1000 | kg   |
|  3 | Coffe With MIlk           |  3 |       3 |     1000 | g    |
3 rows in set (0.00 sec)

mysql> SELECT * FROM db_item LEFT JOIN db_stock ON db_item.id = db_stock.id;
| id | name                      | id   | item_id | quantity | unit |
|----|---------------------------|------|---------|----------|------|
|  1 | Matcha Latte              |    1 |       1 |      500 | g    |
|  2 | Matcha Latte With Avocado |    2 |       2 |     1000 | kg   |
|  3 | Coffe With MIlk           |    3 |       3 |     1000 | g    |
3 rows in set (0.00 sec)

mysql> SELECT * FROM db_item RIGHT JOIN db_stock ON db_item.id = db_stock.id;
| id   | name                      | id | item_id | quantity | unit |
|------|---------------------------|----|---------|----------|------|
|    1 | Matcha Latte              |  1 |       1 |      500 | g    |
|    2 | Matcha Latte With Avocado |  2 |       2 |     1000 | kg   |
|    3 | Coffe With MIlk           |  3 |       3 |     1000 | g    |
3 rows in set (0.00 sec)


mysql> SELECT * FROM db_item CROSS JOIN db_stock;
| id | name                      | id | item_id | quantity | unit |
|----|---------------------------|----|---------|----------|------|
|  1 | Matcha Latte              |  1 |       1 |      500 | g    |
|  2 | Matcha Latte With Avocado |  1 |       1 |      500 | g    |
|  3 | Coffe With MIlk           |  1 |       1 |      500 | g    |
|  1 | Matcha Latte              |  2 |       2 |     1000 | kg   |
|  2 | Matcha Latte With Avocado |  2 |       2 |     1000 | kg   |
|  3 | Coffe With MIlk           |  2 |       2 |     1000 | kg   |
|  1 | Matcha Latte              |  3 |       3 |     1000 | g    |
|  2 | Matcha Latte With Avocado |  3 |       3 |     1000 | g    |
|  3 | Coffe With MIlk           |  3 |       3 |     1000 | g    |
9 rows in set (0.00 sec)

mysql> SELECT * FROM db_item JOIN db_stock ON db_item.id = db_stock.item_id;
| id | name                      | id | item_id | quantity | unit |
|----|---------------------------|----|---------|----------|------|
|  1 | Matcha Latte              |  1 |       1 |      500 | g    |
|  2 | Matcha Latte With Avocado |  2 |       2 |     1000 | kg   |
|  3 | Coffe With MIlk           |  3 |       3 |     1000 | g    |
3 rows in set (0.00 sec)

mysql> SELECT * FROM db_item i JOIN db_stock s ON i.id = s.item_id;
| id | name                      | id | item_id | quantity | unit |
|----|---------------------------|----|---------|----------|------|
|  1 | Matcha Latte              |  1 |       1 |      500 | g    |
|  2 | Matcha Latte With Avocado |  2 |       2 |     1000 | kg   |
|  3 | Coffe With MIlk           |  3 |       3 |     1000 | g    |
3 rows in set (0.00 sec)


mysql> SELECT i.name, SUM(s.quantity) FROM db_item i JOIN db_stock s ON i.id = s.item_id GROUP BY i.id;

| name                      | SUM(s.quantity) |
|---------------------------|-----------------|
| Matcha Latte              |             500 |
| Matcha Latte With Avocado |            1000 |
| Coffe With MIlk           |            1000 |
3 rows in set (0.00 sec)

mysql> SELECT SUM(quantity) FROM db_stock;

| SUM(quantity) |
|---------------|
|          2500 |
1 row in set (0.00 sec)

mysql> SELECT AVG(quantity) FROM db_stock;

| AVG(quantity) |
|---------------|
|      833.3333 |
1 row in set (0.00 sec)


mysql> SELECT item_id, SUM(quantity),unit FROM db_stock GROUP BY item_id, unit;

| item_id | SUM(quantity) | unit |
|---------|---------------|------|
|       1 |           500 | g    |
|       2 |          1000 | kg   |
|       3 |          1000 | g    |
3 rows in set (0.00 sec)

mysql> SELECT item_id, AVG(quantity),unit FROM db_stock GROUP BY item_id, unit;

| item_id | AVG(quantity) | unit |
|---------|---------------|------|
|       1 |      500.0000 | g    |
|       2 |     1000.0000 | kg   |
|       3 |     1000.0000 | g    |
3 rows in set (0.00 sec)