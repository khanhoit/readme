Dưới đây là **cheat sheet đầy đủ** cho **Kubernetes**. Kubernetes là hệ thống mã nguồn mở giúp bạn tự động hóa việc triển khai, mở rộng và quản lý các ứng dụng containerized. Cheat sheet này bao gồm các lệnh cơ bản và nâng cao để bạn làm việc hiệu quả hơn với Kubernetes.

---

### **1. Quản lý Cluster**

- `kubectl version`  
  Kiểm tra phiên bản của `kubectl` và Kubernetes cluster.

- `kubectl cluster-info`  
  Hiển thị thông tin về cluster Kubernetes hiện tại.

- `kubectl get nodes`  
  Liệt kê tất cả các node trong cluster.

- `kubectl describe node <node_name>`  
  Hiển thị thông tin chi tiết về node cụ thể.

- `kubectl top nodes`  
  Hiển thị tài nguyên (CPU, memory) sử dụng trên các node.

- `kubectl get namespaces`  
  Liệt kê tất cả các namespaces trong cluster.

- `kubectl create namespace <namespace_name>`  
  Tạo một namespace mới.

- `kubectl delete namespace <namespace_name>`  
  Xóa một namespace.

---

### **2. Quản lý Pods**

- `kubectl get pods`  
  Liệt kê tất cả các pod trong namespace hiện tại.

- `kubectl get pods -n <namespace_name>`  
  Liệt kê các pod trong một namespace cụ thể.

- `kubectl describe pod <pod_name>`  
  Hiển thị thông tin chi tiết về pod.

- `kubectl logs <pod_name>`  
  Hiển thị log của pod.

- `kubectl logs -f <pod_name>`  
  Theo dõi log của pod theo thời gian thực.

- `kubectl logs <pod_name> -c <container_name>`  
  Hiển thị log của container trong pod.

- `kubectl exec -it <pod_name> -- <command>`  
  Chạy lệnh trong một pod (ví dụ: `kubectl exec -it <pod_name> -- /bin/bash`).

- `kubectl port-forward <pod_name> <local_port>:<remote_port>`  
  Mở một cổng để truy cập vào pod từ máy local.

- `kubectl delete pod <pod_name>`  
  Xóa pod.

- `kubectl delete pod --all`  
  Xóa tất cả các pod trong namespace hiện tại.

---

### **3. Quản lý Deployments**

- `kubectl get deployments`  
  Liệt kê tất cả các deployments trong namespace hiện tại.

- `kubectl describe deployment <deployment_name>`  
  Hiển thị chi tiết về deployment.

- `kubectl create deployment <deployment_name> --image=<image_name>`  
  Tạo một deployment mới với image được chỉ định.

- `kubectl set image deployment/<deployment_name> <container_name>=<new_image>`  
  Cập nhật image cho một container trong deployment.

- `kubectl scale deployment <deployment_name> --replicas=<replica_count>`  
  Thay đổi số lượng replica cho một deployment.

- `kubectl delete deployment <deployment_name>`  
  Xóa một deployment.

- `kubectl rollout status deployment/<deployment_name>`  
  Kiểm tra trạng thái rollout của một deployment.

- `kubectl rollout undo deployment/<deployment_name>`  
  Quay lại phiên bản trước của deployment.

- `kubectl rollout restart deployment/<deployment_name>`  
  Khởi động lại deployment.

---

### **4. Quản lý Services**

- `kubectl get services`  
  Liệt kê tất cả các service trong namespace hiện tại.

- `kubectl describe service <service_name>`  
  Hiển thị chi tiết về service.

- `kubectl expose pod <pod_name> --port=<port>`  
  Tạo service để expose một pod.

- `kubectl expose deployment <deployment_name> --port=<port> --target-port=<target_port>`  
  Tạo service để expose một deployment.

- `kubectl delete service <service_name>`  
  Xóa service.

- `kubectl port-forward service/<service_name> <local_port>:<remote_port>`  
  Forward cổng từ service đến máy local.

---

### **5. Quản lý ReplicaSets**

- `kubectl get replicasets`  
  Liệt kê tất cả các ReplicaSet trong namespace hiện tại.

- `kubectl describe replicaset <replicaset_name>`  
  Hiển thị chi tiết về ReplicaSet.

- `kubectl scale replicaset <replicaset_name> --replicas=<replica_count>`  
  Thay đổi số lượng replica cho một ReplicaSet.

- `kubectl delete replicaset <replicaset_name>`  
  Xóa ReplicaSet.

---

### **6. Quản lý StatefulSets**

- `kubectl get statefulsets`  
  Liệt kê tất cả các StatefulSet trong namespace hiện tại.

- `kubectl describe statefulset <statefulset_name>`  
  Hiển thị chi tiết về StatefulSet.

- `kubectl scale statefulset <statefulset_name> --replicas=<replica_count>`  
  Thay đổi số lượng replica cho StatefulSet.

- `kubectl delete statefulset <statefulset_name>`  
  Xóa StatefulSet.

---

### **7. Quản lý ConfigMaps và Secrets**

