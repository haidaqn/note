# Mô Hình Client-Server
- Một ứng dụng khởi tạo truyền thông từ điểm tới điểm được gọi là client.
- Mô hình Client/Server cố gắng tổ chức lại các máy PC, trên mạng cục bộ, để tương thích với các máy tính lớn, tăng tính thích ứng, tính hiệu quả của hệ thống.
- Client là các máy PC hay là các workstations (máy trạm), truy cập vào mạng và sử dụng các tài nguyên trên mạng.
- Trong hệ thống Client/Server có một vài Client, với mỗi Client sử dụng giao diện riêng của mình. Các Client sử dụng các tài nguyên được chia sẻ bởi Server.
- Server có thể là một workstation lớn.
- Client có thể gửi các truy vấn hoặc các lệnh tới Server, nhưng thực hiện tiến trình này không phải là Client mà Server sẽ trả lại kết quả trên màn hình của Client.
- Server không thể khởi tạo bất kỳ công việc nào, nhưng nó thực hiện các yêu cầu to lớn của Client.
> Server thực hiện việc chia sẻ File, lưu trữ và tìm ra các thông tin, mạng và quản lý tài liệu, quản lý thư điện tử, bảng thông báo và văn bản video.

# Mã hoá trong mô hình Client/Server.
Trong mô hình Client/Server việc trao đổi thông tin diễn ra thường xuyên nên rất dễ bị kẻ xấu lợi dụng, bởi vậy bảo vệ thông tin trên đường truyền là vô cùng quan trọng, chúng đảm bảo thông tin trên đường truyền là đúng đắn. Tại mô hình này mỗi khi những yêu cầu được gửi từ Client đến Server hoặc khi Server gửi trả lại kết quả cho Client thì những thông tin này đều được mã hoá trong khi truyền.
