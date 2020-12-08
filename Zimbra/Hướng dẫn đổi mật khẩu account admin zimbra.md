# Hướng dẫn đổi mật khẩu account admin zimbra

Khi cài đặt email server zimbra mặc định sinh ra một account admin có toàn quyền quản trị trên hệ thống email server. Tuy nhiên trong quá trình vận hành sử dụng người quản trị không nhớ được mật khẩu admin nên phải thực hiện thao tác reset password account admin zimbra.

Bước 1: SSH vào email server và chuyển sang thao tác với user zimbra
```
su - zimbra
```

<img src=https://image.prntscr.com/image/ucPUz-O8ToalIEHgLoq1vw.png>

Bước 2: Kiểm tra những user nào có quyền admin
```
zmprov gaaa
```
<img src=https://image.prntscr.com/image/mjJ9iGnZQDe-TnaDhmhXQg.png>

Bước 3: Thay đổi mật khẩu account có quyền admin
```
zmprov sp <admin email address> <new password>
```

Ví dụ:
```
zmprov sp admin@hieunm29198.xyz Newpassword
```

<img src=https://image.prntscr.com/image/51LOyJmTTGu2YBhZD91RvA.png>

Lưu ý: Mật khẩu phải thiết lập với độ khó cao tối thiểu 8 ký tự bao gồm chữ hoa, chữ thường, số và ký tự đặc biệt.

Password account admin đã được đổi thành công, tiến hành login kiểm tra lại.
