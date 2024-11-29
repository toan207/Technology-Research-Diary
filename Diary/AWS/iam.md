### IAM
- Là dịch vụ kiểm soát truy cập vào tài nguyên của AWS.
- IAM có các thành phần:
    - Users: người dùng AWS dùng để truy cập vào AWS qua AWS console bằng username và password hoặc dùng Access Key ID và Secret Access Key khi dùng AWS CLI và các thư viện.
    - Groups: nhóm người dùng có các quyền truy cập giống nhau.
    - Policies: chính sách quyền truy cập dùng để xác định quyền truy cập của người dùng và nhóm người dùng.
    - Roles: vai trò của người dùng dùng để xác định quyền truy cập của người dùng và nhóm người dùng không đăng nhập mà sử dụng qua cơ chế Assume Role được viết bằng JSON bao gồm:
        - Version: phiên bản của ngôn ngữ sử dụng để định nghĩa policy.
        - Id: Tên của policy.
        - Statement: các câu lệnh để định nghĩa quyền truy cập của người dùng và nhóm người dùng bao gồm:
            - Effect: tác động của câu lệnh, có thể là Allow hoặc Deny.
            - Action: các hành động có thể thực hiện được.
            - Resource: các tài nguyên có thể truy cập được với * là tất cả các tài nguyên.
            - Condition: điều kiện để thực hiện hành động.
            - Principal: người dùng hoặc nhóm người dùng được phép truy cập vào tài nguyên.

### Assume Role
- Là cơ chế cho phép (mượn quyền) người dùng không đăng nhập vào AWS sử dụng vai trò để truy cập vào tài nguyên của AWS.
- Cho phép quản lý quyền truy cập tạm thời một cách linh hoạt, có thời gian mặc định là 1 giờ.

### Best practices
- Không sử dụng Root Account.
- Bật MFA.
- Sử dụng credentials tạm thời, nghĩa là không sử dụng IAM User mà sử dụng AssumeRole để truy cập vào tài nguyên của AWS.
    - Đối với user: sử dụng federated identity để truy cập.
    - Đối với application: sử dụng AssumeRole để truy cập.
- Sử dụng chiến lược least privilege để cấp quyền truy cập cho người dùng và nhóm người dùng, tức là cấp quyền thấp nhất có thể, không gán dư quyền.
