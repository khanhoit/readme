Dưới đây là câu trả lời chi tiết cho từng câu hỏi trong danh sách của bạn:  

---

## 🔹 **1. Câu hỏi về Kiến thức Cơ bản MySQL**  

### 1. **Sự khác biệt giữa InnoDB và MyISAM là gì?**  
| Tiêu chí    | InnoDB  | MyISAM |
|-------------|---------|--------|
| **Hỗ trợ Transaction** | ✔ Có | ❌ Không |
| **Khóa (Locking)** | Row-level Locking (khóa dòng) | Table-level Locking (khóa bảng) |
| **Hỗ trợ Foreign Key** | ✔ Có | ❌ Không |
| **Tốc độ SELECT** | Chậm hơn MyISAM trên dữ liệu tĩnh | Nhanh hơn InnoDB |
| **Tốc độ INSERT/UPDATE/DELETE** | Nhanh hơn khi có nhiều thao tác ghi | Chậm hơn với nhiều thao tác ghi |
| **Khôi phục dữ liệu khi mất điện** | ✔ Có (ACID Compliance) | ❌ Không (Dễ bị mất dữ liệu) |

👉 **Khi nào dùng gì?**  
- **Dùng InnoDB** nếu cần hỗ trợ giao dịch (Transactions), khóa dòng, và an toàn dữ liệu.  
- **Dùng MyISAM** nếu cần tốc độ đọc nhanh, không quan tâm đến giao dịch.  

---

### 2. **Các loại index trong MySQL là gì?**  
- **PRIMARY KEY**: Chỉ mục chính, không cho phép trùng lặp hoặc NULL.  
- **UNIQUE INDEX**: Ngăn chặn giá trị trùng lặp nhưng cho phép NULL.  
- **INDEX (B-Tree Index)**: Chỉ mục giúp tăng tốc truy vấn SELECT.  
- **FULLTEXT INDEX**: Hỗ trợ tìm kiếm văn bản (chỉ có trong MyISAM và InnoDB từ MySQL 5.6).  
- **SPATIAL INDEX**: Dùng cho dữ liệu không gian (chỉ có trong MyISAM, InnoDB từ MySQL 5.7).  

📌 **Cách kiểm tra index trên bảng**:  
```sql
SHOW INDEX FROM table_name;
```

---

### 3. **Sự khác biệt giữa `CHAR` và `VARCHAR` là gì?**  
| Tiêu chí  | CHAR | VARCHAR |
|-----------|------|---------|
| **Kích thước** | Cố định (1-255 ký tự) | Biến đổi (1-65535 ký tự) |
| **Tốc độ** | Nhanh hơn khi dữ liệu có độ dài cố định | Tiết kiệm dung lượng nhưng chậm hơn |
| **Ứng dụng** | Sử dụng cho dữ liệu có độ dài cố định (Mã quốc gia, số CMND) | Sử dụng cho dữ liệu có độ dài thay đổi (Tên, địa chỉ) |

👉 **Dùng `CHAR` khi dữ liệu có độ dài cố định, dùng `VARCHAR` khi dữ liệu có độ dài thay đổi.**

---

### 4. **Khi nào nên dùng `JOIN` thay vì `SUBQUERY`?**  
- **JOIN nhanh hơn** nếu lấy dữ liệu từ nhiều bảng vì MySQL có thể tối ưu hóa tốt hơn.  
- **SUBQUERY dễ đọc hơn**, nhưng trong nhiều trường hợp kém hiệu quả hơn JOIN.  
- **Dùng JOIN khi cần kết hợp dữ liệu từ nhiều bảng**.  
- **Dùng SUBQUERY khi cần xử lý một tập dữ liệu con trước**.  

📌 **Ví dụ:**  
- **Dùng JOIN**:  
```sql
SELECT employees.name, departments.department_name
FROM employees
JOIN departments ON employees.department_id = departments.id;
```
- **Dùng SUBQUERY (chậm hơn)**:  
```sql
SELECT name, 
       (SELECT department_name FROM departments WHERE id = employees.department_id) AS department_name
FROM employees;
```

