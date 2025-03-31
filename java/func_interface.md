Dưới đây là bảng tổng hợp các Functional Interface phổ biến trong Java 8:

| Functional Interface | Mô tả | Ví dụ Lambda |
|----------------------|-------|--------------|
| **Predicate<T>**     | Nhận vào một giá trị kiểu `T`, trả về `boolean`. Thường dùng để kiểm tra điều kiện. | `Predicate<Integer> isPositive = x -> x > 0;` |
| **Consumer<T>**      | Nhận vào một giá trị kiểu `T`, không trả về kết quả. Thường dùng để thực hiện một hành động nào đó. | `Consumer<String> print = s -> System.out.println(s);` |
| **Function<T, R>**   | Nhận vào một giá trị kiểu `T`, trả về một giá trị kiểu `R`. Thường dùng để chuyển đổi dữ liệu từ kiểu này sang kiểu khác. | `Function<String, Integer> length = s -> s.length();` |
| **Supplier<T>**      | Không nhận đầu vào, trả về một giá trị kiểu `T`. Thường dùng để cung cấp hoặc khởi tạo giá trị. | `Supplier<Double> random = () -> Math.random();` |

Các Functional Interface này giúp viết mã ngắn gọn và rõ ràng hơn khi sử dụng biểu thức lambda trong Java 8.