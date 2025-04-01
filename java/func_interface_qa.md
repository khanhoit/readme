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
+ Predicate <T>: nhận đầu vào T trả ra kết quả true/false 
+ Function <T,R>: chuyển đổi từ kiểu T sang kiểu R
#### 3. 
+ Consumer < T >: nhận đầu vào T nhưng không trả ra giá trị nào
+ Function <T,R>: chuyển đổi từ kiểu T sang kiểu R
#### 4. 
+ Supplier < T >: trả ra giá khi mà không cần tham số đầu vào
+ ứng dụng trong các trường hợp
    + lazy initialization: 
```
import java.util.function.Supplier;

class ExpensiveObject {
    public ExpensiveObject() {
        System.out.println("ExpensiveObject được khởi tạo!");
    }
}

public class LazyInitializationExample {
    private static Supplier<ExpensiveObject> lazyObject = () -> new ExpensiveObject();
    
    public static void main(String[] args) {
        System.out.println("Chưa khởi tạo ExpensiveObject...");
        
        // Chỉ khởi tạo khi cần
        ExpensiveObject obj = lazyObject.get();
        
        System.out.println("ExpensiveObject đã được khởi tạo.");
    }
}
```
    
   + tạo dữ liệu động:

```
import java.util.Random;
import java.util.function.Supplier;

public class RandomNumberExample {
    public static void main(String[] args) {
        Supplier<Integer> randomSupplier = () -> new Random().nextInt(100); // Tạo số ngẫu nhiên từ 0-99
        
        System.out.println("Số ngẫu nhiên 1: " + randomSupplier.get());
        System.out.println("Số ngẫu nhiên 2: " + randomSupplier.get());
    }
}
```    
   + Tích hợp với API Streams
```
import java.util.function.Supplier;
import java.util.stream.Stream;
import java.util.Random;

public class StreamExample {
    public static void main(String[] args) {
        Supplier<Integer> randomSupplier = () -> new Random().nextInt(100);
        
        Stream.generate(randomSupplier)
              .limit(5) // Lấy 5 số ngẫu nhiên
              .forEach(System.out::println);
    }
}

```
#### 5. 
Có thể tạo một Functional Interface tùy chỉnh không? có
ví dụ:
```
@FunctionalInterface
public interface MyFunctionInterface {
    double getCalculator(double a, double b);
}

public class MyMain {
    public static void main(String[] args) {
        MyFunctionInterface add = (a, b) -> a + b;
        MyFunctionInterface sub = (a, b) -> a - b;
        System.out.println(add.getCalculator(10, 20));
        System.out.println(sub.getCalculator(10, 20));
    }
}
```
#### 6. 
+ @FunctionalInterface: không bắt buộc
+ thêm vào để
    + hỗ trợ complire nếu thêm một method nữa thì nó sẽ báo lỗi
    + code dễ đọc hơn
#### 7. 
    + không thêm có nhiểu phương thức trong một functionalInterface nhưng nó có thể có các phương thức default và static 
#### 8. 
Trong java, bạn có thể kết hợp nhiều Predicate<T> bằng cách sử dụng các phương thức mặc định như:
+ and(): kết hợp hai Predicate với điều kiện cả 2 cùng đúng
+ or(): kết hợp 2 predicate với điều kiện chỉ cần 1 trong 2 đúng 
+ negate(): phủ định kết quả của predicate
```
public class MyMain {
    public static void main(String[] args) {

        Predicate<Integer> isEven = x -> x % 2 == 0;
        Predicate<Integer> isPositive = num -> num > 0;
        
        // kết hợp 2 điều kiện
        Predicate<Integer> isEvenAndPositive = isEven.and(isPositive);
        
        // kết hợp với or
        Predicate<Integer> isEvenOrPositive = isEven.or(isPositive);
        
        // kết hợp với negate
        Predicate<Integer> isNotEven = isEven.negate();
    }
}
```
#### 9. 
default và static có được khai báo trong functionalInterface

ví dụ:
```
@FunctionalInterface
public interface MyFunctionInterface {
    double getCalculator(double a, double b);
    
    default void printResult(double a, double b) {
        System.out.println("Result: " + getCalculator(a, b));
    }
    
    static void printMessage() {
        System.out.println("This is a functional interface");
    }
}
```
#### 10. 
+ dùng lambda khi có functional interface (một phương thức duy nhất), giúp mã ngắn gọn và dễ đọc
+ dùng Anonymous class khi cần overide nhiều phương thức hoặc truy cập biến và phương thức của lớp bao quanh

### II. Câu hỏi thực hành
#### 1. 
```
    List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
    
    Predicate<Integer> evenNumber = x -> x % 2 == 0;
    List<Integer> evenNumbers = numbers.stream().filter(evenNumber).collect(Collectors.toList());
```
#### 2. 
```
    List<String> names = Arrays.asList("Java", "Lambda", "Stream", "Kotlin");
    
    List<Integer> nameLengths = names.stream().map(String::length).collect(Collectors.toList());
```
#### 3. 
```
        List<String> strings = Arrays.asList("Hello", "World", "Functional", "Interface");

        Consumer<String> print = System.out::println;
        
        strings.forEach(print);
```
#### 4. 
```
        Supplier<Double> random = Math::random;
        System.out.println(random.get());
        System.out.println(random.get());
        System.out.println(random.get());
        System.out.println(random.get());
        System.out.println(random.get());
        random.get();
```
#### 5. 
```
        Predicate<Integer> isPositive = num -> num > 0;

        // Một Predicate kiểm tra số chia hết cho 3 (x % 3 == 0).
        Predicate<Integer> integerPredicate3 = x -> x % 3 == 0;

        List<Integer> numbers1 = Arrays.asList(-3, -2, -1, 0, 1, 2, 3, 4, 5, 6);
        
        // Sử dụng Predicate để lọc các số chia hết cho 3. and isPositive
        List<Integer> result = numbers1.stream().filter(integerPredicate3.and(isPositive)).collect(Collectors.toList());
        
        
        // Sử dụng Predicate để lọc các số chia hết cho 3. and negative
        List<Integer> result1 = numbers1.stream().filter(integerPredicate3.and(isPositive.negate())).collect(Collectors.toList());
```
#### 6.
```
public interface Calculator {

    int calculate(int a, int b);
}


class MyMain1 {
    public static void main(String[] args) {
        Calculator add = (a, b) -> a + b;
        Calculator sub = (a, b) -> a - b;
        Calculator mul = (a, b) -> a * b;
        Calculator div = (a, b) -> a / b;

    }
}
``` 
#### 7. 
```
        UnaryOperator<Integer> add2 = a -> a + 2;
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
        
        numbers.stream().map(add2).forEach(System.out::println);
```
#### 8. 
```
        BinaryOperator<Integer> add3 = (a, b) -> a + b;
        System.out.println(add3.apply(5, 10));
```
#### 9. 
```
    BiFunction<String, String, String> concatString = (a, b) -> a + b;
    System.out.println(concatString.apply("Hello", "World"));
```
#### 10. 
```
        List<String> abc = Arrays.asList("Banana", "Apple", "Cherry", "Mango");
        Comparator<String> comparator = (a, b) -> a.length() - b.length();
        abc.sort(comparator);
        System.out.println(abc);
```

