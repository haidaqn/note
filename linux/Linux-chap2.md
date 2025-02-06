## Luồng tệp
* Có 3 luồng tệp tiêu chuẩn luôn mở để sử dụng:
  1. Tiêu chuẩn đầu vào **(stdin)**.
  2. Tiêu chuẩn đầu ra **(stdout)**.
  3. Tiêu chuẩn lỗi **(stderr)**.
## Tìm tệp
* Tiện ích `locate` tìm kiếm thông qua cơ sở dữ liệu và thư mục được xây dựng trước đó trên hệ thống.
* Hầu hết hệ thống trên Linux chạy mỗi ngày nhưng có thể cập nhật bất cứ lúc nào bằng lệnh `updatedb` với tư cách **root user**.
* Kết quả thu được từ `locate` đôi khi rất dài, có thể sử dụng `grep` làm bộ lọc rút gọn danh sách có liên quan  Nó sẽ chỉ in các dòng có chứa một hoặc nhiều chuỗi được chỉ định như sau: 
```
$ locate zip | grep bin
/usr/bin/gpg-zip
/usr/bin/gunzip
/usr/bin/gzip
/usr/bin/zipdetails
```  
* Có thể sử dụng các ký tự đại diện để tìm kiếm tên tệp có chứa các ký tự cụ thể.

|Ký tự|Kết quả|
|---------|-----------|
|?     |Phù hợp với bất kỳ ký tự đơn nào|
|*     |Phù hợp với bất kỳ chuỗi ký tự nào|
|[set] |Phù hợp với bất kỳ ký tự nào nằm trong tập ký tự|
|[!set]|Phù hợp với bất kỳ ký tự nào không nằm trong tập ký tự|

## Quản lý tệp
|Câu lệnh|Cách sử dụng|
|-------|-----------|
|cat  |Được sử dụng để xem các tệp không quá dài|
|tac  |Được sử dụng để xem tập tin sau cùng, bắt đầu từ dòng cuối cùng|
|less |Được sử dụng để xem các tệp lớn hơn vì nó là một chương trình phân trang; nó tạm dừng ở mỗi màn hình văn bản, cung cấp khả năng cuộn lại và cho phép bạn tìm kiếm và điều hướng trong tệp|
|tail |Được sử dụng để in 10 dòng cuối cùng của một tệp theo mặc định. Bạn có thể thay đổi số dòng bằng cách thực hiện -n 15 hoặc chỉ -15 nếu bạn muốn xem 15 dòng cuối thay vì mặc định|
|head |Ngược lại của ```tail```; theo mặc định nó in 10 dòng đầu tiên của một tập tin|

## So sánh tệp
* Lệnh `diff` được sử dụng để so sánh các tập tin và thư mục.
```
$ diff  file1.txt file2.txt
< Amor, ch'a nullo amato amar perdona,
< Mi prese del costui piacer si forte,
< Che, come vedi, ancor non m'abbandona.
---
> amor, ch'a nullo amato amar perdona,
> mi prese del costui piacer si forte,
> che, come vedi, ancor non m'abbandona.
$ 
```
## Tệp tiện ích

* Bản chất thật của `file` được xác định bởi tiện ích `file`. Nó kiểm tra nội dung và các đặc điểm nhất định để xác định xem các tệp là văn bản thuần túy, thư viện được chia sẻ, chương trình thực thi, tập lệnh hay là một thứ gì khác.
>Bài viết gốc: **[Working with files](https://github.com/lacoski/linux-notes/blob/master/content/working_with_files.md)**
