# Elasticsearch và Các Thành Phần Liên Quan

## Elasticsearch là gì?
Elasticsearch là một công cụ tìm kiếm và phân tích dữ liệu phân tán, mã nguồn mở, được xây dựng trên Apache Lucene. Nó được thiết kế để lưu trữ, tìm kiếm và phân tích dữ liệu lớn trong thời gian thực.

## Các Thành Phần Chính trong Elastic Stack

### 1. **Elasticsearch**
- Là lõi của Elastic Stack, chịu trách nhiệm lưu trữ và tìm kiếm dữ liệu.
- Dữ liệu được lưu trữ dưới dạng JSON và có thể được truy vấn bằng ngôn ngữ truy vấn DSL (Domain Specific Language).

### 2. **Kibana**
- Là giao diện trực quan hóa dữ liệu cho Elasticsearch.
- Cho phép người dùng tạo dashboard, biểu đồ, và phân tích dữ liệu một cách trực quan.

### 3. **Logstash**
- Là công cụ thu thập, xử lý và chuyển đổi dữ liệu trước khi gửi vào Elasticsearch.
- Hỗ trợ nhiều nguồn dữ liệu khác nhau như logs, cơ sở dữ liệu, API.

### 4. **Beats**
- Là bộ công cụ nhẹ để thu thập dữ liệu từ các máy chủ và gửi trực tiếp đến Elasticsearch hoặc Logstash.
- Ví dụ: Filebeat (thu thập log files), Metricbeat (thu thập số liệu hệ thống).

## Cơ Chế Hoạt Động Tối Ưu

### 1. **Tìm kiếm và Lưu trữ Phân tán**
- Elasticsearch chia dữ liệu thành các **shard** và sao chép chúng thành **replica** để đảm bảo tính sẵn sàng và hiệu suất.
- Khi truy vấn, Elasticsearch phân phối công việc đến các shard liên quan, sau đó tổng hợp kết quả.

### 2. **Chỉ mục Ngược (Inverted Index)**
- Elasticsearch sử dụng chỉ mục ngược để tăng tốc độ tìm kiếm. Đây là cấu trúc dữ liệu ánh xạ từ từ khóa đến tài liệu chứa từ khóa đó.

### 3. **Caching**
- Elasticsearch sử dụng bộ nhớ đệm (cache) để lưu trữ kết quả truy vấn thường xuyên, giảm tải cho hệ thống.

### 4. **Pipeline Xử Lý Dữ Liệu**
- Logstash và Beats hoạt động như pipeline xử lý dữ liệu, giúp làm sạch và chuẩn hóa dữ liệu trước khi lưu trữ.

### 5. **Index trong Elasticsearch**
- Trong Elasticsearch, **index** có thể được xem như một "bảng" trong cơ sở dữ liệu quan hệ.
- Mỗi index chứa nhiều tài liệu (documents), và mỗi tài liệu là một bản ghi dữ liệu được lưu trữ dưới dạng JSON.

### 6. **Mapping và Tối Ưu Tìm Kiếm**
- Nếu dữ liệu quá lớn, bạn nên định nghĩa rõ **mapping** cho các trường (fields) trong index để tối ưu hóa tìm kiếm.
- Mapping giúp xác định kiểu dữ liệu (text, keyword, số, ngày tháng, v.v.) và cách Elasticsearch xử lý chúng.

### 7. **Tích Hợp với MongoDB**
- Elasticsearch có thể được sử dụng cùng với MongoDB để tăng tốc độ tìm kiếm:
  1. Đồng bộ dữ liệu từ MongoDB sang Elasticsearch bằng công cụ như **Mongo Connector** hoặc các giải pháp tùy chỉnh.
  2. Sử dụng Elasticsearch để thực hiện các truy vấn tìm kiếm phức tạp hoặc full-text search.

## Ví Dụ Từ Cơ Bản Đến Nâng Cao

### Ví dụ Cơ Bản
- Thu thập log từ một ứng dụng bằng Filebeat, gửi đến Elasticsearch, và hiển thị trên Kibana.

