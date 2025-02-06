## 1. Tìm ứng dụng
* Các chương trình hày phần mềm tùy thuộc vào cách sắp xếp có thể được cài đặt trong các thư mục khác nhau. Các chương trình được thực thi thì nên ở trong các thư mục sau:
```
/bin  
/usr/bin  
/sbin  
/usr/sbin  
/opt. 
```
* Có một cách để định vị chương trình là sử dụng lệnh ***which***. Ví dụ để tìm thư mục diff:
```
$ which diff  
/usr/bin/diff  
```

* */usr/bin/diff là kết quả trả về.*

* Nếu which không tìm được chương trình thì whereis là lựa chọn tốt vì phạm vi tìm kiếm của nó rộng hơn các mục hệ thống.  

> $ whereis diff  
diff: /usr/bin/diff /usr/share/man/man1/diff.1.gz.  
  
## 2. Truy cập thư mục  

* Các lệnh hữu ích cho việc điều hướng thư mục:

|Lệnh|Chức năng|  
|-------------|-------------|  
|cd|Trở về thư mục chính|  
|cd ..| Trở về thư mục gốc|  
|cd -|Trở về thư mục trước|  
|cd /|Từ thư mục hiện tại vào thư mục gốc (/)|  
  
## 3. Khám phá hệ thống tệp tin

* Lệnh ```tree``` là một cách hay để có được cái nhìn toàn cảnh về cây hệ thống tập tin. Các lệnh sau đây có thể giúp khám phá hệ thống tập tin:

|Lệnh|Chức năng|  
|-------|-----------|  
|ls 	  |Liệt kê nội dung thư mục|  
|ls –a  |Liệt kê tất cả các tệp bao gồm các tệp và thư mục ẩn|  
|tree   |Hiển thị cây của hệ thống tệp tin|  
|tree -d|Liệt kê các thư mục và loại bỏ tên tệp|  
  
## 4. Liên kết cứng và liên kết tượng trưng
  
* Lệnh `ln` có thể được sử dụng để tạo liên kết cứng hoặc liên kết mềm, gọi là liên kết tượng trưng (Symbolic links) hay symlinks.  

> Giả sử file1.txt đã tồn tại. Một liên kết cứng được gọi là file2.txt được tạo bằng lệnh:  
``` **# ln file1.txt file2.txt** ```

* Hại tệp này bây giờ gần như tồn tại. Nhưng việc kiểm tra danh sách tệp cho thấy điều này không hoàn toàn chính xác.  

```
# ls -l file*  
-rw-r--r--. 2 root root 604 Feb 16 11:49 file1.txt  
-rw-r--r--. 2 root root 604 Feb 16 11:49 file2.txt  
# ls -li file*  
134415251 -rw-r--r--. 2 root root 604 Feb 16 11:49 file1.txt  
134415251 -rw-r--r--. 2 root root 604 Feb 16 11:49 file2.txt 
```

* tùy chọn -i trong dòng đầu tiên dùng để in ra số i-nút là số duy nhất cho mỗi tệp, và trường này giống nhau cho cả 2 tệp. Điều thực sự xảy ra ở đây là nó chỉ là một tập tin nhưng có nhiều hơn một tập tin với nó như được chỉ ra bởi 2 xuất hiện trong đầu ra.
```
# ln file1.txt file3.txt
# ls -li file*
134415251 -rw-r--r--. 3 root root 604 Feb 16 11:49 file1.txt
134415251 -rw-r--r--. 3 root root 604 Feb 16 11:49 file2.txt
134415251 -rw-r--r--. 3 root root 604 Feb 16 11:49 file3.txt
```
* Thay đổi file3.txt có nghĩa là thay đổi cùng một đối tượng như tên file1.txt, file2.txt và file3.txt.

* Liên kết mềm có thể trỏ đến các đối tượng ngay cả trên các tập tin khác nhau (hoặc các phân vùng) có thể có hoặc không tồn tại. Trong trường hợp liên kết không trỏ đến một đối tượng đang tồn tại, bạn sẽ có được một liên kết treo lơ lửng.

> Bài viết gốc: [Basic Commands](https://github.com/lacoski/linux-notes/blob/master/content/basic_commands.md)
