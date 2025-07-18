| Ngày | Chủ đề                                |
| ---- | ------------------------------------- |
| 1-2  | Thread, Runnable, sleep, join         |
| 3-4  | synchronized, race condition          |
| 5-6  | wait, notify – Producer Consumer      |
| 7-8  | ExecutorService, Future               |
| 9-10 | BlockingQueue, Concurrent Collections |
| 11   | ReentrantLock, Semaphore              |
| 12   | CountDownLatch, CyclicBarrier         |
| 13   | AtomicInteger, volatile               |
| 14   | CompletableFuture – Async handling    |


Thread Lifecycle
New → Runnable → Running → Blocked/Waiting → Terminated

+ thread pool
+ các loại thread pool
+  Callable and Future
  + Callable
  + future
+ Concurrent Collections
  
| Collection            | Đặc điểm chính                   | Khi nào dùng                            |
| --------------------- | -------------------------------- | --------------------------------------- |
| ConcurrentHashMap     | Map thread-safe, hiệu năng cao   | Đa luồng đọc/ghi dữ liệu dạng key-value |
| CopyOnWriteArrayList  | List đọc nhiều, ghi ít           | Nhiều đọc, ít ghi                       |
| ConcurrentLinkedQueue | Hàng đợi thread-safe, không khóa | Hàng đợi không blocking                 |
| BlockingQueue         | Hàng đợi có block                | Producer-consumer, chờ đợi              |
| ConcurrentSkipListMap | Map có thứ tự thread-safe        | Cần map có thứ tự, đa luồng             |

4. Synchronizers
| Class            | Purpose                                                           |
| ---------------- | ----------------------------------------------------------------- |
| `CountDownLatch` | Wait for a fixed number of events to happen                       |
| `CyclicBarrier`  | Synchronize a group of threads to wait for each other             |
| `Semaphore`      | Limit access to a resource                                        |
| `Exchanger`      | Exchange data between two threads                                 |
| `Phaser`         | More flexible alternative to `CountDownLatch` and `CyclicBarrier` |


```
java.util.concurrent
│
├── Executor Framework
│    (Quản lý thread pool và thực thi task bất đồng bộ)
│    ├── Executor
│    ├── ExecutorService
│    │     ├── ThreadPoolExecutor
│    │     ├── ScheduledExecutorService
│    │           └── ScheduledThreadPoolExecutor
│    └── Executors (các factory method tạo Executor)
│
├── Task Interfaces
│    (Định nghĩa và xử lý các tác vụ đa luồng, hỗ trợ trả về kết quả)
│    ├── Runnable           (task không trả về kết quả)
│    ├── Callable<V>        (task trả về kết quả)
│    └── Future<V>          (đại diện kết quả bất đồng bộ)
│          ├── FutureTask<V>
│
├── Concurrent Collections
│    (Bộ sưu tập thread-safe, tránh race condition khi thao tác đa luồng)
│    ├── ConcurrentMap<K,V>
│    │      └── ConcurrentHashMap<K,V>
│    ├── BlockingQueue<E>   (hỗ trợ mô hình producer-consumer)
│    │      ├── ArrayBlockingQueue<E>
│    │      ├── LinkedBlockingQueue<E>
│    │      ├── PriorityBlockingQueue<E>
│    │      ├── DelayQueue<E>
│    │      └── SynchronousQueue<E>
│    ├── ConcurrentLinkedQueue<E>
│    ├── ConcurrentLinkedDeque<E>
│    ├── CopyOnWriteArrayList<E>
│    └── CopyOnWriteArraySet<E>
│
├── Synchronizers
│    (Đồng bộ hóa luồng, điều phối và chờ đợi giữa các thread)
│    ├── CountDownLatch      (đếm ngược chờ nhiều thread hoàn thành)
│    ├── CyclicBarrier       (rào cản vòng, cho nhiều thread chờ đồng thời)
│    ├── Semaphore          (giới hạn số thread truy cập tài nguyên)
│    ├── Exchanger<V>        (trao đổi dữ liệu giữa 2 thread)
│    └── Phaser              (rào cản linh hoạt hơn CountDownLatch/CyclicBarrier)
│
├── Locks
│    (Cung cấp lock linh hoạt, thay thế synchronized, hỗ trợ timeout, đọc-ghi)
│    ├── Lock (interface)
│    │      ├── ReentrantLock
│    │      ├── ReentrantReadWriteLock
│    │      │      ├── ReadLock
│    │      │      └── WriteLock
│    │      └── StampedLock
│    └── Condition (điều phối chờ/đánh thức thread liên quan đến Lock)
│
├── Atomic Variables
│    (Biến nguyên tử, lock-free, đảm bảo cập nhật an toàn trong đa luồng)
│    ├── AtomicBoolean
│    ├── AtomicInteger
│    ├── AtomicLong
│    ├── AtomicReference<V>
│    ├── AtomicIntegerArray
│    ├── AtomicLongArray
│    └── AtomicReferenceArray<E>
│
└── Other Utilities
     (Các tiện ích bổ sung hỗ trợ đa luồng nâng cao)
     ├── ThreadFactory        (tạo thread tùy chỉnh)
     ├── ThreadLocalRandom    (random an toàn đa luồng)
     ├── ForkJoin Framework   (xử lý bài toán chia để trị song song)
     │      ├── ForkJoinPool
     │      └── ForkJoinTask<V>
     │             ├── RecursiveTask<V>
     │             └── RecursiveAction
     └── Locksupport          (hỗ trợ cấp thấp cho thread blocking/unblocking)

```
