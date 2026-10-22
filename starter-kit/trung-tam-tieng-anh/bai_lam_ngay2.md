# BÀI LÀM – ÔN TẬP NGÀY 2

- **Họ tên:** Nguyễn Hoàng Minh Phúc
- **Lớp:** CNTT2
- **Link repository:** 
- **Hệ điều hành (Windows/macOS):** Window

## Bài 1. Lọc log thủ công

### Lệnh đã chạy

```
..Downloads\starter-kit\trung-tam-tieng-anh\logs> gc .\access.log| Select-String "ERROR" > error_report.txt
..Downloads\starter-kit\trung-tam-tieng-anh\logs> gc .\access.log | Select-string "Warning"
..Downloads\starter-kit\trung-tam-tieng-anh\logs> gc .\payment.log | Select-string "Error"
..Downloads\starter-kit\trung-tam-tieng-anh\logs> cd ..
..Downloads\starter-kit\trung-tam-tieng-anh> ni auto_warning.ps1
..Downloads\starter-kit\trung-tam-tieng-anh> Set-ExecutionPolicy Bypass -Scope Process
..Downloads\starter-kit\trung-tam-tieng-anh> .\auto_warning.ps1

```

### 2 dòng lỗi đầu tiên trong error_report.txt

```
2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)
```

## Bài 2. Đếm bằng pipeline

### Lệnh

```
(gc .\logs\access.log | Select-string "Error").Count
(gc .\logs\payment.log | Select-string "Warning").Count

```

### Kết quả đếm (Windows: giá trị Count; macOS: con số in ra)

```
6
5
```

## Bài 3. Chạy script auto_warning (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```
..Downloads\starter-kit\trung-tam-tieng-anh> Set-ExecutionPolicy Bypass -Scope Process
..Downloads\starter-kit\trung-tam-tieng-anh> .\auto_warning.ps1

```

### Nội dung file logs/warning_report.txt

```

2025-10-18 09:19:13 [WARNING] Cong thanh toan phan hoi cham
2025-10-18 09:28:16 [WARNING] Nhieu lan nhap sai ma OTP
2025-10-18 09:43:01 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:46:22 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:49:43 [WARNING] So du vi gan bang hoc phi



```

## Bài 4. Báo cáo tổng hợp

### Các lệnh đã chạy

```
"=== TONG HOP ACCESS LOG ===" > .\logs\tong_hop_ngay2.txt; gc logs/access.log | Select-string "Error" >> logs/tong_hop_ngay2.txt ; gc logs/payment.log | Select-String "Warning" >> logs/tong_hop_ngay2.txt
```

### Nội dung file logs/tong_hop_ngay2.txt

```
=== TONG HOP ACCESS LOG ===

2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:33:51 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:37:19 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:49:43 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:53:11 [ERROR] Het thoi gian cho (timeout)



2025-10-18 09:19:13 [WARNING] Cong thanh toan phan hoi cham
2025-10-18 09:28:16 [WARNING] Nhieu lan nhap sai ma OTP
2025-10-18 09:43:01 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:46:22 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:49:43 [WARNING] So du vi gan bang hoc phi




```

## Bài 5. Câu hỏi ngắn

- **a)** Sự khác nhau ngắn gọn nhất giữa > và >>:
- Ghi đè: Tạo file mới (nếu chưa có) hoặc xóa toàn bộ nội dung cũ trong file rồi ghi nội dung mới vào.
- Ghi nối tiếp: Giữ nguyên nội dung cũ của file và ghi thêm nội dung mới vào cuối file.
- **b)** Nếu dùng > thay cho >> ở lệnh thứ hai:
- Nội dung của file logs/tong_hop_ngay2.txt sẽ bị mất dòng đầu tiên (=== TONG HOP ACCESS LOG ===), và file sẽ chỉ còn lại các dòng lỗi ERROR được ghi đè mới nhất.
- **c)** Vì bó giúp script có tính di động, có thể chạy mượt mà trên mọi máy tính hoặc thư mục khác nhau mà không bị lỗi do thay đổi tên người dùng hay đường dẫn ổ đĩa.

## Tự chấm (điền sau khi có đáp án)

- **Điểm tự chấm:** ..../100
- **Lỗi mình đã mắc và cách sửa:**
