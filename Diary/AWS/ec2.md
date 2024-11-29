### EC2
- Là dịch vụ cở bản của AWS và là dịch vụ nền tảng của một số dịch vụ như ECS, EKS, Lambda.
- Dịch vụ cung cấp một máy chủ ảo (virtual server) để chạy các ứng dụng.
- EC2 có các thành phần:
    - Instance: máy chủ ảo.
    - AMI: template của máy chủ ảo.
    - Instance Type: loại máy chủ ảo.
    - Key Pair: cặp khóa để truy cập vào máy chủ ảo.
    - Security Group: quản lý truy cập inbound và outbound.
    - EBS: ổ đĩa.

### EC2 Instance Types
- Có các loại instance type chính:
    - General Purpose: cân bằng giữa việc sử dụng CPU và bộ nhớ, phù hợp hầu hết các loại ứng dụng.
    - Compute Optimized: tối ưu cho việc sử dụng CPU, phù hợp cho các ứng dụng có hiệu năng cao như batch processing, ad serving, gaming, encoding.
    - Memory Optimized: tối ưu cho việc sử dụng bộ nhớ, phù hợp cho các ứng dụng có hiệu năng cao như in-memory database, in-memory analytics.
    - Accelerated Computing: tối ưu cho việc sử dụng GPU, phù hợp cho các ứng dụng có hiệu năng cao như machine learning, deep learning.
    - Storage Optimized: tối ưu cho việc sử dụng ổ đĩa, phù hợp cho các ứng dụng có hiệu năng cao về disk I/O như data warehousing, relational and NoSQL databases.
    - HPC Optimized: tối ưu cho việc sử dụng CPU và bộ nhớ, phù hợp cho các ứng dụng có hiệu năng rất cao như HPC, engineering and animation.

### Security Group
- Sử dụng để cho phép truy cập inbound và outbound của server qua các rule.
- Cấu trúc của một rule:
    - Type: loại rule, thông dụng như SSH, HTTP, HTTPS.
    - Protocol: giao thức, ở đây là TCP và UDP.
    - Port Range: cổng.
    - Source / Destination: IP address của vào / ra.
- Khi tạo mới một Security Group, mặc định sẽ sẽ có một Outbound rule cho phép truy cập tất cả traffic (all protocols, all ports, all IP addresses).

### Elastic IP
- Khi tạo một EC Instance thì mặc định sẽ là IP động, khi stop instance thì IP sẽ bị giải phóng.
- Elastic IP là IP cố định, khi stop instance thì IP vẫn sẽ giữ nguyên.

### EBS
- Là ổ đĩa của EC Instance.
- Có 2 loại EBS:
    - General Purpose SSD: phù hợp cho hầu hết các loại ứng dụng.
    - Provisioned IOPS SSD: tối ưu cho việc sử dụng disk I/O, phù hợp cho các ứng dụng có hiệu năng cao như database.
- Có thể gắn vào (attach) hoặc gỡ ra (detach) các EC Instance.
- Chỉ có thể tăng size của EBS, không thể giảm size.
- Khi tăng size của EBS thì sẽ tăng size của ổ đĩa vật lý, không tăng được size của file system, ta phải thực hiện thao tác mở rộng phân vùng bên trong EC Instance.

### AMI
- Là template của EC Instance.
- Có thể sử dụng để tạo mới EC Instance.
- Có thể chứa các software và configuration để có thể chạy được ngay khi tạo mới EC Instance.
- Có thể chứa các snapshot của EBS.

### Snapshot
- Là bản sao của EBS.
- Sử dụng để backup dữ liệu của EBS.
- Khi tạo một snapshot đầu tiên từ một EBS Volume, toàn bộ dữ liệu sẽ được sao lưu. Các snapshot sau sẽ ghi nhận các thay đổi kể từ snapshot trước đó.

### SSH
- Khi SSH nếu gặp lỗi Permission too open thì chuyển file .pem lưu sshkey sang quyền 400 với câu lệnh `chmod 400 <file>.pem`.
