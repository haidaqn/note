# Vì sao phải cần có Gateway?
- Gateway là một phần tử không nhất thiết phải có trong một giao tiếp H.323. 
- Nó đóng vai trò làm phần tử cầu nối và chỉ tham gia vào một cuộc gọi khi có sự chuyển tiếp từ mạng H.323 sang mạng phi H.323.

**Vậy H.323 là gì?**
- H323 là một tập các tiêu chuẩn từ **ITU-T (International Telecommunication Union - Telecommunication Standardization Sector - là lĩnh vực Tiêu chuẩn viễn thông thuộc Tổ chức Viễn thông quốc tế.)**, nó định nghĩa một tập các giao thức dùng để liên lạc bằng âm thanh và hình ảnh qua mạng máy tính.
- H.323 chạy trên nền TCP  hoặc UDP. Có các ưu điểm như: 
  - Cung cấp các bộ mã hoá đã được chuẩn hoá.
  - Tính tương thích cao.
  - Hỗ trợ kết nối đa điểm, hỗ trợ nhiều thiết bị đầu cuối.
  - Khả năng hội nghị liên mạng.
- Một mạng sử dụng giao thức H.323 thì hệ thống cần có: Thiết bị đầu cuối (Terminals), đơn vị đa điều khiển (Multipoint Control Units – MCUs), gatekeeper, Gateways ngoài ra còn có các yếu tố biên, thành phần ngang hang.
  - **H.323 terminal:** thiết bị đầu cuối trong mạng LAN có khả năng truyền thông 2 chiều theo thời gian thực, nó có thể là một PC hoặc là một thiết bị độc lập.

  - **Gatekeeper:** một thành phần quan trọng trong mạng H.323. Có thể cung cấp các chức năng như: 
    - *Dịch địa chỉ:* dịch từ địa chỉ hình thức của 1 đầu cuối sang địa chỉ IP tương ứng.
    - *Điều khiển kết nạp:* Gatekeeper sẽ chấp nhận một truy nhập mạng LAN.
    - *Điểu khiển băng thông:* điều khiển việc cấp phát hoặc từ chối cấp phát băng thông cho các cuộc gọi của các thiết bị trong hệ thống.
    - *Quản lý vùng:* một vùng là một nhóm các đầu cuối H.323, các gateways, MCU được quản lý bới gatekeeper. Thông qua các chức năng như: dịch địa chỉ, điều khiển truy nhập, điều khiển độ rộng băng tần gatekeeper cung cấp khả năng quản lý miền.
    - *Gateway:* Như đã nói ở trên, nhiệm vụ của gateway là thực hiện việc kết nối giữa 2 mạng khác nhau. H.323 gateway cung cấp khả năng kết nối giữa 1 mạng H.323 và một mạng không phải H.323.

  - **MCU (Multipoint Control Unit):** Hỗ trợ việc thực hiện các cuộc đàm thoại hội nghị giữa nhiều thiết bị đầu cuối. Nhiệm vụ của MCU là 
    - Điều tiết khả năng của âm thanh, hình ảnh và dữ liệu giữa các thiết bị đầu cuối.
    - Điều khiển các tài nguyên của hội thoại bằng việc xác định các dòng âm thanh, hình ảnh, xác định dữ liệu nào cần được gửi đến các thiết bị đầu cuối.
