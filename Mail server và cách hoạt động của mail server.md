# Mail server và cách hoạt động của mail server

## 1. Mail server là gì?

- Mail Server hay Email Server là hệ thống máy chủ được cấu hình riêng theo tên miền của doanh nghiệp dùng để gửi và nhận thư điện tử.

- Mail Server cơ bản vẫn là Dedicated Server (Server riêng lẻ) hay Cloud Server (Server điện toán đám mây) được cấu hình để biến thành một cỗ máy gửi và nhận thư điện tử. Nó cũng có đầy đủ các thông số như một Server bình thường như Ram, CPU, Storage,… ngoài ra, nó còn có các thông số khác liên quan đến yếu tố Email như số lượng tài khoản Email, Email fowarder, Mail list,…

## 2. Cách thức hoạt động của mail server

- Mail Server hoạt động dựa trên 3 giao thức cơ bản bao gồm:

<img src=https://image.prntscr.com/image/GGKPHB7uRH_Z-NjZz_0ERg.png>

### Outgoing Mail Server là gì?

- Outgoing Mail Server hay Mail Server gửi đi sử dụng giao thức SMTP (Simple Mail Transfer Protocol). Đây là giao thức dịch chuyển mail đơn giản được dùng để liên lạc với server từ xa. Đồng thời cho phép gửi nhiều thư cùng một lúc tới các server khác nhau.

    - Giao thức STMP: SMTP là viết tắt của Simple Mail Transfer Protocol hay giao thức truyền tải thư tín đơn giản là một chuẩn truyền tải thư điện tử qua mạng Internet.
    SMTP được dùng để liên lạc với server từ xa và gửi email từ mail client tới mail server và sau đó được gửi đến server mail của email nhận. Quá trình này được điều khiển bởi Mail Transfer Agent (MTA) trên email server của bạn. Cũng vậy, SMTP chỉ được dùng cho mục đích gửi email.

<img src= https://image.prntscr.com/image/uEXl7vESTNStEc4LMzofXg.png>

    - SMTP sử dụng ports:
        - Port 25 – port không mã hóa
        - Port 465 – SSL/TLS port, cũng có thể được gọi là SMTPS

### Incoming Mail Server là gì?

- Incoming Mail Server sử dụng 2 giao thức POP3 và IMAP:
    - POP3  là viết tắt của Post Office Protocol version 3 là một giao thức tầng ứng dụng, dùng để lấy thư điện tử từ server mail, thông qua kết nối TCP/IP.
        - POP3 được sử dụng để kết nối tới server email và tải email xuống máy tính cá nhân thông qua ứng dụng email client như Outlook, Thunderbird, Windows Mail, Mac Mail…

<img src= https://image.prntscr.com/image/LzXxs699S3ic3C0oI-igVw.png>


        - Thông  thường, email client sẽ có tùy chọn bạn có muốn giữ mail trên server sau khi tải về hay không. Nếu bạn đang truy cập một tài khoản bằng nhiều thiết, chúng tôi khuyên là nên chọn giữ lại bản copy trên server nếu không thiết bị thứ 2 sẽ không thể tải mail về được vì nó đã bị xóa sau khi tải về trên thiết bị 1.

        - Cũng đáng để lưu ý là POP3 là giao thức 1 chiều, có nghĩa là email được “kéo” từ email server từ xa xuống email client.

        - Mặc đình, port POP3 là:

        Port 110 – port không mã hóa
        Port 995 – SSL/TLS port, cũng có thể được gọi là POP3S

     - IMAP là viết tắt của Internet Message Access Protocol, là giao thức chuẩn Internet được sử dụng bởi các ứng dụng email để truy xuất thư email từ máy chủ thư qua kết nối TCP/IP.

     Giống như POP3, IMAP cũng  được dùng để kéo email về emails client, tuy nhiên khác biệt với POP3 là nó chỉ kéo email headers về, nội dung email vẫn còn trên server. Đây là kênh liên lạc 2 chiều, thay đổi trên mail client sẽ được chuyển lên server.

<img src= https://image.prntscr.com/image/AzUhYkduRaWg1xyGyMf1gw.png>

    Sau này, giao thức này trở nên phổ biến nhờ nhà cung cấp mail lớn nhất thế giới, Gmail, khuyên dùng thay vì POP3.

    - Port IMAP mặc định:

    Port 143 – port không mã hóa
    Port 993 – SSL/TLS port, cũng có thể được gọi là IMAPS


### Tính năng nổi bật của Mail Server

- Mail Server mang đến cho người dùng cá nhân và doanh nghiệp nhiều tính năng:

    - Cho phép người dùng khi gửi email hay nhận mail có thể thông qua Internet trực tiếp với những tên miền cụ thể của từng tổ chức.
    - Hạn chế tối đa các thư spam hoặc chứa virus.
    - Đảm bảo sự bảo mật thông tin nội bộ một cách chặt chẽ.
    - Có thể thiết lập dung lượng tối đa cho từng người dùng Mail Server.
    - Quản lý được toàn bộ nội dung mail của tất cả các thành viên thuộc hệ thống.
    - Thiết lập được chức năng sao lưu dữ liệu tự động. Đảm bảo thông tin cần thiết luôn tồn tại.

### Phân loại Mail Server

- Mail Server Microsoft, Google là gì?
Mail server Microsoft và Google là 2 cái tên lớn đại diện cho dịch vụ này. Nền tảng xây dựng loại server mail này có quy mô lớn, hệ thống bảo mật chặt chẽ. Có thể quản lý tốt những dữ liệu hiện có. Người dùng có thể sử dụng được nhiều tiện ích khác nhau. Cũng chính vì thế mà giá cả sử dụng dịch vụ server mail loại này thường khá cao. Ví dụ: Email 365 (Microsoft), G Suite (Google),….

- Mail Server độc lập là gì?
Mail Server độc lập là hệ thống Mail Server được thiết kế cho các tổ chức hoặc ISP xử lý khối lượng thư lớn, yêu cầu kiểm soát và linh hoạt hơn đối với các dịch vụ thư. Nó bổ sung các tính năng như hợp tác, đồng bộ hóa Outlook, quản trị từ xa, Webmail và Quản trị Web nâng cao hơn và kết nối cơ sở dữ liệu, cung cấp cho bạn sức mạnh và kiểm soát cần thiết cho các hoạt động quy mô lớn.