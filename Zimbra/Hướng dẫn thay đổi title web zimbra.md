# Hướng dẫn thay đổi title web zimbra

Mặc định khi triển khai xong hệ thống email server zimbra ở phần user login `title` trên thanh trình duyệt sẽ là `Zimbra Web Client Sign In`, phần admin login là `Zimbra Administration` một số khách hàng muốn thay đổi title thành tên của đơn vị, tổ chức của mình.

1. Thay đổi title web login client
- Title web client mặc định

<img src=https://image.prntscr.com/image/RhclJr1sSjG3WpqEttwQsA.png>

- Thay đổi title web client

Chỉnh sửa file/opt/zimbra/jetty/webapps/zimbra/WEB-INF/classes/messages/ZmMsg.properties

Tìm từ zimbraLoginTitle ở dòng 3749 sửa giá trị thành title mong muốn (tiếng Anh hoặc tiếng Việt không dấu).


<img src=https://image.prntscr.com/image/LWm8q8ptRjuBstrs-iHRHw.png>

Restart service `mailboxd`

```
su zimbra
zmmailboxdctl restart
```
- Kiểm tra

<img src=https://image.prntscr.com/image/4WqU1vjeTeW9wFSA93916Q.png>

2. Thay đổi title web mail client
Khi login vào giao diện web email để tiến thành gửi/nhận thư title trên thành trình duyệt sẽ hiển thị dạng Zimbra: bạn có thể chỉnh sửa theo ý muốn.

- Title web mail client mặc định

<img src=https://image.prntscr.com/image/MxjdKHgtSKqaB3UhmDCGfA.png>

- Thay đổi web mail client

Chỉnh sửa file /opt/zimbra/jetty/webapps/zimbra/WEB-INF/classes/messages/ZmMsg.properties
Tìm từ `zimbraTitle` ở dòng `3747` sửa giá trị thành title mong muốn (tiếng Anh hoặc tiếng Việt không dấu).

<img src=https://image.prntscr.com/image/WXMGnUHpSLa5T2fI5FrfHA.png>

Restart service mailboxd

```
su zimbra
zmmailboxdctl restart
```
- Kiểm tra

<img src= https://image.prntscr.com/image/4kbBPXToQG2ABROPBxmHlA.png>

3. Thay đổi title web administrator
- Title web login administrator mặc định

<img src=https://image.prntscr.com/image/97FDeZRcQq6c4xcrU31wfQ.png>

- Thay đổi web web login administrator

Chỉnh sửa file /opt/zimbra/jetty_base/webapps/zimbraAdmin/WEB-INF/classes/messages/ZabMsg.properties
Tìm từ zimbraAdminTitle ở dòng 20 sửa giá trị thành title mong muốn (tiếng Anh hoặc tiếng Việt không dấu).

<img src=https://image.prntscr.com/image/pbluDdhlTLadpu8K42TdvQ.png>

Restart service mailboxd

```
su zimbra
zmmailboxdctl restart
```
- Kiểm tra

Xóa cache trình duyệt và kiểm tra lại

<img src=https://image.prntscr.com/image/YDXaGobPQOmr8G5vm6WYOQ.png>