---

### 5. **Khác nhau giữa `PRIMARY KEY`, `UNIQUE KEY` và `FOREIGN KEY`?**  
| Loại | Chức năng |
|------|----------|
| **PRIMARY KEY** | Xác định duy nhất mỗi bản ghi, không cho phép NULL |
| **UNIQUE KEY** | Ngăn trùng lặp nhưng cho phép NULL |
| **FOREIGN KEY** | Ràng buộc với một PRIMARY KEY ở bảng khác để đảm bảo tính toàn vẹn dữ liệu |

---

### 6. **Auto Increment có thể đặt lại giá trị không? Nếu có thì làm thế nào?**  
Có, dùng:  
```sql
ALTER TABLE table_name AUTO_INCREMENT = 100;
```
⚠ **Lưu ý**: Nếu đã có giá trị cao hơn trong bảng, MySQL vẫn sẽ tiếp tục từ giá trị lớn nhất.

---

### 7. **Các kiểu dữ liệu nào phù hợp để lưu trữ JSON trong MySQL?**  
- **JSON** (MySQL 5.7+)  
- **TEXT** (nếu MySQL không hỗ trợ JSON)  

📌 **Ví dụ lưu JSON**:  
```sql
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    details JSON
);
```

---

## 🔹 **2. Câu hỏi về Quản trị & Tối ưu Hóa CSDL**  

### 8. **Làm thế nào để tối ưu hiệu suất của MySQL?**  
✔ **Tạo index hợp lý** (tránh index thừa)  
✔ **Dùng EXPLAIN SELECT** để kiểm tra truy vấn  
✔ **Tối ưu cache (`query_cache_size`)**  
✔ **Dùng partitioning (chia bảng nhỏ hơn)**  

---

### 9. **Cách kiểm tra các truy vấn đang chạy trong MySQL?**  
```sql
SHOW PROCESSLIST;
```

---

### 10. **Làm sao để xác định câu truy vấn chậm và cách tối ưu nó?**  
✔ **Bật slow query log**:  
```sql
SET GLOBAL slow_query_log = 'ON';
SET GLOBAL long_query_time = 2;
```
✔ **Dùng `EXPLAIN SELECT` để kiểm tra kế hoạch truy vấn**  

---

### 11. **Làm sao để tối ưu chỉ mục (Index)?**  
- **Loại bỏ index không cần thiết**  
- **Tránh quá nhiều index trên một bảng**  
- **Dùng `OPTIMIZE TABLE`**  

---

### 12. **Cách tối ưu hóa bảng trong MySQL?**  
```sql
OPTIMIZE TABLE table_name;
```

---

### 13. **Làm thế nào để cải thiện hiệu suất JOIN trên các bảng lớn?**  
- **Tạo index trên các cột JOIN**  
- **Dùng INNER JOIN thay vì LEFT JOIN nếu có thể**  
- **Tránh JOIN quá nhiều bảng**  

---

## 🔹 **3. Câu hỏi về Sao lưu & Khôi phục Dữ Liệu**  

### 14. **Làm sao để backup database MySQL?**  
```bash
mysqldump -u root -p mydb > backup.sql
```

---

### 15. **Cách restore database từ file backup?**  
```bash
mysql -u root -p mydb < backup.sql
```

---

### 16. **Sự khác biệt giữa FULL BACKUP, INCREMENTAL BACKUP và DIFFERENTIAL BACKUP?**  
| Loại Backup | Đặc điểm |
|-------------|---------|
| **Full Backup** | Sao lưu toàn bộ dữ liệu |
| **Incremental Backup** | Chỉ sao lưu dữ liệu thay đổi từ lần backup trước |
| **Differential Backup** | Sao lưu dữ liệu thay đổi từ lần full backup gần nhất |

---

### 17. **Cách xuất dữ liệu MySQL ra CSV?**  
```sql
SELECT * FROM users INTO OUTFILE '/path/users.csv'
FIELDS TERMINATED BY ',' ENCLOSED BY '"'
LINES TERMINATED BY '\n';
```

