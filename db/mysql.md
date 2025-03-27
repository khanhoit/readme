
### 🔹 **1. Câu hỏi về Kiến thức Cơ bản MySQL**  
💡 **Ví dụ:**  
1. **Sự khác biệt giữa InnoDB và MyISAM là gì?**  
2. **Các loại index trong MySQL là gì?**  
3. **Sự khác biệt giữa `CHAR` và `VARCHAR` là gì?**  
4. **Khi nào nên dùng `JOIN` thay vì `SUBQUERY`?**  
5. **Khác nhau giữa `PRIMARY KEY`, `UNIQUE KEY` và `FOREIGN KEY`?**  
6. **Auto Increment có thể đặt lại giá trị không? Nếu có thì làm thế nào?**  
7. **Các kiểu dữ liệu nào phù hợp để lưu trữ JSON trong MySQL?**  

---

### 🔹 **2. Câu hỏi về Quản trị & Tối ưu Hóa CSDL**  
💡 **Ví dụ:**  
8. **Làm thế nào để tối ưu hiệu suất của MySQL?**  
9. **Cách kiểm tra các truy vấn đang chạy trong MySQL?**  
   - (Gợi ý: Dùng `SHOW PROCESSLIST;`)  
10. **Làm sao để xác định câu truy vấn chậm và cách tối ưu nó?**  
    - (Gợi ý: Dùng `EXPLAIN SELECT ...`)  
11. **Làm sao để tối ưu chỉ mục (Index)?**  
12. **Cách tối ưu hóa bảng trong MySQL?**  
    - (Gợi ý: `OPTIMIZE TABLE users;`)  
13. **Làm thế nào để cải thiện hiệu suất JOIN trên các bảng lớn?**  

---

### 🔹 **3. Câu hỏi về Sao lưu & Khôi phục Dữ Liệu**  
💡 **Ví dụ:**  
14. **Làm sao để backup database MySQL?**  
    - (Gợi ý: `mysqldump -u root -p mydb > backup.sql`)  
15. **Cách restore database từ file backup?**  
    - (Gợi ý: `mysql -u root -p mydb < backup.sql`)  
16. **Sự khác biệt giữa FULL BACKUP, INCREMENTAL BACKUP và DIFFERENTIAL BACKUP?**  
17. **Cách xuất dữ liệu MySQL ra CSV?**  

---

### 🔹 **4. Câu hỏi về Bảo mật MySQL**  
💡 **Ví dụ:**  
18. **Làm thế nào để bảo mật MySQL?**  
19. **Cách kiểm tra user nào có quyền gì trong MySQL?**  
    - (Gợi ý: `SHOW GRANTS FOR 'user'@'host';`)  
20. **Cách thay đổi mật khẩu user MySQL?**  
    - (Gợi ý: `ALTER USER 'user'@'host' IDENTIFIED BY 'newpassword';`)  
21. **Làm sao để chống SQL Injection?**  
22. **Cách giới hạn quyền truy cập của user MySQL?**  

---

### 🔹 **5. Câu hỏi về Giao Dịch & Khóa (Locking)**  
💡 **Ví dụ:**  
23. **Giao dịch (Transaction) trong MySQL là gì?**  
24. **Sự khác biệt giữa `COMMIT` và `ROLLBACK`?**  
25. **Sự khác nhau giữa Row-level Locking và Table-level Locking?**  
26. **Làm thế nào để tránh Deadlock trong MySQL?**  

---

### 🔹 **6. Câu hỏi về Replication & High Availability**  
💡 **Ví dụ:**  
27. **Replication trong MySQL là gì?**  
28. **Các loại Replication trong MySQL?**  
29. **Làm thế nào để cấu hình Replication Master-Slave?**  
30. **Sự khác nhau giữa Synchronous và Asynchronous Replication?**  
31. **Cách kiểm tra trạng thái của Replication?**  
    - (Gợi ý: `SHOW SLAVE STATUS\G;`)  

---


## **📌 Các loại dữ liệu trong MySQL**  

Trong MySQL, dữ liệu được chia thành 4 nhóm chính:  
1️⃣ **Số (Numeric Data Types)**  
2️⃣ **Chuỗi (String Data Types)**  
3️⃣ **Ngày & Giờ (Date and Time Data Types)**  
4️⃣ **Dữ liệu khác (Other Data Types)**  

---

## **1️⃣ Kiểu số (Numeric Data Types)**
| **Loại** | **Tên** | **Kích thước** | **Phạm vi giá trị** |
|----------|--------|-------------|---------------------------|
| ✅ **Số nguyên** | `TINYINT` | 1 byte | -128 đến 127 (có dấu), 0-255 (không dấu) |
|  | `SMALLINT` | 2 bytes | -32,768 đến 32,767 |
|  | `MEDIUMINT` | 3 bytes | -8,388,608 đến 8,388,607 |
|  | `INT` / `INTEGER` | 4 bytes | -2,147,483,648 đến 2,147,483,647 |
|  | `BIGINT` | 8 bytes | -9,223,372,036,854,775,808 đến 9,223,372,036,854,775,807 |
| ✅ **Số thực (Decimal & Floating Point)** | `FLOAT(M,D)` | 4 bytes | Độ chính xác thấp |
|  | `DOUBLE(M,D)` | 8 bytes | Độ chính xác cao hơn `FLOAT` |
|  | `DECIMAL(M,D)` | Tùy thuộc M | Sử dụng cho số chính xác cao, lưu dưới dạng chuỗi |