- `kubectl get configmaps`  
  Liệt kê tất cả các ConfigMap trong namespace hiện tại.

- `kubectl describe configmap <configmap_name>`  
  Hiển thị chi tiết về ConfigMap.

- `kubectl create configmap <configmap_name> --from-literal=<key>=<value>`  
  Tạo ConfigMap từ key-value pair.

- `kubectl delete configmap <configmap_name>`  
  Xóa ConfigMap.

- `kubectl get secrets`  
  Liệt kê tất cả các Secret trong namespace hiện tại.

- `kubectl describe secret <secret_name>`  
  Hiển thị chi tiết về Secret.

- `kubectl create secret generic <secret_name> --from-literal=<key>=<value>`  
  Tạo Secret từ key-value pair.

- `kubectl delete secret <secret_name>`  
  Xóa Secret.

---

### **8. Quản lý Volumes và Persistent Volumes**

- `kubectl get pvc`  
  Liệt kê tất cả các Persistent Volume Claim (PVC) trong namespace hiện tại.

- `kubectl describe pvc <pvc_name>`  
  Hiển thị chi tiết về PVC.

- `kubectl get pv`  
  Liệt kê tất cả các Persistent Volumes (PV).

- `kubectl describe pv <pv_name>`  
  Hiển thị chi tiết về PV.

- `kubectl apply -f <file>.yaml`  
  Áp dụng cấu hình từ một tệp YAML để tạo hoặc cập nhật các resource.

- `kubectl delete pvc <pvc_name>`  
  Xóa Persistent Volume Claim.

- `kubectl delete pv <pv_name>`  
  Xóa Persistent Volume.

---

### **9. Quản lý Namespaces**

- `kubectl get namespaces`  
  Liệt kê tất cả các namespaces.

- `kubectl create namespace <namespace_name>`  
  Tạo namespace mới.

- `kubectl delete namespace <namespace_name>`  
  Xóa namespace.

- `kubectl config set-context --current --namespace=<namespace_name>`  
  Chuyển sang làm việc trong một namespace khác.

---

### **10. Quản lý CronJobs**

- `kubectl get cronjobs`  
  Liệt kê tất cả các CronJob trong namespace hiện tại.

- `kubectl describe cronjob <cronjob_name>`  
  Hiển thị chi tiết về CronJob.

- `kubectl create cronjob <cronjob_name> --schedule="*/5 * * * *" --image=<image_name>`  
  Tạo CronJob mới.

- `kubectl delete cronjob <cronjob_name>`  
  Xóa CronJob.

---

### **11. Quản lý Hạ Tầng (Ingress)**

- `kubectl get ingress`  
  Liệt kê tất cả các Ingress.

- `kubectl describe ingress <ingress_name>`  
  Hiển thị chi tiết về Ingress.

- `kubectl apply -f <ingress_file>.yaml`  
  Áp dụng cấu hình Ingress từ tệp YAML.

---

### **12. Cấu Hình và Quản lý RBAC (Role-Based Access Control)**

- `kubectl get roles`  
  Liệt kê tất cả các role trong namespace hiện tại.

- `kubectl describe role <role_name>`  
  Hiển thị chi tiết về role.

- `kubectl create role <role_name> --verb=<verb> --resource=<resource>`  
  Tạo role mới.

- `kubectl get rolebindings`  
  Liệt kê tất cả các rolebinding trong namespace hiện tại.

- `kubectl describe rolebinding <rolebinding_name>`  
  Hiển thị chi tiết về rolebinding.

- `kubectl create rolebinding <rolebinding_name> --role=<role_name> --user=<username>`  
  Tạo rolebinding mới.

---

### **13. Khắc phục sự cố**

- `kubectl describe <resource> <resource_name>`  
  Xem thông tin chi tiết về resource để kiểm tra lỗi.

- `kubectl logs <pod_name>`  
  Xem log của pod để xác định lỗi.

- `kubectl get events`  
  Hiển thị các sự kiện của Kubernetes để giúp khắc phục sự cố.

- `kubectl top pods`  
  Xem tài nguyên sử dụng của các pod.

- `kubectl get all`  
  Liệt kê tất cả các resource trong namespace hiện tại.

---

### **14. Quản lý Context và Kubeconfig**

- `kubectl config view`  
  Xem nội dung của kubeconfig.

- `kubectl config get-contexts`  
  Liệt kê tất cả các context trong kubeconfig.

- `kubectl config use-context <context_name>`  
  Chuyển sang context khác.

---

### **15. Quản lý Helm (Package Manager)**

- `helm list`  
  Liệt kê tất cả các release được quản lý bởi Helm.

- `helm install <release_name> <chart_name>`  
  Cài đặt một Helm chart.

- `helm upgrade <release_name> <chart_name>`  
  Cập nhật một release của Helm.

- `helm uninstall <release_name>`  
  Gỡ bỏ một release.

---

Đây là **cheat sheet Kubernetes** đầy đủ giúp bạn quản lý và triển khai ứng dụng trên Kubernetes một cách hiệu quả.
