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
- K8s cung cấp khả năng:
  + Phát hiện dịch vụ và cân bằng tải: Kubernetes có thể hiển thị container bằng cách sử dụng tên miền DNS hoặc sử dụng địa chỉ IP của chính nó. Nếu lưu lượng truy cập vào container cao, Kubernetes có thể cân bằng tải và phân phối lưu lượng mạng để quá trình triển khai ổn định.
  + Quản trị, điều phối storage: Điều phối lưu trữ Kubernetes cho phép bạn tự động gắn hệ thống lưu trữ mà bạn chọn, chẳng hạn như kho lưu trữ cục bộ, cung cấp public cloud, v.v.
  + Triển khai và khôi phục tự động: ta có thể mô tả trạng thái mong muốn cho các container đã triển khai của mình bằng Kubernetes và nó có thể thay đổi trạng thái thực tế thành trạng thái mong muốn với tốc độ được kiểm soát. Ví dụ: bạn có thể tự động hóa Kubernetes để tạo container mới cho quá trình triển khai của mình, xóa container hiện có và áp dụng tất cả tài nguyên của chúng vào container mới.
  + Đóng gói tự động: cung cấp cho Kubernetes một cụm các nút mà nó có thể sử dụng để chạy các tác vụ trong container. Thực hiện khai báo cho Kubernetes biết lượng CPU và bộ nhớ (RAM) mà mỗi container cần. Kubernetes có thể sắp xếp các container vào node tương ứng để tận dụng tốt nhất các tài nguyên.
  + Sefl healing: K8s có thể restart, replace hoặc kill các containers fail k có phản hồi
  + Quản lý cấu hình và bảo mật: Kubernetes cho phép lưu trữ và quản lý thông tin mật, chẳng hạn như password, OAuth tokens và SSH keys.có thể triển khai và cập nhật các secret cũng như cấu hình ứng dụng mà không cần build lại images container cũng như không để lộ secret trong cấu hình ngăn xếp
# K8s components
## Control Plane Components
- kube-apiserver: 
  + API server là một thành phần của control plane Kubernetes hiển thị API Kubernetes. API server là giao diện người dùng cho mặt phẳng điều khiển Kubernetes.
  + kube-apiserver được thiết kế để mở rộng quy mô theo chiều ngang—nghĩa là nó mở rộng quy mô bằng cách triển khai nhiều phiên bản hơn. Bạn có thể chạy một số phiên bản kube-apiserver và cân bằng lưu lượng giữa các phiên bản đó.
- etcd:
  + Là các file có dạng key-value làm kho lưu trữ sao lưu của Kubernetes cho tất cả dữ liệu cụm.
- kube-scheduler
  + Thành phần thực hiện nhiệm vụ theo dõi các Pod mới được tạo chưa được phân phối vào node nào và thực hiện schedule pod đó cho một node tương ứng.
  + Các yếu tố được tính đến cho các quyết định lập lịch trình bao gồm: các yêu cầu tài nguyên, các ràng buộc về phần cứng/phần mềm/chính sách, các thông số kỹ thuật về mối quan hệ và chống mối quan hệ, vị trí dữ liệu.
- kube-controller-manager
  + Thành phần chạy các quy trình của bộ điều khiển.
  + Về mặt logic, mỗi bộ điều khiển là một quy trình riêng biệt, nhưng để giảm độ phức tạp, tất cả chúng được biên dịch thành một nhị phân duy nhất và chạy trong một quy trình duy nhất.
  + Một số loại bộ điều khiển là:
    Node Controller: Chịu trách nhiệm thông báo và phản hồi khi các node ngừng hoạt động.  
    Job Controller: Theo dõi các đối tượng Công việc đại diện cho các tác vụ một lần, sau đó tạo các pods để chạy các tác vụ đó cho đến khi hoàn thành.  
    EndpointSlice Controller: Điền vào các đối tượng EndpointSlice (để cung cấp liên kết giữa service và pod).
    ServiceAccount Controller: Tạo ServiceAccounts mặc định cho các namespaces mới.
- cloud-controller-manager:
  + liên kết cụm với API của public cloud và tách các thành phần tương tác với nền tảng đám mây đó khỏi các thành phần chỉ tương tác với cụm của bạn.
  + Các bộ điều khiển sau có thể có phần phụ thuộc của public cloud:
    Node controller: Để kiểm tra cloud provider nhằm xác định xem một nút đã bị xóa trong cloud sau khi nút ngừng phản hồi hay chưa
    Route controller: Để thiết lập các tuyến trong cơ sở hạ tầng cloud bên dưới
    Service controller: Để tạo, cập nhật và xóa bộ cân bằng tải (load balancers) của nhà cung cấp dịch vụ đám mây
- Node Components
  + kubelet: Agent chạy trong mỗi node. Nó đảm bảo các Pod luôn trong trạng thái running
  + kube-proxy: kube-proxy là một network proxy chạy trên mỗi node trong cụm, triển khai một phần của các service Kubernetes. kube-proxy duy trì các quy tắc mạng trên các nodes. Các quy tắc mạng này cho phép giao tiếp mạng với các pod từ các phiên mạng bên trong hoặc bên ngoài cụm. 
  + Container runtime: running container
