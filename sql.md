# 📌 MySQL Cheat Sheet

Tài liệu này cung cấp danh sách các lệnh MySQL quan trọng, bao gồm **DDL, DML, DQL, DCL, TCL**.

---

## 1️⃣ Lệnh DDL (Data Definition Language - Ngôn ngữ định nghĩa dữ liệu)
Dùng để tạo, thay đổi hoặc xóa cấu trúc của cơ sở dữ liệu và bảng.

| Lệnh | Mô tả | Ví dụ |
|------|------|------|
| `CREATE DATABASE` | Tạo cơ sở dữ liệu mới | `CREATE DATABASE mydb;` |
| `DROP DATABASE` | Xóa cơ sở dữ liệu | `DROP DATABASE mydb;` |
| `CREATE TABLE` | Tạo bảng mới | `CREATE TABLE users (id INT PRIMARY KEY, name VARCHAR(100));` |
| `ALTER TABLE` | Thay đổi cấu trúc bảng | `ALTER TABLE users ADD COLUMN email VARCHAR(100);` |
| `DROP TABLE` | Xóa bảng khỏi cơ sở dữ liệu | `DROP TABLE users;` |
| `TRUNCATE TABLE` | Xóa toàn bộ dữ liệu nhưng giữ lại cấu trúc bảng | `TRUNCATE TABLE users;` |

---

## 2️⃣ Lệnh DML (Data Manipulation Language - Ngôn ngữ thao tác dữ liệu)
Dùng để thao tác với dữ liệu trong bảng.

| Lệnh | Mô tả | Ví dụ |
|------|------|------|
| `INSERT INTO` | Chèn dữ liệu vào bảng | `INSERT INTO users (id, name) VALUES (1, 'John');` |
| `UPDATE` | Cập nhật dữ liệu trong bảng | `UPDATE users SET name = 'John Doe' WHERE id = 1;` |
| `DELETE FROM` | Xóa dữ liệu khỏi bảng | `DELETE FROM users WHERE id = 1;` |

---

## 3️⃣ Lệnh DQL (Data Query Language - Ngôn ngữ truy vấn dữ liệu)
Dùng để truy vấn dữ liệu từ bảng.

| Lệnh | Mô tả | Ví dụ |
|------|------|------|
| `SELECT *` | Lấy toàn bộ dữ liệu từ bảng | `SELECT * FROM users;` |
| `SELECT DISTINCT` | Lấy các giá trị khác nhau | `SELECT DISTINCT name FROM users;` |
| `WHERE` | Lọc dữ liệu theo điều kiện | `SELECT * FROM users WHERE id = 1;` |
| `ORDER BY` | Sắp xếp kết quả | `SELECT * FROM users ORDER BY name ASC;` |
| `GROUP BY` | Nhóm dữ liệu | `SELECT COUNT(id), name FROM users GROUP BY name;` |
| `HAVING` | Lọc dữ liệu nhóm | `SELECT name, COUNT(id) FROM users GROUP BY name HAVING COUNT(id) > 1;` |
| `LIMIT` | Giới hạn số dòng trả về | `SELECT * FROM users LIMIT 5;` |

---

## 4️⃣ Lệnh DCL (Data Control Language - Ngôn ngữ kiểm soát dữ liệu)
Dùng để phân quyền truy cập dữ liệu.

| Lệnh | Mô tả | Ví dụ |
|------|------|------|
| `GRANT` | Cấp quyền cho user | `GRANT SELECT, INSERT ON mydb.users TO 'user1'@'localhost';` |
| `REVOKE` | Thu hồi quyền của user | `REVOKE INSERT ON mydb.users FROM 'user1'@'localhost';` |

---

## 5️⃣ Lệnh TCL (Transaction Control Language - Ngôn ngữ điều khiển giao dịch)
Dùng để quản lý giao dịch trong cơ sở dữ liệu.

| Lệnh | Mô tả | Ví dụ |
|------|------|------|
| `START TRANSACTION` | Bắt đầu một giao dịch | `START TRANSACTION;` |
| `COMMIT` | Xác nhận thay đổi vĩnh viễn | `COMMIT;` |
| `ROLLBACK` | Hoàn tác thay đổi | `ROLLBACK;` |
| `SAVEPOINT` | Tạo điểm lưu tạm trong giao dịch | `SAVEPOINT sp1;` |
| `ROLLBACK TO SAVEPOINT` | Hoàn tác về một điểm lưu | `ROLLBACK TO sp1;` |

---

📌 **Lưu ý:**  
- **DDL & DCL** thường **tự động COMMIT**, không thể ROLLBACK.  
- **DML** có thể được ROLLBACK nếu chưa COMMIT.  
- **TCL** giúp kiểm soát giao dịch để tránh mất dữ liệu quan trọng.  

🚀 **Tài liệu tham khảo:** [MySQL Documentation](https://dev.mysql.com/doc/)
