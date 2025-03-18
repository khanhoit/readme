Dưới đây là **cheat sheet đầy đủ** cho các câu lệnh **Docker**. Docker giúp bạn tạo, triển khai và quản lý các ứng dụng container. Đây là tài liệu tham khảo giúp bạn làm việc hiệu quả hơn với Docker.

---

### **1. Quản lý Docker (Khởi động, Dừng và Kiểm tra)**

- `docker --version`  
  Kiểm tra phiên bản Docker hiện tại.

- `docker info`  
  Hiển thị thông tin chi tiết về Docker daemon.

- `docker version`  
  Kiểm tra thông tin về phiên bản của Docker client và Docker server.

- `docker run <options> <image>`  
  Chạy một container từ một image.

- `docker ps`  
  Hiển thị các container đang chạy.

- `docker ps -a`  
  Hiển thị tất cả các container (đang chạy và đã dừng).

- `docker start <container_id>`  
  Khởi động container từ một container ID hoặc tên.

- `docker stop <container_id>`  
  Dừng container.

- `docker restart <container_id>`  
  Khởi động lại container.

- `docker pause <container_id>`  
  Tạm dừng container.

- `docker unpause <container_id>`  
  Tiếp tục container đã tạm dừng.

- `docker kill <container_id>`  
  Dừng container ngay lập tức.

- `docker rm <container_id>`  
  Xóa container (nếu container đã dừng).

- `docker rm $(docker ps -a -q)`  
  Xóa tất cả các container đã dừng.

---

### **2. Quản lý Images (Ảnh Docker)**

- `docker images`  
  Hiển thị tất cả các images có sẵn trên máy.

- `docker pull <image_name>`  
  Tải image từ Docker Hub hoặc registry.

- `docker build <options> <path>`  
  Xây dựng một image từ Dockerfile trong thư mục `<path>`.

- `docker tag <image_id> <new_image_name>`  
  Gắn nhãn cho image với một tên mới.

- `docker rmi <image_id>`  
  Xóa image.

- `docker rmi $(docker images -q)`  
  Xóa tất cả các image không còn được sử dụng.

- `docker history <image_name>`  
  Xem lịch sử của một image.

---

### **3. Quản lý Container (Xem và Thao Tác với Containers)**

- `docker exec -it <container_id> /bin/bash`  
  Chạy shell tương tác (bash) trong một container đang chạy.

- `docker exec -it <container_id> <command>`  
  Thực thi một lệnh trong một container đang chạy.

- `docker attach <container_id>`  
  Kết nối đến một container đang chạy (với chế độ tương tác).

- `docker logs <container_id>`  
  Xem log của container.

- `docker stats`  
  Hiển thị thông tin thống kê thời gian thực về CPU, bộ nhớ, I/O của các container.

- `docker top <container_id>`  
  Hiển thị các tiến trình đang chạy trong một container.

- `docker inspect <container_id>`  
  Hiển thị chi tiết thông tin của container (dưới dạng JSON).

- `docker exec <container_id> <command>`  
  Chạy lệnh trong một container đang chạy.

---

### **4. Quản lý Mạng (Networks)**

- `docker network ls`  
  Liệt kê tất cả các network Docker.

- `docker network inspect <network_name>`  
  Hiển thị chi tiết thông tin của một network.

- `docker network create <network_name>`  
  Tạo một network mới.

- `docker network rm <network_name>`  
  Xóa network.

- `docker run --network <network_name> <image_name>`  
  Chạy một container và kết nối vào network cụ thể.

---

### **5. Quản lý Volume (Lưu trữ)**

- `docker volume ls`  
  Liệt kê tất cả các volume.

- `docker volume inspect <volume_name>`  
  Xem chi tiết của một volume.

- `docker volume create <volume_name>`  
  Tạo một volume mới.

- `docker volume rm <volume_name>`  
  Xóa volume.

- `docker run -v <volume_name>:<mount_path> <image_name>`  
  Mount volume vào container khi chạy.

