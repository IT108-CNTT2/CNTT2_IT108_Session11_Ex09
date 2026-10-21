# Tra cứu dữ liệu bằng VLOOKUP

## Phần 1: Phân tích

Trong Sheet `DanhSachBaoCao`, mã tác giả nằm ở ô `C2`.

Công thức VLOOKUP có dạng:

`=VLOOKUP(lookup_value,table_array,col_index_num,FALSE)`

Trong bài này:

- **Lookup_value:** `TRIM(C2)` → mã tác giả cần tìm và xóa khoảng trắng thừa.
- **Table_array:** `DanhMucTacGia!$A$2:$E$100` → vùng bảng tra cứu, dùng `$` để cố định.
- **Col_index_num:**
  - Tên tác giả: cột `2`
  - Phòng trình bày: cột `4`
  - Thù lao: cột `5`
- **FALSE:** tìm đúng chính xác mã tác giả.

Nếu không tìm thấy mã thì dùng `IFERROR` để không hiện lỗi `#N/A`.

## Phần 2: Công thức

### Ô D2 - Tên tác giả

`=IFERROR(VLOOKUP(TRIM(C2),DanhMucTacGia!$A$2:$E$100,2,FALSE),"Chưa cập nhật")`

### Ô E2 - Phòng trình bày

`=IFERROR(VLOOKUP(TRIM(C2),DanhMucTacGia!$A$2:$E$100,4,FALSE),"Chưa cập nhật")`

### Ô F2 - Thù lao

`=IFERROR(VLOOKUP(TRIM(C2),DanhMucTacGia!$A$2:$E$100,5,FALSE),"Chưa cập nhật")`

Sau đó kéo các công thức xuống các dòng còn lại.

Dấu `$` giúp vùng `A2:E100` không bị thay đổi khi kéo công thức xuống. Hàm `TRIM()` giúp xử lý trường hợp mã như `TG001 ` có khoảng trắng ở cuối.
