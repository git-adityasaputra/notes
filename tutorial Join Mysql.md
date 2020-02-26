## 

mysql> show databases;
| Database           |
----------------------
| information_schema |
| dbSchool           |
| db_item            |
| db_mahasiswa       |
| mahasiswa          |
| mysql              |
| performance_schema |
| sys                |
8 rows in set (0.00 sec)


mysql> use db_item;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> SHOW TABLES;
| Tables_in_db_item |
---------------------
| db_item           |
| db_stock          |
2 rows in set (0.00 sec)

mysql> CREATE TABLE unit (id INT UNSIGNED PRIMARY KEY NOT NULL,)
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 1
mysql> 
mysql> CREATE TABLE unit (id INT UNSIGNED PRIMARY KEY NOT NULL,
    -> name VARCHAR(20) NOT NULL);
Query OK, 0 rows affected (0.00 sec)

mysql> INSERT INTO unit (1, 'g');
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '1, 'g')' at line 1
mysql> INSERT INTO unit VALUES (1, 'g');
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO unit VALUES (2, 'kg');
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO unit VALUES (3, 'liter');
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO unit VALUES (4, 'pack');
Query OK, 1 row affected (0.00 sec)

mysql> SELECT * FROM unit;
| id | name  |
--------------
|  1 | g     |
|  2 | kg    |
|  3 | liter |
|  4 | pack  |
4 rows in set (0.00 sec)

mysql> SELECT * FROM tb_stock;
ERROR 1146 (42S02): Table 'db_item.tb_stock' doesn't exist
mysql> 
mysql> SELECT * FROM db_stock;
| id | item_id | quantity | unit |
----------------------------------
|  1 |       1 |      500 | g    |
|  2 |       2 |     1000 | kg   |
|  3 |       3 |     1000 | g    |
3 rows in set (0.00 sec)

mysql> INSERT INTO db_stock (id, item_id, quantity, unit) VALUES (4, 4, "400",""pack);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'pack)' at line 1
mysql> mysql> INSERT INTO db_stock (id, item_id, quantity, unit) VALUES (4, 4, "400","pack");
ERROR 1452 (23000): Cannot add or update a child row: a foreign key constraint fails (`db_item`.`db_stock`, CONSTRAINT `db_stock_ibfk_1` FOREIGN KEY (`item_id`) REFERENCES `db_item` (`id`))
mysql> desc db_stock;
| Field    | Type             | Null | Key | Default | Extra          |
-----------------------------------------------------------------------
| id       | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| item_id  | int(11) unsigned | NO   | MUL | NULL    |                |
| quantity | int(11)          | NO   |     | NULL    |                |
| unit     | varchar(20)      | NO   |     | NULL    |                |
4 rows in set (0.00 sec)

mysql> INSERT INTO db_stock (id, item_id, quantity, unit) VALUES (4, 4, 300 ,"pack");
ERROR 1452 (23000): Cannot add or update a child row: a foreign key constraint fails (`db_item`.`db_stock`, CONSTRAINT `db_stock_ibfk_1` FOREIGN KEY (`item_id`) REFERENCES `db_item` (`id`))
mysql> SELECT * FROM db_item;
| id | name                      |
----------------------------------
|  1 | Matcha Latte              |
|  2 | Matcha Latte With Avocado |
|  3 | Coffe With MIlk           |
3 rows in set (0.00 sec)

mysql> INSERT INTO db_stock (id, name) VALUES (4, "Mie Goreng");
ERROR 1054 (42S22): Unknown column 'name' in 'field list'
mysql> INSERT INTO db_item (id, name) VALUES (4, "Mie Goreng");
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO db_item (id, name) VALUES (5, "Mie Goreng");
Query OK, 1 row affected (0.00 sec)

mysql> SELECT * FROM db_item;
| id | name                      |
----------------------------------
|  1 | Matcha Latte              |
|  2 | Matcha Latte With Avocado |
|  3 | Coffe With MIlk           |
|  4 | Mie Goreng                |
|  5 | Mie Goreng                |
5 rows in set (0.00 sec)

mysql> INSERT INTO db_stock (id, item_id, quantity, unit) VALUES (4, 4, 300 ,"pack");
Query OK, 1 row affected (0.00 sec)

