# Bài 2: Mô Phỏng Nhà Hàng với Đồng Bộ Tiến Trình

## Mô tả

Dự án này mô phỏng hoạt động của một nhà hàng với ba loại tiến trình: đầu bếp, phục vụ và thực khách. Chương trình sử dụng shared memory và semaphore để đồng bộ các tiến trình, đảm bảo việc phục vụ thức ăn được thực hiện một cách có tổ chức và hiệu quả.

## Yêu cầu hệ thống

- Hệ điều hành Unix/Linux
- Trình biên dịch GCC
- Make

## Cài đặt và Biên dịch

```bash
# Biên dịch cả hai phiên bản chương trình
make

# Chạy phiên bản 1 với 5 thực khách
make run

# Chạy phiên bản 2 với 5 thực khách
make run2

# Xóa các file đã biên dịch
make clean
```

## Cách sử dụng

```bash
# Phiên bản 1: Một tiến trình thực khách
./canteen K

# Phiên bản 2: Nhiều tiến trình thực khách
./canteen_2 K
```

Trong đó:

- K: Số lượng thực khách cần phục vụ

## Chức năng

### Đầu bếp (Chef)

1. Nấu các món ăn ngẫu nhiên (khai vị P, món chính C, bánh ngọt D)
2. Đảm bảo số lượng mỗi loại không vượt quá số thực khách
3. Thông báo số lượng món đã nấu

### Phục vụ (Waiter)

1. Lấy món ăn từ bếp
2. Mang món đến cho thực khách
3. Đảm bảo mỗi thực khách nhận đủ 3 món
4. Thông báo số lượng món đang cầm

### Thực khách (Customer)

1. Đợi phục vụ mang đủ 3 món
2. Nhận món và rời đi
3. Thông báo khi đã được phục vụ

## Cấu trúc dữ liệu

```c
typedef struct {
    int k;                    // Số lượng thực khách
    int p, c, d;             // Số lượng món đã nấu
    int holding_p, holding_c, holding_d;  // Số lượng món phục vụ đang cầm
    int served;              // Số thực khách đã phục vụ
} SharedData;
```

## Cấu trúc thư mục

```
Bai2/
├── canteen.c      // Phiên bản 1: Một tiến trình thực khách
├── canteen_2.c    // Phiên bản 2: Nhiều tiến trình thực khách
├── Makefile
└── README.md
```

## Công nghệ sử dụng

- Ngôn ngữ C
- System calls (fork, wait)
- Shared Memory (shmget, shmat, shmdt)
- Semaphore (semget, semop, semctl)
- Make build system

## Tác giả

[Nguyễn Thế Anh] - [Horob1] - [CT060202]

## Cảm ơn

Cảm ơn 🦹 thầy Quân Saitama đã hướng dẫn và đánh giá bài tập này!
