- Trước khi đến với các dải mạng thì chúng ta nên tìm hiểu đến Switch ảo (Virtual Switch), card mạng máy ảo, DHCP và LAN Segment.
### 1. Switch ảo (Virtual Switch)
- Tương tự như một [Switch vật lý](https://vi.wikipedia.org/wiki/Switch_(m%E1%BA%A1ng)) thì Switch ảo kết nối các thành phần mạng ảo với nhau.
- Những  switch ảo hay còn gọi là mạng ảo, chúng có tên là VMnet0, VMnet1, VMnet2… một số switch ảo được gắn vào mạng một cách mặc định.
- Khi ta tạo các VMnet, thì trên máy thật sẽ tạo ra những card mạng ảo tương ứng với VMnet đó, dùng để kết nối Virtual Switch với máy tính thật, giúp máy thật và máy ảo có thể liên lạc được với nhau.
### 2. Card mạng máy ảo
- Khi bạn tạo một máy ảo mới, card mạng được tạo ra cho máy ảo, những card mạng này hiển thị trên hệ điều hành máy ảo với tên thiết bị như là AMD PCNET PCI hay Intel Pro/1000 MT Server Adapter.
>Lưu ý: Khi copy một máy ảo thì nên thay đổi địa chỉ MAC của nó, vì địa chỉ MAC là địa chỉ duy nhất, vậy nên chúng ta nên thay đổi địa chỉ MAC để tránh gặp lỗi khi làm việc với thệ thống.
```
Địa chỉ MAC: là địa chỉ định danh duy nhất hay còn gọi là số nhận dạng của mỗi thiết bị được các nhà sản xuất gán trên mỗi thiết bị.
```
### 3. DHCP server ảo của VMnet
- DHCP (Dynamic Host Configuration) server ảo đảm nhiệm việc cung cấp địa chỉ IP cho các máy ảo trong việc kết nối máy ảo vào các Switch ảo không có tính năng Bridged (VMnet0) là NAT và host only.
### 4. LAN Segment.
- Các card mạng của máy ảo có thể gắn kết với nhau thành từng LAN Segment. Không giống như VMnet, LAN Segment chỉ kết nối các máy ảo được gán trong một LAN Segment lại với nhau mà không có những tính năng như DHCP và LAN Segment không thể kết nối ra máy thật như các Virtual Switch VMnet.
>LAN Segment rất ít được sử dụng trong công việc.
## Dải mạng trong máy ảo
- Mỗi máy ảo sẽ có 3 loại dải mạng để lựa chọn kết nối:
  - Dải mạng Bridged.
  - Dải mạng NAT.
  - Dải mạng host-only.  
  
**1. Dải mạng Bridged:** sử dụng switch ảo VMnet0, card mạng của máy ảo này gắn trực tiếp với card mạng của máy tính thật. Máy ảo sẽ đóng vai trò như một máy trong mạng thật, có thể nhận được DHCP từ mạng ngoài hoặc đặt IP tĩnh cùng dải với mạng ngoài để có thể giao tiếp với các máy tính ngoài mạng hay lên Internet.  

**2. Dải NAT (Network Address Translation):** sử dụng switch ảo VMnet8 kết nối với máy thật, sử dụng IP của máy thật để giao tiếp với các mạng ngoài. Máy ảo được cấp IP nhờ DHCP ảo của VMware và máy thật sẽ đóng vai trò là NAT server cho các máy ảo.  

**3. Dải host-only:**  Ở chế độ này, Switch ảo không được kết nối gì với các card vật lý của máy tính thật, Vmware có lựa chọn cho phép Vmware là 1 thiết bị cấp phát DHCP cho các thiết bị kết nối vào Switch ảo. Các thiết bị nối đến Switch ảo này sẽ nhận được địa chỉ do chính VMware cấp. Các máy tính ở chế độ Host-Only có cùng dải IP sẽ kết nối được với nhau.