mysql> SELECT * FROM db_stock;
| id | item_id | quantity | unit |
----------------------------------
|  1 |       1 |      500 | g    |
|  2 |       2 |     1000 | kg   |
|  3 |       3 |     1000 | g    |
|  4 |       4 |      300 | pack |
4 rows in set (0.00 sec)

mysql> desc db_stock;
| Field    | Type             | Null | Key | Default | Extra          |
-----------------------------------------------------------------------
| id       | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| item_id  | int(11) unsigned | NO   | MUL | NULL    |                |
| quantity | int(11)          | NO   |     | NULL    |                |
| unit     | varchar(20)      | NO   |     | NULL    |                |
4 rows in set (0.00 sec)

mysql> UPDATE db_stock SET unit= NULL;
ERROR 1048 (23000): Column 'unit' cannot be null
mysql> ALTER TABLE db_stock MODIFY COLUMN unit VARCHAR(10);
Query OK, 4 rows affected (0.01 sec)
Records: 4  Duplicates: 0  Warnings: 0

mysql> UPDATE db_stock SET unit= NULL;
Query OK, 4 rows affected (0.00 sec)
Rows matched: 4  Changed: 4  Warnings: 0

mysql> ALTER TABLE db_stock MODIFY COLUMN unit INT UNSIGNED;
Query OK, 4 rows affected (0.01 sec)
Records: 4  Duplicates: 0  Warnings: 0

mysql> desc db_stock;
| Field    | Type             | Null | Key | Default | Extra          |
-----------------------------------------------------------------------
| id       | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| item_id  | int(11) unsigned | NO   | MUL | NULL    |                |
| quantity | int(11)          | NO   |     | NULL    |                |
| unit     | int(10) unsigned | YES  |     | NULL    |                |
4 rows in set (0.00 sec)

