# Back End — Databases & SQL

## Relational Concepts

- **Table** (relation) · **Row** (record) · **Column** (attribute).
- **Primary key** — unique row identifier, not null.
- **Foreign key** — references another table's primary key; enforces referential integrity.
- Relationships: 1:1, 1:N, M:N (needs junction table).

## Normalization

| Form | Rule |
|------|------|
| 1NF | Atomic values, no repeating groups |
| 2NF | 1NF + no partial dependency on composite key |
| 3NF | 2NF + no transitive dependency |

Goal: reduce redundancy and update anomalies. Denormalize only for proven performance need.

## Schema Example

```sql
CREATE TABLE customers (
  id    INT AUTO_INCREMENT PRIMARY KEY,
  name  VARCHAR(100) NOT NULL,
  email VARCHAR(150) NOT NULL UNIQUE
);

CREATE TABLE orders (
  id          INT AUTO_INCREMENT PRIMARY KEY,
  customer_id INT NOT NULL,
  total       DECIMAL(10,2) NOT NULL CHECK (total >= 0),
  created_at  TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (customer_id) REFERENCES customers(id)
);
```

Use `DECIMAL` for money, never `FLOAT`.

## CRUD

```sql
INSERT INTO customers (name, email) VALUES ('Ana', 'ana@example.com');
SELECT id, name FROM customers WHERE email = 'ana@example.com';
UPDATE customers SET name = 'Ana Cruz' WHERE id = 1;
DELETE FROM customers WHERE id = 1;
```

**Always include WHERE on UPDATE/DELETE** — otherwise every row changes.

## Joins

```sql
SELECT c.name, o.total
FROM customers c
INNER JOIN orders o ON o.customer_id = c.id;      -- only matches

SELECT c.name, o.total
FROM customers c
LEFT JOIN orders o ON o.customer_id = c.id;       -- all customers, even without orders
```

## Aggregation

```sql
SELECT customer_id, COUNT(*) AS order_count, SUM(total) AS spent
FROM orders
GROUP BY customer_id
HAVING SUM(total) > 1000
ORDER BY spent DESC;
```

`WHERE` filters rows before grouping. `HAVING` filters groups after.

## Indexes

- Speed up reads on searched/joined columns.
- Slow down writes, use storage.
- Index foreign keys and frequent `WHERE` columns.

## Transactions & ACID

```sql
START TRANSACTION;
UPDATE accounts SET balance = balance - 500 WHERE id = 1;
UPDATE accounts SET balance = balance + 500 WHERE id = 2;
COMMIT;      -- or ROLLBACK on error
```

- **A**tomicity — all or nothing.
- **C**onsistency — rules always hold.
- **I**solation — concurrent transactions don't interfere.
- **D**urability — committed data survives crash.

## Java + JDBC

```java
String sql = "INSERT INTO customers (name, email) VALUES (?, ?)";
try (Connection conn = DriverManager.getConnection(url, user, password);
     PreparedStatement ps = conn.prepareStatement(sql)) {
    ps.setString(1, name);
    ps.setString(2, email);
    ps.executeUpdate();
} catch (SQLException e) {
    throw new RuntimeException("Insert failed", e);
}
```

try-with-resources closes connection automatically.

## SQL vs NoSQL

- **SQL** — structured schema, joins, ACID. Use for relational business data.
- **NoSQL** — flexible schema, horizontal scaling (document, key-value, graph). Use for unstructured/high-volume data.

## Gotchas

- `NULL = NULL` is not true — use `IS NULL`.
- `SELECT *` in production code hides schema changes and wastes bandwidth.
- Deleting a parent row with children fails unless `ON DELETE CASCADE` or children removed first.
- Back up before schema migrations.
