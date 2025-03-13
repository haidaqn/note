# Giới thiệu về MongoDB

MongoDB là một cơ sở dữ liệu NoSQL mã nguồn mở, được thiết kế để lưu trữ và truy vấn dữ liệu dạng tài liệu (document-oriented). Khác với các cơ sở dữ liệu quan hệ (RDBMS) như MySQL, PostgreSQL, MongoDB sử dụng cấu trúc JSON-like (BSON) để lưu trữ dữ liệu, giúp dễ dàng mở rộng và linh hoạt hơn trong việc quản lý dữ liệu phi cấu trúc.

## Tính năng nổi bật của MongoDB so với các cơ sở dữ liệu khác

- **Linh hoạt trong việc lưu trữ dữ liệu**: MongoDB không yêu cầu schema cố định, cho phép lưu trữ dữ liệu với cấu trúc linh hoạt.
- **Khả năng mở rộng**: Hỗ trợ sharding, giúp phân phối dữ liệu trên nhiều máy chủ để tăng khả năng xử lý và lưu trữ.
- **Hiệu suất cao**: Tối ưu hóa cho các truy vấn đọc và ghi nhanh chóng.
- **Hỗ trợ đa nền tảng**: Chạy trên nhiều hệ điều hành khác nhau như Windows, Linux, macOS.
- **Cộng đồng và tài liệu phong phú**: Có một cộng đồng lớn và nhiều tài liệu hỗ trợ.

---

MongoDB cung cấp nhiều toán tử (`$operator`) giúp truy vấn và xử lý dữ liệu trong `find()`, `aggregate()`, hoặc cập nhật dữ liệu (`update()`). Dưới đây là danh sách các nhóm toán tử quan trọng kèm theo giải thích và ví dụ.

---

## 1️⃣ **Toán tử so sánh**
Dùng để so sánh giá trị của một trường.

| Toán tử   | Ý nghĩa |
|-----------|--------|
| `$eq`     | Bằng (`=`) |
| `$ne`     | Không bằng (`!=`) |
| `$gt`     | Lớn hơn (`>`) |
| `$gte`    | Lớn hơn hoặc bằng (`>=`) |
| `$lt`     | Nhỏ hơn (`<`) |
| `$lte`    | Nhỏ hơn hoặc bằng (`<=`) |
| `$in`     | Nằm trong danh sách giá trị |
| `$nin`    | Không nằm trong danh sách |

🔹 **Ví dụ**: Tìm sản phẩm có giá từ 100,000 đến 500,000
```js
db.products.find({
  price: { $gte: 100000, $lte: 500000 }
})
```

🔹 **Ví dụ**: Tìm sản phẩm có danh mục là "quần áo" hoặc "phụ kiện"
```js
db.products.find({
  category: { $in: ["quần áo", "phụ kiện"] }
})
```

---

## 2️⃣ **Toán tử logic**
Dùng để kết hợp nhiều điều kiện.

| Toán tử  | Ý nghĩa |
|----------|--------|
| `$and`   | Thỏa tất cả điều kiện (`&&`) |
| `$or`    | Chỉ cần một trong các điều kiện đúng (`||`) |
| `$nor`   | Phủ định của `$or` (không thỏa mãn bất kỳ điều kiện nào) |
| `$not`   | Phủ định một điều kiện |

🔹 **Ví dụ**: Tìm sản phẩm giá trên 200k và thuộc danh mục "quần áo"
```js
db.products.find({
  $and: [{ price: { $gt: 200000 } }, { category: "quần áo" } ]
})
```

🔹 **Ví dụ**: Tìm sản phẩm không thuộc danh mục "điện tử" và không có giá dưới 500k
```js
db.products.find({
  $nor: [{ category: "điện tử" }, { price: { $lt: 500000 } } ]
})
```

---

## 3️⃣ **Toán tử mảng**
Dùng để kiểm tra giá trị trong một mảng.

| Toán tử  | Ý nghĩa |
|----------|--------|
| `$all`   | Phải chứa tất cả giá trị trong mảng |
| `$size`  | Kiểm tra số lượng phần tử trong mảng |
| `$elemMatch` | Kiểm tra điều kiện trên phần tử của mảng |

🔹 **Ví dụ**: Tìm sản phẩm có tất cả tag "mới" và "bán chạy"
```js
db.products.find({
  tags: { $all: ["mới", "bán chạy"] }
})
```

🔹 **Ví dụ**: Tìm sản phẩm có ít nhất 3 tag
```js
db.products.find({
  tags: { $size: 3 }
})
```

