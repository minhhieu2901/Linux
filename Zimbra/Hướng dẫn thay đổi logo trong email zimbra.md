# Hướng dẫn thay đổi logo trong email zimbra

Phiên bản email server zimbra Network Edition hỗ trợ việc thay đổi logo trực tiếp trên giao diện web admin một các dễ dàng, còn ở phiên bản email server zimbra Open Source có thể thiết lập thay đổi logo theo ý muốn thông qua một số thao tác.

- Logo mặc định

+Logo trước khi đăng nhập (440×60 px)

<img src=https://image.prntscr.com/image/Ue19e8PgTguCInOkDFYIiw.png>

+Logo sau khi đăng nhập (200×35 px)

<img src=https://image.prntscr.com/image/5keKcaGqTMOshit7oE9XIg.png>

Lựa chọn logo đúng kích thước khuyến cáo khi thay thế sẽ vừa khung và đẹp hơn.

- Thay đổi logo

Bước 1: Tạo thư mục và upload logo
```
su zimbra
mkdir /opt/zimbra/jetty/webapps/zimbra/logos/
```

<img src= https://image.prntscr.com/image/2XFvgLcuRxG-kTpJblMuUw.png>

Upload ảnh mới và phân quyền zimbra:zimbra

<img src= https://image.prntscr.com/image/zOTSRiQoSmuJXI_cnxejnA.png>

Bước 2: Thay thế logo
```
zmprov md congtynhanhoa.space zimbraSkinLogoURL /logos/logo1.jpg

zmprov md congtynhanhoa.space zimbraSkinLogoLoginBanner /logos/logo1.jpg

zmprov md congtynhanhoa.space zimbraSkinLogoAppBanner /logos/logo1.jpg

zmmailboxdctl restart
```

<img src=https://image.prntscr.com/image/-Iy4xi73S02PaSPQhLRI6A.png>


Bước 3: Xóa cache và kiểm tra