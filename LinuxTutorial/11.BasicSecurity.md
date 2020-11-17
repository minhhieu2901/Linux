# Basic Security

Theo mặc định, Linux phân chia các loại tài khoản ra cho các tác vụ và chương trình:

- Root
- System
- Normal
- Network
Để có 1 môi trường làm việc an toàn, ta chỉ nên cấp các đặc quyền tối thiểu có thể và cần thiết cho từng tài khoản và gỡ bỏ các tài khoản không hoạt động.

Lệnh `last` sẽ cho ta biết lần cuối mỗi người dùng đăng nhập vào hệ thống. Từ đó, ta có thể xác định các tài khoản không hoạt động để có thể gỡ bỏ nếu tài khoản đó không cần thiết.

```
[root@localhost ~]# last
root     pts/1        192.168.233.1    Tue Nov 17 12:21   still logged in
root     pts/0        192.168.233.1    Tue Nov 17 10:57   still logged in
reboot   system boot  3.10.0-1127.el7. Tue Nov 17 10:56 - 13:03  (02:07)
root     pts/0        192.168.233.1    Tue Nov 17 10:55 - 10:56  (00:01)
root     tty1                          Tue Nov 17 10:51 - 10:56  (00:05)
reboot   system boot  3.10.0-1127.el7. Tue Nov 17 10:50 - 13:03  (02:12)

wtmp begins Tue Nov 17 10:50:57 2020
```
Tài khoản **root** là tài khoản đặc quyền nhất trên hệ thống Linux/UNIX. Tài khoản này có thể thực hiện tất cả các khía cạnh của quản trị hệ thống, bao gồm: thêm tài khoản, thay đổi mật khẩu người dùng, kiểm tra các file log, cài đặt thêm phần mềm,...

Các tài khoản thông thường có thể thực hiện được một số thao tác mà cần yêu cầu quyền đặc biệt. Tuy nhiên, cấu hình hệ thống phải cho phép các khả năng đó được thực hiện. Chạy một `network client` hay truyền file qua mạng là những quyền không cần yêu cầu tài khoản `root`.

Trong Linux, bạn có thể sử dụng lệnh `su` hoặc `sudo` để có thể cấp quyền root cho các tài khoản bình thường. 2 lệnh này có những sự khác nhau:

##  Lệnh `su`

**Su** là viết tắt của switch user. Với su, bạn có thể chuyển đổi bất kể user nào, Nói chung là chỉ cần sử dụng **su-username** và nhập mật khẩu vào là được, nhưng root thì không cần nhập mật khẩu khi chuyển sang danh tính khác với **su**.

Có 2 định dạng:

```
su -l username
su username
```

**-l** là viết tắt của login.

Nếu bạn không chỉ định tên user, thì root được coi là tùy chọn mặc định, vì vậy lệnh để chuyển sang root là: **su -root** hoặc **su-**, **su root** hoặc **su**.

**su username** khác với **su-username** như sau:

**su-username** sau khi chuyển đổi user, cũng đồng thời chuyển sang môi trường làm việc của user mới. Sau khi **su username** chuyển đổi user, thư mục làm việc của user ban đầu và các thư mục biến môi trường khác không thay đổi.
### Lệnh su-

Khi lệnh **su-**, **su -l** hoặc **su --login** thay đổi danh tính, thư mục đang làm việc, home, shell, user, logname đồng thời cũng thay đổi. Ngoài ra, biến path cũng được thay đổi. Việc sử dụng lệnh su- sẽ được chuyển đổi thành người dùng root theo mặc định.

Lệnh su- không có tham số không thay đổi thư mục làm việc hiện tại, cũng như home, shell, user, logname. Nó chỉ có quyền root.

*Lưu ý*: su- sử dụng mật khẩu của root và sudo sử dụng mật khẩu của user.

## Lệnh `sudo`

**Sudo** là một cơ chế quản lý quyền, phụ thuộc vào **/etc/sudoers**, xác định người dùng nào được phép thực hiện loại lệnh quản lý nào. Định dạng lệnh là:
```
sudo -u username command
```

Theo mặc định, chỉ người dùng root mới có thể thực thi lệnh sudo. Người dùng root cần chỉnh sửa file cấu hình sudo /etc/sudoers bằng cách sử dụng lệnh visudo để cho phép những người dùng bình thường khác thực thi lệnh sudo.

Sudo chạy như sau:

1) Khi người dùng chạy sudo, hệ thống sẽ tìm trong **file /etc/sudoers** để xem người dùng có quyền chạy sudo hay không.

2) Nếu người dùng có quyền chạy sudo, thì việc tiếp theo cần làm là nhập mật khẩu của chính user đó.

3) Giả sử mật khẩu là chính xác. Bắt đầu lệnh sau sudo, bạn không cần nhập mật khẩu để chạy sudo với tư cách root nữa.

## Tiến trình độc lập(The process isolation)

Linux được cho là nền tảng bảo mật hơn các hệ điều hành khác bởi các tiến trình luôn chạy độc lập với nhau. Một tiến trình không thể truy cập vào tài nguyên của tiến trình khác kể cả khi nó đang chạy với cùng phiên của 1 người dùng. Các cơ chế bảo mật bổ sung đã được giới thiệu để giảm thiểu rủi ro gây ra:
1. **Control Groups**: cho phép người quản trị phân nhóm các tiến trình và cấp tài nguyên hữu hạn cho mỗi nhóm.
2. **Linux Containers**: cho phép chạy nhiều phiên bản Linux trên cùng một hệ thống
3. **Virtualization**: phần cứng được tính toán sao cho không chỉ tách biệt các tiến trình, đồng thời cũng cũng phải tách biệt với phần cứng mà các máy ảo sử dụng trên cùng một host vật lý.

## Mã hóa mật khẩu (Password Encryption)
Bảo vệ mật khẩu là một việc rất quan trọng. Hầu hết các phiên bản của Linux đều sử dụng cơ chế mã hóa mật khẩu bằng thuật toán `SHA-512` (Secure Hashing Algorithm 512bits) phát triển bởi NSA ( U.S. National Security Agency ).

`SHA-512` được sử dụng rộng rãi để bảo vệ các ứng dụng và giao thức như TLS, SSL, PHP, S/MINE và IPSec.

## Vòng đời password (Password Aging)
Password Aging là 1 phương pháp để nhắc nhở người dùng tạo mật khẩu mới sau 1 thời gian dài sử dụng, nhằm nâng cao tính bảo mật. Điều này có thể củng cố cho việc bảo mật, nếu hệ thống bị xâm nhập thì cũng chỉ có thể sử dụng trong một thời gian nhất định.

Sử dụng lệnh `chage` - cấu hình thông tin mật khẩu cho người dùng:
```
[root@localhost ~]# chage -l root
Last password change                                    : never
Password expires                                        : never
Password inactive                                       : never
Account expires                                         : never
Minimum number of days between password change          : 0
Maximum number of days between password change          : 99999
Number of days of warning before password expires       : 7
```