### Ví dụ Nâng Cao
- Xây dựng hệ thống giám sát hiệu suất ứng dụng:
  1. Sử dụng Metricbeat để thu thập số liệu CPU, RAM.
  2. Dùng Logstash để chuẩn hóa dữ liệu log.
  3. Lưu trữ dữ liệu trong Elasticsearch.
  4. Tạo dashboard trong Kibana để giám sát hiệu suất theo thời gian thực.

### Ví dụ Nâng Cao (Tiếp Theo)
- **Use Cases khi sử dụng Elasticsearch với NestJS**:
  1. **Full-Text Search**:
     - Tìm kiếm toàn văn bản với các từ khóa trong nội dung.
  2. **Autocomplete**:
     - Gợi ý từ khóa khi người dùng nhập liệu.
  3. **Log Autocomplete / Suggest Search có lọc (Filter & Facet)**:
     - Gợi ý tìm kiếm với các bộ lọc và phân nhóm dữ liệu.
  4. **Did You Mean / Spell Check**:
     - Đưa ra gợi ý khi người dùng nhập sai chính tả.
  5. **Logging & Monitoring**:
     - Lưu trữ và phân tích log hệ thống hoặc ứng dụng.
  6. **Analytics - Thống kê theo thời gian**:
     - Phân tích dữ liệu và tạo báo cáo theo thời gian thực.

### Ví dụ với NestJS: Thêm Dữ Liệu và Truy Vấn Elasticsearch

#### 1. **Thêm Dữ Liệu vào Elasticsearch**
- Sử dụng thư viện `@nestjs/elasticsearch` để kết nối và thêm dữ liệu vào Elasticsearch.

```typescript
import { Injectable } from '@nestjs/common';
import { ElasticsearchService } from '@nestjs/elasticsearch';

@Injectable()
export class ElasticService {
  constructor(private readonly elasticsearchService: ElasticsearchService) {}

  async addData(index: string, id: string, data: Record<string, any>) {
    return await this.elasticsearchService.index({
      index,
      id,
      body: data,
    });
  }
}
```

#### 2. **Truy Vấn Dữ Liệu (Full-Text Search)**
- Thực hiện tìm kiếm toàn văn bản với từ khóa.

```typescript
async searchData(index: string, query: string) {
  return await this.elasticsearchService.search({
    index,
    body: {
      query: {
        match: { content: query },
      },
    },
  });
}
```

#### 3. **Autocomplete**
- Gợi ý từ khóa khi người dùng nhập liệu.

```typescript
async autocomplete(index: string, prefix: string) {
  return await this.elasticsearchService.search({
    index,
    body: {
      suggest: {
        text: prefix,
        simple_phrase: {
          phrase: {
            field: 'content',
            size: 5,
          },
        },
      },
    },
  });
}
```

#### 4. **Filter & Facet**
- Lọc dữ liệu và phân nhóm theo trường cụ thể.

```typescript
async filterAndFacet(index: string, filterField: string, filterValue: string) {
  return await this.elasticsearchService.search({
    index,
    body: {
      query: {
        term: { [filterField]: filterValue },
      },
      aggs: {
        group_by_field: {
          terms: { field: filterField },
        },
      },
    },
  });
}
```

#### 5. **Did You Mean / Spell Check**
- Gợi ý sửa lỗi chính tả.

```typescript
async spellCheck(index: string, text: string) {
  return await this.elasticsearchService.search({
    index,
    body: {
      suggest: {
        text,
        spellcheck: {
          term: {
            field: 'content',
          },
        },
      },
    },
  });
}
```

#### 6. **Logging & Monitoring**
- Lưu trữ log hệ thống hoặc ứng dụng.

```typescript
async logData(index: string, log: Record<string, any>) {
  return await this.elasticsearchService.index({
    index,
    body: log,
  });
}
```

#### 7. **Analytics - Thống Kê Theo Thời Gian**
- Phân tích dữ liệu theo thời gian.

```typescript
async timeBasedAnalytics(index: string, dateField: string) {
  return await this.elasticsearchService.search({
    index,
    body: {
      aggs: {
        logs_over_time: {
          date_histogram: {
            field: dateField,
            interval: 'day',
          },
        },
      },
    },
  });
}
```

