# Tìm hiểu về IOPS

## 1. IOPS là gì?

- IOPS được viết tắt bởi cụm từ Input – output operation per second được hiểu nôm na là 1 truy cập đọc và viết với mỗi giây. Đối với các thiết bị lưu trữ file thì băng thông chính là thông số quan trọng nhất. Còn các thiết bị cho đám mây Cloud thì IOPS quyết định độ nhạy và nhanh của máy ảo.

- Thông số IOPS càng cao thì tốc độ xử lý sẽ càng nhanh, số tác vụ được xử lý đồng thời cũng sẽ nhiều hơn. Và tất nhiên dẫn đến hiệu năng xử lý của các ứng dụng càng cao. Nhưng cũng có trường hợp khi IOPS quá cao, đến giới hạn vật lý sẽ gây ra tình trạng thắt cổ chai (IOPS quá cao –> độ trễ cao –> làm giảm hiêu năng).

- Đối với IOPS, thứ quan trọng nhất ta cần chú ý đến là tỉ lệ Read và Write (thông thường tỉ lệ này 70% (Read) và 30%(Write) – có thể tuỳ chỉnh được).

VD:
- Hệ thống lưu trữ sử dụng ổ SAS 15k
- Dung lượng mỗi ổ là 900Gb.
- Tỉ lệ Read/Write tương ứng: 7:3
- Cấu hình RAID 10
- IOPS per Disk là 176

=> __Yêu cầu: IOPS > 1000__

Hệ thống lúc này cần 8 cứng là đủ, số IOPS của hệ thống lúc này là 1200.

```
RAID    Level   Capacity    IOPS
RAID    10      3,215 GB    1200
RAID    6       4,822 GB    624
RAID    5       5,626 GB    821
```

__Các công thức tính trong bài:__

```
Tổng IOPS = IOPS per Disk * Số ổ cứng

IOPS thực = (Tổng IOPS * Write%)/(Raid Penalty) + (Tổng IOPS * Read %)

Số ổ cứng = ((Read IOPS) + (Write IOPS*Raid Penalty))/ IOPS per Disk
```
__Bảng IOPS tương ứng với từng loại ổ cứng__

<img src=https://image.prntscr.com/image/bgWhvHr5QVi67IvLLDWa3A.png>


## 2. Các thông số khi test Disk

- Tốc độ đạt yêu cầu của 1 ổ cứng SSD là trên 200MB/s là đạt yêu cầu sử dụng. Còn dưới 200MB/s thì sẽ bị coi như không đạt yêu cầu và loại bỏ.

- Tốc độ đạt yêu cầu của 1 ổ cứng HDD là trên 100MB/s.

VD:

<img src=https://image.prntscr.com/image/Z4z9Qmm4SHq9SeJVCfJV2w.png>

__Các thông số__

- File size: Kích cỡ tệp (400MB)

- Block size: Kích thước khối (1MB)

- Seq. Write Speed: Tốc độ ghi của ổ đĩa  tuần tự là 250.5 MB/s

- Seq. Read Speed: Tốc độ đọc tuần tự của ổ đĩa là 261 MB/s

- Random QD32: 
    - Của tốc độ ghi là: IOPS 9314.8, thời gian khởi động là 0.11ms

    - Của tốc độ đọc là: IOPS 6417.3, thời gian khởi động là 0.16ms



