
Таблицы использованные для демонстрации объединений в разных версиях ClickHouse:

CREATE TABLE test1 (id UInt64, value String) ENGINE=MergeTree ORDER BY id;
CREATE TABLE test2 (id UInt64, value String) ENGINE=MergeTree ORDER BY id;
INSERT INTO test1 SELECT number, number FROM numbers(150000000);
INSERT INTO test2 SELECT number, number FROM numbers(150000000);
SELECT * FROM test1 AS lhs INNER JOIN test2 AS rhs ON lhs.id = rhs.id WHERE test1.id = 3;

