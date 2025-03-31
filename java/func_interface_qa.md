Dưới đây là một bộ câu hỏi giúp bạn luyện tập về **Functional Interface** trong Java 8:  

---

### **I. Câu hỏi lý thuyết**  

1. **Functional Interface là gì?** Tại sao chúng quan trọng trong Java 8?  
2. **Sự khác nhau giữa `Predicate<T>` và `Function<T, R>` là gì?**  
3. **Khi nào nên sử dụng `Consumer<T>` thay vì `Function<T, R>`?**  
4. **`Supplier<T>` thường được sử dụng trong những trường hợp nào?**  
5. **Có thể tạo một Functional Interface tùy chỉnh không? Nếu có, hãy nêu cách thực hiện.**  
6. **Annotation `@FunctionalInterface` có bắt buộc không? Nó có tác dụng gì?**  
7. **Có thể sử dụng nhiều phương thức trừu tượng trong một Functional Interface không?** Giải thích.  
8. **Làm thế nào để kết hợp nhiều `Predicate<T>` với nhau?**  
9. **Default method và static method có được khai báo trong Functional Interface không?** Nếu có, hãy nêu ví dụ.  
10. **So sánh Functional Interface với Anonymous Class: Khi nào nên dùng cái nào?**  

---

### **II. Câu hỏi thực hành (viết code Java)**  

#### **1. Sử dụng `Predicate<T>` để lọc danh sách số nguyên**  
Viết một chương trình Java sử dụng `Predicate<Integer>` để lọc ra các số chẵn trong danh sách `[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]`.  

#### **2. Viết hàm chuyển đổi danh sách kiểu `String` sang danh sách độ dài chuỗi**  
Sử dụng `Function<String, Integer>` để chuyển đổi danh sách `["Java", "Lambda", "Stream", "Kotlin"]` thành danh sách chứa độ dài của từng chuỗi.  

#### **3. Tạo `Consumer<T>` để in danh sách chuỗi**  
Sử dụng `Consumer<String>` để duyệt danh sách `["Hello", "World", "Functional", "Interface"]` và in từng phần tử ra màn hình.  

#### **4. Viết một `Supplier<Double>` để sinh số ngẫu nhiên**  
Tạo một `Supplier<Double>` để trả về số ngẫu nhiên trong khoảng `[0,1]`. Gọi `get()` 5 lần để in ra 5 số ngẫu nhiên khác nhau.  

#### **5. Kết hợp nhiều `Predicate<T>`**  
Viết một chương trình Java sử dụng **2 Predicate**:
   - Một Predicate kiểm tra số dương (`x > 0`).
   - Một Predicate kiểm tra số chia hết cho 3 (`x % 3 == 0`).  
Sử dụng `and()`, `or()`, `negate()` để lọc danh sách `[ -3, -2, -1, 0, 1, 2, 3, 4, 5, 6]`.  

#### **6. Tạo Functional Interface tùy chỉnh**  
Tạo một Functional Interface tên `Calculator` có phương thức `int calculate(int a, int b);`.  
Viết một chương trình sử dụng biểu thức lambda để thực hiện các phép toán:
   - Cộng (`+`)  
   - Trừ (`-`)  
   - Nhân (`*`)  
   - Chia (`/`)  

#### **7. Viết một `UnaryOperator<T>` để tăng mỗi phần tử trong danh sách lên 2 đơn vị**  
Dùng `UnaryOperator<Integer>` để cộng thêm `2` vào từng phần tử trong danh sách `[1, 2, 3, 4, 5]`.  

#### **8. Viết một `BinaryOperator<T>` để tính tổng của hai số nguyên**  
Tạo một `BinaryOperator<Integer>` để tính tổng của hai số nguyên `a, b`. Gọi nó với các giá trị `(5, 10)`.  

#### **9. Viết một `BiFunction<T, U, R>` để nối hai chuỗi lại với nhau**  
Tạo một `BiFunction<String, String, String>` để nối hai chuỗi `"Hello"` và `"World"` thành `"Hello World"`.  

#### **10. Viết chương trình sử dụng `Comparator` với Lambda**  
Tạo danh sách `[ "Banana", "Apple", "Cherry", "Mango"]` và sắp xếp theo độ dài chuỗi sử dụng **Comparator và Lambda Expression**.  

---

💡 **Gợi ý**: Sau khi làm xong các bài tập này, bạn có thể thử kết hợp chúng lại bằng cách sử dụng Stream API để viết code ngắn gọn hơn! 🚀

<br>



# Bài làm

### I. Câu hỏi lý thuyết
#### 1.
Functional interface là một interface có duy nhất một method và được đánh dấu bằng @FunctionalInterface

ví dụ:
```
@FunctionalInterface
public interface abc {
    void doSomething();
}
```

functional interface xuất hiện từ java8 và nó quan trọng vì:
+ **Hỗ trợ lập trình hàm trong java**
+ Hỗ trợ lambda
+ Giúp code theo hướng behavior


#### 2. 
ádsad

#### 3. 
#### 4. 
#### 5. 
#### 6. 
#### 7. 
#### 8. 
#### 9. 
#### 10. 

### II. Câu hỏi thực hành
#### 1. 
#### 2. 
#### 3. 
#### 4. 
#### 5. 
#### 6. 
#### 7. 
#### 8. 
#### 9. 
#### 10. 

