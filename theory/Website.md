# *CÁCH MỘT TRANG WEB VẬN HÀNH*

## Cách thức một trình duyệt truy cập

1. Tra cứu DNS.
2. Trình duyệt gửi một yêu cầu HTTP.
3. Sever phản hời và gửi lại file HTML được yêu cầu.
4. Trình duyệt bắt đầu thông dịch thành HTML.
5. Trình duyệt gửi yêu cầu bổ sung cho đối tượng được những trong file HTML (các tệp CSS, các ảnh, JavaScript,...).

### 1. Tra cứu DNS:

>Bước đầu tiên để truy cập một trang là chuyển đổi từ miển sang một địa chỉ IP và truy cập vào một trong những server để trình duyệt biết địa chỉ IP chính xác rồi gửi yêu cầu của nó đến.

**Danh sách các thiết bị sẽ lưu trữ bộ nhớ đệm theo thứ tự chúng được chọn:**

* Bộ nhớ đệm của trình duyệt.
* Bộ nhớ đệm của hệ điều hành.
* Bộ nhớ đệm của Router.
* Bộ nhớ đệm của ISP DNS.

>Bộ nhớ đệm được lưu trữ lần lượt từng thiết bị lưu trữ bộ nhớ đệm. Nếu không có thông tin cần thiết thì tìm kiếm đệ quy của server gốc sẽ diễn ra.

### 2. Trình duyệt gửi yêu cầu:

>Sau khi trình duyệt thực hiện xong tra cứu DNS, nó gửi một yêu cầu HTTP đến một server thích hợp. Không nhất thiết là HTTP, có thể là HTTPS hoặc gần hơn là HTTP/2. Nó sẽ gửi một file cụ thể, thưởng là HTML.

### 3. Phản hồi của server:

>Một khi máy chủ nhận được một yêu cầu thì nó sẽ trả lời. Mặc dù vậy, nó phụ thuộc vào một số thứ. **Ví dụ:** *Nếu trang được truy cập nó không còn trên server nó sẽ gửi lại lỗi 404 (không tìm thấy file).*

>Mỗi trạng thái thì máy chủ gửi về một mã khác nhau. Lý tưởng nhất là 200 những truy cập lại có thể là 404 hoặc 301 hoăc 500. Bất cứ mã nào ngoài 200 nghĩa là trình duyệt của bạn đang có lỗi.

### 4. Trình duyệt thông dịch trang:

>Mỗi lần trình duyệt nhận được một file HTML thì nó cần thông dịch trang và nó phải làm một vài bước trước khi hiển thị. Các bước đó được gọi là ***đường dẫn thông dịch quan trọng*** trong đó trình duyệt của bạn cần: 
>1. Xử lý HTML, đánh dấu và xây dựng cây DOM.
>2. Xử lý CSS, đánh dấu và xây dựng cây CSSOM.
>3. Kết hợp DOM và CSSOM vào một cây thông dịch.
>4. Chạy bố cục trên cây thông dịch để tính toán các nút.
>5. In các nút lên màn hình.
>
> Để thực hiện các bước trên, trình duyệt có thể cần các file bổ sung được nhúng trong HTML.

**Nguồn:** [What Happens When Your Browser Requests a Web Page?](https://vanseodesign.com/web-design/browser-requests/).
