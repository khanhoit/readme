### **Kiến trúc của JDK, JRE, JVM**  

#### 🔹 **1. Kiến trúc của JVM (Java Virtual Machine)**
JVM là thành phần quan trọng nhất trong Java, nó đảm bảo Java có thể chạy trên nhiều nền tảng khác nhau. JVM có 3 phần chính:

1. **Class Loader** (Bộ nạp lớp)  
   - Nạp các file `.class` (bytecode) vào bộ nhớ.  
   - Kiểm tra tính hợp lệ của bytecode trước khi chạy.  
   - Có 3 loại Class Loader:  
     - **Bootstrap ClassLoader** (nạp các thư viện lõi của Java)  
     - **Extension ClassLoader** (nạp các thư viện mở rộng từ `lib/ext/`)  
     - **Application ClassLoader** (nạp các class từ ứng dụng).  

2. **Runtime Data Areas** (Vùng dữ liệu runtime)  
   - Chứa các khu vực bộ nhớ được JVM sử dụng:  
     - **Method Area**: Chứa thông tin về class, method, field.  
     - **Heap**: Chứa các object, quản lý bởi **Garbage Collector**.  
     - **Stack**: Mỗi thread có một Java Stack để chứa các frame (biến local, tham số).  
     - **PC Register**: Lưu trữ địa chỉ của lệnh bytecode đang thực thi.  
     - **Native Method Stack**: Dùng khi gọi các phương thức native (không phải Java).  

3. **Execution Engine** (Bộ máy thực thi)  
   - **Interpreter**: Dịch bytecode thành mã máy nhưng chậm.  
   - **JIT Compiler (Just-In-Time)**: Tăng tốc bằng cách biên dịch thành mã máy một lần.  
   - **Garbage Collector**: Tự động thu hồi bộ nhớ không sử dụng.  

4. **Native Interface (JNI - Java Native Interface)**  
   - Cho phép Java gọi các thư viện native như C, C++.  

---

#### 🔹 **2. Kiến trúc của JRE (Java Runtime Environment)**
JRE là tập hợp các thành phần cần thiết để chạy ứng dụng Java. JRE **chứa JVM** và các thư viện runtime:

- **JVM**: Máy ảo Java (như đã mô tả ở trên).  
- **Core Libraries**: Các thư viện cần thiết (`java.lang, java.util, java.io, java.sql`...).  
- **Supporting Files**: Các file cấu hình, tài nguyên hệ thống.  

JRE **không bao gồm trình biên dịch (javac)**, vì vậy nó chỉ có thể chạy ứng dụng, không thể biên dịch.

---

#### 🔹 **3. Kiến trúc của JDK (Java Development Kit)**
JDK là bộ công cụ phát triển đầy đủ, bao gồm **JRE + công cụ phát triển**:

- **JRE**: Chứa JVM + Thư viện Java.  
- **Development Tools**:
  - **javac** (Java Compiler): Dịch `.java` thành `.class`.  
  - **jar** (Java Archive): Đóng gói các file `.class` thành `.jar`.  
  - **jdb** (Java Debugger): Công cụ debug.  
  - **javadoc**: Tạo tài liệu API từ comment JavaDoc.  
  - **jshell**: Chạy thử code Java mà không cần tạo class.  

---

### **📌 Tóm tắt mối quan hệ:**
- **JDK** ⊃ **JRE** ⊃ **JVM**.  
- **JDK** = **JRE + Công cụ phát triển**.  
- **JRE** = **JVM + Thư viện Java**.  
- **JVM** thực thi bytecode `.class` trên từng hệ điều hành khác nhau.  

Bạn có đang muốn tối ưu hiệu suất JVM hay cần hiểu sâu để debug ứng dụng? 😊


# **Tìm Hiểu Về JVM (Java Virtual Machine)**

## **1. JVM Là Gì?**
JVM (Java Virtual Machine) là một máy ảo thực thi mã bytecode Java, cung cấp môi trường runtime để chạy các ứng dụng Java. JVM giúp Java đạt được tính **"Write Once, Run Anywhere"** (viết một lần, chạy mọi nơi) vì nó hoạt động độc lập với phần cứng và hệ điều hành.

