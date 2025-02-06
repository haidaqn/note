## Cấu trúc filesystem

* Trên nhiều hệ thống, bao gốm cả Linux, `filesystem` được cấu trúc như một cái cây. Cây thường được vẽ đảo ngược, và bắt đầu từ thư mục gốc, đánh dấu khởi đầu của `filesystem` phân cấp và được biểu thị bằng **/**.
* Một số ví dụ về các loại hệ thống tập tin mà Linux hỗ trợ là:
  1. ext3, ext4, btrfs, xfs (filesystems gốc của Linux)
  2. vfat, ntfs, hfs (filesystems từ các hệ điều hành khác)
* Lệnh `mount` được sử dụng để đính kèm một `filesystem` ở đâu đó trong cây `filesytem`. Đối số bao gồm nút thiết bị và điểm gắn kết.
```
$ mount /dev/sda5 /mnt
```
* Lệnh `umount` được sử dụng để tách `filesystem` khỏi điểm gắn kết.
```
$ umount /mnt
```
* Lệnh `df -Th` (disk-free) sẽ hiển thị thông tin về các `filesystem` được gắn bao gồm các kiểu và thống kê không gian hiện đang sử dụng và sẵn có.
```
# df -Th
Filesystem                 Type      Size  Used Avail Use% Mounted on
/dev/mapper/os-root        xfs        50G  2.0G   48G   4% /
devtmpfs                   devtmpfs  1.8G     0  1.8G   0% /dev
tmpfs                      tmpfs     1.9G  4.0K  1.9G   1% /dev/shm
tmpfs                      tmpfs     1.9G  8.6M  1.8G   1% /run
tmpfs                      tmpfs     1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/mapper/swift01-zone01 xfs        49G   33M   49G   1% /srv/node/z1d1
/dev/mapper/swift02-zone02 xfs        49G   33M   49G   1% /srv/node/z2d1
/dev/sda1                  xfs       497M  167M  331M  34% /boot
/dev/mapper/os-data        xfs        20G  261M   20G   2% /data
```
## Thư mục home
* Trong bất kỳ hệ thống UNIX nào, mỗi người dùng đều có thư mục chính của riêng mình, thường được đặt trong `/ home`.
* Thư mục `/ home` thường được gắn kết như là một `filesystem` riêng biệt trên phân vùng riêng của nó, hoặc thậm chí được xuất khẩu từ xa trên mạng thông qua NFS.
## Thư mục nhị phân
* Thư mục `/ bin` chứa các tệp nhị phân thực thi
* Tất cả các thư mục nhị phân nằm trong phân vùng gốc.
## Thư mục thiết bị
* Thư mục `/ dev` chứa các nút thiết bị, một loại `pseudo-file` được hầu hết các thiết bị phần cứng và phần mềm sử dụng, ngoại trừ các thiết bị mạng. Thư mục `/ dev` chứa các mục như:
```
/dev/sda1
/dev/lp1
/dev/dvd1
```
## Thư mục biến
* Thư mục `/ var` chứa các tệp được dự kiến sẽ thay đổi về kích thước và nội dung khi hệ thống đang chạy ví dụ như: 
  * Tệp nhật ký hệ thống: / var / log
  * Gói tệp: / var / lib
  * Hàng đợi in: / var / spool
  * Tệp tạm thời: / var / tmp
  * Thư mục chính của FTP: / var / ftp
  * Thư mục máy chủ web: / var / www
## Thư mục cấu hình hệ thống
 * Thư mục `/ etc` là trang chủ cho các tệp cấu hình hệ thống. Nó không chứa các chương trình nhị phân, mặc dù có một số tập lệnh thực thi.
## Thư mục khởi động
 * Thư mục `/ boot` chứa một số tệp cần thiết cần thiết để khởi động hệ thống. Đối với mỗi hạt nhân thay thế được cài đặt trên hệ thống có bốn tập tin:
  * `vmlinuz` là hạt nhân Linux được nén, cần thiết để khởi động
  * `initramfs` là hệ thống tệp ram ban đầu, bắt buộc để khởi động
  * `config` là tệp cấu hình hạt nhân, chỉ được sử dụng để gỡ lỗi
  * `System.map` chứa bảng ký hiệu hạt nhân, chỉ được sử dụng để gỡ lỗi
## Thư mục thư viện
* Thư mục `/ lib` chứa các thư viện (mã chung được các ứng dụng chia sẻ và cần thiết để chúng chạy) cho các chương trình cần thiết trong thư mục `/ bin` và `/ sbin`.
*  Hầu hết trong số này được gọi là các thư viện được nạp động (hay các thư viện chia sẻ hoặc đối tượng chia sẻ).
## Thư mục bổ sung
|Thư mục|Cách sử dụng|
|---------|-----|
| /opt | Các gói phần mềm ứng dụng tùy chọn |
| /sys | Pseudo-filesystem ảo cung cấp thông tin về hệ thống và phần cứng. Có thể được sử dụng để thay đổi thông số hệ thống và dùng cho mục đích gỡ lỗi |
| /srv | Dữ liệu trang web cụ thể được hệ thống phân phối. Ít khi sử dụng |
| /tmp | Hồ sơ tạm thời; trên một số bản phân phối những tập tin này bị xóa khi khởi động lại |
| /media | thường được đặt ở nơi các thiết bị di động, chẳng hạn như đĩa CD, DVD và ổ USB được lắp. Trừ khi cấu hình cấm nó, Linux sẽ tự động gắn kết phương tiện lưu động trong thư mục này khi chúng được phát hiện |
| /usr | Ứng dụng, tiện ích và dữ liệu đa người dùng |
| /usr/include | Các tệp tiêu đề được sử dụng để biên dịch các ứng dụng |
| /usr/lib | Thư viện cho các chương trình nhị phân |
| /usr/lib64 | Thư viện 64 bit cho các chương trình nhị phân |
| /usr/share | Dữ liệu chia sẻ được các ứng dụng sử dụng, thường độc lập về kiến trúc |
| /usr/src | Mã nguồn, thường cho hạt nhân Linux |
| /usr/local | Dữ liệu và chương trình cụ thể cho máy cục bộ |
>Bài viết gốc: [Filesystem](https://github.com/lacoski/linux-notes/edit/master/content/filesytem.md)
