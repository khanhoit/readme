# Kubernetes API Versions

## Giới thiệu
Kubernetes cung cấp nhiều phiên bản API (`apiVersion`) để quản lý các tài nguyên (`kind`) khác nhau trong hệ thống. Dưới đây là danh sách các API phổ biến cùng với các loại tài nguyên đi kèm.

---

## 1. API Core (`v1`)
- **apiVersion**: `v1`
- **Các tài nguyên (kind) chính**:
  - `Pod` - Đơn vị triển khai nhỏ nhất trong Kubernetes, chứa một hoặc nhiều container.
  - `Service` - Cung cấp kết nối mạng ổn định giữa các Pod.
  - `ConfigMap` - Lưu trữ dữ liệu cấu hình không bảo mật.
  - `Secret` - Lưu trữ dữ liệu nhạy cảm như mật khẩu, khóa API.
  - `PersistentVolume (PV)` - Quản lý lưu trữ dữ liệu lâu dài.
  - `PersistentVolumeClaim (PVC)` - Yêu cầu sử dụng lưu trữ từ PV.
  - `Namespace` - Phân chia không gian quản lý tài nguyên trong cluster.
  - `Node` - Đại diện cho một máy chủ trong cluster.
  - `ResourceQuota` - Giới hạn tài nguyên sử dụng trong một Namespace.
  - `LimitRange` - Giới hạn tài nguyên cho từng Pod hoặc Container.
  - `ReplicationController` - Đảm bảo số lượng Pod chạy đúng theo yêu cầu.
  - `ServiceAccount` - Tài khoản dịch vụ cho các ứng dụng chạy trong cluster.
  - `Endpoints` - Lưu thông tin kết nối của Service.

---

## 2. Workloads API (`apps/v1`)
- **apiVersion**: `apps/v1`
- **Các tài nguyên (kind) chính**:
  - `Deployment` - Quản lý và cập nhật phiên bản ứng dụng tự động.
  - `StatefulSet` - Quản lý các ứng dụng có trạng thái như database.
  - `DaemonSet` - Đảm bảo mỗi Node chạy một bản sao của Pod.
  - `ReplicaSet` - Đảm bảo số lượng bản sao của Pod.
  - `ControllerRevision` - Lưu trữ lịch sử thay đổi của StatefulSet.

---

## 3. Batch API (`batch/v1`)
- **apiVersion**: `batch/v1`
- **Các tài nguyên (kind) chính**:
  - `Job` - Chạy một tác vụ ngắn hạn và kết thúc sau khi hoàn thành.
  - `CronJob` - Chạy Job theo lịch trình định sẵn.

---

## 4. AutoScaling API (`autoscaling/v2`)
- **apiVersion**: `autoscaling/v2`
- **Các tài nguyên (kind) chính**:
  - `HorizontalPodAutoscaler (HPA)` - Tự động tăng hoặc giảm số lượng Pod dựa trên tài nguyên sử dụng.

---

## 5. Network Policy & Security
### 5.1 Network Policy (`networking.k8s.io/v1`)
- **apiVersion**: `networking.k8s.io/v1`
- **Tài nguyên**:
  - `NetworkPolicy` - Quy tắc kiểm soát lưu lượng mạng giữa các Pod.

### 5.2 Pod Security Policy (Deprecated) (`policy/v1beta1`)
- **apiVersion**: `policy/v1beta1`
- **Tài nguyên**:
  - `PodSecurityPolicy` - Xác định các quyền và hạn chế bảo mật cho Pod (đã bị loại bỏ từ Kubernetes 1.25).

---

## 6. Storage API (`storage.k8s.io/v1`)
- **apiVersion**: `storage.k8s.io/v1`
- **Tài nguyên**:
  - `StorageClass` - Xác định loại lưu trữ động.
  - `CSIDriver` - Giao diện lưu trữ Container Storage Interface (CSI).
  - `CSINode` - Đại diện cho Node sử dụng CSI.
  - `VolumeAttachment` - Liên kết volume với Node.

---

## 7. Role-based Access Control (RBAC) (`rbac.authorization.k8s.io/v1`)
- **apiVersion**: `rbac.authorization.k8s.io/v1`
- **Tài nguyên**:
  - `Role` - Định nghĩa quyền trong một Namespace.
  - `RoleBinding` - Gán quyền Role cho người dùng hoặc nhóm.
  - `ClusterRole` - Giống Role nhưng có phạm vi toàn cluster.
  - `ClusterRoleBinding` - Gán quyền ClusterRole trên toàn bộ cluster.

---

## 8. Admission Controllers
- **apiVersion**: `admissionregistration.k8s.io/v1`
- **Tài nguyên**:
  - `MutatingWebhookConfiguration` - Điều chỉnh tài nguyên trước khi lưu vào etcd.
  - `ValidatingWebhookConfiguration` - Kiểm tra tài nguyên trước khi lưu vào etcd.

---

## 9. Custom Resources API (`apiextensions.k8s.io/v1`)
- **apiVersion**: `apiextensions.k8s.io/v1`
- **Tài nguyên**:
  - `CustomResourceDefinition (CRD)` - Cho phép mở rộng Kubernetes bằng các tài nguyên tùy chỉnh.

---

## 10. Metrics & Events API
### 10.1 Metrics (`metrics.k8s.io/v1beta1`)
- **apiVersion**: `metrics.k8s.io/v1beta1`
- **Tài nguyên**:
  - `NodeMetrics` - Thu thập dữ liệu sử dụng tài nguyên của Node.
  - `PodMetrics` - Thu thập dữ liệu sử dụng tài nguyên của Pod.

### 10.2 Events (`events.k8s.io/v1`)
- **apiVersion**: `events.k8s.io/v1`
- **Tài nguyên**:
  - `Event` - Lưu trữ các sự kiện xảy ra trong cluster.

---

## 11. Ingress API (`networking.k8s.io/v1`)
- **apiVersion**: `networking.k8s.io/v1`
- **Tài nguyên**:
  - `Ingress` - Định tuyến HTTP(S) từ bên ngoài vào cluster.
  - `IngressClass` - Xác định loại Ingress Controller sử dụng.

---

## 12. Scheduling API (`scheduling.k8s.io/v1`)
- **apiVersion**: `scheduling.k8s.io/v1`
- **Tài nguyên**:
  - `PriorityClass` - Xác định mức độ ưu tiên của Pod.

---

## 🔹 Ghi chú
- Một số API có thể bị **thay đổi hoặc deprecated** theo từng phiên bản Kubernetes.
- Để kiểm tra phiên bản API trong cluster của bạn, có thể dùng lệnh:
  ```sh
  kubectl api-versions
  ```
- Nếu muốn biết thông tin chi tiết của một tài nguyên:
  ```sh
  kubectl explain <kind> --api-version=<apiVersion>
  ```

