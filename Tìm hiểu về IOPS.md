# Tìm hiểu về IOPS

## 1. IOPS là gì?

- IOPS - Input/Output operation per Second là đơn vị đo lường được sử dụng cho các thiết bị lưu trữ như HDD, SSD hoặc SAN – cho biết số lượng tác vụ Write hoặc Read được hoàn thành trong 1 giây. Số IOPS được publish bởi các nhà sản xuất thiết bị, và không liên quan gì đến các ứng dụng đo lường hiệu năng cả.

- Đối với Cloud server, thông số IOPS càng cao thì tốc độ xử lý càng nhanh, số tác vụ được xử lý sẽ nhiều hơn, và tất nhiên, hiệu năng của ứng dụng trên Cloud Server sẽ cao hơn. Tuy nhiên, có trường hợp IOPS quá cao đến giới hạn vật lý sẽ gây ra tình trạng thắt cổ chai (IOPS quá cao –> độ trễ cao –> làm giảm hiêu năng).

- Đối với IOPS, thứ quan trọng nhất ta cần chú ý đến là tỉ lệ Read và Write (thông thường tỉ lệ này 70% (Read) và 30%(Write) – có thể tuỳ chỉnh được).

- Thông số 
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
__Bảng IOPS tương ứng với từng loại Raid__

<img src=https://image.prntscr.com/image/bgWhvHr5QVi67IvLLDWa3A.png>

__Bảng IOPS tương ứng với từng loại ổ cứng__

<img src= https://image.prntscr.com/image/seW6FUJfTZCA2RHMcbHnuQ.png>


## 2. Các thông số khi test Disk

- Tốc độ đạt yêu cầu của 1 ổ cứng SSD là trên 200MB/s là đạt yêu cầu sử dụng. Còn dưới 200MB/s thì sẽ bị coi như không đạt yêu cầu và loại bỏ. Thông thường test đạt thông tầm 240MB/s.

- Tốc độ đạt yêu cầu của 1 ổ cứng HDD là trên 100MB/s.

VD:

<img src=https://image.prntscr.com/image/Z4z9Qmm4SHq9SeJVCfJV2w.png>

__Các thông số__

- File size: Kích cỡ tệp (400MB)

- Block size: Kích thước khối (1MB)

- Seq. Write Speed: Tốc độ ghi của ổ đĩa  tuần tự là 250.5 MB/s

- Seq. Read Speed: Tốc độ đọc tuần tự của ổ đĩa là 261 MB/s

- Random QD32: 
    - số lần ghi ngẫu nhiên là: IOPS 9314.8, độ trễ là 0.11ms

    - số lần đọc ngẫu nhiên là: IOPS 6417.3, độ trễ là 0.16ms

- Test tốc độ bằng lệnh: Thông thường, chúng ta thực hiện việc test thông qua lệnh `dd`, ghi một file dữ liệu xuống ổ cứng. Lệnh này rất phổ biến vì được cài đặt mặc định trên hầu hết các phiên bản OS của Linux và hiển thị thông tin trực quan, dễ hiểu.
```
dd if=/dev/zero of=test bs=64k count=16k conv=fdatasync
```