### **Vai Trò Của JVM**
- **Thực thi mã bytecode** (`.class` file)
- **Quản lý bộ nhớ** (Heap, Stack, Method Area)
- **Cung cấp tính bảo mật** (Sandboxing, Class Verification)
- **Tối ưu hiệu suất** (JIT Compilation, Garbage Collection)

---

## **2. Kiến Trúc JVM**
JVM gồm 3 thành phần chính:

### **a. Class Loader**
- **Tải class file** vào bộ nhớ khi cần thiết.
- **3 loại Class Loader:**
  1. **Bootstrap ClassLoader**: Tải các thư viện core Java (`rt.jar`, `java.lang`, `java.util`).
  2. **Extension ClassLoader**: Tải các thư viện mở rộng (`javax`, `jre/lib/ext`).
  3. **Application ClassLoader**: Tải các class từ `CLASSPATH` của ứng dụng.

### **b. Runtime Data Areas (Vùng Nhớ JVM)**
| Vùng Nhớ | Mô Tả |
|----------|-------|
| **Method Area** | Lưu trữ metadata của class, static variables, constant pool. |
| **Heap** | Chứa tất cả đối tượng (Objects), là nơi **Garbage Collection (GC)** hoạt động. |
| **Stack** | Mỗi thread có một stack riêng, lưu biến local và method calls (LIFO). |
| **PC Register** | Lưu địa chỉ lệnh hiện tại đang thực thi cho từng thread. |
| **Native Method Stack** | Hỗ trợ thực thi native code (viết bằng C/C++). |

### **c. Execution Engine**
- **Interpreter**: Đọc và thực thi từng dòng bytecode (chậm).
- **JIT Compiler (Just-In-Time)**: Tối ưu bằng cách biên dịch bytecode thành native code (nhanh hơn).
- **Garbage Collector (GC)**: Tự động thu hồi bộ nhớ không dùng (Heap).

---

## **3. Quá Trình Thực Thi Một Chương Trình Java**
1. **Biên dịch mã nguồn (`*.java`)** → **Bytecode (`*.class`)** (bằng `javac`).
2. **Class Loader** tải `.class` vào **Method Area**.
3. **Execution Engine** thực thi bytecode:
   - **Interpreter** chạy từng lệnh.
   - **JIT Compiler** tối ưu các đoạn code thường dùng.
4. **Runtime Data Areas** cấp phát bộ nhớ (Heap, Stack).
5. **Garbage Collector** dọn dẹp bộ nhớ khi cần.

---

## **4. JVM vs JDK vs JRE**
| Thành Phần | Mô Tả |
|------------|-------|
| **JVM (Java Virtual Machine)** | Máy ảo thực thi bytecode, quản lý bộ nhớ. |
| **JRE (Java Runtime Environment)** | Bao gồm JVM + thư viện cần thiết để **chạy** ứng dụng Java. |
| **JDK (Java Development Kit)** | Bao gồm JRE + công cụ phát triển (`javac`, `javadoc`, debugger). |

---

## **5. Các Phiên Bản JVM**
- **HotSpot JVM** (Oracle, phổ biến nhất)
- **OpenJ9** (IBM, tiết kiệm bộ nhớ)
- **GraalVM** (Hỗ trợ đa ngôn ngữ, Native Image)
- **Zing** (Azul Systems, GC tốt cho ứng dụng real-time)

---

## **6. Các Lệnh Quản Lý JVM**
| Lệnh | Mô Tả |
|------|-------|
| `java -version` | Kiểm tra phiên bản JVM |
| `java -Xms256m -Xmx1024m MyApp` | Cấu hình kích thước Heap |
| `jps` | Liệt kê các Java process đang chạy |
| `jstat -gc <pid>` | Theo dõi GC |
| `jmap -heap <pid>` | Xem thông tin Heap |
| `jconsole` | Giám sát JVM bằng GUI |

---

## **7. Tối Ưu JVM**
- **Cấu hình Heap**: `-Xms` (khởi tạo), `-Xmx` (tối đa).
- **Chọn GC phù hợp**:
  - **Serial GC** (ứng dụng nhỏ)
  - **Parallel GC** (tốc độ xử lý)
  - **G1 GC** (cân bằng)
  - **ZGC/Shenandoah** (low latency)
