# Overview
- K8s là một phần mềm mã nguồn mở, có thể mở rộng để quản lý khối lượng công việc và dịch vụ trên nền tảng container, hỗ trợ cả cấu hình khai báo và tự động hóa. Nó có một hệ sinh thái lớn, phát triển nhanh chóng. Các dịch vụ, supports và công cụ Kubernetes được phổ biến rộng rãi.
- Tại sao K8s lại hữu dụng và phổ biến

- **Traditional deployment**: Trước đây, các tổ chức triển khai các ứng dụng trên các server vật lý. Không có cách nào có thể phân định ranh giới tài nguyên giữa các ứng dụng, đó là lý do gây ra các vấn đề về phân bổ tài nguyên. Ví dụ, nếu nhiều ứng dụng cùng chạy trên một server vật lý , trong đó có một ứng dụng chiếm dụng phần lớn tài nguyên , vì thế mà các ứng dụng khác sẽ hoạt động kém hiệu quả dó không có đủ tài nguyên cấp phát. Một giải pháp đặt ra là trên mỗi server vật lý , chỉ chạy một ứng dụng duy nhất. Tuy nhiên điều đó gây ra việc khó mở rộng quy mô, và nó tốn rất nhiều chi phí  cho việc duy trì hệ thống.
- **Virtualized deployment**: Nền tảng ảo hóa cho phép chạy nhiều Máy ảo (VM) trên một CPU của máy chủ vật lý. Ảo hóa cho phép các ứng dụng được triển khai tách biệt giữa các máy ảo và cung cấp mức độ bảo mật vì thông tin của một ứng dụng không thể được truy cập tự do bởi ứng dụng khác. 
  Ảo hóa cho phép tận dụng tốt hơn các tài nguyên trong máy chủ vật lý và cho phép khả năng mở rộng tốt hơn vì có thể thêm hoặc cập nhật ứng dụng một cách dễ dàng, giảm chi phí phần cứng, v.v. Với ảo hóa, bạn có thể trình bày một tập hợp các tài nguyên vật lý dưới dạng một cụm các máy ảo. Mỗi VM là một máy đầy đủ chạy tất cả các thành phần, bao gồm cả hệ điều hành riêng của nó, trên phần cứng ảo hóa.
- **Container deployment**: Container tương tự như các VMs, nhưng nó có các đặc tính linh hoạt để chia sẻ OS giữa các ứng dụng. Tương tự như một VM, một container chứa các filesystem, chỉa sẻ CPU, bộ nhớ, tiến trình. Nó linh hoạt có thể di chuyển giữa cloud và OS
  Container cung cấp các lợi ích:
  + Tạo và triển khai ứng dụng linh hoạt: tăng tính dễ dàng và hiệu quả của việc tạo images của container so với việc sử dụng hình ảnh VM.
  + Phát triển, tích hợp và triển khai liên tục: cung cấp khả năng xây dựng và triển khai images của container thường xuyên và đáng tin cậy với các lần khôi phục nhanh chóng và hiệu quả (do tính bất biến của images).
  + Phân tách mối quan tâm của Dev và Ops: tạo hình ảnh vùng chứa ứng dụng tại thời điểm xây dựng/phát hành thay vì thời gian triển khai, do đó tách ứng dụng khỏi cơ sở hạ tầng.
  + Khả năng quan sát: không chỉ hiển thị thông tin và chỉ số ở cấp hệ điều hành mà còn cả tình trạng ứng dụng và các tín hiệu khác.
  + Tính nhất quán về môi trường trong suốt quá trình phát triển, thử nghiệm và sản xuất: Chạy giống nhau trên máy tính xách tay cũng như trên cloud.
  + Khả năng di động phân phối cloud và hệ điều hành: Chạy trên Ubuntu, RHEL, CoreOS, on-premis, trên public cloud và mọi nơi khác.
  + Quản lý lấy ứng dụng làm trung tâm: Tăng mức độ trừu tượng từ việc chạy HĐH trên phần cứng ảo sang chạy ứng dụng trên HĐH sử dụng tài nguyên logic.
  + Các dịch vụ vi mô được kết hợp phân tán, đàn hồi, tự do: các ứng dụng được chia thành các phần nhỏ hơn, độc lập và có thể được triển khai cũng như quản lý một cách linh hoạt
  + Cách ly tài nguyên: hiệu suất ứng dụng có thể dự đoán được.
  + Sử dụng tài nguyên: hiệu quả và mật độ cao.
