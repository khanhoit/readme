Dưới đây là một **cheat sheet đầy đủ** cho các câu lệnh trong **Linux**, bao gồm các lệnh cơ bản, quản lý tệp, quản lý hệ thống, mạng, người dùng, và nhiều lệnh khác. Đây sẽ là tài liệu tham khảo hữu ích cho các bạn làm việc với hệ điều hành Linux.

---

### **1. Quản lý Tệp và Thư Mục**

- `ls`  
  Liệt kê các tệp và thư mục trong thư mục hiện tại.

- `ls -l`  
  Liệt kê các tệp và thư mục với chi tiết (quyền, kích thước, ngày tạo).

- `ls -a`  
  Liệt kê tất cả các tệp, bao gồm các tệp ẩn.

- `ls -lh`  
  Liệt kê tệp với kích thước dễ đọc (KB, MB, GB).

- `cd <thư_mục>`  
  Di chuyển vào thư mục `<thư_mục>`.

- `cd ..`  
  Di chuyển lên thư mục cấp trên.

- `pwd`  
  Hiển thị đường dẫn đầy đủ của thư mục hiện tại.

- `mkdir <tên_thư_mục>`  
  Tạo một thư mục mới với tên `<tên_thư_mục>`.

- `rmdir <tên_thư_mục>`  
  Xóa thư mục (chỉ khi thư mục trống).

- `rm <tên_tệp>`  
  Xóa tệp `<tên_tệp>`.

- `rm -r <tên_thư_mục>`  
  Xóa thư mục và tất cả các tệp con bên trong.

- `cp <tệp_nguồn> <tệp_đích>`  
  Sao chép tệp từ `<tệp_nguồn>` sang `<tệp_đích>`.

- `mv <tệp_nguồn> <tệp_đích>`  
  Di chuyển hoặc đổi tên tệp.

- `touch <tên_tệp>`  
  Tạo tệp rỗng với tên `<tên_tệp>`.

- `cat <tên_tệp>`  
  Hiển thị nội dung của tệp.

- `more <tên_tệp>`  
  Hiển thị nội dung tệp từng trang.

- `less <tên_tệp>`  
  Hiển thị nội dung tệp và cho phép cuộn lên/xuống.

- `head <tên_tệp>`  
  Hiển thị 10 dòng đầu tiên của tệp.

- `tail <tên_tệp>`  
  Hiển thị 10 dòng cuối cùng của tệp.

- `find <thư_mục> -name <tên_tệp>`  
  Tìm tệp theo tên trong thư mục.

- `grep <chuỗi_tìm_kiếm> <tên_tệp>`  
  Tìm chuỗi trong tệp.

---

### **2. Quản lý Quy Trình**

- `ps`  
  Hiển thị các tiến trình đang chạy.

- `top`  
  Hiển thị các tiến trình đang chạy và thông tin hệ thống thời gian thực.

- `htop`  
  Hiển thị thông tin các tiến trình (có giao diện đồ họa).

- `kill <PID>`  
  Dừng tiến trình với ID tiến trình `<PID>`.

- `killall <tên_tiến_trình>`  
  Dừng tất cả các tiến trình với tên `<tên_tiến_trình>`.

- `bg`  
  Chạy tiến trình đang tạm dừng trong nền.

- `fg`  
  Chạy tiến trình trong foreground (màn hình chính).

- `jobs`  
  Hiển thị các tiến trình nền đang chạy.

---

### **3. Quản Lý Người Dùng và Quyền**

- `whoami`  
  Hiển thị tên người dùng hiện tại.

- `id`  
  Hiển thị thông tin người dùng và nhóm.

- `passwd`  
  Thay đổi mật khẩu người dùng hiện tại.

- `useradd <tên_người_dùng>`  
  Tạo người dùng mới với tên `<tên_người_dùng>`.

- `usermod`  
  Chỉnh sửa người dùng (ví dụ, thay đổi nhóm).

- `userdel <tên_người_dùng>`  
  Xóa người dùng `<tên_người_dùng>`.

- `groupadd <tên_group>`  
  Tạo nhóm mới.

- `groups <tên_người_dùng>`  
  Liệt kê các nhóm mà người dùng thuộc về.

- `chmod <quyền> <tên_tệp>`  
  Thay đổi quyền của tệp (ví dụ: `chmod 755 <tên_tệp>`).

- `chown <người_dùng>:<nhóm> <tên_tệp>`  
  Thay đổi chủ sở hữu và nhóm của tệp.

- `chgrp <nhóm> <tên_tệp>`  
  Thay đổi nhóm của tệp.

---

### **4. Quản Lý Gói Phần Mềm**

#### **Ubuntu/Debian:**