- **JIT Tuning**: `-XX:+AggressiveOpts` (bật tối ưu hóa)

---

## **Kết Luận**
JVM là trái tim của nền tảng Java, giúp chạy ứng dụng độc lập với hệ điều hành. Hiểu rõ JVM giúp:
- **Tối ưu hiệu suất** (GC, JIT)
- **Debug memory leak** (Heap, Stack)
- **Lựa chọn JVM phù hợp** (HotSpot, OpenJ9, GraalVM)

Bạn có thể dùng các công cụ như **VisualVM, JConsole, JProfiler** để phân tích JVM trong thực tế. 🚀



Dưới đây là sơ đồ kiến trúc của **JVM**, mô tả các thành phần chính và cách chúng tương tác trong quá trình thực thi chương trình Java.  


------
<br>
<br>

### 🔹 **1. Kiến trúc tổng thể của JVM**
```plaintext
----------------------------------------------------
|                  Java Application               |
----------------------------------------------------
|          Java Standard Libraries (JRE)         |
----------------------------------------------------
|      Java Virtual Machine (JVM)                |
|  --------------------------------------------  |
|  |  Class Loader (Nạp lớp)                   |  |
|  --------------------------------------------  |
|  |  Runtime Data Areas                       |  |
|  |  - Method Area (Thông tin class)         |  |
|  |  - Heap (Đối tượng, GC)                  |  |
|  |  - Stack (Frame cho từng method)         |  |
|  |  - PC Register (Địa chỉ lệnh hiện tại)   |  |
|  |  - Native Stack (Hàm native)             |  |
|  --------------------------------------------  |
|  |  Execution Engine                         |  |
|  |  - Interpreter (Dịch từng lệnh)          |  |
|  |  - JIT Compiler (Tối ưu mã)              |  |
|  |  - Garbage Collector (Quản lý bộ nhớ)    |  |
|  --------------------------------------------  |
|  |  Native Method Interface & Libraries     |  |
|  --------------------------------------------  |
----------------------------------------------------
|            Underlying Operating System        |
----------------------------------------------------
```

---

### 🔹 **2. Sơ đồ chi tiết của JVM**
Sơ đồ này minh họa quá trình **nạp, thực thi, và quản lý bộ nhớ** trong JVM:

```plaintext
+-------------------------+
|    Java Source Code     |  <-- Viết mã nguồn (.java)
+-------------------------+
             |
             V
+-------------------------+
|    Java Compiler (Javac)|  <-- Biên dịch mã nguồn thành bytecode (.class)
+-------------------------+
             |
             V
+-------------------------+
|      Class Loader       |  <-- Nạp class vào bộ nhớ
+-------------------------+
             |
             V
+-------------------------------------+
|        Runtime Data Areas           |
|-------------------------------------|
|  Method Area  |  Heap Memory        |  <-- Chứa thông tin class, object
|-------------- |---------------------|
|  Stack Memory |  PC Register        |  <-- Quản lý ngăn xếp cho mỗi thread
|-------------- |---------------------|
|  Native Stack|                      |
+-------------------------------------+
             |
             V
+-------------------------+
|    Execution Engine     |  <-- Thực thi bytecode
|-------------------------|
|  Interpreter            |  <-- Dịch từng dòng bytecode
|  JIT Compiler           |  <-- Tối ưu bytecode thành mã máy
|  Garbage Collector      |  <-- Quản lý bộ nhớ
+-------------------------+
             |
             V
+-------------------------+
|     Native Libraries    |  <-- Gọi thư viện C/C++
+-------------------------+
```

---

### 🔹 **3. Mô hình quản lý bộ nhớ trong JVM**
Quản lý bộ nhớ trong JVM gồm các vùng chính:

