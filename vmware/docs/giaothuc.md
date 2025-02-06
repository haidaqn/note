# Mục Lục
[I. Giao Thức SSH](#SSH)  
  - [1. Tổng Quan](#1TQ)  
  - [2. SSH Là Gì?](#SSHLG)
  - [3. Cách Thức Làm Việc](#SSHCTLV)  

[II. Giao Thức DHCP](#DHCP)  
  - [1. Tổng Quan](#2TQ)  
  - [2. Kiến Trúc DHCP](#KT)
  - [3. Cách hoạt động của DHCP](#CTHD)  

## <a name = "SSH"></a> I. Giao Thức SSH
### <a name = "1TQ"></a> 1. Tổng Quan
- SSH (Secure Shell) là một giao thức mạng dùng để thiết lập kết nối mạng một cách bảo mật.  
- SSH hoạt động ở lớp trên trong mô hình phân lớp TCP/IP.
- Các công cụ SSH cung cấp cho người dùng cách thức để thiết lập kết nối mạng được mã hoá để tạo một kênh kết nối riêng tư.

### <a name = "SSHLG"></a> 2. SSH Là Gì?
- SSH là một chương trình tương tác giữa máy chủ và máy khách có sử dụng cơ chế mã hoá nhằm ngăn chặn các hiện tượng đánh cắp thông tin trên đường truyền.

### <a name = "SSHCTLV"></a> 3. Cách Thức Làm Việc?

SSH làm việc thông qua 3 bước đơn giản:
- **Định danh host:** 
  - Việc định danh host được thực hiện qua việc trao đổi khoá. Mỗi máy tính có hỗ trợ kiểu truyền thông SSH có một khoá định danh duy nhất. Khoá này gồm **hai thành phần**: *khoá riêng và khoá công cộng*.  
  - **Khoá công cộng** được sử dụng khi cần trao đổi giữa các máy chủ với nhau trong phiên làm việc SSH, dữ liệu sẽ được mã hoá bằng khoá công khai và chỉ có thể giải mã bằng **khoá riêng**.
  - Khi hai hệ thống bắt đầu một phiên làm việc SSH, máy chủ sẽ gửi khoá công cộng của nó cho máy khách. Máy khách sinh ra một khoá phiên ngẫu nhiên và mã hoá khoá này bằng khoá công cộng của máy chủ, sau đó gửi lại cho máy chủ. Máy chủ sẽ giải mã khoá phiên này bằng khoá riêng của mình và nhận được khoá phiên. 
  - Khoá phiên này sẽ là khoá sử dụng để trao đổi dữ liệu giữa hai máy.

- **Mã hoá:** 
  - Dữ liệu gửi/nhận trên đường truyền đều được mã hoá và giải mã theo cơ chế đã thoả thuận trước giữa máy chủ và máy khách.
  - Các cơ chế mã hoá thường được chọn bao gồm: 3DES, IDEA, và Blowfish.

- **Chứng thực:** Xác thực người sử dụng có quyền đăng nhập hệ thống.

## <a name = "DHCP"></a> II. Giao Thức DHCP
### <a name = "2TQ"></a> 1. Tổng Quan
**DHCP - Giao thức cấu hình động máy chủ (Dynamic Host Configuration Protocol)**
- Là một giao thức cho phép cấp phát địa chỉ IP một cách tự động cùng với các cấu hình liên quan khác
- Máy tính được cấu hình một cách tự động vì thế sẽ giảm việc can thiệp vào hệ thống mạng.
- Nó cung cấp một database trung tâm để theo dõi tất cả các máy tính trong hệ thống mạng.
- Tránh trường hợp hai máy tính khác nhau lại có cùng địa chỉ IP.

### <a name = "KT"></a> 2. Kiến trúc DHCP
Có 3 thành phần bên trong kiến trúc DHCP bao gồm DHCP client, DHCP server, và DHCP relay agents:  
- **DHCP client** là thiết bị bất kỳ có thể kết nối vào mạng, và có thể giao tiếp với máy chủ DHCP.
- **DHCP server** là thiết bị cấp phát địa chỉ IP.
- **DHCP relay agents** là thiết bị trung gian chuyển tiếp yêu cầu giữa DHCP client và DHCP server.

### <a name = "CTHD"></a> 3. Cách Thức Hoạt Động
**Chức năng chủ yếu:**
- DHCP tự động quản lý các địa chỉ IP và loại bỏ được các lỗi có thể làm mất liên lạc.
- Nó tự động gán lại các địa chỉ chưa được sử dụng.

**Cách thức vận hành:**
- DHCP khai thác ưu điểm của giao thức truyền tin và các kỹ thuật khai báo cấu hình được định nghĩa trong **[BOOTP (bootstrap protocol)](#BOOTP)**, trong đó có khả năng gán địa chỉ.  

**Bước 1:** Máy trạm khởi động với "địa chỉ IP rỗng" cho phép liên lạc với máy chủ DHCP bằng giao thức TCP/IP. Nó chuẩn bị một thông điệp chứa **[địa chỉ MAC (Media Access Control)](#DCM)** và tên máy tính. Máy trạm phát tán liên tục thông điệp này lên mạng cho đến khi nhận được phản hồi từ máy chủ.  

**Bước 2:** Mọi máy chủ DHCP có thể nhận thông điệp và chuẩn bị địa chỉ IP cho máy trạm. Nếu máy chủ có cấu hình hợp lệ cho máy trạm, nó chuẩn bị thông điệp chứa địa chỉ MAC của khách, địa chỉ IP mượn, subnet mask, địa chỉ IP của máy chủ và thời gian cho mượn. Địa chỉ mượn được đánh dấu là "reserve". Máy chủ DHCP phát tán thông điệp mượn này lên mạng.

**Bước 3:** Khi máy khách nhận thông điệp và chấp nhận một trong các địa chỉ IP, máy trạm phát tán thông điệp này để khẳng định nó đã chấp nhận địa chỉ IP và từ máy chủ DHCP nào.

**Bước 4:** Máy chủ DHCP khẳng định toàn bộ sự việc với máy trạm. Máy trạm chỉ chấp nhận một thông điệp, sau đó phát tán thông điệp khẳng định lên mạng, vì thế các máy chủ DHCP khác rút lại thông điệp của mình và hoàn trả địa chỉ IP vào vùng địa chỉ.

# Chú Thích: 
<a name = "BOOTP"></a> **1. BOOTP:** là một giao thức Internet protocol được sử dụng để gán một địa chỉ IP và một loạt các tham số bổ sung cho một máy tính trong mạng TCP/IP.  
<a name = "DCM"></a> **2. Địa chỉ MAC:** là mã duy nhất được gán bởi nhà sản xuất cho từng phần cứng mạng
