### Tính chất của Transaction  
#### 4 tính chất ACID  
- Atomicity: Thay đổi về mặt dữ liệu phải trọn vẹn khi thành công hoặc không có bất kì sự thay đổi nào về mặt dữ liệu nếu xảy ra sự cố.  
> Trong hệ cơ sở dữ liệu, tính nguyên tử là một trong các tính chất ACID của giao dịch cơ sở dữ liệu. Giao dịch nguyên tử là dãy thao tác trên cơ sở dữ liệu, có tính không thể phân chia và không thể rút gọn, sao cho hoặc tất cả các bước đều xảy ra, hoặc là không gì xảy ra cả.
- Consistency: Sau khi một **Transaction** kết thúc thì tất cả dữ liệu phải được nhất quán dù thành công hay thất bại.  
- Isolation: Các **Transaction** khi đồng thời thực thi trên hệ thống thì không có bất kì ảnh hưởng nào tới nhau.  
- Durability: Sau khi một **Transaction** thành công thì hành động nó tạo ra phải bền vững trong cơ sở dữ liệu dù hệ thống có xảy ra lỗi.

### Cấu trúc của Transaction
Một transaction được định nghĩa dựa trên:  
- BEGIN TRANSACTION: Bắt đầu một transaction.  
- SAVE TRANSACTION: Đánh dấu vị trí trong transaction(điểm đánh dấu).  
- ROLLBACK TRANSACTION: Quay lui lại đầu transaction hoặc điểm đánh dấu trước đó trong transaction.  
- COMMIT TRANSACTION: Đánh dấu điểm kết thúc của một transaction, khi câu lệnh này thực thi có nghĩa là transaction thực hiện thành công.  

**Note**:  
- Khi Client hoạt động, DB có thể được truy cập bởi nhiều Clients nên sẽ có tình trạng mất mát dữ liệu hoặc Clients sẽ đọc được các dữ liệu của Transaction mà chưa được commit khi các Clients cùng truy xuất vào một phần dữ liệu.  
> Thực hiện cơ chế Transaction và cơ chế khóa. Một transaction khi muốn cập nhật bất cứ bản ghi nào, sẽ phải giữ lock cho bản ghi đó, lock này chỉ được trả lại sau khi transaction đã commit hoăc bị rollback. Nếu lock của bản ghi đang bị giữ bởi transaction khác, transaction hiện tại sẽ phải đợi cho tới khi lock đó được trả lại.