```plaintext
+-------------------------------+
|        Heap Memory            |  <-- Chứa tất cả đối tượng Java
|  --------------------------   |
|  | Young Generation      |   |  <-- Chứa đối tượng mới sử dụng Minor GC
|  | - Eden Space         |   |
|  | - Survivor S0, S1    |   |
|  ----------------------  |   |
|  | Old Generation (Tenured) |  <-- Chứa đối tượng lâu dài sử dụng Major GC (Full GC)
|  --------------------------  |
|  | Metaspace (Java 8+)  |   |  <-- Thay thế PermGen, lưu metadata class
|  --------------------------  |
+-------------------------------+

+-------------------------------+
|     Stack Memory (per thread) |
|  --------------------------   |
|  | Stack Frame 1          |   |
|  | Stack Frame 2          |   |
|  --------------------------  |
+-------------------------------+

+-------------------------------+
|       PC Register             |  <-- Lưu lệnh bytecode hiện tại
+-------------------------------+

+-------------------------------+
|       Native Method Stack      |  <-- Dùng cho JNI (Java Native Interface)
+-------------------------------+
```

🔥 **Tóm lại**:
- **Heap** chứa tất cả các object.
- **Stack** chứa thông tin thực thi từng thread.
- **Method Area** chứa metadata class.
- **PC Register** lưu lệnh hiện tại.
- **Garbage Collector (GC)** tự động dọn dẹp bộ nhớ.


## **🚀 Các tham số cấu hình JVM quan trọng**  

Khi chạy ứng dụng Java, bạn có thể **tinh chỉnh hiệu suất JVM** bằng cách sử dụng các **tham số dòng lệnh** (`-XX`, `-Xms`, `-Xmx`, `-D`, `-server`, v.v.).  

-----
<br>
<br>

Dưới đây là danh sách **các tham số JVM quan trọng** giúp tối ưu bộ nhớ, GC, hiệu suất và giám sát ứng dụng.  

---

# **1️⃣ Cấu hình Heap Memory**
Heap Memory lưu trữ tất cả **object** trong ứng dụng Java, và có thể được điều chỉnh bằng các tham số sau:  

| **Tham số** | **Ý nghĩa** | **Ví dụ** |
|------------|------------|-----------|
| `-Xms<size>` | Đặt kích thước **tối thiểu** của Heap Memory | `-Xms512m` (512MB) |
| `-Xmx<size>` | Đặt kích thước **tối đa** của Heap Memory | `-Xmx4g` (4GB) |
| `-XX:NewRatio=<n>` | Tỷ lệ giữa Old Generation / Young Generation | `-XX:NewRatio=2` (Old = 2x Young) |
| `-XX:SurvivorRatio=<n>` | Tỷ lệ giữa Eden và Survivor trong Young Gen | `-XX:SurvivorRatio=8` |
| `-XX:MaxMetaspaceSize=<size>` | Giới hạn kích thước tối đa của Metaspace (Java 8+) | `-XX:MaxMetaspaceSize=256m` |

📌 **Ví dụ cài đặt Heap Memory:**  
```sh
java -Xms512m -Xmx2g -XX:NewRatio=2 -XX:SurvivorRatio=8 -jar app.jar
```

---

# **2️⃣ Cấu hình Garbage Collector (GC)**
JVM hỗ trợ nhiều loại GC, bạn có thể bật/tắt bằng tham số sau:  

| **Tham số** | **Ý nghĩa** | **Ví dụ** |
|------------|------------|-----------|
| `-XX:+UseSerialGC` | Dùng **Serial GC** (phù hợp ứng dụng nhỏ) | `java -XX:+UseSerialGC -jar app.jar` |
| `-XX:+UseParallelGC` | Dùng **Parallel GC** (tối ưu hiệu suất đa nhân) | `java -XX:+UseParallelGC -jar app.jar` |
| `-XX:+UseG1GC` | Dùng **G1 GC** (tối ưu hiệu suất & độ trễ thấp) | `java -XX:+UseG1GC -jar app.jar` |
| `-XX:+UseZGC` | Dùng **ZGC (Zero Latency GC)** | `java -XX:+UseZGC -jar app.jar` |
| `-XX:MaxGCPauseMillis=<ms>` | Giới hạn thời gian GC tối đa | `-XX:MaxGCPauseMillis=200` |
| `-XX:+PrintGCDetails` | Hiển thị log chi tiết của GC | `java -XX:+PrintGCDetails -jar app.jar` |
| `-XX:+PrintGCDateStamps` | In timestamp mỗi lần GC chạy | `-XX:+PrintGCDateStamps` |
| `-Xlog:gc` | Ghi log của GC vào file | `-Xlog:gc:file=gc.log` |