mysql> ALTER TABLE db_stock CHANGE COLUMN unit  unit_id INT UNSIGNED;
Query OK, 0 rows affected (0.00 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc db_stock;
| Field    | Type             | Null | Key | Default | Extra          |
-----------------------------------------------------------------------
| id       | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| item_id  | int(11) unsigned | NO   | MUL | NULL    |                |
| quantity | int(11)          | NO   |     | NULL    |                |
| unit_id  | int(10) unsigned | YES  |     | NULL    |                |
4 rows in set (0.00 sec)

mysql> RENAME TABLE db_item TO item;
Query OK, 0 rows affected (0.00 sec)

mysql> RENAME TABLE db_stock TO stock;
Query OK, 0 rows affected (0.00 sec)

mysql> show tables;
---------------------
| Tables_in_db_item |
---------------------
| item              |
| stock             |
| unit              |
---------------------
3 rows in set (0.00 sec)

mysql> select * from stock;
| id | item_id | quantity | unit_id |
-------------------------------------
|  1 |       1 |      500 |    NULL |
|  2 |       2 |     1000 |    NULL |
|  3 |       3 |     1000 |    NULL |
|  4 |       4 |      300 |    NULL |
4 rows in set (0.00 sec)

mysql> UPDATE stock SET 'unit_id' = 1 WHERE id < 4;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''unit_id' = 1 WHERE id < 4' at line 1
mysql> UPDATE stock SET unit_id = 1 WHERE id < 4;
Query OK, 3 rows affected (0.00 sec)
Rows matched: 3  Changed: 3  Warnings: 0

mysql> select * from stock;
| id | item_id | quantity | unit_id |
-------------------------------------
|  1 |       1 |      500 |       1 |
|  2 |       2 |     1000 |       1 |
|  3 |       3 |     1000 |       1 |
|  4 |       4 |      300 |    NULL |
4 rows in set (0.00 sec)

mysql> UPDATE stock SET unit_id = 1 WHERE id >= 4;
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> select * from stock;
| id | item_id | quantity | unit_id |
-------------------------------------
|  1 |       1 |      500 |       1 |
|  2 |       2 |     1000 |       1 |
|  3 |       3 |     1000 |       1 |
|  4 |       4 |      300 |       1 |
4 rows in set (0.00 sec)

mysql> ALTER TABLE stock MODIFY COLUMN unit_id INT UNSIGNED NOT NULL;
Query OK, 0 rows affected (0.03 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> select * from stock;
| id | item_id | quantity | unit_id |
-------------------------------------
|  1 |       1 |      500 |       1 |
|  2 |       2 |     1000 |       1 |
|  3 |       3 |     1000 |       1 |
|  4 |       4 |      300 |       1 |
4 rows in set (0.00 sec)

mysql> desc stock;
| Field    | Type             | Null | Key | Default | Extra          |
-----------------------------------------------------------------------
| id       | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| item_id  | int(11) unsigned | NO   | MUL | NULL    |                |
| quantity | int(11)          | NO   |     | NULL    |                |
| unit_id  | int(10) unsigned | NO   |     | NULL    |                |
4 rows in set (0.00 sec)

mysql> SELECT * FROM item;
| id | name                      |
----------------------------------
|  1 | Matcha Latte              |
|  2 | Matcha Latte With Avocado |
|  3 | Coffe With MIlk           |
|  4 | Mie Goreng                |
|  5 | Mie Goreng                |
5 rows in set (0.00 sec)

mysql> ALTER TABLE ADD FOREIGN KEY (unit_id) REFERENCES unit(id);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'ADD FOREIGN KEY (unit_id) REFERENCES unit(id)' at line 1
mysql> ALTER TABLE stock ADD FOREIGN KEY (unit_id) REFERENCES unit(id);
Query OK, 4 rows affected (0.01 sec)
Records: 4  Duplicates: 0  Warnings: 0

mysql> desc stock;
| Field    | Type             | Null | Key | Default | Extra          |
-----------------------------------------------------------------------
| id       | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| item_id  | int(11) unsigned | NO   | MUL | NULL    |                |
| quantity | int(11)          | NO   |     | NULL    |                |
| unit_id  | int(10) unsigned | NO   | MUL | NULL    |                |
4 rows in set (0.00 sec)

mysql> SELECT * FROM stock;
| id | item_id | quantity | unit_id |
-------------------------------------
|  1 |       1 |      500 |       1 |
|  2 |       2 |     1000 |       1 |
|  3 |       3 |     1000 |       1 |
|  4 |       4 |      300 |       1 |
4 rows in set (0.00 sec)

mysql> SELECT * FROM unit;
| id | name  |
--------------
|  1 | g     |
|  2 | kg    |
|  3 | liter |
|  4 | pack  |
4 rows in set (0.00 sec)

mysql> SELECT * FROM stock s, unit u WHERE  s.unit_id = u.id;
| id | item_id | quantity | unit_id | id | name |
-------------------------------------------------
|  1 |       1 |      500 |       1 |  1 | g    |
|  2 |       2 |     1000 |       1 |  1 | g    |
|  3 |       3 |     1000 |       1 |  1 | g    |
|  4 |       4 |      300 |       1 |  1 | g    |
4 rows in set (0.00 sec)

mysql> SELECT s.id, s.item_id, s.quantity, u.name FROM stock s, unit u WHERE  s.unit_id = u.id;
| id | item_id | quantity | name |
----------------------------------
|  1 |       1 |      500 | g    |
|  2 |       2 |     1000 | g    |
|  3 |       3 |     1000 | g    |
|  4 |       4 |      300 | g    |
4 rows in set (0.00 sec)

mysql> SELECT s.id, s.item_id, s.quantity, u.name FROM stock s, unit u WHERE  s.unit_id = u.id
    -> .;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 2
mysql> SELECT s.id, s.item_id, s.quantity, u.name
    -> FROM stock s
    -> INNER JOIN unit u ON s.unit_id =u.id;
    
| id | item_id | quantity | name |
----------------------------------
|  1 |       1 |      500 | g    |
|  2 |       2 |     1000 | g    |
|  3 |       3 |     1000 | g    |
|  4 |       4 |      300 | g    |
4 rows in set (0.00 sec)

mysql> select * from item;
| id | name                      |
----------------------------------
|  1 | Matcha Latte              |
|  2 | Matcha Latte With Avocado |
|  3 | Coffe With MIlk           |
|  4 | Mie Goreng                |
|  5 | Mie Goreng                |
5 rows in set (0.00 sec)

mysql> select * from stock;
| id | item_id | quantity | unit_id |
-------------------------------------
|  1 |       1 |      500 |       1 |
|  2 |       2 |     1000 |       1 |
|  3 |       3 |     1000 |       1 |
|  4 |       4 |      300 |       1 |
-------------------------------------
4 rows in set (0.00 sec)

mysql> desc stock;
| Field    | Type             | Null | Key | Default | Extra          |
-----------------------------------------------------------------------
| id       | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| item_id  | int(11) unsigned | NO   | MUL | NULL    |                |
| quantity | int(11)          | NO   |     | NULL    |                |
| unit_id  | int(10) unsigned | NO   | MUL | NULL    |                |
4 rows in set (0.00 sec)

mysql> SELECT * FROM stock CROSS JOIN unit;
| id | item_id | quantity | unit_id | id | name  |
--------------------------------------------------
|  1 |       1 |      500 |       1 |  1 | g     |
|  2 |       2 |     1000 |       1 |  1 | g     |
|  3 |       3 |     1000 |       1 |  1 | g     |
|  4 |       4 |      300 |       1 |  1 | g     |
|  1 |       1 |      500 |       1 |  2 | kg    |
|  2 |       2 |     1000 |       1 |  2 | kg    |
|  3 |       3 |     1000 |       1 |  2 | kg    |
|  4 |       4 |      300 |       1 |  2 | kg    |
|  1 |       1 |      500 |       1 |  3 | liter |
|  2 |       2 |     1000 |       1 |  3 | liter |
|  3 |       3 |     1000 |       1 |  3 | liter |
|  4 |       4 |      300 |       1 |  3 | liter |
|  1 |       1 |      500 |       1 |  4 | pack  |
|  2 |       2 |     1000 |       1 |  4 | pack  |
|  3 |       3 |     1000 |       1 |  4 | pack  |
|  4 |       4 |      300 |       1 |  4 | pack  |
--------------------------------------------------
16 rows in set (0.00 sec)

mysql> SELECT * FROM unit CROSS JOIN stock;
| id | name  | id | item_id | quantity | unit_id |
--------------------------------------------------
|  1 | g     |  1 |       1 |      500 |       1 |
|  2 | kg    |  1 |       1 |      500 |       1 |
|  3 | liter |  1 |       1 |      500 |       1 |
|  4 | pack  |  1 |       1 |      500 |       1 |
|  1 | g     |  2 |       2 |     1000 |       1 |
|  2 | kg    |  2 |       2 |     1000 |       1 |
|  3 | liter |  2 |       2 |     1000 |       1 |
|  4 | pack  |  2 |       2 |     1000 |       1 |
|  1 | g     |  3 |       3 |     1000 |       1 |
|  2 | kg    |  3 |       3 |     1000 |       1 |
|  3 | liter |  3 |       3 |     1000 |       1 |
|  4 | pack  |  3 |       3 |     1000 |       1 |
|  1 | g     |  4 |       4 |      300 |       1 |
|  2 | kg    |  4 |       4 |      300 |       1 |
|  3 | liter |  4 |       4 |      300 |       1 |
|  4 | pack  |  4 |       4 |      300 |       1 |
16 rows in set (0.00 sec)

mysql> SELECT * FROM item CROSS JOIN stock;
| id | name                      | id | item_id | quantity | unit_id |
----------------------------------------------------------------------
|  1 | Matcha Latte              |  1 |       1 |      500 |       1 |
|  1 | Matcha Latte              |  2 |       2 |     1000 |       1 |
|  1 | Matcha Latte              |  3 |       3 |     1000 |       1 |
|  1 | Matcha Latte              |  4 |       4 |      300 |       1 |
|  2 | Matcha Latte With Avocado |  1 |       1 |      500 |       1 |
|  2 | Matcha Latte With Avocado |  2 |       2 |     1000 |       1 |
|  2 | Matcha Latte With Avocado |  3 |       3 |     1000 |       1 |
|  2 | Matcha Latte With Avocado |  4 |       4 |      300 |       1 |
|  3 | Coffe With MIlk           |  1 |       1 |      500 |       1 |
|  3 | Coffe With MIlk           |  2 |       2 |     1000 |       1 |
|  3 | Coffe With MIlk           |  3 |       3 |     1000 |       1 |
|  3 | Coffe With MIlk           |  4 |       4 |      300 |       1 |
|  4 | Mie Goreng                |  1 |       1 |      500 |       1 |
|  4 | Mie Goreng                |  2 |       2 |     1000 |       1 |
|  4 | Mie Goreng                |  3 |       3 |     1000 |       1 |
|  4 | Mie Goreng                |  4 |       4 |      300 |       1 |
|  5 | Mie Goreng                |  1 |       1 |      500 |       1 |
|  5 | Mie Goreng                |  2 |       2 |     1000 |       1 |
|  5 | Mie Goreng                |  3 |       3 |     1000 |       1 |
|  5 | Mie Goreng                |  4 |       4 |      300 |       1 |
20 rows in set (0.00 sec)

mysql> SELECT s.id, s.item_id, s.quantity, u.name
    -> FROM stock s LEFT JOIN unit u ON s.unit_id = u.id;
| id | item_id | quantity | name |
----------------------------------
|  1 |       1 |      500 | g    |
|  2 |       2 |     1000 | g    |
|  3 |       3 |     1000 | g    |
|  4 |       4 |      300 | g    |
4 rows in set (0.01 sec)

mysql> SELECT s.id, s.item_id, s.quantity, u.name FROM unit u LEFT JOIN stock s ON s.unit_id =u.id;
| id   | item_id | quantity | name  |
-------------------------------------
|    1 |       1 |      500 | g     |
|    2 |       2 |     1000 | g     |
|    3 |       3 |     1000 | g     |
|    4 |       4 |      300 | g     |
| NULL |    NULL |     NULL | kg    |
| NULL |    NULL |     NULL | liter |
| NULL |    NULL |     NULL | pack  |
7 rows in set (0.00 sec)

mysql> SELECT id,name FROM item UNION SELECT id, name FROM unit;
| id | name                      |
----------------------------------
|  1 | Matcha Latte              |
|  2 | Matcha Latte With Avocado |
|  3 | Coffe With MIlk           |
|  4 | Mie Goreng                |
|  5 | Mie Goreng                |
|  1 | g                         |
|  2 | kg                        |
|  3 | liter                     |
|  4 | pack                      |
9 rows in set (0.00 sec)


mysql> INSERT INTO item VALUES(10,'X');
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO unit VALUES(10,'X');
Query OK, 1 row affected (0.00 sec)

mysql> SELECT * FROM unit;
| id | name  |
--------------
|  1 | g     |
|  2 | kg    |
|  3 | liter |
|  4 | pack  |
| 10 | X     |
5 rows in set (0.00 sec)

mysql> SELECT * FROM item;
| id | name                      |
----------------------------------
|  1 | Matcha Latte              |
|  2 | Matcha Latte With Avocado |
|  3 | Coffe With MIlk           |
|  4 | Mie Goreng                |
|  5 | Mie Goreng                |
| 10 | X                         |
6 rows in set (0.00 sec)

mysql> SELECT id,name FROM item UNION SELECT id, name FROM unit;
| id | name                      |
----------------------------------
|  1 | Matcha Latte              |
|  2 | Matcha Latte With Avocado |
|  3 | Coffe With MIlk           |
|  4 | Mie Goreng                |
|  5 | Mie Goreng                |
| 10 | X                         |
|  1 | g                         |
|  2 | kg                        |
|  3 | liter                     |
|  4 | pack                      |
10 rows in set (0.00 sec)

mysql> SELECT id,name FROM item UNION ALL SELECT id, name FROM unit;
| id | name                      |
----------------------------------
|  1 | Matcha Latte              |
|  2 | Matcha Latte With Avocado |
|  3 | Coffe With MIlk           |
|  4 | Mie Goreng                |
|  5 | Mie Goreng                |
| 10 | X                         |
|  1 | g                         |
|  2 | kg                        |
|  3 | liter                     |
|  4 | pack                      |
| 10 | X                         |
11 rows in set (0.01 sec)

mysql> show tables;
| Tables_in_db_item |
---------------------
| item              |
| stock             |
| unit              |
3 rows in set (0.00 sec)

mysql> DELETE FROM unit WHERE id=10;
Query OK, 1 row affected (0.00 sec)

mysql> DELETE FROM item WHERE id=10;
Query OK, 1 row affected (0.00 sec)

mysql> SELECT i.id, i.name, s.quantity, u.name FROM item i
    -> JOIN stock s ON s.item_id = i.id
    -> JOIN unit u ON u.id  = s.unit_id;
| id | name                      | quantity | name |
----------------------------------------------------
|  1 | Matcha Latte              |      500 | g    |
|  2 | Matcha Latte With Avocado |     1000 | g    |
|  3 | Coffe With MIlk           |     1000 | g    |
|  4 | Mie Goreng                |      300 | g    |
4 rows in set (0.01 sec)

mysql> SELECT i.id, i.name, s.quantity, u.name AS unit FROM item i JOIN stock s ON s.item_id = i.id JOIN unit u ON u.id  = s.unit_id;
| id | name                      | quantity | unit |
----------------------------------------------------
|  1 | Matcha Latte              |      500 | g    |
|  2 | Matcha Latte With Avocado |     1000 | g    |
|  3 | Coffe With MIlk           |     1000 | g    |
|  4 | Mie Goreng                |      300 | g    |
4 rows in set (0.00 sec)

mysql> SELECT i.id, i.name, s.quantity AS qty, u.name AS unit FROM item i JOIN stock s ON s.item_id = i.id JOIN unit u ON u.id  = s.unit_id;
| id | name                      | qty  | unit |
------------------------------------------------
|  1 | Matcha Latte              |  500 | g    |
|  2 | Matcha Latte With Avocado | 1000 | g    |
|  3 | Coffe With MIlk           | 1000 | g    |
|  4 | Mie Goreng                |  300 | g    |
4 rows in set (0.00 sec)

mysql> select count(quantity), avg(quantity), min(quantity), max(quantity) from stock;

| count(quantity) | avg(quantity) | min(quantity) | max(quantity) |
-------------------------------------------------------------------
|               4 |      700.0000 |           300 |          1000 |
1 row in set (0.00 sec)



mysql> select count(quantity), avg(quantity), min(quantity), max(quantity), sum(quantity) from stock;
| count(quantity) | avg(quantity) | min(quantity) | max(quantity) | sum(quantity) |
-----------------------------------------------------------------------------------
|               4 |      700.0000 |           300 |          1000 |          2800 |
1 row in set (0.00 sec)


mysql> SELECT i.id, i.name, s.quantity AS qty, u.name AS unit FROM item i JOIN stock s ON s.item_id = i.id JOIN unit u ON u.id  = s.unit_id GROUP BY i.id,s.id,u.id;
| id | name                      | qty  | unit |
------------------------------------------------
|  1 | Matcha Latte              |  500 | g    |
|  2 | Matcha Latte With Avocado | 1000 | g    |
|  3 | Coffe With MIlk           | 1000 | g    |
|  4 | Mie Goreng                |  300 | g    |
4 rows in set (0.00 sec)


mysql> SELECT i.id, i.name, SUM(s.quantity) AS qty, u.name AS unit FROM item i JOIN stock s ON s.item_id = i.id JOIN unit u ON u.id  = s.unit_id GROUP BY i.id,s.id,u.id;
| id | name                      | qty  | unit |
------------------------------------------------
|  1 | Matcha Latte              |  500 | g    |
|  2 | Matcha Latte With Avocado | 1000 | g    |
|  3 | Coffe With MIlk           | 1000 | g    |
|  4 | Mie Goreng                |  300 | g    |
4 rows in set (0.00 sec)

mysql> select * from stock;
| id | item_id | quantity | unit_id |
-------------------------------------
|  1 |       1 |      500 |       1 |
|  2 |       2 |     1000 |       1 |
|  3 |       3 |     1000 |       1 |
|  4 |       4 |      300 |       1 |
4 rows in set (0.00 sec)


mysql> insert into stock VALUES (NULL, 1, 23, 1);
Query OK, 1 row affected (0.00 sec)

mysql> select * from stock;
| id | item_id | quantity | unit_id |
-------------------------------------
|  1 |       1 |      500 |       1 |
|  2 |       2 |     1000 |       1 |
|  3 |       3 |     1000 |       1 |
|  4 |       4 |      300 |       1 |
|  5 |       1 |       23 |       1 |
5 rows in set (0.00 sec)

mysql> SELECT i.id, i.name, SUM(s.quantity) AS qty, u.name AS unit FROM item i JOIN stock s ON s.item_id = i.id JOIN unit u ON u.id  = s.unit_id GROUP BY i.id,s.id,u.id;
| id | name                      | qty  | unit |
------------------------------------------------
|  1 | Matcha Latte              |  500 | g    |
|  1 | Matcha Latte              |   23 | g    |
|  2 | Matcha Latte With Avocado | 1000 | g    |
|  3 | Coffe With MIlk           | 1000 | g    |
|  4 | Mie Goreng                |  300 | g    |
5 rows in set (0.00 sec)

mysql> SELECT i.id, i.name, SUM(s.quantity) AS qty, u.name AS unit FROM item i JOIN stock s ON s.item_id = i.id JOIN unit u ON u.id  = s.unit_id GROUP BY i.id,u.id;
| id | name                      | qty  | unit |
------------------------------------------------
|  1 | Matcha Latte              |  523 | g    |
|  2 | Matcha Latte With Avocado | 1000 | g    |
|  3 | Coffe With MIlk           | 1000 | g    |
|  4 | Mie Goreng                |  300 | g    |
4 rows in set (0.00 sec)

mysql> SELECT i.id, i.name, SUM(s.quantity) AS qty, u.name AS unit FROM item i JOIN stock s ON s.item_id = i.id JOIN unit u ON u.id  = s.unit_id GROUP BY i.id,u.id;
| id | name                      | qty  | unit |
------------------------------------------------
|  1 | Matcha Latte              |  523 | g    |
|  2 | Matcha Latte With Avocado | 1000 | g    |
|  3 | Coffe With MIlk           | 1000 | g    |
|  4 | Mie Goreng                |  300 | g    |
4 rows in set (0.00 sec)

mysql> SELECT i.id, i.name, SUM(s.quantity) AS qty, u.name AS unit FROM item i JOIN stock s ON s.item_id = i.id JOIN unit u ON u.id  = s.unit_id GROUP BY i.id,u.id
    -> ;
| id | name                      | qty  | unit |
------------------------------------------------
|  1 | Matcha Latte              |  523 | g    |
|  2 | Matcha Latte With Avocado | 1000 | g    |
|  3 | Coffe With MIlk           | 1000 | g    |
|  4 | Mie Goreng                |  300 | g    |
4 rows in set (0.00 sec)

mysql> insert into stock VALUES (NULL, 2, 70, 1);                                                                                                     
Query OK, 1 row affected (0.00 sec)

mysql> SELECT i.id, i.name, SUM(s.quantity) AS qty, u.name AS unit FROM item i JOIN stock s ON s.item_id = i.id JOIN unit u ON u.id  = s.unit_id GROUP BY i.id,u.id;
| id | name                      | qty  | unit |
------------------------------------------------
|  1 | Matcha Latte              |  523 | g    |
|  2 | Matcha Latte With Avocado | 1070 | g    |
|  3 | Coffe With MIlk           | 1000 | g    |
|  4 | Mie Goreng                |  300 | g    |
4 rows in set (0.00 sec)

mysql> insert into stock VALUES (NULL, 3, 900, 1);
Query OK, 1 row affected (0.00 sec)

mysql> SELECT i.id, i.name, SUM(s.quantity) AS qty, u.name AS unit FROM item i JOIN stock s ON s.item_id = i.id JOIN unit u ON u.id  = s.unit_id GROUP BY i.id,u.id;
| id | name                      | qty  | unit |
------------------------------------------------
|  1 | Matcha Latte              |  523 | g    |
|  2 | Matcha Latte With Avocado | 1070 | g    |
|  3 | Coffe With MIlk           | 1900 | g    |
|  4 | Mie Goreng                |  300 | g    |
4 rows in set (0.00 sec)

mysql> SELECT i.id, i.name, AVG(s.quantity) AS qty, u.name AS unit FROM item i JOIN stock s ON s.item_id = i.id JOIN unit u ON u.id  = s.unit_id GROUP BY i.id,u.id;
| id | name                      | qty      | unit |
----------------------------------------------------
|  1 | Matcha Latte              | 261.5000 | g    |
|  2 | Matcha Latte With Avocado | 535.0000 | g    |
|  3 | Coffe With MIlk           | 950.0000 | g    |
|  4 | Mie Goreng                | 300.0000 | g    |
4 rows in set (0.00 sec)

mysql> SELECT i.id, i.name, AVG(s.quantity) AS qty, u.name AS unit FROM item i JOIN stock s ON s.item_id = i.id JOIN unit u ON u.id  = s.unit_id GROUP BY i.id,u.id HAVING unit IS NOT NULL;
| id | name                      | qty      | unit |
----------------------------------------------------
|  1 | Matcha Latte              | 261.5000 | g    |
|  2 | Matcha Latte With Avocado | 535.0000 | g    |
|  3 | Coffe With MIlk           | 950.0000 | g    |
|  4 | Mie Goreng                | 300.0000 | g    |
4 rows in set (0.00 sec)

mysql> 
mysql> SELECT * FROM stock;
| id | item_id | quantity | unit_id |
-------------------------------------
|  1 |       1 |      500 |       1 |
|  2 |       2 |     1000 |       1 |
|  3 |       3 |     1000 |       1 |
|  4 |       4 |      300 |       1 |
|  5 |       1 |       23 |       1 |
|  6 |       2 |       70 |       1 |
|  7 |       3 |      900 |       1 |
7 rows in set (0.00 sec)

mysql> SELECT * FROM stock WHERE item_id IN (1,3);
| id | item_id | quantity | unit_id |
-------------------------------------
|  1 |       1 |      500 |       1 |
|  3 |       3 |     1000 |       1 |
|  5 |       1 |       23 |       1 |
|  7 |       3 |      900 |       1 |
4 rows in set (0.00 sec)

mysql> SELECT * FROM stock WHERE item_id IN (1,3,5);
| id | item_id | quantity | unit_id |
-------------------------------------
|  1 |       1 |      500 |       1 |
|  3 |       3 |     1000 |       1 |
|  5 |       1 |       23 |       1 |
|  7 |       3 |      900 |       1 |
4 rows in set (0.00 sec)

mysql> SELECT * FROM stock WHERE item_id 
    -> IN (SELECT id FROM item WHERE id % 2 = 1);

| id | item_id | quantity | unit_id |
-------------------------------------
|  1 |       1 |      500 |       1 |
|  5 |       1 |       23 |       1 |
|  3 |       3 |     1000 |       1 |
|  7 |       3 |      900 |       1 |
4 rows in set (0.00 sec)

mysql> CREATE VIEW summary AS SELECT i.id, i.name, SUM(s.quantity) AS qty, u.name AS unit FROM item i JOIN stock s ON s.item_id = i.id JOIN unit u ON u.id  = s.unit_id GROUP BY i.id,u.id HAVING unit IS NOT NULL;
Query OK, 0 rows affected (0.00 sec)

mysql> SELECT * FROM summary;
| id | name                      | qty  | unit |
------------------------------------------------
|  1 | Matcha Latte              |  523 | g    |
|  2 | Matcha Latte With Avocado | 1070 | g    |
|  3 | Coffe With MIlk           | 1900 | g    |
|  4 | Mie Goreng                |  300 | g    |
4 rows in set (0.01 sec)




CREATE PROCEDURE summary_by_unit (IN in_unit VARCHAR(20)) BEGIN SELECT i.id, i.name, SUM(s.quantity) AS qty, u.name AS unit FROM item i LEFT JOIN stock s ON s.item_id = i.id LEFT JOIN unit u ON u.id  = s.unit_id GROUP BY i.id,u.id HAVING unit = in_unit; END//


delimiter;