🔹 **Ví dụ**: Tìm đơn hàng có ít nhất một sản phẩm có giá trên 1 triệu
```js
db.orders.find({
  products: { $elemMatch: { price: { $gt: 1000000 } } }
})
```

---

## 4️⃣ **Toán tử đánh giá (Evaluation Operators)**
Dùng để kiểm tra giá trị bằng cách sử dụng biểu thức hoặc điều kiện đặc biệt.

| Toán tử    | Ý nghĩa |
|------------|--------|
| `$regex`   | Tìm kiếm theo chuỗi ký tự (Regex) |
| `$mod`     | Lấy phần dư của phép chia |
| `$text`    | Tìm kiếm toàn văn (full-text search) |
| `$where`   | Chạy JavaScript tùy chỉnh để lọc dữ liệu |

🔹 **Ví dụ**: Tìm sản phẩm có tên chứa từ "Nike" (không phân biệt hoa thường)
```js
db.products.find({
  name: { $regex: "Nike", $options: "i" }
})
```

🔹 **Ví dụ**: Tìm sản phẩm có giá chia hết cho 5
```js
db.products.find({
  price: { $mod: [5, 0] }
})
```

---

## 5️⃣ **Toán tử cập nhật**
Dùng trong `update()` để thay đổi dữ liệu.

| Toán tử  | Ý nghĩa |
|----------|--------|
| `$set`   | Cập nhật giá trị của một trường |
| `$unset` | Xóa một trường |
| `$inc`   | Tăng/giảm giá trị số |
| `$push`  | Thêm phần tử vào mảng |
| `$pull`  | Xóa phần tử khỏi mảng |
| `$addToSet` | Thêm phần tử vào mảng nếu chưa tồn tại |

🔹 **Ví dụ**: Cập nhật giá sản phẩm lên 50k
```js
db.products.updateOne(
  { _id: ObjectId("123456") },
  { $set: { price: 50000 } }
)
```

🔹 **Ví dụ**: Tăng số lượng hàng tồn kho thêm 10
```js
db.products.updateOne(
  { _id: ObjectId("123456") },
  { $inc: { stock: 10 } }
)
```

🔹 **Ví dụ**: Thêm tag "giảm giá" nếu chưa có
```js
db.products.updateOne(
  { _id: ObjectId("123456") },
  { $addToSet: { tags: "giảm giá" } }
)
```

🔹 **Ví dụ**: Xóa trường `description` khỏi sản phẩm
```js
db.products.updateOne(
  { _id: ObjectId("123456") },
  { $unset: { description: "" } }
)
```

---

## 6️⃣ **Toán tử lookup (dùng trong aggregation)**
Dùng để join dữ liệu giữa các collection.

| Toán tử   | Ý nghĩa |
|-----------|--------|
| `$lookup` | Join hai collection |
| `$group`  | Gom nhóm dữ liệu |
| `$project` | Lựa chọn trường hiển thị |
| `$sort`   | Sắp xếp dữ liệu |
| `$limit`  | Giới hạn số lượng kết quả |
| `$skip`   | Bỏ qua một số kết quả |

🔹 **Ví dụ**: Join collection `orders` với `users` để lấy thông tin người mua
```js
db.orders.aggregate([
  {
    $lookup: {
      from: "users",
      localField: "userId",
      foreignField: "_id",
      as: "user_info"
    }
  }
])
```

---

## 7️⃣ **Toán tử hình học (GeoSpatial Operators)**
Dùng cho dữ liệu tọa độ.

| Toán tử     | Ý nghĩa |
|-------------|--------|
| `$near`     | Tìm địa điểm gần nhất |
| `$geoWithin` | Tìm địa điểm trong một vùng |
| `$geoIntersects` | Tìm địa điểm giao nhau với vùng |

🔹 **Ví dụ**: Tìm cửa hàng gần một vị trí (lat, lon)
```js
db.stores.find({
  location: { $near: { $geometry: { type: "Point", coordinates: [106.7, 10.8] } } }
})
```

---

## 🔥 **Tóm tắt**
- **Toán tử so sánh**: `$eq`, `$ne`, `$gt`, `$lt`, `$in`, `$nin`
- **Toán tử logic**: `$and`, `$or`, `$not`, `$nor`
- **Toán tử mảng**: `$all`, `$size`, `$elemMatch`
- **Toán tử cập nhật**: `$set`, `$inc`, `$unset`, `$push`, `$pull`
- **Toán tử tìm kiếm**: `$regex`, `$text`
- **Toán tử aggregation**: `$lookup`, `$group`, `$sort`
- **Toán tử hình học**: `$near`, `$geoWithin`

Anh Đăng cần làm gì với MongoDB? 🚀