📌 **Ví dụ bật G1 GC và giới hạn GC pause time:**  
```sh
java -XX:+UseG1GC -XX:MaxGCPauseMillis=200 -Xlog:gc -jar app.jar
```

---

# **3️⃣ Cấu hình Thread & CPU**
Các tham số này giúp **tối ưu hiệu suất đa luồng**:  

| **Tham số** | **Ý nghĩa** | **Ví dụ** |
|------------|------------|-----------|
| `-XX:ParallelGCThreads=<n>` | Số luồng GC chạy song song | `-XX:ParallelGCThreads=4` |
| `-XX:ConcGCThreads=<n>` | Số luồng GC chạy nền trong G1 GC | `-XX:ConcGCThreads=2` |
| `-XX:ActiveProcessorCount=<n>` | Giới hạn số CPU sử dụng | `-XX:ActiveProcessorCount=4` |
| `-Djava.util.concurrent.ForkJoinPool.common.parallelism=<n>` | Giới hạn số thread trong ForkJoinPool | `-Djava.util.concurrent.ForkJoinPool.common.parallelism=8` |

📌 **Ví dụ tối ưu GC cho CPU 4 nhân:**  
```sh
java -XX:+UseG1GC -XX:ParallelGCThreads=4 -XX:ConcGCThreads=2 -jar app.jar
```

---

# **4️⃣ Cấu hình Debug & Logging**
Các tham số này giúp debug và giám sát JVM runtime:

| **Tham số** | **Ý nghĩa** | **Ví dụ** |
|------------|------------|-----------|
| `-Xdebug` | Bật chế độ debug | `-Xdebug` |
| `-Xrunjdwp:transport=dt_socket,server=y,suspend=n,address=<port>` | Cho phép debug từ xa | `-Xrunjdwp:transport=dt_socket,server=y,suspend=n,address=5005` |
| `-XX:+HeapDumpOnOutOfMemoryError` | Tạo file dump khi lỗi `OutOfMemoryError` | `-XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=./heapdump.hprof` |
| `-XX:+UnlockDiagnosticVMOptions` | Bật các tùy chọn ẩn của JVM | `-XX:+UnlockDiagnosticVMOptions` |

📌 **Ví dụ bật debug từ xa trên cổng 5005:**  
```sh
java -Xdebug -Xrunjdwp:transport=dt_socket,server=y,suspend=n,address=5005 -jar app.jar
```

---

# **5️⃣ Cấu hình Performance Tuning**
Các tham số này giúp **tinh chỉnh JVM để tối ưu hiệu suất**:

| **Tham số** | **Ý nghĩa** | **Ví dụ** |
|------------|------------|-----------|
| `-XX:+AlwaysPreTouch` | Cấp phát bộ nhớ Heap ngay từ đầu | `-XX:+AlwaysPreTouch` |
| `-XX:+UseStringDeduplication` | Giảm bộ nhớ dùng cho chuỗi (String) | `-XX:+UseStringDeduplication` |
| `-XX:+TieredCompilation` | Kết hợp JIT compiler C1 và C2 | `-XX:+TieredCompilation` |
| `-XX:+UseCompressedOops` | Dùng pointer 32-bit trong Heap < 32GB | `-XX:+UseCompressedOops` |

📌 **Ví dụ tối ưu hiệu suất:**  
```sh
java -XX:+UseG1GC -XX:+AlwaysPreTouch -XX:+UseStringDeduplication -jar app.jar
```

---

# **6️⃣ Cấu hình System Properties**
Các tham số dạng `-D` cho phép cấu hình properties của ứng dụng Java:

| **Tham số** | **Ý nghĩa** | **Ví dụ** |
|------------|------------|-----------|
| `-Dfile.encoding=UTF-8` | Đặt encoding mặc định | `-Dfile.encoding=UTF-8` |
| `-Duser.timezone=UTC` | Cấu hình múi giờ | `-Duser.timezone=UTC` |
| `-Dlog4j.configuration=file:/path/to/log4j.xml` | Chỉ định file config log4j | `-Dlog4j.configuration=file:log4j.xml` |

