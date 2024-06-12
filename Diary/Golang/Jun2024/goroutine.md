### Goroutine
- Tồn tài ít nhất một **Goroutine** gọi là **main Goroutine**.  
- Nếu **main Goroutine** kết thúc thì toàn bộ Goroutine khác đều bị dừng và kết thúc ngay.
- Là một **lightweight execution thread** sẽ có chi phí thấp hơn rất nhiều so với OS thread (Goroutine sử dụng 2KB memory stack còn OS thread lên đến 2MB).  
- có thế được ánh xạ hoạt động trên nhiều OS thread.  

```
func name(){
// statements
}

// using go keyword as the 
// prefix of your function call
go name()
```

>Lightweight execution thread là một logical thread, 1 OS thread (physical thread) chứa nhiều lightweight execution thread.  

### Capture variable trong Goroutine Golang

```
for i := 1; i <= 100; i++ {
    go func() {
        fmt.Println(i) // biến i ở đây là một pointer
    }()
}
```

- **Problem:** In ra rất nhiều `i` bị trùng lặp.
- Một hàm sử dụng biến ngoài thì biến đó sẽ được gọi là `capture` là một tham chiếu đến biến ngoài, không phải giá trị mà các Goroutines được thực thi ngay nên việc `i` ở ngoài bị thay đổi sẽ dẫn đến `i` ở trong hàm bị thay đổi.  
- Để tránh vấn đề này thì cần copy giá trị `i` cho từng Goroutine function.  

```
for i := 1; i <= 100; i++ {
    go func(value int) {
        fmt.Println(value) // value ở đây độc lập với i ở ngoài
    }(i) // value i được copy ở đây
}
```

### Sử dụng Gosched() để force schedule Goroutines

```
go func() {
    for i := 1; i <= 50; i++ {
        fmt.Println("I am Goroutine 1")
    }
}()

go func() {
    for i := 1; i <= 50; i++ {
        fmt.Println("I am Goroutine 2")
    }
}()
```

- Khả năng cao sẽ thấy in ra 1 trong 2 liên tục đến hết rồi mới in cái còn lại -> khiến ứng dụng chạy kém hiệu quả, chiếm dụng tài nguyên lớn và gây tắc cổ chai nghiêm trọng.  
- Cách giải quyết:  
    1. Sleep một chút ở mỗi vòng lặp, chấp nhận hy sinh performance do sleep thêm thời gian.  
    2. Sử dụng hàm `Gosched()` của package runtime để schedule goroutine ngay lập tức sau mỗi vòng lặp.

```
go func() {
    for i := 1; i <= 50; i++ {
        fmt.Println("I am Goroutine 1")
        runtime.Gosched()
    }
}()

go func() {
    for i := 1; i <= 50; i++ {
        fmt.Println("I am Goroutine 2")
        runtime.Gosched()
    }
}()
```

- `Gosched()` chỉ giúp schedule goroutines còn việc chọn Goroutines nào thực thi tiếp theo là do runtime quyết định.  