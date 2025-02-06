## Dữ liệu và thông tin
### Dữ liệu
- Là các sự kiện được ghi lại và lưu trữ trong thiết bị lưu trữ.
- Là sự kiện, văn bản... có giá trị cho mục đích của một nhóm người sử dụng.
### Thông tin
- Là dữ liệu được xử lí để tăng thêm giá trị cho người sử dụng.
- Thể hiện qua các giá trị của dữ liệu.
## Hệ thống file
- Dữ liệu được định nghĩa và tổ chức bằng các cấu trúc của ngôn ngữ lập trình.
### Các hạn chế
- Tổ chức lưu trữ dữ liệu phụ thuộc hoàn toàn vào ngôn
ngữ sử dụng để xây dựng chương trình ứng dụng
- Việc chia sẻ dữ liệu với các hệ thống khác hạn chế
- Mỗi ứng dụng cần một hệ thống tệp riêng
- Nếu cải tiến ứng dụng thì có thể phải thay đổi cả cấu trúc
hệ thống file dữ liệu do không tương thích với ngôn ngữ
mới hoặc một vài công cụ không được hỗ trợ
- Tìm kiếm dữ liệu chậm do duyệt tuần tự trên file dữ liệu
- Chi phí bảo trì dữ liệu lớn
## Cơ sở dữ liệu
- Còn được gọi là `Database`.
- Là hệ thống tích hợp các tập tin liên kết với nhau về mặt logic.
- File: Chứa các bản ghi **(record)**.
- Record: Gồm các tập tin trên các trường **(field)**.
- Field: xác định dữ liệu lưu trữ cho tất cả các bản ghi.
### Hiệu quả
- Hạn chế dư thừa, nâng cao tính nhất quán
- Độc lập giữa Dữ liệu – Chương trình
- Giảm thời gian phát triển chương trình ứng dụng để đáp
ứng nghiệp vụ mới
- Nâng cao chất lượng dữ liệu và các tiêu chuẩn khác sau đó
tạo quy trình thống nhất khi cập nhật, bảo vệ dữ liệu
- Tăng khả năng tìm kiếm, tổng hợp dữ liệu nhanh
- Giảm chi phí bảo trì dữ liệu, chương trình
### Mục đích  
Tích hợp

- Tập trung và quản lí các dữ liệu rời rạc.
- Dữ liệu không tồn tại riêng lẻ mà có sự phụ thuộc lẫn nhau.  

Chia sẻ

- Nhiều user cùng sử dụng đồng thời.
- Dữ liệu có thể sử dụng được cho nhiều mục đích, nhiều ứng dụng.

## Hệ Quản Trị Cơ Sở Dữ Liệu (Database Management System - DBMS)
- Phần mềm cho phép tạo lập, quản lý và truy xuất các tập tin CSDL.  

Tính năng:
- Quản lý dữ liệu cố định.  
- Truy xuất hiện quả dữ liệu lớn.  
- Hỗ trợ ít nhất một mô hình dữ liệu.  
- Hộ trợ ngôn ngữ bậc cao để người sử dụng định nghĩa cấu trúc, truy xuất và thao tác dữ liệu.  
- Quản lý giao dịch.  
- Tự thích ứng, phục hồi nếu có sự cố.  

## Các Mức Trừu Tượng Trong Hệ Thống Cơ Sở Dữ Liệu
**Mức Vật Lý (Physical Level)**  
- Tập hợp các tập tin, các chỉ mục, những cấu trúc lưu trữ khác dùng để truy xuất.  
- Tồn tại trong các thiết bị lưu trữ.  
- Quản trị bởi phần mềm quản trị CSDL.  

**Mức Khái Niệm (Conceptual Level)**  
- Trừu tượng hóa thế giới thực.  
- CSDL khái niệm được thiết kế như một hệ thống đồng nhất.  
- DBMS cho phép gộp các tập tin lại và đọc chúng theo phương pháp riêng.  

**Mức Khung Hình (Extenal Level)**  
- Khung nhìn hay lược đồ con được rút ra từ CSDL khái niệm, cần thiết cho chương trình của một nhóm người sử dụng.  
- DBMS cung cấp phương tiện khai báo khung nhìn, diễn đạt câu vấn tin và thao tác trên khung nhìn.  
- Đảm bảo “an ninh” của hệ thống.  
- DL được xử lý trong khung nhìn có thể được xây dựng từ CSDL khái niệm mà không thực sự tồn tại.  