📌 **Ví dụ đặt encoding UTF-8 và múi giờ UTC:**  
```sh
java -Dfile.encoding=UTF-8 -Duser.timezone=UTC -jar app.jar
```

---

## **📌 Tổng kết**
✅ **Tối ưu Heap Memory:** `-Xms`, `-Xmx`, `-XX:NewRatio`  
✅ **Chọn GC phù hợp:** `-XX:+UseG1GC`, `-XX:+UseZGC`  
✅ **Giám sát GC & Heap:** `-XX:+PrintGCDetails`, `-XX:+HeapDumpOnOutOfMemoryError`  
✅ **Tối ưu CPU & Thread:** `-XX:ParallelGCThreads`, `-XX:ConcGCThreads`  
✅ **Debug & Logging:** `-Xdebug`, `-XX:+UnlockDiagnosticVMOptions`  




## **🔍 Cách chọn cấu hình JVM tối ưu cho hệ thống**  

Việc cấu hình JVM tối ưu phụ thuộc vào nhiều yếu tố như **loại ứng dụng, tài nguyên hệ thống, workload, và yêu cầu hiệu suất**. Dưới đây là cách bạn có thể xác định cấu hình phù hợp bằng cách theo dõi hiệu suất và thử nghiệm.  

---

## **1️⃣ Tối ưu Heap Memory (`-Xms`, `-Xmx`, `-XX:NewRatio`)**  

### **🎯 Khi nào cần tối ưu Heap Memory?**
- Ứng dụng **tốn nhiều bộ nhớ** (ví dụ: xử lý dữ liệu lớn, microservices nhiều request).  
- Thường xuyên gặp lỗi **OutOfMemoryError (OOM)**.  
- GC chạy quá nhiều lần, gây gián đoạn hiệu suất.  

### **🔬 Dựa vào đâu để cấu hình Heap Memory?**
1. **Theo dõi Heap Usage:**  
   - Sử dụng **VisualVM, JConsole, jstat** để xem mức sử dụng Heap.  
   - Nếu Heap **thường xuyên đạt 80-90%** → cần tăng `-Xmx`.  

   📌 **Lệnh kiểm tra Heap Memory real-time:**  
   ```sh
   jstat -gc <PID> 1000
   ```

2. **Dựa vào tổng RAM của hệ thống:**  
   - **Ứng dụng nhỏ (<2GB RAM)** → `-Xms512m -Xmx1g`  
   - **Ứng dụng vừa (~4GB RAM)** → `-Xms2g -Xmx4g`  
   - **Ứng dụng lớn (>8GB RAM)** → `-Xms4g -Xmx8g`  

3. **Tính toán `NewRatio` hợp lý:**  
   - `-XX:NewRatio=2`: Young Gen chiếm 1/3 Heap, Old Gen chiếm 2/3 Heap (mặc định).  
   - `-XX:NewRatio=1`: Young Gen = Old Gen (có nhiều object ngắn hạn).  
   - `-XX:NewRatio=3`: Old Gen chiếm phần lớn (nếu ít object cần thu gom).  

   📌 **Ví dụ cấu hình Heap Memory:**  
   ```sh
   java -Xms2g -Xmx4g -XX:NewRatio=2 -jar app.jar
   ```

---

## **2️⃣ Chọn Garbage Collector phù hợp (`-XX:+UseG1GC`, `-XX:+UseZGC`)**  

### **🎯 Khi nào cần tối ưu GC?**  
- Ứng dụng bị **Stop-the-World (STW)** quá lâu khi GC chạy.  
- Yêu cầu **độ trễ thấp**, không muốn gián đoạn request.  
- Ứng dụng chạy trên **nhiều CPU** hoặc **Heap lớn** (>4GB).  

### **🔬 Dựa vào đâu để chọn GC phù hợp?**  