---

Dưới đây là câu trả lời chi tiết cho các câu hỏi còn lại từ **18 đến 31** 🚀  

---

## 🔹 **4. Câu hỏi về Bảo mật MySQL**  

### 18. **Làm thế nào để bảo mật MySQL?**  
✔ **Đặt mật khẩu mạnh cho tài khoản root**  
✔ **Chỉ cho phép truy cập từ IP cụ thể (`bind-address` trong `my.cnf`)**  
✔ **Tạo user với quyền hạn tối thiểu cần thiết**  
✔ **Tắt truy cập từ xa nếu không cần thiết (`skip-networking`)**  
✔ **Mã hóa dữ liệu với SSL nếu cần**  

---

### 19. **Cách kiểm tra user nào có quyền gì trong MySQL?**  
📌 Dùng lệnh:  
```sql
SHOW GRANTS FOR 'username'@'host';
```
📌 Kiểm tra tất cả user:  
```sql
SELECT user, host FROM mysql.user;
```

---

### 20. **Cách thay đổi mật khẩu user MySQL?**  
📌 Cách 1 (MySQL 5.7+):  
```sql
ALTER USER 'username'@'host' IDENTIFIED BY 'newpassword';
```
📌 Cách 2 (MySQL 5.6 trở xuống):  
```sql
SET PASSWORD FOR 'username'@'host' = PASSWORD('newpassword');
```

---

### 21. **Làm sao để chống SQL Injection?**  
✔ **Dùng Prepared Statements thay vì query trực tiếp**  
✔ **Không bao giờ nối chuỗi trực tiếp vào câu lệnh SQL**  
✔ **Hạn chế quyền của user MySQL (chỉ cấp quyền cần thiết)**  
✔ **Sử dụng WAF (Web Application Firewall) để bảo vệ ứng dụng**  

📌 **Ví dụ dùng Prepared Statements trong PHP:**  
```php
$stmt = $conn->prepare("SELECT * FROM users WHERE email = ?");
$stmt->bind_param("s", $email);
$stmt->execute();
```

---

### 22. **Cách giới hạn quyền truy cập của user MySQL?**  
📌 Cấp quyền chỉ cho phép `SELECT` trên bảng `users`:  
```sql
GRANT SELECT ON mydb.users TO 'readonly_user'@'host';
```
📌 Thu hồi quyền:  
```sql
REVOKE INSERT, UPDATE ON mydb.users FROM 'readonly_user'@'host';
```

---

## 🔹 **5. Câu hỏi về Giao Dịch & Khóa (Locking)**  

### 23. **Giao dịch (Transaction) trong MySQL là gì?**  
🔹 Giao dịch là một tập hợp các lệnh SQL thực hiện như một đơn vị duy nhất.  
🔹 Giao dịch giúp đảm bảo tính **toàn vẹn dữ liệu** (ACID).  

📌 **Ví dụ về giao dịch:**  
```sql
START TRANSACTION;
UPDATE accounts SET balance = balance - 100 WHERE id = 1;
UPDATE accounts SET balance = balance + 100 WHERE id = 2;
COMMIT;
```

---

### 24. **Sự khác biệt giữa `COMMIT` và `ROLLBACK`?**  
| Lệnh | Chức năng |
|------|----------|
| **COMMIT** | Lưu thay đổi vào database |
| **ROLLBACK** | Hủy bỏ tất cả thay đổi trong transaction |

📌 **Ví dụ rollback khi có lỗi:**  
```sql
START TRANSACTION;
UPDATE accounts SET balance = balance - 100 WHERE id = 1;
UPDATE accounts SET balance = balance + 100 WHERE id = 2;
ROLLBACK;
```

---

