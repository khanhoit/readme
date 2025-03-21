# Kubernetes Components

Kubernetes (K8s) là một hệ thống quản lý container phổ biến giúp tự động hóa việc triển khai, mở rộng và quản lý các ứng dụng. Dưới đây là các thành phần chính của Kubernetes.

---

## 1️⃣ Control Plane (Mặt phẳng điều khiển)
Control Plane quản lý toàn bộ cluster, xử lý việc lập lịch và điều phối tài nguyên.

### 📌 API Server (`kube-apiserver`)
- Cung cấp giao diện RESTful API để giao tiếp với Kubernetes.
- Nhận yêu cầu từ `kubectl`, Dashboard hoặc các hệ thống khác.

### 📌 Controller Manager (`kube-controller-manager`)
- Chạy các controller để giám sát và phản ứng với thay đổi trong cluster.
- Một số controller quan trọng:
  - **Node Controller**: Giám sát trạng thái các node.
  - **Replication Controller**: Quản lý số lượng Pod theo mong muốn.
  - **Endpoints Controller**: Kết nối Pod với Service.

### 📌 Scheduler (`kube-scheduler`)
- Chọn **Node phù hợp** để chạy Pod dựa trên tài nguyên, ràng buộc và chính sách.

### 📌 etcd
- Lưu trữ dữ liệu trạng thái của cluster dưới dạng **key-value**.
- Là cơ sở dữ liệu quan trọng của Kubernetes.

---

## 2️⃣ Node Components (Thành phần của nút)
Mỗi **Node** trong cluster có các thành phần giúp chạy ứng dụng.

### 📌 Kubelet
- Thành phần chính trên mỗi node, nhận lệnh từ API Server.
- Quản lý vòng đời của Pod và container.

### 📌 Kube Proxy
- Điều khiển lưu lượng mạng giữa các Pod và Service.

### 📌 Container Runtime
- Chạy container trong Pod.  
- Hỗ trợ nhiều trình chạy container như **Docker, containerd, CRI-O**.

---

## 3️⃣ Add-ons (Thành phần bổ sung)
Các thành phần giúp mở rộng và hỗ trợ Kubernetes.

### 📌 CoreDNS
- Cung cấp dịch vụ **DNS nội bộ** trong cluster.

### 📌 Ingress Controller
- Quản lý truy cập từ bên ngoài vào các dịch vụ trong cluster.

### 📌 Monitoring & Logging
- Giám sát và ghi log sử dụng **Prometheus, Grafana, ELK Stack**.

---

## 📌 Tóm tắt
| Thành phần | Chức năng |
|------------|----------|
| **API Server** | Cung cấp API để quản lý cluster |
| **Controller Manager** | Giám sát và điều khiển trạng thái cluster |
| **Scheduler** | Lập lịch và gán Pod vào Node |
| **etcd** | Lưu trữ dữ liệu cluster |
| **Kubelet** | Quản lý Pod trên mỗi Node |
| **Kube Proxy** | Điều phối mạng giữa các Pod |
| **Container Runtime** | Chạy container (Docker, containerd, CRI-O) |
| **CoreDNS** | Cung cấp DNS nội bộ |
| **Ingress Controller** | Quản lý truy cập từ ngoài vào cluster |
| **Monitoring & Logging** | Giám sát và ghi log hệ thống |

🚀 **Kubernetes giúp triển khai, mở rộng và quản lý ứng dụng container một cách tự động!**
