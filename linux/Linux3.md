## Nhân hệ điều hành
- Là thành phần trung tâm của các OS.  
- Quản lý các tài nguyên phần cứng và phần mềm
- Nhân có thể cung cấp *các tầng trừu tượng mức thấp nhất* cho các tài nguyên máy tính (đặc biệt là bộ nhớ, CPU, và các thiết bị vào ra mà phần mềm ứng dụng cần điều khiển để thực hiện các chức năng của mình).  
- Nhân hệ điều hành thường cung cấp các tiện ích xử lý này cho các tiến trình của các phần mềm ứng dụng qua các cơ chế liên lạc giữa các *tiến trình* (inter-process communication) và *các hàm hệ thống* (system call).  
>  Nhân hệ điều hành dưới một khía cạnh nào đó là một cái tên đơn giản *biếu thị cho* **tầng trừu tượng ở mức thấp nhất** được xử lý trong các phần mềm trước khi đi qua trình biên dịch ngôn ngữ assembly sang ngôn ngữ máy và đưa đến phần cứng của máy tính để thi hành.  
  
-  Khi *boot loader* bắt đầu thực thi nhân hệ điều hành trong *supervisor mode*, nhân hệ điều hành sau đó được *nạp phần đầu* của nó và thi hành tiến trình đầu tiên. 
- Sau khi khởi động hoàn tất, nhân hệ điều hành *không được thực thi ngay lập tức*, nó chỉ nằm trong *lời trả lời cho sự kiện bên ngoài*.
- Ngoài ra, nhân hệ điều hành còn cung cấp một vòng lặp được thực thi bất cứ lúc nào mà không có tiến trình nào được thực thi; được gọi là *tiến trình nhàn rỗi*.  
![](https://www.google.com.vn/search?q=Nhân+hệ+điều+hành&tbm=isch&tbs=rimg:CaMqyFfuSYZcIjixYUjkD0x9VwV3nTbABLo05xStMHosizJ4A7_1G3m5_1dCF7cNKRi0UM1I9rYgi7_1UkkPkp9yAZTZioSCbFhSOQPTH1XEeanz0tJIq_1zKhIJBXedNsAEujQR1fOQ6Igkxg8qEgnnFK0weiyLMhH_16298Fhqd8CoSCXgDv8bebn90EWuEwx0uPerZKhIJIXtw0pGLRQwRfIcGLwFBE2UqEgnUj2tiCLv9SREdEHb8N9ITfyoSCSQ-Sn3IBlNmEXJOuOigJSti&tbo=u&sa=X&ved=2ahUKEwi2renMwqrcAhWJwI8KHT0-BVcQ9C96BAgBEBs&biw=1366&bih=635&dpr=1#imgrc=GKXm47WukF_atM:)  
