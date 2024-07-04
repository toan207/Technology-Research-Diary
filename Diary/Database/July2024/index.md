## Index là gì?
- Là một cấu trúc dữ liệu để cải thiện tốc độ thao tác truy xuất dữ liệu và được thường lưu trữ trên disk.

## Cấu trúc dữ liệu được sử dụng trong Index
### B-Tree (Blanced Tree)
- Cây cân bằng được sắp xếp với các node bên trái luôn nhỏ hơn node bên phải.
- Có độ phức tạp Insert, delete, delete là O(logN) Time.

### B+Tree
- Là một biến thể của B-Tree có các pointer ở node lá như một dạng linked list, các pointer ở đây sẽ có dạng 2 chiều để duyệt theo chiều tăng dần hoặc giảm dần.
- Một node có thể chứa nhiều key để giảm độ cao của cây và hạn chế số lần truy cập xuống ổ đĩa.
- Phù hợp cho những truy vấn theo dạng range.

### Hash
- Dùng hash function để hash key, từ một key sẽ ra vị trí của dữ liệu.
- Phù hợp cho các truy vấn bằng `=`.

## Physical Storage Index
### Clustered Index
- Dùng để xác định vị trí vật lý của dữ liệu trên disk dưới dạng cấu trúc B+Tree.
- Các node lá sẽ chứa thông tin của record.
- Một bảng chỉ có một clusterd index.
- Khi tạo một primary key thì database sẽ ngầm tạo Clustered Index.

### Non-Clusterd Index
- Tạo ra các index cho các cột khác theo dạng cấu trúc B+Tree.
- Tại node lá sẽ chứa thông tin của Clustered Index (primary key).
- Địa chỉ vật lý có thể bị thay đổi nên các node lá sẽ không lưu lại địa chỉ vật lý trong secondary index.

>Index sẽ khiến cho các phương thức write vào database chậm đi, tốn tài nguyên lưu trữ vật lý.

## Tính chất của Index
- Key sẽ có những ràng buộc trên một cột.
- Index là một cấu trúc dữ liệu để tăng tốc việc tìm kiếm dữ liệu.

### Primary Index
- Khi tạo primary key thì database sẽ khởi tạo primary index.
- Primary index là unique cho mỗi dòng trong bảng.
- Primary key có giá trị tăng dần thì sẽ hiệu quả trong việc ghi vào trong bảng.

### Unique Index
- Những cái giá trị trong cột phải là duy nhất.
- Cho phép giá trị null.

## Index trên nhiều cột
### Composite Index
- Có thể đánh trên nhiều cột.
- Tạo ra một composite index file và trỏ đến clustered index.
- Do sử dụng nhiều cột khi tạo ra composite index nên chiếm nhiều không gian lưu trữ vật lý.
- Được sắp xếp toàn cục theo một column chính (column đầu tiên) và các column sau sẽ được sắp xếp cục bộ (khi column chính bằng nhau).
- Query sử dụng composite index khi có điều kiện với column chính trong index.
- Column nên đặt đầu tiên trong composite index là column có nhiều giá trị distinct (high cardinality).