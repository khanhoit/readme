Dưới đây là danh sách các cấu hình của Kafka kèm theo **giá trị mặc định** cho từng cấu hình, giúp bạn dễ dàng tham khảo và điều chỉnh khi cần thiết.

### 1. **Cấu hình của Kafka Broker**
Các cấu hình này thường được định nghĩa trong file `server.properties`.

#### **Các cấu hình chung của Broker:**
- **`broker.id`**:  
  - Mặc định: `0`
  - Mã định danh duy nhất cho mỗi broker trong cluster.

- **`listeners`**:  
  - Mặc định: `PLAINTEXT://0.0.0.0:9092`
  - Địa chỉ và cổng mà Kafka broker lắng nghe.

- **`advertised.listeners`**:  
  - Mặc định: `PLAINTEXT://localhost:9092`
  - Địa chỉ mà Kafka sẽ quảng bá cho các client kết nối.

- **`zookeeper.connect`**:  
  - Mặc định: `localhost:2181`
  - Địa chỉ kết nối tới Zookeeper.

- **`log.dirs`**:  
  - Mặc định: `/tmp/kafka-logs`
  - Thư mục lưu trữ logs của các topic.

- **`num.partitions`**:  
  - Mặc định: `1`
  - Số partition mặc định khi tạo topic mới.

- **`log.retention.hours`**:  
  - Mặc định: `168` (7 ngày)
  - Thời gian giữ logs trước khi Kafka xóa chúng.

- **`log.segment.bytes`**:  
  - Mặc định: `1073741824` (1GB)
  - Kích thước tối đa của mỗi log segment.

- **`message.max.bytes`**:  
  - Mặc định: `1000000` (1MB)
  - Kích thước tối đa của message Kafka có thể nhận.

- **`replica.fetch.max.bytes`**:  
  - Mặc định: `1048576` (1MB)
  - Kích thước tối đa cho mỗi fetch request từ replica.

- **`num.recovery.threads.per.data.dir`**:  
  - Mặc định: `1`
  - Số thread phục hồi logs khi broker khởi động lại.

- **`log.cleaner.enable`**:  
  - Mặc định: `true`
  - Cho phép log cleaner để xóa dữ liệu cũ.

---

#### **Cấu hình về Cluster và Partition:**
- **`default.replication.factor`**:  
  - Mặc định: `1`
  - Số lượng bản sao mặc định cho mỗi topic mới.

- **`min.insync.replicas`**:  
  - Mặc định: `1`
  - Số replica tối thiểu phải đồng bộ trước khi Kafka chấp nhận một message.

- **`unclean.leader.election.enable`**:  
  - Mặc định: `false`
  - Cho phép cuộc bầu cử leader không đồng bộ.

- **`auto.leader.rebalance.enable`**:  
  - Mặc định: `true`
  - Cho phép tự động cân bằng lại leader partitions khi có sự thay đổi.

---

#### **Cấu hình về Logging và Monitoring:**
- **`log.cleaner.backoff.ms`**:  
  - Mặc định: `15000`
  - Thời gian giãn cách giữa các lần làm sạch logs.

- **`metrics.sample.window.ms`**:  
  - Mặc định: `30000` (30 giây)
  - Thời gian mỗi cửa sổ mẫu để thống kê metrics.

- **`metric.reporters`**:  
  - Mặc định: không có.
  - Các class custom để báo cáo metrics.

---

### 2. **Cấu hình của Kafka Producer**
Các cấu hình của Producer điều chỉnh cách gửi dữ liệu vào Kafka.

- **`acks`**:  
  - Mặc định: `1`
  - Xác nhận gửi dữ liệu (0: không cần xác nhận, 1: xác nhận bởi leader, all: xác nhận bởi tất cả các replica).

- **`batch.size`**:  
  - Mặc định: `16384` (16KB)
  - Kích thước batch tối đa khi producer gửi dữ liệu.

- **`linger.ms`**:  
  - Mặc định: `0`
  - Thời gian producer chờ trước khi gửi batch.

- **`compression.type`**:  
  - Mặc định: `none`
  - Phương thức nén dữ liệu (`none`, `gzip`, `snappy`, `lz4`).

- **`buffer.memory`**:  
  - Mặc định: `33554432` (32MB)
  - Tổng bộ nhớ dành cho buffer khi producer gửi dữ liệu.

- **`key.serializer`**:  
  - Mặc định: `org.apache.kafka.common.serialization.StringSerializer`
  - Serializer cho key.

- **`value.serializer`**:  
  - Mặc định: `org.apache.kafka.common.serialization.StringSerializer`
  - Serializer cho value.

- **`max.request.size`**:  
  - Mặc định: `1048576` (1MB)
  - Kích thước tối đa của một request gửi từ producer.

