 select * from Users inner join Orders on Users.user_id = Orders.user_id;
+---------+-------------+---------------+---------+------------+-----------+---------------------+----------+---------+--------------+--------+---------------------+
| user_id | username    | password_hash | email   | first_name | last_name | created_at          | order_id | user_id | total_amount | status | created_at          |
+---------+-------------+---------------+---------+------------+-----------+---------------------+----------+---------+--------------+--------+---------------------+
|       1 | nehaprakash | neha          | neha123 | neha       | prakash   | 2025-06-30 13:02:09 |        1 |       1 |       754.32 | unpaid | 2025-06-30 13:08:33 |
|       2 | rudradev    | rudi          | rudi555 | rudra      | dev       | 2025-06-28 10:15:08 |        2 |       2 |       450.00 | paid   | 2025-06-28 10:15:08 |
|       2 | rudradev    | rudi          | rudi555 | rudra      | dev       | 2025-06-28 10:15:08 |        3 |       2 |       350.00 | paid   | 2025-06-28 10:15:08 |
+---------+-------------+---------------+---------+------------+-----------+---------------------+----------+---------+--------------+--------+---------------------+
3 rows in set (0.019 sec)

mysql> select Users.username,Users.email,Orders.total_amount from Users inner join Orders on Users.user_id = Orders.user_id;
+-------------+---------+--------------+
| username    | email   | total_amount |
+-------------+---------+--------------+
| nehaprakash | neha123 |       754.32 |
| rudradev    | rudi555 |       450.00 |
| rudradev    | rudi555 |       350.00 |
+-------------+---------+--------------+
3 rows in set (0.009 sec)

mysql> select Users.username,Users.email,Orders.total_amount,orders.status from Users inner join Orders on Users.user_id = Orders.user_id;
+-------------+---------+--------------+--------+
| username    | email   | total_amount | status |
+-------------+---------+--------------+--------+
| nehaprakash | neha123 |       754.32 | unpaid |
| rudradev    | rudi555 |       450.00 | paid   |
| rudradev    | rudi555 |       350.00 | paid   |
+-------------+---------+--------------+--------+
3 rows in set (0.009 sec)

mysql> select * from Users left join Orders on Users.user_id = Orders.user_id order by Users.username;
+---------+---------------+---------------+---------+------------+-----------+---------------------+----------+---------+--------------+--------+---------------------+
| user_id | username      | password_hash | email   | first_name | last_name | created_at          | order_id | user_id | total_amount | status | created_at          |
+---------+---------------+---------------+---------+------------+-----------+---------------------+----------+---------+--------------+--------+---------------------+
|       1 | nehaprakash   | neha          | neha123 | neha       | prakash   | 2025-06-30 13:02:09 |        1 |       1 |       754.32 | unpaid | 2025-06-30 13:08:33 |
|       3 | parvathygowri | paru          | paru23  | parvathy   | gowri     | 2025-06-30 13:05:11 |     NULL |    NULL |         NULL | NULL   | NULL                |
|       2 | rudradev      | rudi          | rudi555 | rudra      | dev       | 2025-06-28 10:15:08 |        3 |       2 |       350.00 | paid   | 2025-06-28 10:15:08 |
|       2 | rudradev      | rudi          | rudi555 | rudra      | dev       | 2025-06-28 10:15:08 |        2 |       2 |       450.00 | paid   | 2025-06-28 10:15:08 |
+---------+---------------+---------------+---------+------------+-----------+---------------------+----------+---------+--------------+--------+---------------------+
4 rows in set (0.016 sec)

mysql> select Users.username,Users.email,Orders.total_amount,orders.status from Users left join Orders on Users.user_id = Orders.user_id;
+---------------+---------+--------------+--------+
| username      | email   | total_amount | status |
+---------------+---------+--------------+--------+
| nehaprakash   | neha123 |       754.32 | unpaid |
| rudradev      | rudi555 |       350.00 | paid   |
| rudradev      | rudi555 |       450.00 | paid   |
| parvathygowri | paru23  |         NULL | NULL   |
+---------------+---------+--------------+--------+
4 rows in set (0.011 sec)

mysql> select Users.username,Users.email,Orders.total_amount,orders.status from Users right join Orders on Users.user_id = Orders.user_id;
+-------------+---------+--------------+--------+
| username    | email   | total_amount | status |
+-------------+---------+--------------+--------+
| nehaprakash | neha123 |       754.32 | unpaid |
| rudradev    | rudi555 |       450.00 | paid   |
| rudradev    | rudi555 |       350.00 | paid   |
+-------------+---------+--------------+--------+