- `docker run -v <host_path>:<container_path>`  
  Mount thư mục hoặc tệp từ host vào container.

---

### **6. Quản lý Docker Compose**

- `docker-compose --version`  
  Kiểm tra phiên bản Docker Compose.

- `docker-compose up`  
  Khởi động các container theo cấu hình trong file `docker-compose.yml`.

- `docker-compose up -d`  
  Khởi động các container trong chế độ nền (detached).

- `docker-compose down`  
  Dừng và xóa tất cả các container, mạng và volumes được tạo bởi `docker-compose up`.

- `docker-compose ps`  
  Liệt kê tất cả các container của Docker Compose.

- `docker-compose logs`  
  Xem logs của các container trong Docker Compose.

- `docker-compose exec <service_name> /bin/bash`  
  Mở một terminal tương tác trong một service của Docker Compose.

---

### **7. Quản lý Docker Registry**

- `docker login <registry_url>`  
  Đăng nhập vào Docker registry.

- `docker logout <registry_url>`  
  Đăng xuất khỏi Docker registry.

- `docker push <image_name>`  
  Đẩy image lên Docker registry (Docker Hub hoặc custom registry).

- `docker pull <image_name>`  
  Tải image từ Docker registry.

---

### **8. Quản lý Docker Daemon**

- `sudo systemctl start docker`  
  Khởi động Docker daemon.

- `sudo systemctl stop docker`  
  Dừng Docker daemon.

- `sudo systemctl restart docker`  
  Khởi động lại Docker daemon.

- `sudo systemctl enable docker`  
  Kích hoạt Docker daemon khởi động cùng hệ thống.

- `sudo systemctl disable docker`  
  Vô hiệu hóa Docker daemon khỏi quá trình khởi động cùng hệ thống.

---

### **9. Quản lý Docker Logs và Xử Lý Sự Cố**

- `docker logs <container_id>`  
  Xem log của một container.

- `docker logs -f <container_id>`  
  Theo dõi log theo thời gian thực.

- `docker logs --tail 100 <container_id>`  
  Xem 100 dòng cuối cùng của log.

- `docker logs --since 10m <container_id>`  
  Xem log từ 10 phút trước.

- `docker system df`  
  Xem dung lượng sử dụng bởi images, containers, volumes, và build cache.

- `docker system prune`  
  Dọn dẹp Docker (xóa container dừng, image không sử dụng, volumes không sử dụng).

- `docker system prune -a`  
  Dọn dẹp tất cả các container, image không sử dụng, mạng và volume.

---

### **10. Quản lý Docker trên Cloud**

- **AWS (Elastic Container Service)**  
  `docker` có thể được sử dụng để tương tác với Amazon ECS (Elastic Container Service). Bạn sẽ cần cấu hình AWS CLI và sử dụng các lệnh như `aws ecs` để quản lý containers trên AWS.

- **Azure Container Instances**  
  Trên Azure, bạn có thể sử dụng Docker để quản lý container và triển khai các dịch vụ container qua Azure CLI.

- **Google Cloud Platform (GKE)**  
  Docker có thể được sử dụng trên Google Kubernetes Engine (GKE) để triển khai và quản lý container trong môi trường Kubernetes.

---

### **11. Các Lệnh Docker Khác**

- `docker exec -it <container_id> sh`  
  Truy cập vào container và sử dụng shell `sh` thay vì `bash` (đặc biệt khi `bash` không có sẵn).

- `docker cp <container_id>:<path> <host_path>`  
  Sao chép tệp từ container vào hệ thống host.

- `docker cp <host_path> <container_id>:<path>`  
  Sao chép tệp từ hệ thống host vào container.

---

Đây là **cheat sheet Docker** đầy đủ, bao gồm các lệnh cơ bản và nâng cao, giúp bạn quản lý và làm việc với containers, images, volumes, và Docker Compose dễ dàng hơn.
