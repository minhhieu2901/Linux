# Hướng dẫn cài đặt SSL Let's Encrypt email server zimbra

Email server zimbra hỗ trợ việc cài đặt chứng chỉ SSL miễn phí Let's Encrypt cho mail.domain đại diện cho email server.

Sử dụng công cụ online để check trạng thái chứng chỉ SSL cho tền miền **https://www.sslshopper.com/ssl-checker.html**

Cài đặt Let's Encrypt cho mail.hieunm29198.xyz

- **Trước khi cài đặt SSL free**

<img src=https://image.prntscr.com/image/nebym2NLRoWNWlGwt7YQRg.png>

- **Các bước cài đặt**

**Bước 1**: Truy cập ssh vào server zimbra và stop hết các service
```
su zimbra
zmcontrol stop
```

<img src=https://image.prntscr.com/image/Qz8mptQHTgWLOejbNMsPyg.png >

**Bước 2**: Cài đặt git cho server
```
yum install git -y
```

**Bước 3**: Download Let's Encrypt
```
yum -y install epel-release
git clone https://github.com/letsencrypt/letsencrypt
cd letsencrypt
```

<img src=https://image.prntscr.com/image/DxtDO7QoTA2qMyI1s713hw.png>

Bước 4: Chạy auto chứng chỉ Let's Encrypt cho tên miền hieunm29198.xyz

```
./letsencrypt-auto certonly --standalone -d mail.hieunm29198.xyz
```
Sau khi chạy lệnh trên hệ thống sẽ hiển thị thông tin cần nhập

<img src= https://image.prntscr.com/image/GAgECF11SpqubEiHku7few.png>

Kết quả trả về như hình bên dưới là đã thành công ở bước này

<img src=https://image.prntscr.com/image/1gai9RA-T8Kv2BQQYXy0JA.png>


Bước 6: Kiểm tra lại key đã được tạo ra trong đường dẫn `/etc/letsencrypt/live/$domain` với `$domain` là tên domain mail.hieunm29198.xyz vừa nhập ở bước trên. Kết quả sẽ hiển thị giống ảnh bên dưới.

<img src=https://image.prntscr.com/image/dIp6GRFXRgu6-r-RlkVXqA.png>

Bước 7: Cần sửa lại file chain.pem trong thư mục trên để trust root CA

Mở file /etc/letsencrypt/live/mail.hieunm29198.xyz/chain.pem và chèn thêm đoạn mã sau vào cuối file.
```
-----BEGIN CERTIFICATE-----
MIIDSjCCAjKgAwIBAgIQRK+wgNajJ7qJMDmGLvhAazANBgkqhkiG9w0BAQUFADA/
MSQwIgYDVQQKExtEaWdpdGFsIFNpZ25hdHVyZSBUcnVzdCBDby4xFzAVBgNVBAMT
DkRTVCBSb290IENBIFgzMB4XDTAwMDkzMDIxMTIxOVoXDTIxMDkzMDE0MDExNVow
PzEkMCIGA1UEChMbRGlnaXRhbCBTaWduYXR1cmUgVHJ1c3QgQ28uMRcwFQYDVQQD
Ew5EU1QgUm9vdCBDQSBYMzCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEB
AN+v6ZdQCINXtMxiZfaQguzH0yxrMMpb7NnDfcdAwRgUi+DoM3ZJKuM/IUmTrE4O
rz5Iy2Xu/NMhD2XSKtkyj4zl93ewEnu1lcCJo6m67XMuegwGMoOifooUMM0RoOEq
OLl5CjH9UL2AZd+3UWODyOKIYepLYYHsUmu5ouJLGiifSKOeDNoJjj4XLh7dIN9b
xiqKqy69cK3FCxolkHRyxXtqqzTWMIn/5WgTe1QLyNau7Fqckh49ZLOMxt+/yUFw
7BZy1SbsOFU5Q9D8/RhcQPGX69Wam40dutolucbY38EVAjqr2m7xPi71XAicPNaD
aeQQmxkqtilX4+U9m5/wAl0CAwEAAaNCMEAwDwYDVR0TAQH/BAUwAwEB/zAOBgNV
HQ8BAf8EBAMCAQYwHQYDVR0OBBYEFMSnsaR7LHH62+FLkHX/xBVghYkQMA0GCSqG
SIb3DQEBBQUAA4IBAQCjGiybFwBcqR7uKGY3Or+Dxz9LwwmglSBd49lZRNI+DT69
ikugdB/OEIKcdBodfpga3csTS7MgROSR6cz8faXbauX+5v3gTt23ADq1cEmv8uXr
AvHRAosZy5Q6XkjEGB5YGV8eAlrwDPGxrancWYaLbumR9YbK+rlmM6pZW87ipxZz
R8srzJmwN0jP41ZL9c8PDHIyh8bwRLtTcm1D9SZImlJnt1ir/md2cXjbDaJWFBM5
JDGFoqgCWjBH4d1QB7wCCZAA62RjYJsWvIjJEubSfZGL+T0yjWW06XyxV3bqxbYo
Ob8VZRzI9neWagqNdwvYkQsEjgfbKbYK7p2CNTUQ
-----END CERTIFICATE-----
```

<img src= https://image.prntscr.com/image/XEhp01nERKqkfTI404mhUg.png>

Bước 8:Verify certificate

+ Copy Let’s Encrypt folder trong /etc/letsencrypt/live/$domain tới thư mục /opt/zimbra/ssl/letsencrypt
```
mkdir /opt/zimbra/ssl/letsencrypt
cp /etc/letsencrypt/live/mail.hieunm29198.xyz/* /opt/zimbra/ssl/letsencrypt/
chown zimbra:zimbra /opt/zimbra/ssl/letsencrypt/*
```
Bước 9: Verify chứng chỉ, với phiên bản zimbra 8.7 trở lên (Với phiên bản từ 8.6 trỏ xuống dùng user root nên bỏ qua lệnh su zimbra).
```
su zimbra
cd /opt/zimbra/ssl/letsencrypt
/opt/zimbra/bin/zmcertmgr verifycrt comm privkey.pem cert.pem chain.pem
```
<img src=https://image.prntscr.com/image/6XCrBIvZQsuNgxPLZoGc1g.png>

Bước 10: Deploy Let’s Encrypt SSL certificate mới, lệnh bên dưới sử dụng với quyền user root

+ Backup thư mục SSL của zimbra
```
cp -a /opt/zimbra/ssl/zimbra /opt/zimbra/ssl/zimbra.$(date "+%Y%m%d")
```
+ Copy private key tới đường dẫn Zimbra SSL commercial
```
cp /opt/zimbra/ssl/letsencrypt/privkey.pem /opt/zimbra/ssl/zimbra/commercial/commercial.key
```
chown zimbra:zimbra /opt/zimbra/ssl/zimbra/commercial/commercial.key
+ Deploy SSL
```
su zimbra
cd /opt/zimbra/ssl/letsencrypt
/opt/zimbra/bin/zmcertmgr deploycrt comm cert.pem chain.pem
```
Lưu ý: Lệnh deploy SSL áp dụng với zimbra version 8.7 trỏ lên, với zimbra version 8.6 trở xuống bỏ qua su zimbra

<img src=https://image.prntscr.com/image/THZ1KUdKQameQmFfUTtmLQ.png>

Bước 11: Restart service zimbra
```
su zimbra
zmcontrol restart
```
- **Kiểm tra sau khi cài đặt SSL Let's Encrypt**

<img src=https://image.prntscr.com/image/KdEdE42iRJWieWDiQ61zEw.png>

