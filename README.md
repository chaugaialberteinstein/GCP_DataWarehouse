# GCP_DataWarehouse

Dự án: Đồng bộ dữ liệu sản phẩm Tiki lên Data Warehouse BigQuery
Mục tiêu:

Xây dựng một hệ thống đồng bộ dữ liệu sản phẩm từ MongoDB lên Google Cloud Storage (GCS) và sau đó vào BigQuery.
Tạo một data mart về seller và sản phẩm để phục vụ cho các hoạt động phân tích dữ liệu.
Tự động hóa quá trình đồng bộ và load dữ liệu.
Tối ưu hóa chi phí cho các thành phần được sử dụng.
Mô tả chi tiết:

1. Chuẩn bị môi trường:

Tạo một Compute Engine instance và cài đặt MongoDB.
Restore dữ liệu từ MongoDB local lên MongoDB trên VM.
Tham khảo: https://www.youtube.com/watch?v=AxrA35Itv64, https://www.youtube.com/watch?v=PMvp9MDKrJI&t=194s

2. Đồng bộ dữ liệu lên GCS:

Sử dụng FileZilla để backup dữ liệu từ MongoDB lên GCS.
Lịch: Hàng ngày lúc 20h.
Tự động hóa: Sử dụng Crontab và Cloud Function để trigger.


3. Thiết kế Data Warehouse:

BigQuery: Thiết kế schema và load dữ liệu từ GCS.
Data mart: Tạo một table data mart về seller và sản phẩm.

4. Phân tích dữ liệu:

Data Studio: Kết nối với BigQuery và tạo dashboard:
Số lượng sản phẩm đã bán theo danh mục.
Phân bố sản phẩm của các nhãn hàng Trung Quốc theo danh mục.
Mối quan hệ giữa rating và giá sản phẩm.
Top 10 seller nhiều sản phẩm nhất.

5. Tự động hóa:

Sử dụng Crontab và Cloud Function để:
Đồng bộ dữ liệu từ MongoDB lên GCS.
Trigger load dữ liệu từ GCS vào BigQuery.

6. Tối ưu hóa chi phí:

Đánh giá: Đánh giá chi phí sử dụng của các thành phần (Compute Engine, Storage, BigQuery).
Tối ưu:
Compute Engine: Điều chỉnh kích thước instance, sử dụng spot instance.
Storage: Chọn loại storage phù hợp (Standard, Nearline, Coldline).
BigQuery: Tối ưu hóa schema, sử dụng partition, clustering.
Công nghệ sử dụng:

Cloud: Google Cloud Platform (Compute Engine, Cloud Storage, BigQuery, Cloud Functions, Crontab)
Database: MongoDB
BI: Data Studio
Tools: FileZilla
Cấu trúc dự án:

(Mô tả cấu trúc thư mục và các file trong dự án)
Hướng dẫn sử dụng:

(Hướng dẫn cách chạy dự án, cài đặt các dependency, ...)
Lưu ý:

(Các vấn đề cần lưu ý, ví dụ: định dạng dữ liệu, lỗi thường gặp, ...)
Chiến lược tối ưu chi phí:
Compute Engine:
Sử dụng spot instance cho các tác vụ không yêu cầu thời gian thực.
Tắt instance khi không sử dụng.
Điều chỉnh kích thước instance theo tải công việc.
Cloud Storage:
Chọn loại storage phù hợp với tần suất truy cập dữ liệu.
Sử dụng lifecycle management để tự động chuyển dữ liệu sang lớp lưu trữ rẻ hơn.
BigQuery:
Tối ưu hóa schema: Sử dụng các kiểu dữ liệu phù hợp, nén dữ liệu.
Sử dụng partition và clustering để cải thiện hiệu suất truy vấn.
Kiểm tra và xóa các bảng không sử dụng.