### 25. **Sự khác nhau giữa Row-level Locking và Table-level Locking?**  
| Loại khóa | Mô tả |
|-----------|-------|
| **Row-level Locking** | Chỉ khóa dòng bị ảnh hưởng (có trong InnoDB) |
| **Table-level Locking** | Khóa toàn bộ bảng khi có thao tác ghi (dùng trong MyISAM) |

📌 **Ví dụ khóa dòng (Row-level Locking):**  
```sql
SELECT * FROM accounts WHERE id = 1 FOR UPDATE;
```

📌 **Ví dụ khóa bảng (Table-level Locking):**  
```sql
LOCK TABLES accounts WRITE;
```

---

### 26. **Làm thế nào để tránh Deadlock trong MySQL?**  
✔ **Truy vấn dữ liệu theo cùng một thứ tự giữa các giao dịch**  
✔ **Dùng khóa dòng thay vì khóa bảng**  
✔ **Giữ khóa trong thời gian ngắn nhất có thể**  
✔ **Dùng `SHOW ENGINE INNODB STATUS;` để kiểm tra deadlock**  

---

## 🔹 **6. Câu hỏi về Replication & High Availability**  

### 27. **Replication trong MySQL là gì?**  
✔ **Replication** là quá trình sao chép dữ liệu từ một **Master** sang một hoặc nhiều **Slave**.  
✔ Giúp **cân bằng tải**, **dự phòng dữ liệu**, và **tăng hiệu suất**.  

---

### 28. **Các loại Replication trong MySQL?**  
| Loại Replication | Mô tả |
|-----------------|-------|
| **Asynchronous** | Slave nhận dữ liệu từ Master nhưng không đồng bộ ngay lập tức |
| **Synchronous** | Slave chỉ xác nhận khi đã nhận đầy đủ dữ liệu từ Master |
| **Semi-Synchronous** | Kết hợp giữa Async và Sync, có độ trễ thấp hơn |

---

### 29. **Làm thế nào để cấu hình Replication Master-Slave?**  
📌 **Bước 1: Cấu hình Master** (`my.cnf` hoặc `my.ini`):  
```ini
[mysqld]
server-id=1
log-bin=mysql-bin
binlog-do-db=mydatabase
```
📌 **Bước 2: Tạo user replication trên Master:**  
```sql
GRANT REPLICATION SLAVE ON *.* TO 'replica_user'@'%' IDENTIFIED BY 'password';
```
📌 **Bước 3: Cấu hình Slave** (`my.cnf`):  
```ini
[mysqld]
server-id=2
relay-log=mysql-relay-bin
```
📌 **Bước 4: Kết nối Slave với Master:**  
```sql
CHANGE MASTER TO MASTER_HOST='master_ip',
MASTER_USER='replica_user',
MASTER_PASSWORD='password',
MASTER_LOG_FILE='mysql-bin.000001',
MASTER_LOG_POS=154;
START SLAVE;
```

---

### 30. **Sự khác nhau giữa Synchronous và Asynchronous Replication?**  
| Loại Replication | Ưu điểm | Nhược điểm |
|-----------------|---------|-----------|
| **Synchronous** | Dữ liệu luôn đồng bộ | Chậm hơn |
| **Asynchronous** | Hiệu suất cao hơn | Có thể mất dữ liệu nếu Master bị lỗi |

---

### 31. **Cách kiểm tra trạng thái của Replication?**  
📌 Kiểm tra trên Slave:  
```sql
SHOW SLAVE STATUS\G;
```
📌 Kiểm tra trên Master:  
```sql
SHOW MASTER STATUS;
```

⚠ **Lưu ý quan trọng**:  
- Nếu `Slave_IO_Running` hoặc `Slave_SQL_Running` = **No**, cần kiểm tra lỗi và khởi động lại Slave.

---

💡 **Tóm tắt nhanh các chủ đề quan trọng:**  
✅ **Tối ưu hóa MySQL** – Dùng index, EXPLAIN, cache  
✅ **Bảo mật MySQL** – Tạo user với quyền hạn chế, chống SQL Injection  
✅ **Replication & High Availability** – Cấu hình Master-Slave, kiểm tra trạng thái  