📌 **Lưu ý:**  
- `DECIMAL` dùng khi cần **tính toán chính xác số tiền** (tránh lỗi làm tròn).  
- `FLOAT` và `DOUBLE` sử dụng dấu chấm động (floating point) nên có thể gặp lỗi làm tròn.  

---

## **2️⃣ Kiểu chuỗi (String Data Types)**
| **Tên** | **Kích thước** | **Mô tả** |
|---------|-------------|-------------|
| `CHAR(N)` | 1 - 255 bytes | Chuỗi cố định độ dài (tốn nhiều bộ nhớ nhưng truy vấn nhanh hơn) |
| `VARCHAR(N)` | 1 - 65535 bytes | Chuỗi có độ dài thay đổi (tốn ít bộ nhớ hơn `CHAR`) |
| `TEXT` | 1 - 4GB | Dữ liệu văn bản lớn (không hỗ trợ index tốt) |
| `TINYTEXT` | 255 bytes | Văn bản nhỏ |
| `TEXT` | 65,535 bytes (~64KB) | Văn bản trung bình |
| `MEDIUMTEXT` | 16,777,215 bytes (~16MB) | Văn bản lớn |
| `LONGTEXT` | 4,294,967,295 bytes (~4GB) | Văn bản rất lớn |
| `BLOB` | 64KB - 4GB | Dữ liệu nhị phân (ảnh, file) |
| `ENUM` | 1 - 2 bytes | Danh sách cố định giá trị (ví dụ: 'Nam', 'Nữ', 'Khác') |
| `SET` | 1 - 8 bytes | Cho phép chọn nhiều giá trị trong danh sách |

📌 **Lưu ý:**  
- `VARCHAR` **tốt hơn `CHAR` nếu độ dài chuỗi không cố định**.  
- `TEXT` **không thể dùng trong index trực tiếp**.  
- `ENUM` giúp tiết kiệm bộ nhớ nhưng khó mở rộng danh sách giá trị.  

---

## **3️⃣ Kiểu ngày & giờ (Date and Time Data Types)**
| **Tên** | **Kích thước** | **Phạm vi** | **Mô tả** |
|---------|------------|------------|------------|
| `DATE` | 3 bytes | `1000-01-01` đến `9999-12-31` | Ngày (YYYY-MM-DD) |
| `DATETIME` | 8 bytes | `1000-01-01 00:00:00` đến `9999-12-31 23:59:59` | Ngày & Giờ |
| `TIMESTAMP` | 4 bytes | `1970-01-01 00:00:01` đến `2038-01-19 03:14:07` | Lưu thời gian tính theo UNIX timestamp |
| `TIME` | 3 bytes | `-838:59:59` đến `838:59:59` | Chỉ lưu giờ phút giây |
| `YEAR` | 1 byte | `1901` đến `2155` | Lưu năm (YYYY) |

📌 **Lưu ý:**  
- `TIMESTAMP` **tự động cập nhật theo múi giờ của server**.  
- `DATETIME` **không bị ảnh hưởng bởi múi giờ**.  

---

## **4️⃣ Kiểu dữ liệu khác (Other Data Types)**
| **Tên** | **Mô tả** |
|---------|------------|
| `JSON` | Lưu trữ dữ liệu JSON, hỗ trợ truy vấn JSON |
| `GEOMETRY` | Lưu dữ liệu không gian (GIS, bản đồ) |

📌 **Lưu ý:**  
- `JSON` rất hữu ích để lưu **dữ liệu động** (ví dụ: thông tin cấu hình).  
- `GEOMETRY` dùng trong ứng dụng bản đồ (Google Maps, OpenStreetMap).  

---

## **📌 Khi nào chọn kiểu dữ liệu nào?**
| **Trường hợp** | **Nên dùng kiểu dữ liệu** |
|---------------|---------------------------|
| Lưu số đếm, ID | `INT` hoặc `BIGINT` |
| Lưu số tiền, số liệu chính xác cao | `DECIMAL(M,D)` |
| Lưu nội dung văn bản ngắn | `VARCHAR(N)` |
| Lưu văn bản dài (mô tả, bài viết) | `TEXT` |
| Lưu thời gian tạo bản ghi | `TIMESTAMP` hoặc `DATETIME` |
| Lưu trạng thái (`Nam`, `Nữ`, `Khác`) | `ENUM` |
| Lưu file, ảnh | `BLOB` |

Cần giải thích thêm phần nào không? 🚀