| **Loại GC** | **Dành cho loại ứng dụng** | **Ưu điểm** | **Nhược điểm** | **Lệnh bật** |
|------------|------------------|-----------|--------------|---------------|
| **Serial GC** | Ứng dụng nhỏ, single-thread | Ít tốn CPU | STW lâu, không tối ưu cho đa nhân | `-XX:+UseSerialGC` |
| **Parallel GC** | Ứng dụng cần throughput cao | Tận dụng nhiều CPU | GC pause time dài | `-XX:+UseParallelGC` |
| **G1 GC** | Heap > 4GB, ứng dụng yêu cầu độ trễ thấp | Giảm STW, tối ưu vùng nhớ | Hiệu suất thấp hơn Parallel GC | `-XX:+UseG1GC` |
| **ZGC** | Ứng dụng lớn (Heap > 16GB), cần latency cực thấp | STW gần như bằng 0 | Tốn RAM hơn | `-XX:+UseZGC` |

📌 **Ví dụ bật G1 GC và giảm GC pause time:**  
```sh
java -XX:+UseG1GC -XX:MaxGCPauseMillis=200 -jar app.jar
```

📌 **Ví dụ bật ZGC cho ứng dụng yêu cầu latency thấp:**  
```sh
java -XX:+UseZGC -jar app.jar
```

🔍 **Dùng `jstat` để kiểm tra GC hoạt động thế nào:**  
```sh
jstat -gcutil <PID> 1000
```
> **GC Time (%) > 10-15%** → GC đang chiếm quá nhiều tài nguyên, cần tối ưu.  

---

## **3️⃣ Tối ưu CPU & Thread (`-XX:ParallelGCThreads`, `-XX:ConcGCThreads`)**  

### **🎯 Khi nào cần tối ưu CPU & Thread?**
- Ứng dụng chạy trên **server nhiều nhân CPU**.  
- GC mất quá nhiều thời gian xử lý **do thiếu luồng**.  
- Cần kiểm soát **số luồng GC** để tránh quá tải CPU.  

### **🔬 Dựa vào đâu để cấu hình CPU & Thread?**
1. **Xác định số CPU khả dụng:**  
   📌 **Lệnh kiểm tra số CPU có thể dùng:**  
   ```sh
   cat /proc/cpuinfo | grep processor | wc -l
   ```
   Hoặc trong Java:  
   ```java
   System.out.println(Runtime.getRuntime().availableProcessors());
   ```

2. **Cấu hình số thread GC theo CPU:**  
   - **Máy có 4-8 CPU** → `-XX:ParallelGCThreads=4 -XX:ConcGCThreads=2`  
   - **Máy có 8-16 CPU** → `-XX:ParallelGCThreads=8 -XX:ConcGCThreads=4`  
   - **Máy có 16+ CPU** → `-XX:ParallelGCThreads=16 -XX:ConcGCThreads=8`  

📌 **Ví dụ cấu hình GC Threads cho máy 8 CPU:**  
```sh
java -XX:+UseG1GC -XX:ParallelGCThreads=8 -XX:ConcGCThreads=4 -jar app.jar
```

📌 **Dùng `top` hoặc `htop` để kiểm tra mức sử dụng CPU:**  
```sh
top -H -p <PID>
```

---

## **📌 Kết luận**  

### ✅ **Tối ưu Heap Memory (`-Xms`, `-Xmx`, `-XX:NewRatio`)**  
- **Dựa vào RAM máy & ứng dụng**: Dùng `jstat`, `VisualVM` để theo dõi.  
- **Heap thường xuyên đầy?** → Tăng `-Xmx`.  
- **GC chạy quá nhiều lần?** → Điều chỉnh `NewRatio`.  

### ✅ **Chọn GC phù hợp (`-XX:+UseG1GC`, `-XX:+UseZGC`)**  
- **Ứng dụng nhỏ** → `Serial GC` (`-XX:+UseSerialGC`).  
- **Ứng dụng cần throughput cao** → `Parallel GC` (`-XX:+UseParallelGC`).  
- **Ứng dụng Heap lớn (4GB+) & yêu cầu latency thấp** → `G1 GC` (`-XX:+UseG1GC`).  
- **Ứng dụng cần gần như không bị GC pause** → `ZGC` (`-XX:+UseZGC`).  

### ✅ **Tối ưu CPU & Thread (`-XX:ParallelGCThreads`, `-XX:ConcGCThreads`)**  
- **Máy có nhiều CPU** → Tăng `ParallelGCThreads`, `ConcGCThreads` để tận dụng CPU.  
- **Dùng `top` hoặc `jstat` để theo dõi mức sử dụng CPU & GC time.**  

