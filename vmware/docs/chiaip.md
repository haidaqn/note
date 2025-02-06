## Chia IP
Ví dụ:    
**Có IP là 192.168.1.0. Yêu cầu phân làm chia làm 3 mạng con**

**Bước 1: Trước hết ta phân tích cấu trúc của địa chỉ: 192.168.1.0 như sau:**
  - Địa chỉ NetMask: 255.255.255.0
  - Network ID: 11111111.11111111.11111111
  - HostID: 00000000

**Bước 2: Tìm số bit cần mượn**
 - Để chia thành 3 mạng con ta cần mượn thêm 2 bit. Để tìm số bit cần mượn ta làm theo công thức 2^n >= m (m là số subnet cần chia, n là số bit mượn).

||||||||||  
|---|---|---|---|---|---|---|---|---|  
|n (số bit mượn)|	1|	2|	3|	4|	5|	6|	7|	8|  
|Bước nhảy|	128|	64|	32|	16|	8|	4|	2|	1|  

- Sau khi mượn 2 bit, ta có cấu trúc mới ở dạng nhị phân là:
  - Địa chỉ NetMask: 255.255.255.11111111.11111111.11111111.11000000 (2 bit mượn ta đặt là 1)
  - Network ID: 11111111.11111111.11111111.11
  - Host ID: 000000  
  - Địa chỉ NetMask dạng thập phân: 255.255.255.192
**Bước 3: Xác định bước nhảy**
- Địa chỉ IP mới lúc này là: 192.168.1.0 / 26 (26 = 24 + 2 bit mượn)
- Bước nhảy: k = 64

**Kết quả: Vậy ta có những mạng con sau:**

|IP|Netmask|
|:---:|:---:|
|192.168.1.0| Netmask: 255.255.255.192|
|192.168.1.64| Netmask:  255.255.255.192|
|192.168.1.128| Netmask: 255.255.255.192|
|192.168.1.192| Netmask: 255.255.255.192|

**Ngoài ra ta có vài công thức sau:**
  - Công thức xác định số lượng mạng mà một netmask có thể hỗ trợ   
    `2^(độ dài netmask - Số lượng phân đoạn đã sử dụng) - 2 `  
  > VD: Trong 24-bit netmask, 225.225.225.0 (có 3 phân đoạn được sử dụng) => số lượng mạng nó có thể hỗ trợ là: 2^(21-3) - 2 = 2097152
    
  - Công thức xác định số lượng máy chủ mà một netmask có thể hỗ trợ   
   `2^(số lượng số "0") - 2`
   > VD: Trong 24-bit netmask, 225.225.225.0 (được viết dưới dạng nhị phân là: 11111111.11111111.11111111.00000000 - Có 8 số "0") => số lượng máy chủ nó có thể hỗ trợ là: 2^(8) - 2 = 254  
   > => Mạng lớp c có thể hỗ trợ tối đa là 254 máy chủ.
