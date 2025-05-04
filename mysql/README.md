# MySQL

## Giới thiệu về MySQL
MySQL là một hệ quản trị cơ sở dữ liệu quan hệ mã nguồn mở phổ biến, được phát triển bởi Oracle. Nó được sử dụng rộng rãi trong các ứng dụng web và doanh nghiệp nhờ hiệu suất cao, tính ổn định và dễ sử dụng.

## Tính năng nổi bật của MySQL
- **Hiệu suất cao**: Tối ưu hóa cho các ứng dụng có khối lượng dữ liệu lớn.
- **Bảo mật mạnh mẽ**: Hỗ trợ xác thực người dùng và mã hóa dữ liệu.
- **Khả năng mở rộng**: Hỗ trợ nhiều loại cơ sở dữ liệu và khối lượng công việc khác nhau.
- **Tương thích đa nền tảng**: Chạy trên nhiều hệ điều hành như Windows, Linux, macOS.
- **Hỗ trợ giao dịch**: Đảm bảo tính toàn vẹn dữ liệu với các tính năng như commit, rollback.

## Toán tử so sánh và logic trong MySQL
### Toán tử so sánh:
- `=`: So sánh bằng.
- `!=` hoặc `<>`: So sánh khác.
- `<`, `<=`, `>`, `>=`: So sánh lớn hơn, nhỏ hơn.
- `BETWEEN ... AND ...`: Kiểm tra giá trị trong khoảng.
- `LIKE`: Tìm kiếm mẫu chuỗi.
- `IN`: Kiểm tra giá trị trong danh sách.

### Toán tử logic:
- `AND`: Kết hợp nhiều điều kiện, tất cả phải đúng.
- `OR`: Kết hợp nhiều điều kiện, chỉ cần một đúng.
- `NOT`: Phủ định điều kiện.

## Mảng trong MySQL
MySQL không hỗ trợ trực tiếp kiểu dữ liệu mảng, nhưng có thể sử dụng:
- **Chuỗi JSON**: Lưu trữ và truy vấn dữ liệu dạng mảng.
- **Bảng liên kết**: Mô phỏng mảng bằng cách sử dụng các bảng.

## Đánh giá và cập nhật
- **Đánh giá**: MySQL được đánh giá cao nhờ hiệu suất, tính ổn định và cộng đồng hỗ trợ lớn.
- **Cập nhật**: Các phiên bản mới thường xuyên được phát hành với các tính năng cải tiến và sửa lỗi.


## QUÁ TRÌNH TỐI ƯU HOÁ VÀ THỰC THI
-**Phân tích và tối ưu hoá**: MySQL phân tích cú pháp truy vấn để tạo ra một cấu trúc nội bộ
(cây phân tích) và sau đó áp dụng nhiều kỹ thuật tối ưu hóa. Các kỹ thuật này bao gồm việc
thay đổi cấu trúc truy vấn, xác định thứ tự đọc các bảng, chọn Index sử dụng, và các tối ưu
hóa khác. MySQL có thể nhận các gợi ý tối ưu hóa từ người dùng qua các từ khóa đặc biệt
trong truy vấn và cung cấp thông tin về các quyết định tối ưu hóa thông qua lệnh EXPLAI

-**Thực thi truy vấn**: Optimizer không quan tâm storage engine cụ thể nào đang được sử dụng,
nhưng storage engine ảnh hưởng đến cách MySQL tối ưu hóa truy vấn. Optimizer sẽ hỏi
storage engine về các khả năng tối ưu mà storage engine có thể cung cấp, cũng như các chi
phí khi áp dụng các tối ưu này. Ví dụ, một số storage engine có thể hỗ trợ một số loại index
đặc biệt hữu ích trong một số truy vấn cụ thể.

## SO SÁNH InnoDB và MyISAM trong MySQL
MySQL hỗ trợ nhiều loại storage engine, trong đó hai loại phổ biến nhất là InnoDB và MyISAM. Mỗi
loại có những đặc điểm, ưu điểm và nhược điểm riêng, phù hợp với các tình huống và nhu cầu khác
nhau.

### ACID trong MySQL

ACID là viết tắt của bốn thuộc tính quan trọng đảm bảo tính toàn vẹn dữ liệu trong các hệ quản trị cơ sở dữ liệu:

1. **Atomicity (Tính nguyên tử)**:
    - Một giao dịch phải được thực hiện hoàn toàn hoặc không thực hiện gì cả. Nếu có bất kỳ lỗi nào xảy ra, toàn bộ giao dịch sẽ bị hủy bỏ và cơ sở dữ liệu sẽ trở về trạng thái ban đầu.

2. **Consistency (Tính nhất quán)**:
    - Sau khi một giao dịch hoàn tất, cơ sở dữ liệu phải ở trạng thái hợp lệ, tuân thủ tất cả các ràng buộc và quy tắc đã được định nghĩa.

3. **Isolation (Tính độc lập)**:
    - Các giao dịch đồng thời phải được thực hiện mà không ảnh hưởng lẫn nhau. Kết quả của một giao dịch không được hiển thị cho các giao dịch khác cho đến khi nó hoàn tất.

4. **Durability (Tính bền vững)**:
    - Sau khi một giao dịch được cam kết (commit), dữ liệu phải được lưu trữ vĩnh viễn, ngay cả khi hệ thống gặp sự cố.

Trong MySQL, InnoDB là storage engine hỗ trợ đầy đủ các thuộc tính ACID, giúp đảm bảo tính toàn vẹn và an toàn dữ liệu trong các ứng dụng quan trọng.


## Tóm tắt
MySQL là một hệ quản trị cơ sở dữ liệu mạnh mẽ, phù hợp cho nhiều loại ứng dụng. Với các tính năng nổi bật, hỗ trợ toán tử so sánh và logic, cùng khả năng mở rộng, MySQL là lựa chọn hàng đầu cho các nhà phát triển và doanh nghiệp.
