# Java Collection Framework (JCF)

Java Collection Framework (JCF) là một tập hợp các interface và class giúp quản lý dữ liệu một cách hiệu quả. JCF cung cấp các cấu trúc dữ liệu như **List, Set, Queue, Map** để lưu trữ và xử lý tập hợp phần tử.

## 1. Tổng quan JCF
```
Collection (Interface)
│
├── List (Interface)  → Danh sách có thứ tự, cho phép trùng lặp
│   ├── ArrayList      → Mảng động, truy xuất nhanh, thêm/xóa giữa chậm
│   ├── LinkedList     → Danh sách liên kết đôi, chèn/xóa nhanh, truy xuất chậm
│   └── Vector         → Giống ArrayList nhưng thread-safe
│
├── Set (Interface)  → Tập hợp không chứa phần tử trùng lặp
│   ├── HashSet        → Không có thứ tự, hiệu suất cao
│   ├── LinkedHashSet  → Giữ nguyên thứ tự chèn
│   ├── SortedSet (Interface) → Tập hợp có thứ tự
│   │   └── TreeSet    → Sắp xếp tự động theo thứ tự tự nhiên hoặc Comparator
│
├── Queue (Interface)  → Hàng đợi (FIFO - First In First Out)
│   ├── PriorityQueue  → Hàng đợi ưu tiên (phần tử có độ ưu tiên cao ra trước)
│   └── LinkedList     → Cũng có thể dùng làm Queue (Deque)
│
└── Map (Interface)  → Lưu dữ liệu theo cặp key-value
    ├── HashMap        → Không có thứ tự, hiệu suất cao
    ├── LinkedHashMap  → Giữ nguyên thứ tự chèn
    ├── SortedMap (Interface) → Ánh xạ có thứ tự
    │   └── TreeMap    → Sắp xếp key theo thứ tự tự nhiên hoặc Comparator
    └── Hashtable      → Giống HashMap nhưng thread-safe
```

## 2. Các Interface Chính

### List (Danh sách có thứ tự, cho phép trùng lặp)
- **`ArrayList`**: Truy xuất nhanh (O(1)), nhưng thêm/xóa giữa danh sách chậm (O(n)).
- **`LinkedList`**: Chèn/xóa nhanh (O(1)), nhưng truy xuất chậm (O(n)).
- **`Vector`**: Giống `ArrayList`, nhưng **thread-safe**.

### Set (Tập hợp không chứa phần tử trùng lặp)
- **`HashSet`**: Dùng bảng băm, không đảm bảo thứ tự.
- **`LinkedHashSet`**: Duy trì thứ tự chèn.
- **`TreeSet`**: Sắp xếp theo thứ tự tự nhiên hoặc Comparator.

### Queue (Hàng đợi)
- **`PriorityQueue`**: Hàng đợi ưu tiên.
- **`LinkedList`**: Có thể dùng như Queue hoặc List.

### Map (Lưu dữ liệu theo cặp key-value)
- **`HashMap`**: Không đảm bảo thứ tự.
- **`LinkedHashMap`**: Giữ nguyên thứ tự chèn.
- **`TreeMap`**: Sắp xếp key theo thứ tự tự nhiên.
- **`Hashtable`**: Giống `HashMap` nhưng thread-safe.

## 3. Ví dụ Code

### 3.1. Sử dụng `ArrayList`
```java
import java.util.*;
public class Main {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>();
        list.add("Java");
        list.add("Python");
        System.out.println(list.get(0)); // Java
    }
}
```

### 3.2. Sử dụng `HashSet`
```java
Set<Integer> set = new HashSet<>();
set.add(10);
set.add(20);
set.add(10); // Bị loại bỏ
System.out.println(set);
```

### 3.3. Sử dụng `HashMap`
```java
Map<Integer, String> map = new HashMap<>();
map.put(1, "Java");
map.put(2, "Python");
System.out.println(map.get(1)); // Java
```

## 4. Khi nào nên dùng gì?
| Trường hợp | Giải pháp |
|------------|----------------|
| Duyệt Collection | `forEach()` với Lambda |
| Lọc dữ liệu | `filter()` với Stream API |
| Chuyển đổi dữ liệu | `map()` với Stream API |
| Xóa phần tử thỏa điều kiện | `removeIf()` |
| Xử lý Map hiệu quả | `computeIfAbsent()`, `merge()`, `forEach()` |
| Tăng hiệu suất | `parallelStream()` |

📌 **JCF giúp lập trình viên xử lý dữ liệu một cách linh hoạt và tối ưu. Bạn có thể lựa chọn cấu trúc phù hợp tùy theo yêu cầu của ứng dụng.** 🚀

