Dưới đây là một **cheat sheet** các câu lệnh cơ bản của **Vim** để bạn dễ dàng tham khảo khi sử dụng.

### Các chế độ trong Vim:

1. **Normal Mode**: Chế độ mặc định, dùng để điều khiển con trỏ và thực hiện các thao tác chỉnh sửa.
2. **Insert Mode**: Chế độ nhập liệu, nơi bạn có thể gõ văn bản.
3. **Visual Mode**: Chế độ chọn văn bản.
4. **Command-Line Mode**: Chế độ thực hiện các lệnh.

### Chuyển đổi giữa các chế độ:

- **Normal Mode** → **Insert Mode**: nhấn `i` (hoặc `I` để vào đầu dòng, `a` để thêm sau con trỏ)
- **Insert Mode** → **Normal Mode**: nhấn `Esc`
- **Normal Mode** → **Visual Mode**: nhấn `v`
- **Normal Mode** → **Command-Line Mode**: nhấn `:`

### Các câu lệnh cơ bản trong **Normal Mode**:

#### Di chuyển con trỏ:

- `h`: di chuyển sang trái (1 ký tự)
- `j`: di chuyển xuống (1 dòng)
- `k`: di chuyển lên (1 dòng)
- `l`: di chuyển sang phải (1 ký tự)
- `w`: di chuyển đến đầu từ tiếp theo
- `b`: di chuyển đến đầu từ trước đó
- `0`: di chuyển đến đầu dòng
- `$`: di chuyển đến cuối dòng
- `gg`: di chuyển đến đầu tài liệu
- `G`: di chuyển đến cuối tài liệu
- `H`: di chuyển lên 1/3 trên của màn hình
- `M`: di chuyển đến giữa màn hình
- `L`: di chuyển xuống 1/3 dưới của màn hình

#### Chỉnh sửa và xóa:

- `x`: xóa ký tự dưới con trỏ
- `dd`: xóa cả dòng
- `d$`: xóa từ con trỏ đến cuối dòng
- `d0`: xóa từ con trỏ đến đầu dòng
- `dgg`: xóa từ con trỏ đến đầu tài liệu
- `dG`: xóa từ con trỏ đến cuối tài liệu
- `yy`: sao chép cả dòng (yank)
- `yw`: sao chép từ con trỏ đến hết từ
- `p`: dán nội dung sau con trỏ
- `P`: dán nội dung trước con trỏ
- `u`: hoàn tác (undo)
- `Ctrl + r`: làm lại (redo)

#### Chèn và sửa văn bản:

- `i`: chuyển sang chế độ nhập liệu tại vị trí con trỏ
- `I`: chuyển sang chế độ nhập liệu ở đầu dòng
- `a`: thêm văn bản sau con trỏ
- `A`: thêm văn bản ở cuối dòng
- `o`: tạo dòng mới và chuyển sang chế độ nhập liệu
- `O`: tạo dòng mới trên dòng hiện tại và chuyển sang chế độ nhập liệu

#### Tìm kiếm và thay thế:

- `/text`: tìm kiếm từ "text" trong tài liệu
- `?text`: tìm kiếm từ "text" ngược lại
- `n`: tìm kiếm kết quả tiếp theo
- `N`: tìm kiếm kết quả trước đó
- `:%s/old/new/g`: thay thế tất cả từ "old" bằng "new" trong tài liệu
- `:s/old/new/g`: thay thế trong dòng hiện tại

#### Lưu và thoát:

- `:w`: lưu tài liệu
- `:wq`: lưu và thoát
- `:q`: thoát (nếu không có thay đổi)
- `:q!`: thoát mà không lưu thay đổi
- `:x`: tương tự `:wq`, lưu và thoát

#### Các câu lệnh Visual Mode:

- `v`: chọn ký tự theo vị trí con trỏ
- `V`: chọn cả dòng
- `Ctrl + v`: chọn vùng khối (block selection)
- `y`: sao chép (yank) vùng đã chọn
- `d`: xóa vùng đã chọn
- `p`: dán vùng đã chọn sau con trỏ

#### Các lệnh khác:

- `.`: thực hiện lại lệnh trước đó
- `Ctrl + f`: cuộn xuống 1 trang
- `Ctrl + b`: cuộn lên 1 trang
- `Ctrl + d`: cuộn xuống nửa trang
- `Ctrl + u`: cuộn lên nửa trang

### Các lệnh mạnh mẽ:

- `:set number`: hiển thị số dòng
- `:set nonumber`: ẩn số dòng
- `:set relativenumber`: hiển thị số dòng tương đối
- `:syntax on`: bật đánh dấu cú pháp (syntax highlighting)
- `:help`: mở tài liệu trợ giúp của Vim

Hy vọng cheat sheet này giúp bạn nhanh chóng làm quen và sử dụng Vim hiệu quả hơn!
