# Mô Hình Thực Thể Liên Hệ (Entity Relationship Model - ER)
- ER thường được dùng như công cụ kết nối giữa nhà thiết kế CSDL và NSD.  
- ER là mô hình ngữ nghĩa để biểu diễn ngữ nghĩa của dữ liệu trong thế giới thực.  
- ER cho phép mô tả lược đồ khái niệm của một tổ chức mà không cần chú ý đến hiệu quả hoặc thiết kế CSDL vật lý.  

# Thành Phần Của ER
- Thực thể (Kiểu thực thể) - Tập thực thể.  
- Thuộc tính - Tập thuộc tính.  
- Liên kết (Kiểu liên kết) - Tập liên kết.  
- Khóa.  

## 1. Thực Thể - Tập Thực Thể
**Thực Thể (Entity):** Là đối tượng cụ thể hay trừu tượng, tồn tại thực sự và khá ổn định, có thể phân biệt được với nhau.  

**Tập Thực Thể (Entity Set):** Là nhóm các thực thể cùng kiểu.  

## 2. Thuộc Tính - Tập Thuộc Tính
**Thuộc Tính (Attribute):**  
- Mô tả 1 khía cạnh, 1 đặc tính của thực thể.  
- Kết hợp 1 thực thể trong tập thực thể với một giá trị trong miền giá trị của thuộc tính đó.  

**Tập Thuộc Tính (Attribute Set):**  
- Nhóm các đặc tính mô tả một tập thực thể.  

**Thuộc tính** có thể là đơn trị, đa trị hoặc phức hợp.  
  - *Thuộc tính phức hợp:* giá trị của thuộc tính có thể chia nhỏ thành các phần có ý nghĩa.  

  - *Thuộc tính đa trị:* giá trị của thuộc tính là những thành phần thuộc cùng một loại.  

  - *Thuộc tính dẫn xuất:* giá trị của thuộc tính được tính hoặc suy dẫn từ một hoặc nhiều giá trị của thuộc tính khác.  

**Định danh - Khóa (Key):** Một hoặc một tập các thuộc tính xác định duy nhất một thực thể trong một tập thực thể.  

## 3. Quan Hệ - Tập Quan Hệ
**Quan Hệ - Liên Kết (Relationship):**
- Sự kết hợp giữa một số thực thể thành 1 thể thống nhất, phản ánh sự tương quan giữa dữ liệu.  
- Là quan hệ dữ liệu giữa một hoặc nhiều tập thực thể.  
- Quan hệ có hai chiều.  

**Tập Quan Hệ (Relationship Set):**
- Là một tập các quan hệ cùng kiểu.  

> Một thực thể ở tập thể A thay đổi sẽ thay đổi các thực thể ở tập thực thể B mà có quan hệ về mặt dữ liệu với nó.  

**Xác định quan hệ dựa vào:**  
- Kết quả khảo sát thực tế.  
- Ngữ nghĩa của bài toán cần mô hình hóa.  

**Một số khái niệm trong quan hệ:**  
- Bậc của quan hệ (degree) – ngôi của quan hệ:  
> Đơn phân, Nhị phân, Tam phân,...  

Lực lượng tham gia vào mối liên hệ (cardinality)  
> 1–1, 1-1-1, 1-n, n-1, n-n-n, …  

- Ràng buộc tham gia của quan hệ  
> Tùy chọn  
> Bắt buộc  

# Khóa (Key)
**Khoá bao hàm – Siêu khoá (Super key)** lập một hoặc nhiều thuộc tính mà các giá trị của chúng xác định duy nhất một thực thể.  

**Khóa dự tuyển (Candidate Key)** là khóa bao hàm nhỏ nhất.  

**Khóa chính (Primary Key)** là một khoá dự tuyển được chuyển để xác định chính thực thể trong tập thực thể đó.  

# Ký Hiệu Trong Sơ Đồ ER

![](https://image.slidesharecdn.com/final-131107182926-phpapp02/95/final-31-638.jpg?cb=1383851922)  

# Một Số Vấn Đề Khác Trong Quan Hệ
## 1. Vai Trò Của Thực Thể Trong Quan Hệ
- Các tập thực thể tham gia vào mối quan hệ có thể không phân biệt.  
- Một quan hệ có thể có vai trò của thực thể, nếu nó làm rõ ngữ nghĩa của thực thể.  
- Nhãn (Label) chính là vai trò của thực thể khi tham gia vào quan hệ.  
- Trong quan hệ đệ quy cần chỉ rõ vai trò của thực thể khi tham gia vào mối quan hệ đó.  
- Trong quan hệ nhị phân, cần vẽ riêng các quan hệ đó và tên quan hệ chính là vai trò của thực thể đó khi tham gia vào quan hệ với thực thể khác.  

## 2. Thực Thể Yếu
Là thực thể  
- Mà sự tồn tại của nó phụ thuộc vào sự tồn tại của thực thể khác.  
- Không có khóa chính để xác định thực thể đó.  

- Trong ER, tập thực thể yếu luôn phải biểu diễn cùng với tập thực thể mà nó bị phụ thuộc.  
- Thực thể yếu được biểu diện bởi hình chữ nhật có hai nét.  

- Nếu mối quan hệ giữa 2 tập thực thể có thuộc tính định danh mô tả cho quan hệ đó, chuyển tập quan hệ thành tập thực thể gồm thực thể yếu.  
- Tập thực thể mới còn gọi là Thực thể đi lên từ mối quan hệ.  

## 3. Specialization/ Generalization
Là 2 tiến trình ngược nhau:  
- Specialization: Thiết kế Top - Down, chia 1 lớp cha (Superclass) thành nhiều lớp con (Subclass).  
- Generalization: Thiết kế Bottom - Up, gộp vài thực thể có chung đặc tính thành thực thể có mức cao hơn.  

Hai cách thiết kế trên kết quả thể hiện trên lược đồ ER giống nhau.  
Thực thể lớp con có thể tham gia:  
- Trực tiếp vào một quan hệ.  
- Gián tiếp vào một quan hệ thông qua lớp cha.  

## 4. Quan Hệ Kế Thừa (ISA)  
- A là một B.  
- A là subtype; B là supertype.  
- A kế thừa các thuộc tính của B và có thể có thêm những thuộc tính riêng mô tả A.  
- Có thể nghĩ tới quan hệ ISA khi có một số tập thực thể mà có các thuộc tính chung.  
- Các thuộc tính chung sẽ trở thành thuộc tính của tập thực thể cha (supertype).  
- Các tập thực thể con (subtype) chỉ còn các thuộc tính của riêng nó và khóa của tập thực thể cha.  
> A ISA B.  

## 5. Gộp nhóm (Aggregation)
- Thể hiện mối liên hệ giữa các mối quan hệ - mỗi giá trị của mối quan hệ đó lại tham gia vào một mối quan hệ khác.  
