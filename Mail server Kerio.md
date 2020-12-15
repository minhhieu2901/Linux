# Hướng dẫn cài đặt mail server Kerio
## Cài đặt mail server kerio
 Sử dung Kerio connect 9.2
- Bước 1: Tải Kerio về bằng lệnh wget:
```
wget http://cdn.kerio.com/dwn/connect/connect-9.2.12-5000/kerio-connect-9.2.12-5000-linux-x86_64.rpm
```

- Bước 2: Install mail Kerio
```
yum install kerio-connect-9.2.12-5000-linux-x86_64.rpm -y
```

- Bước 3: Đăng nhập mail bằng địa chỉ IP:4040 dán key và cài đặt.

Tắt hết postfix, sendmail,...

Bắt đầu cài đặt:
<img src=https://image.prntscr.com/image/sPaylA16T2WY0bsLZj5vNg.png>


<img src=https://image.prntscr.com/image/98zgyZroRamzngnXbSzhzw.png>



- Thay đổi thông tin về tên miền và hostname của mail server kerio:

<img src=https://image.prntscr.com/image/uNrOd-bQQBKFqEZjpZe6Xw.png>

- Sau khi cài đặt xong đăng nhập bằng IP:4040 vào bằng user và password vừa tạo:

<img src=https://image.prntscr.com/image/4gDGLyKrS3aadC7MyXWEZQ.png>

Giao diện của mail server Kerio:

<img src= https://image.prntscr.com/image/-QGxvDJIS2qGPFTkFWOENw.png>

- Các dịch vụ mail server đang chay

<img src= https://image.prntscr.com/image/J9BW9wCBS6S2RNxJvIQ12g.png>

- Tạo user trên mail server Kerio:

<img src= https://image.prntscr.com/image/W-IiReEXQzW19_bA5kOSSw.png>

Đăng nhập bằng user vừa tạo xong:

<img src= https://image.prntscr.com/image/hMJcfMmiTRKNT6iZaogK6Q.png>

<img src=https://image.prntscr.com/image/V_Dnh81DSXCLttpgB6Z8Zg.png>

- Tạo bản ghi DKIM để gửi nhận mail:

<img src= https://image.prntscr.com/image/LeXtjTZJRhqpy-qZOS-Zlw.png>

<img src= https://image.prntscr.com/image/FiAQ-dS7RdWJL42feT7Ydw.png>

Sau đó tạo record để gửi nhận.

- Test gửi nhận bằng mail kerio vừa cài: 

<img src=https://image.prntscr.com/image/6myrKs4_SniWQ_rbehqwKg.png>

<img src= https://image.prntscr.com/image/TNkE7H0fQ2aEYqIRnZUgaA.png>


- Cách đọc log trên giao diện mail kerio và trên command:

<img src=https://image.prntscr.com/image/-vGSpOMiTRSRfj08iteowg.png>

<img src=https://image.prntscr.com/image/vl_YrlfZTKu-VWt9bnu1Ow.png>

- Thay đổi logo 

<img src=https://image.prntscr.com/image/bwVFA3ezRVW6Jod-9DjJ0w.png>


## Đặt lại mật khẩu quản trị viên trong Kerio Connect

- Nếu bạn không thể đăng nhập bằng  thông tin đăng nhập quản trị viên Kerio Connect của  mình, bạn có thể khôi phục tài khoản quản trị viên bằng cách sửa đổi tệp hoặc tệp theo cách thủ công . Sau đó, bạn sẽ có thể đăng nhập và đặt mật khẩu mới`.users.cfg`  `mailserver.cfg`

 - Đổi mật khẩu admin:
- Chỉnh sửa `.users.cfg` tệp
Vào thư mục `/opt/kerio/mailserver` mở file `.users.cfg`

<img src=https://image.prntscr.com/image/7WIqEcc7S8yvTB0mq2MiKQ.png>

Tìm 2 dòng ở trên và thay đổi:

- Thay đổi `Password` giá trị biến thành `NUL`:
```
<variable name="Password">NUL:</variable>
```
- (Tùy chọn) Thay đổi giá trị của nó thành  1 ( chỉ đọc toàn bộ máy chủ ) hoặc 3( đọc / ghi toàn bộ máy chủ ):

- Chỉnh sửa `mailserver.cfg` tệp

Vào thư mục `/opt/kerio/mailserver` mở file `mailserver.cfg`

<img src=https://image.prntscr.com/image/oMH2GDHVSzGArHtUOIjoIA.png>

Đặt BuiltInAdminEnabled giá trị biến thành 1.

Thay đổi BuiltInAdminUsername giá trị biến thành kerioadmin.

Xóa giá trị cho BuiltInAdminPassword biến.

- Đăng nhập vào cổng WebAdmin bằng  kerioadmin tên người dùng ( không cần mật khẩu ).

- Đặt mật khẩu mới:

<img src=https://image.prntscr.com/image/fY3n_dt-SNOBqiWSImdN0g.png>