- `sudo apt update`  
  Cập nhật danh sách các gói phần mềm.

- `sudo apt upgrade`  
  Cập nhật các gói đã cài đặt.

- `sudo apt install <tên_gói>`  
  Cài đặt gói phần mềm mới.

- `sudo apt remove <tên_gói>`  
  Gỡ bỏ gói phần mềm.

- `sudo apt purge <tên_gói>`  
  Gỡ bỏ gói phần mềm và xóa cấu hình.

- `sudo apt autoremove`  
  Gỡ bỏ các gói không còn sử dụng.

#### **CentOS/RHEL:**

- `sudo yum update`  
  Cập nhật các gói phần mềm.

- `sudo yum install <tên_gói>`  
  Cài đặt gói phần mềm mới.

- `sudo yum remove <tên_gói>`  
  Gỡ bỏ gói phần mềm.

---

### **5. Quản Lý Hệ Thống**

- `df`  
  Hiển thị dung lượng ổ đĩa.

- `du`  
  Hiển thị dung lượng thư mục.

- `free`  
  Hiển thị bộ nhớ RAM và swap.

- `uptime`  
  Hiển thị thời gian hệ thống đã chạy.

- `reboot`  
  Khởi động lại hệ thống.

- `shutdown`  
  Tắt hệ thống.

- `hostname`  
  Hiển thị hoặc thay đổi tên máy tính.

- `date`  
  Hiển thị hoặc thay đổi ngày và giờ.

- `dmesg`  
  Hiển thị thông báo hệ thống (kernel messages).

---

### **6. Mạng**

- `ping <địa_chỉ>`  
  Kiểm tra kết nối mạng đến địa chỉ (IP/hostname).

- `ifconfig`  
  Hiển thị cấu hình mạng của các interface.

- `ip a`  
  Hiển thị thông tin mạng của các interface (thay thế `ifconfig`).

- `curl <URL>`  
  Truy cập URL và hiển thị phản hồi.

- `wget <URL>`  
  Tải tệp từ URL.

- `netstat`  
  Hiển thị các kết nối mạng và trạng thái cổng.

- `ssh <người_dùng>@<địa_chỉ>`  
  Kết nối đến một máy chủ qua SSH.

- `scp <tệp> <người_dùng>@<địa_chỉ>:<đường_dẫn>`  
  Sao chép tệp tới máy chủ từ xa qua SSH.

- `ftp <địa_chỉ>`  
  Kết nối đến máy chủ FTP.

---

### **7. Quản Lý Tệp Nén**

- `tar -czvf <tên_tệp.tar.gz> <thư_mục>`  
  Nén thư mục thành tệp `.tar.gz`.

- `tar -xzvf <tên_tệp.tar.gz>`  
  Giải nén tệp `.tar.gz`.

- `zip <tên_tệp.zip> <tên_tệp>`  
  Nén tệp thành `.zip`.

- `unzip <tên_tệp.zip>`  
  Giải nén tệp `.zip`.

---

### **8. Tìm Kiếm và Chỉnh Sửa Tệp**

- `find <thư_mục> -name <tên_tệp>`  
  Tìm tệp theo tên trong thư mục.

- `grep <chuỗi> <tên_tệp>`  
  Tìm chuỗi trong tệp.

- `nano <tên_tệp>`  
  Mở tệp trong trình soạn thảo văn bản `nano`.

- `vim <tên_tệp>`  
  Mở tệp trong trình soạn thảo văn bản `vim`.

- `sed`  
  Thực hiện thay thế chuỗi trong tệp.

---

### **9. Quản Lý Tài Nguyên Hệ Thống**

- `top`  
  Hiển thị các tiến trình đang chạy và các thông số hệ thống thời gian thực.

- `htop`  
  Hiển thị tiến trình và thông tin hệ thống với giao diện dễ nhìn.

- `iotop`  
  Hiển thị thông tin về I/O của tiến trình.

- `uptime`  
  Hiển thị thời gian hệ thống đã chạy và tải hệ thống.

- `lscpu`  
  Hiển thị thông tin về CPU.

- `lsblk`  
  Hiển thị thông tin về các ổ đĩa và phân vùng.

---

### **10. Các Lệnh Khác**

- `clear`  
  Dọn sạch màn hình terminal.

- `exit`  
  Thoát khỏi terminal.

- `alias`  
  Tạo alias cho các lệnh.

- `history`  
  Hiển thị lịch sử các lệnh đã thực hiện.

- `man <lệnh>`  
  Hiển thị tài liệu hướng dẫn cho lệnh.

---

Đây là một cheat sheet đầy đủ cho các lệnh Linux, giúp bạn có thể tham khảo nhanh chóng khi cần thực hiện các công việc khác nhau trên hệ điều hành này.
