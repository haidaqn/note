## Internet Protocol Address
- Địa chỉ IP ( viết tắt   Internet Protocol Address) là một con số duy nhất dùng để xác định một thiết bị đầu cuối ( ví dụ : máy tính, router…. ). Địa chỉ IP giống như số nhà của chúng ta , nó là duy nhất . Địa chỉ IP  cho phép các máy tính có thể truyền tải  thông tin , giao tiếp với nhau , và chúng đảm bảo cho các thiết bị  có thể hiểu được và chia sẻ  dữ liệu với nhau.
- Địa chỉ IP có 2 phiên bản là:
  - IPv4.
  - IPv6.
### 1. IPv4
- Là địa chỉ IP gồm 32 bit nhị phân, chia thành 4 cụm 8 bit (gọi là các octet). Các octet được biểu diễn dưới dạng thập phân và được ngăn cách nhau bằng các dấu chấm.
- Với 32 bit, giới hạn của địa chỉ IPv4 là từ 0.0.0.0 đến 255.255.255.255.
- Trong đó mỗi ký tự là một con số mà người dùng, modem hay máy chủ có dịch vụ DHCP (Dynamic Host Configuration Protocol) gán cho chúng.
### 2. IPv6
- Sử dụng 128 bit nên sẽ sử dụng được gấp nhiều lần IPv4 để thay thế cho IPv4 đang dần cạn kiệt.
## Subnet Mask
Thường mỗi tổ chức, công ty hay quốc gia đựơc cấp cho một số địa chỉ IP nhất định và có các máy tính đặt ở các vùng khác nhau. Cách để quản lý là chia ra thành các mạng nhỏ và kết nối với nhau bởi router - Những mạng nhỏ như thế gọi là **Subnets**. 

Khi chia ra thành các Subnet nhằm làm:
- Giảm giao dịch trên mạng: lúc này router sẽ kiểm soát các gói tin trên mạng – chỉ có gói tin nào có địa chỉ đích ở ngoài mới đựoc chuyển ra.
- Quản lý đơn giản hơn và nếu có sự cố thì cũng dễ kiểm tra và xác định đựơc nguyên nhân gây lỗi.

Subnet mask là một số 32 Bit gồm các Bit 1 và 0 – Các Bit 1 ở các vị trí của Network Address hoặc Subnet mask còn các Bit 0 ở vị trí của Node Address còn lại.

## TCP/IP
**Bộ giao thức TCP/IP** (Internet protocol suite – Bộ giao thức liên mạng) là một bộ các giao thức truyền thống cài đặt chồng giao thức mà Internet và hầu hết các mạng máy tính thương mại đang chạy trên đó.
TCP/IP gồm 4 tầng:  
- **Tầng ứng dụng:** 
  - Là nơi các chương trình mạng thường dùng làm việc nhất nhằm liên lạc giữa các nút trong một mạng
- **Tầng giao vận:** 
  - Kết hợp các khả năng truyền thông điệp trực tiếp không phụ thuộc vào mạng bên dưới, kèm theo kiểm soát lỗi, phân mảnh và điều khiển lưu lượng.
- **Tầng mạng:**
  - Giải quyết các vấn đề dẫn các gói tin qua một mạng đơn. 
  - Dẫn đường cho dữ liệu từ mạng nguồn đến mạng đích.
- **Tầng liên kết:**
  - Chuyển các gói tin từ tầng mạng tơi các máy chủ khác nhau.
  - Là nơi các tập tin được chặn để gửi qua một mạng riêng ảo
  - Còn có thể xem là bao gồm cả tầng vật lý.
