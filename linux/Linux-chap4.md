## Quyền file
* Trong Linux và các hệ điều hành UNIX khác, mọi tệp đều được liên kết với người dùng là chủ sở hữu.
* Mỗi tệp có quyền nhất định: đọc, ghi và thực thi.

|Câu lệnh|Kết quả|
|-------|-----------|
|chown| Được sử dụng để thay đổi quyền sở hữu người dùng của một tệp hoặc thư mục |
|chgrp|Được sử dụng để thay đổi quyền sở hữu nhóm|
|chmod|Được sử dụng để thay đổi quyền trên tệp|

* Tệp có ba loại quyền: đọc (r), viết (w), thực thi (x). Được biểu diễn theo thứ tự sau rwx.
* Các quyền này ảnh hưởng đến ba nhóm chủ sở hữu: người dùng (u), nhóm (g) và những người khác (o). Do đó, bạn có ba nhóm ba quyền sau đây:

|rwx:|rwx:|rwx|
|----|----|---|
|u:|g:|o|

* Có một số cách khác nhau để sử dụng lệnh `chmod`. Ví dụ: để cho phép chủ sở hữu thực thi quyền:
```
$ ls -l test1
-rw-rw-r-- 1 joy caldera 1601 Mar 9 15:04 test1
$ chmod u+x test1
$ ls -l test1
-rwxrw-r-- 1 joy caldera 1601 Mar 9 15:04 test1
```

>Bài viết gốc: [File permission](https://github.com/lacoski/linux-notes/blob/master/content/file_permissions.md).