Việc kết nối với các mức lược đồ là cần thiết.  
- Chương trình kết nối với lược đồ ngoài.  
- Chương trình kết nối với lược đồ trong để thực hiện.  

## Tính Độc Lập Dữ Liệu
Có 2 mức:  
- **Độc lập vật lý:** Khả năng thay đổi lược đồ Internal nhưng không làm thay đổi lược đồ Logic, External hay chương trình ứng dụnng.  
- **Độc lập Logic:** Khả năng thay đổi lược đồ Logic mà không làm thay đổi lược đồ External hay chương trình ứng dụng.  

Giao diện giữa các mức thành phần khác nhau.  

Sự độc lập của dữ liệu được chia sẻ làm cho  
- Người sử dụng chia sẻ dữ liệu mà không cần quan tâm tới cấu trúc lưu trữ dữ liệu, tăng linh hoạt trong lập trình.  
- Có thể sửa các CSDL mà không quan tâm đến các chương trình của người sử dụng.  

## Logic Data Model
**Ngôn ngữ định nghĩa dữ liệu (Data Definition Language - DDL)** dùng để mô tả lược đồ CSDL.  
- Mối quan hệ giữa các dữ liệu.  
- Ngữ nghĩa của dữ liệu.  
- Ràng buộc giữa các dữ liệu.  
**Ngôn ngữ thao tác dữ liệu (Data Manipulation Language - DML)** dùng để truy vấn và cập nhật CSDL hiện hành.  
Mô hình dữ liệu gồm 2 phần:  
- DDL: Hệ thống ký hiệu để mô tả dữ liệu.  
- DML: Tập hợp các phép toán thao tác trên dữ liệu.  

Mô hình dữ liệu cho biết cấu trúc của CSDL.  

Các loại mô hình dữ liệu:  
- Cơ sở bản ghi (Record – based)  
  - Mô hình dữ liệu phân cấp (Hierarchical data model)  
  - Mô hình dữ liệu mạng (Network data model)  
  - Mô hình dữ liệu quan hệ (Relational data model)  
- Cơ sở đối tượng (Object – based)  
  - Mô hình dữ liệu ngữ nghĩa (Sematic data model)  
  - Mô hình dữ liệu hướng đối tượng (Oriented data model)  

### 1. Mô hình dữ liệu quan hệ 
- Mô hình dữ liệu quan hệ bao gồm một hoặc nhiều quan hệ.  
- Phép toán thao tác dữ liệu: dựa trên Lý thuyết tập hợp của Toán học gọi là *Đại số quan hệ*.  

### 2. Mô hình dữ liệu mạng
- Là mô hình thực thể trong đó các mối liên hệ bị hạn chế trong kiểu nhị phân và nhiều - một.  
- Phép toán thao tác dữ liệu: dùng đường nối.  


### 3. Mô hình dữ liệu phân cấp
- Là mô hình dữ liệu mạng gồm nhiều cây, trong đó đường nối
chỉ đi theo hướng từ con đến cha.  

### 4. Mô hình dữ liệu hướng đối tượng
- Là mô hình dữ liệu trong đó các thuộc tính dữ liệu và các phương thức thao tác trên các thuộc tính đó đều được đóng gói trong các cấu trúc gọi là đối tượng.  

## Kiến trúc Client - Server
- Hệ thống CSDL không thay đổi, công việc được phân chia.  
- CSDL đặt ở Database Server.  
- Client gửi các query và các câu lệnh khác tới Server.  
- Server gửi trả lời dưới dạng bảng hoặc quan hệ tới Client.  
- Xu hướng chuyển nhiều công việc hơn cho Client bởi vì Server sẽ bị nghẽn nếu có nhiều người dùng cùng truy nhập.  

### Database server  
- Quản lý một CSDL để nhiều user cùng sử dụng đồng
thời.  
- Điều khiển an toàn trong các form truy nhập dữ liệu.  
- Bảo vệ dữ liệu bằng backup và recovery.  
- Các qui tắc toàn vẹn dữ liệu bắt buộc thông qua client
application.  
Client application
- Thể hiện giao diện với user.  
- Quản lý các logic trình diễn thông qua GUI.  
- Thực hiện logic của ƯD thông qua field checking.  
- Yêu cầu và nhận dữ liệu từ server.  
