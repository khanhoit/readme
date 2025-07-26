# Java Concurrent Programming - Lý thuyết và Bài tập

Tài liệu tổng hợp lý thuyết và bài tập thực hành cho lập trình song song và bất đồng bộ trong Java.

---

## 📘 Chương 1: Executor Framework

### 🔎 Lý thuyết
- `Executor` là interface đơn giản để thực thi các task bất đồng bộ.
- `ExecutorService` mở rộng Executor, cung cấp nhiều tính năng quản lý pool, shutdown, submit.
- `Executors` cung cấp các phương thức tiện lợi để tạo thread pool như:
  - `newFixedThreadPool(n)` – tạo pool cố định
  - `newCachedThreadPool()` – pool linh hoạt
  - `newSingleThreadExecutor()` – đơn luồng
  - `newScheduledThreadPool(n)` – hẹn lịch thực thi

### ✅ Bài tập
1. Tạo `Executor` đơn giản và submit 10 task.
2. Dùng `FixedThreadPool` xử lý 5 task giả lập tải API (dùng `Thread.sleep`).
3. Dùng `ScheduledExecutorService` để in ra "Tick" mỗi giây.
4. So sánh thời gian thực thi giữa `SingleThreadExecutor` và `FixedThreadPool`.
5. Tạo custom `ThreadFactory` để đặt tên thread tự động.

---

## 📘 Chương 2: Task Interfaces (Runnable, Callable, Future)

### 🔎 Lý thuyết
- `Runnable`: interface cho task không trả kết quả.
- `Callable<V>`: task có kết quả trả về (dùng `Future<V>` để nhận kết quả).
- `Future<V>`: đại diện cho kết quả của task bất đồng bộ.
- `FutureTask`: vừa là `Runnable`, vừa là `Future`.

### ✅ Bài tập
1. Tạo `Runnable` in ra số từ 1 đến 100.
2. Tạo `Callable` tính tổng 1..100 và lấy kết quả với `Future.get()`.
3. Gửi nhiều `Callable` và nhận kết quả theo thứ tự hoàn thành.
4. Dùng `future.get(timeout)` để xử lý timeout.
5. Kết hợp `FutureTask` và `Thread` mô phỏng xử lý nền.

---

## 📘 Chương 3: Concurrent Collections

### 🔎 Lý thuyết
- `ConcurrentHashMap`: Map thread-safe, hiệu suất cao.
- `CopyOnWriteArrayList`: phù hợp cho đọc nhiều, ghi ít.
- `ConcurrentLinkedQueue`: queue không blocking.
- `BlockingQueue`: hỗ trợ blocking cho producer/consumer.

### ✅ Bài tập
1. Dùng `ConcurrentHashMap` để đếm số lần xuất hiện của từ.
2. `CopyOnWriteArrayList` – thêm và xoá phần tử từ nhiều thread.
3. Mô phỏng task queue bằng `ConcurrentLinkedQueue`.
4. Tạo hệ thống producer-consumer với `LinkedBlockingQueue`.
5. Dùng `DelayQueue` xử lý thông điệp theo thời gian delay.

---

## 📘 Chương 4: Synchronizers

### 🔎 Lý thuyết
- `CountDownLatch`: chờ nhiều thread hoàn thành.
- `CyclicBarrier`: đồng bộ nhiều thread tại cùng điểm.
- `Semaphore`: giới hạn số thread truy cập tài nguyên.
- `Phaser`: thay thế linh hoạt hơn cho latch và barrier.
- `Exchanger`: trao đổi dữ liệu giữa 2 thread.

### ✅ Bài tập
1. `CountDownLatch`: chờ 3 worker xong mới in kết quả.
2. `CyclicBarrier`: 4 thread chạy đồng bộ.
3. `Semaphore`: giới hạn 2 thread truy cập.
4. `Phaser`: xử lý 3 pha, các thread đợi nhau.
5. `Exchanger`: hai thread trao đổi danh sách dữ liệu.

---

## 📘 Chương 5: Locks

### 🔎 Lý thuyết
- `ReentrantLock`: thay thế `synchronized`, hỗ trợ try-lock.
- `ReadWriteLock`: chia lock cho đọc và ghi.
- `StampedLock`: hỗ trợ optimistic lock.
- `Condition`: dùng với Lock để chờ và đánh thức thread.

### ✅ Bài tập
1. Counter an toàn dùng `ReentrantLock`.
2. Cho nhiều thread đọc và một thread ghi bằng `ReadWriteLock`.
3. Dùng `Condition` xử lý buffer giới hạn.
4. Dùng `StampedLock` với optimistic read.
5. Mô phỏng tài khoản ngân hàng thread-safe.

---

## 📘 Chương 6: Atomic Variables

### 🔎 Lý thuyết
- `AtomicInteger`, `AtomicLong`: tăng/giảm không cần lock.
- `AtomicReference`: cập nhật object an toàn.
- `volatile`: đảm bảo visibility giữa các thread.

### ✅ Bài tập
1. Dùng `AtomicInteger` để tăng trong 1000 thread.
2. So sánh `synchronized` vs `AtomicInteger` về tốc độ.
3. Dùng `AtomicReference` cập nhật thông tin User.
4. Dùng `AtomicIntegerArray` cho mảng.
5. Dùng `volatile` để dừng thread qua flag.

---

## 📘 Chương 7: Other Utilities

### 🔎 Lý thuyết
- `ThreadLocal`: biến riêng cho từng thread.
- `ThreadLocalRandom`: random an toàn cho đa luồng.
- `ForkJoinPool`: xử lý chia để trị song song hiệu quả.

### ✅ Bài tập
1. Gán ID ngẫu nhiên cho mỗi request bằng `ThreadLocal`.
2. Sinh 1000 số ngẫu nhiên bằng `ThreadLocalRandom`.
3. Cài đặt merge sort bằng `ForkJoinTask`.
4. Tính tổng mảng dài bằng `RecursiveTask`.
5. So sánh hiệu suất `ForkJoin` và `ExecutorService`.

---

## 🌟 Mini-Project gợi ý
- Web crawler song song dùng `BlockingQueue`
- Hệ thống ngân hàng thread-safe (`ReentrantLock`, `Atomic`)
- Async aggregator dùng `CompletableFuture` + `Executor`
- Merge sort hiệu suất cao với `ForkJoin` so sánh với `ThreadPool`
