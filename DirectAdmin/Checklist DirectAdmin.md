# Check list Directadmin
# Mục Lục

1. Cài đặt DirectAdmin (DA)
2. Tạo gói
3. Tạo client 
4. Tạo domain, tài khoản FTP, database, up site ví dụ wordpress
5. Tạo email cho các khg theo tên miền.
6. Gửi email khi tạo gói cho KHG hoặc thay đổi các thông tin của client
7. Backup / restore code, db trên chính máy DA
8. Backup / restore code, db trên 2 máy DA khác nhau
9. Cấu hình SSL Let's encrypt
10. Sử dụng custombuid để thay đổi phiên bản các ứng dụng (hay dùng PHP, MySQL, build Multil version PHP)
11. Xác định file log của DA.
12. Đặt lịch backup code + DB định kỳ
13. KIểm tra log http, ram, cpu
14. Change IP của các máy DA khi đổi máy chủ
15. Add thêm IP cho các domain chạy các IP khác nhau
16. Cấu hình chuyển các mode httpd
17. Cài đặt và sử dụng CSF

## Thực Hiện

### 1. Cài đặt DA

### 2. Tạo gói (Packages)

- đăng nhập tài khoản reseller:
    - tick chọn `manage User package` rồi tiến hành `add Package`.

<img src="https://image.prntscr.com/image/RhI6g11HSg_77HiJs7nNRQ.png">

- Tạo gói (Packages)

<img src=https://image.prntscr.com/image/9a3ZDEa0QDKugfQkI3G5aA.png>

- Chỉnh sửa tên gói và lưu lại

<img src=https://image.prntscr.com/image/OQ_OO80GQFGaz2V4B0EIcg.png>

- Tạo gói thành công.

<img src=https://image.prntscr.com/image/9hgScg_hRTSaK9x50SI63g.png>

### 3. Tạo client

- Tạo client:

<img src=https://image.prntscr.com/image/nUmsaEIeSlyhx752GkeFJg.png>

- Điền thông tin client mới:

<img src="https://image.prntscr.com/image/wHwVxBapSE67JfpP9LuXIQ.png">

- Trong đó:
    - Username: Tên của user, dùng để đăng nhập vào quản lý hosting của user đó.
    - E-mail: E-mail dùng để liên lạc với user đó, bao gồm việc gửi thông tin về tài khoản và các thông báo từ Reseller.
    - Enter Password: Đặt mật khẩu cho user.
    - Re-enter Password: Gõ lại mật khẩu cho user ( cần gõ chính xác với mật khẩu ở trên)
    - Domain: Tên miền của user.
    - Use User Package: Chọn gói cho user này.
    - IP; Chọn IP cho user, nếu không có IP riêng thì user sẽ sử dụng IP của share hosting.
    - Send Email Notification: Gửi thông tin về tài khoản cho user. Tùy chọn Edit User Message dùng để chỉnh sửa email mà bạn sẽ thông báo cho user này về thông tin tài khoản. Nếu bạn không muốn chỉnh sửa Email thông báo mặc định thì bỏ dấu tích ở tùy chọn này.
- Sau đó bạn ấn vào Submit để hoàn thành việc tạo 1 user mới.

### 4. Tạo domain, tài khoản FTP, database, up site ví dụ wordpress

- Tạo tên miền : sau khi đăng nhập bằng tài khoản user hệ thống yêu cầu nhập thông tin tên miền hoặc tạo mới. Chọn `Domain setup` và nhập tên miền.

<img src=https://image.prntscr.com/image/TA1EJhaESYaXHIvpAWJmEg.png>

- Tạo tài khoản FTP:
    - Chọn vào `FTP managenment` rồi tạo tài khoản FTP:

<img src=https://image.prntscr.com/image/rmXOg7BxRpmnARL4-m-KJw.png>

- Tạo database: `Create database`

<img src=https://image.prntscr.com/image/gSUGy4PmTF2yFa8YMeJofw.png>

    - Điền thông tin database rồi chọn pass random và bấm vào Create để tạo mới database:

<img src="https://image.prntscr.com/image/v6dmOpDeSd2P81RdA8B02w.png">

    - sau khi hoàn thành hệ thống sẽ hiển thị thông tin database

<img src=https://image.prntscr.com/image/gh0hb4Q9SR6wdalNpCwkAg.png>

- up site ví dụ wordpress
    - Đầu tiên phải tải file của wordpress: https://wordpress.org/download/

    - Các bước up site:

<img src="https://image.prntscr.com/image/yvFc2mw9RmirSTtfdeWBwQ.png">

<img src=https://image.prntscr.com/image/r8Jgh8LbSBCAmMzyD66gqQ.png>

<img src=https://image.prntscr.com/image/i9EAiCPrTaClTyhVG9xIOw.png>

<img src=https://image.prntscr.com/image/cZgygIwERlGg6TN5nbPRxg.png>

<img src=https://image.prntscr.com/image/sajUs0U_TuK4hicZbZT_Lw.png>

<img src=https://image.prntscr.com/image/o-bDOg2tT3yZdQuSbGKXSA.png>

    - sau khi up site  xong:

<img src= https://image.prntscr.com/image/kPZUuhZrSF_JlGqedNQaWw.png>


### 5. Tạo email cho các khg theo tên miền.

- Chọn tên miền muốn sử dụng, ở đây tôi chọn tên miền hieunm29198.xyz:

<img src=https://image.prntscr.com/image/DrsDXokxS06F-ez3jDXvcw.png>

- Vào email Account chọn `Create mail account`:

<img src= https://image.prntscr.com/image/r4qSaBtiT1_gTYO8HaGgLw.png>

- Sau khi tạo thành công:

<img src=https://image.prntscr.com/image/f9T1OvENRPiRk4k79dxnOA.png>

- Đăng nhập Webmail:

<img src=https://image.prntscr.com/image/wxtntdYQSGS5MSWgPKmKEw.png>


### 6. Gửi mail khi tạo gói cho khg hoặc thay đổi các thông tin của client

- Khi tạo gói cho khách hàng để gửi mail thông báo ta tích chọn vào `Send Email Notification`:

<img src= https://image.prntscr.com/image/OTMo0mLhShWZiHMLp003Og.png>



### 7. Backup / restore code, db trên chính máy DA

- Backup:
    - user: chọn `Create Restore/Backups` bỏ tick phần `E-mail và FTP` sau đó chọn create backups:

<img src=https://image.prntscr.com/image/XTOxOIS-Smy-pWO3CZzipQ.png>

- Sau khi hoàn thành backup thì ta có thể xem lại:

<img src= https://image.prntscr.com/image/wBJ03lgiTWm-Ff05RcJb9Q.png>

- Admin:

    - Đối với tài khoản admin có thể đặt lịch backup hay chọn backup theo user hoặc tất cả user
    - có thể sử dụng tính năng backup lưu trữ sang server khác.

<img src=https://image.prntscr.com/image/2acPS0wxTR2i3I0ww_668A.png>

```
    - step 1: đối tượng backups
    - step 2: thời gian backups
    - step 3: vị trí lưu
    - Step 4: nội dung backup
```

- Restore:
    - User:
        - Để restore dữ liệu ở mục Select a File to Restore chọn bản backup phù hợp và chọn restore

<img src=https://image.prntscr.com/image/rliMqHscTQO9yC0oaoQ6aQ.png>

    - Admin:
        - có thể restore từ file backups trong máy hoặc up file từ thiết bị khác

<img src=https://image.prntscr.com/image/iV1dn1JjR_2A8B3mRldJPQ.png>
