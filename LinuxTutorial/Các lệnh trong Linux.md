# Các lệnh trong linux

## 1. lệnh ls

- `ls` :Liệt kê các tập tin mà không có tùy chọn

- `ls -l`:  hiển thị tệp hoặc thư mục, kích thước, ngày, thời gian đã sửa đổi, tên tệp hoặc tên thư mục và chủ sở hữu (owner) tệp file và đó là sự cho phép (permission).

- `ls -a`: Xem tập tin ẩn. Liệt kê tất cả các tệp tin kể cả tệp ẩn bắt đầu bằng ‘.’.

- `ls -alh`: Xem tất cả các tệp tin ẩn và tệp tin có thể đọc được.

- `ls -F` : Liệt kê các Tệp và Thư Mục với Ký tự ‘/’  ở cuối.

- `ls -R` : Liệt kê các cây thư mục liệt kê rất dài.

- `ls -N` : Hiển thị UID và GID của Tệp

- `ls -i` : Hiển thị số Inode của File hoặc Directory.

- `ls -lS` : Sắp xếp tệp theo Kích thước tệp.

## 2. lên cd

- `cd` : di chuyển vào thưu mục mong muốn.

- `cd-` : Di chuyển một thư mục từ nơi bạn đang ở.

- `cd..`: Thay đổi thư mục hiện tại thành thư mục cha.

- `cd --` : Hiển thị thư mục làm việc cuối cùng từ nơi bạn di chuyển.

- `cd~` : Di chuyển đến thư mục chính của người dùng từ bất cứ đâu.

## 3. lệnh mkdir

- `mkdir <path_name_1>`: Tạo thư mục tại thư mục hiện hành

- `mkdir <path_name_1> <path_name_2> <path_name_3>`: tạo nhiều thư mục cùng lúc.

## 4. lệnh rm

- `rm <ten_tep_tin>` : xóa 1 tập tin
- `rm <tap_tin_1> <tap_tin_2> ...` : xóa nhiều tập tin
- `rm /a/b/c/<tap_tin>` : xóa tập tin theo đường dẫn
- `rm -i <ten_tep_tin>` : xóa có xác nhận
- `rm -f <ten_tap_tin>` : xóa không xác nhận
- `rm -I <ten_thu_muc>/file*` : xóa hàng loạt file có kiểu file[...]

## 5. lệnh rmdir

- `rmdir <ten_thu_muc>` hoặc rm -d : xóa 1 thư mục rỗng
- `rm -r <ten_thu_muc>` : xóa thư mục chứa các thư mục con và tập tin có xác nhận từng đối tượng.

## 6. Các option dùng với lệnh tar
- c : tạo file nén .tar.

- x : bung file nén .tar.

- v : show quá trình nén hoặc giải nén dữ liệu ra màn hình.

- f : chỉ định nén thành file.
- t : Xem dữ liệu trong file nén.
- j : tạo file nén với bzip2 có định dạng file.tar.bz2
- z : tạo file nén với gzip có định dạng file.tar.gz.
- r : thêm một file và thư mục vào file nén đã tồn tại.
- --wildcards : tìm và xuất file bất kỳ trong file nén.