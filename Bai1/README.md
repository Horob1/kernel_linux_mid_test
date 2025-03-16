# Bài 1: Xử Lý File và Đồng Bộ Tiến Trình

## Mô tả

Dự án này bao gồm hai chương trình C (progA và progB) thực hiện xử lý file và đồng bộ tiến trình sử dụng semaphore. Chương trình A sẽ đọc dữ liệu từ hai file đầu vào và ghi vào file thứ ba, sau đó chương trình B sẽ xử lý dữ liệu từ file thứ ba và ghi kết quả vào file thứ tư.

## Yêu cầu hệ thống

- Hệ điều hành Unix/Linux
- Trình biên dịch GCC
- Make

## Cài đặt và Biên dịch

```bash
# Biên dịch cả hai chương trình
make

# Xóa các file đã biên dịch và file kết quả
make clean
```

## Cách sử dụng

### Chương trình A (progA)

```bash
./progA F1 F2 F3 time
```

- F1: File đầu vào thứ nhất
- F2: File đầu vào thứ hai
- F3: File kết quả
- time: Thời gian chờ (giây)

### Chương trình B (progB)

```bash
./progB F3 F4 time
```

- F3: File đầu vào (kết quả từ progA)
- F4: File kết quả
- time: Thời gian chờ (giây)

### Chạy cả chương trình cùng lúc 
```bash
./progA F1 F2 F3 time1 && ./progB F3 F4 time2
```
- F1: File đầu vào thứ nhất
- F2: File đầu vào thứ hai
- F3: File kết quả
- time1: Thời gian chờ (giây)
- F4: File kết quả
- time2: Thời gian chờ (giây)

## Chức năng

### Chương trình A

1. Đọc dữ liệu từ file F1 và ghi vào F3
2. Đọc dữ liệu từ file F2 và ghi tiếp vào F3
3. Chờ theo thời gian được chỉ định
4. Tăng giá trị semaphore để báo hiệu cho progB

### Chương trình B

1. Đợi tín hiệu từ progA thông qua semaphore
2. Đọc dữ liệu từ file F3
3. Thực hiện hai xử lý song song:
   - Đảo ngược thứ tự các từ
   - Lấy từ đầu tiên và từ cuối cùng
4. Ghi kết quả vào file F4
5. Chờ theo thời gian được chỉ định

## Cấu trúc thư mục

```
Bai1/
├── progA.c
├── progB.c
├── Makefile
└── README.md
```

## Công nghệ sử dụng

- Ngôn ngữ C
- System calls (fork, wait, read, write)
- Semaphore cho đồng bộ tiến trình
- Make build system

## Tác giả

[Nguyễn Thế Anh]- [Horob1] - [CT060202]

## Cảm ơn

Cảm ơn 🦹 thầy Quân Saitama đã hướng dẫn và đánh giá bài tập này!