## Sharding trong Elasticsearch và Khả Năng Mở Rộng

### Sharding trong Elasticsearch
Sharding là một khái niệm cơ bản trong Elasticsearch, cho phép phân phối dữ liệu trên nhiều node trong một cụm (cluster). Mỗi index trong Elasticsearch được chia thành các đơn vị nhỏ hơn gọi là **shard**. Các shard này có thể được lưu trữ trên các node khác nhau, giúp Elasticsearch mở rộng theo chiều ngang và xử lý lượng dữ liệu lớn một cách hiệu quả.

#### Các Điểm Chính về Sharding
- **Primary Shards**: Là các shard chính, chứa dữ liệu gốc của một index.
- **Replica Shards**: Là các bản sao của primary shards, cung cấp khả năng chịu lỗi và cải thiện hiệu suất đọc.
- **Shard Allocation**: Elasticsearch tự động phân phối các shard trên các node trong cụm để cân bằng tải.
- **Rebalancing**: Khi thêm hoặc xóa node, Elasticsearch sẽ cân bằng lại các shard để duy trì sự phân phối đồng đều.

### Khả Năng Mở Rộng
Elasticsearch đạt được khả năng mở rộng thông qua sharding và replication:
- **Horizontal Scaling**: Bằng cách thêm nhiều node vào cụm, Elasticsearch có thể phân phối các shard trên các node này, cho phép xử lý lượng dữ liệu lớn hơn và tải truy vấn cao hơn.
- **High Availability**: Replica shards đảm bảo dữ liệu vẫn khả dụng ngay cả khi một node bị lỗi.
- **Parallel Processing**: Các truy vấn được thực thi song song trên các shard, cải thiện hiệu suất cho các tập dữ liệu lớn.

### Best Practices
- Chọn số lượng primary shards phù hợp dựa trên kích thước dự kiến của index và khả năng của cụm.
- Theo dõi kích thước shard để tránh các shard quá lớn, có thể ảnh hưởng đến hiệu suất.
- Sử dụng replica để cân bằng tải đọc và đảm bảo tính dư thừa dữ liệu.

## Replication trong Elasticsearch

Replication là cơ chế sao chép dữ liệu trong Elasticsearch để đảm bảo tính sẵn sàng cao và cải thiện hiệu suất đọc. Mỗi shard chính (primary shard) có thể có một hoặc nhiều bản sao (replica shard).

### Lợi Ích của Replication
1. **Tính Sẵn Sàng Cao (High Availability)**:
    - Nếu một node chứa primary shard bị lỗi, replica shard có thể được sử dụng để thay thế, đảm bảo dữ liệu vẫn khả dụng.
2. **Cải Thiện Hiệu Suất Đọc**:
    - Replica shard có thể xử lý các truy vấn đọc, giảm tải cho primary shard và tăng tốc độ phản hồi.

### Cách Hoạt Động
- Khi một tài liệu được ghi vào primary shard, Elasticsearch sẽ tự động sao chép tài liệu đó vào các replica shard.
- Replica shard không được lưu trữ trên cùng một node với primary shard để tránh mất dữ liệu khi node đó gặp sự cố.

### Cấu Hình Replication
- Số lượng replica shard có thể được cấu hình khi tạo index hoặc thay đổi sau đó bằng lệnh:

```json
PUT /<index>/_settings
{
  "number_of_replicas": 1
}
```

### Lưu Ý Khi Sử Dụng Replication
- **Tăng Số Lượng Replica**: Cải thiện hiệu suất đọc nhưng tiêu tốn thêm tài nguyên.
- **Giảm Số Lượng Replica**: Tiết kiệm tài nguyên nhưng giảm khả năng chịu lỗi.
- **Cluster Health**: Đảm bảo cụm Elasticsearch có đủ node để chứa tất cả primary và replica shard.

### Best Practices
- Đặt số lượng replica shard phù hợp với yêu cầu về hiệu suất và tính sẵn sàng.
- Theo dõi trạng thái cụm (cluster health) để đảm bảo replica shard được phân phối đúng cách.
- Tránh cấu hình quá nhiều replica nếu cụm có ít node, vì điều này có thể gây mất cân bằng tải.