- **`retries`**:  
  - Mặc định: `2147483647` (không giới hạn số lần thử lại)
  - Số lần thử lại khi gửi dữ liệu thất bại.

- **`retry.backoff.ms`**:  
  - Mặc định: `100`
  - Thời gian giãn cách giữa các lần thử lại.

---

### 3. **Cấu hình của Kafka Consumer**
Các cấu hình của Consumer quyết định cách thức tiêu thụ dữ liệu từ Kafka.

- **`group.id`**:  
  - Mặc định: không có (consumer hoạt động độc lập).
  - Mã định danh của consumer group.

- **`auto.offset.reset`**:  
  - Mặc định: `latest`
  - Hành vi khi không tìm thấy offset (`earliest`: đọc từ đầu, `latest`: đọc từ cuối).

- **`enable.auto.commit`**:  
  - Mặc định: `true`
  - Cho phép tự động commit offset.

- **`auto.commit.interval.ms`**:  
  - Mặc định: `5000` (5 giây)
  - Thời gian giữa các lần commit tự động.

- **`fetch.min.bytes`**:  
  - Mặc định: `1`
  - Số byte tối thiểu yêu cầu từ broker.

- **`fetch.max.wait.ms`**:  
  - Mặc định: `500`
  - Thời gian tối đa consumer sẽ chờ để nhận dữ liệu từ broker.

- **`max.poll.records`**:  
  - Mặc định: `500`
  - Số records tối đa mỗi lần consumer poll dữ liệu.

- **`session.timeout.ms`**:  
  - Mặc định: `10000` (10 giây)
  - Thời gian mà Kafka coi một consumer là "bị lỗi" nếu không nhận được heartbeat.

- **`heartbeat.interval.ms`**:  
  - Mặc định: `3000` (3 giây)
  - Thời gian giữa các lần gửi heartbeat tới Kafka.

- **`max.poll.interval.ms`**:  
  - Mặc định: `300000` (5 phút)
  - Thời gian tối đa giữa các lần poll trước khi Kafka đánh dấu consumer là bị lỗi.

---

### 4. **Cấu hình của Zookeeper**
Các cấu hình cho Zookeeper thường nằm trong file `zoo.cfg`.

- **`clientPort`**:  
  - Mặc định: `2181`
  - Cổng mà Zookeeper lắng nghe các kết nối từ client.

- **`dataDir`**:  
  - Mặc định: `/tmp/zookeeper`
  - Thư mục lưu trữ dữ liệu của Zookeeper.

- **`tickTime`**:  
  - Mặc định: `2000` (2 giây)
  - Thời gian cơ bản (ms) cho các timers trong Zookeeper.

- **`initLimit`**:  
  - Mặc định: `10`
  - Số tick yêu cầu để đồng bộ các server trong cluster.

- **`syncLimit`**:  
  - Mặc định: `5`
  - Thời gian tối đa giữa các lần đồng bộ giữa các server.

- **`maxClientCnxns`**:  
  - Mặc định: `60`
  - Số kết nối tối đa từ một client tới Zookeeper.

---

### 5. **Cấu hình của Kafka Connect**
Kafka Connect giúp kết nối Kafka với các hệ thống bên ngoài.

- **`tasks.max`**:  
  - Mặc định: `1`
  - Số lượng task tối đa mà connector có thể sử dụng.

- **`connector.class`**:  
  - Mặc định: không có.
  - Class của connector.

- **`key.converter`**:  
  - Mặc định: `org.apache.kafka.connect.storage.StringConverter`
  - Converter cho key.

- **`value.converter`**:  
  - Mặc định: `org.apache.kafka.connect.storage.StringConverter`
  - Converter cho value.

- **`topics`**:  
  - Mặc định: không có.
  - Danh sách topics mà connector sẽ ghi dữ liệu vào hoặc đọc từ.

- **`file.delimiter`**:  
  - Mặc định: `,`
  - Dấu phân cách khi đọc dữ liệu từ file.

---

### 6. **Các Cấu hình Khác**
- **`security.inter.broker.protocol`**:  
  - Mặc định: `PLAINTEXT`
  - Giao thức an ninh giữa các broker.

- **`ssl.keystore.location`**:  
  - Mặc định: không có.
  - Đường dẫn tới file keystore khi sử dụng SSL.

- **`sasl.mechanism`**:  
  - Mặc định: `PLAIN`
  - Cơ chế xác thực khi sử dụng SASL (PLAIN, SCRAM, GSSAPI).

- **`inter.broker.listener.name`**:  
  - Mặc định: `PLAINTEXT`
  - Giao thức mà broker sẽ sử dụng cho các kết nối nội bộ.

---

Danh sách trên bao gồm các cấu hình mặc định của Kafka, và bạn có thể điều chỉnh các giá trị này tùy theo yêu cầu của hệ thống của mình để tối ưu hóa hiệu suất và độ ổn định.