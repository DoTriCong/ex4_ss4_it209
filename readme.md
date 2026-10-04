# Bài 4: Quản lý tệp tin bỏ qua (.gitignore) và Sửa lịch sử (Amend)

## 1. Mục tiêu

* Cấu hình `.gitignore` để Git bỏ qua file chứa thông tin nhạy cảm.
* Gỡ `credentials.txt` khỏi Git cache/index nhưng vẫn giữ file trên máy tính.
* Sử dụng `git commit --amend` để sửa thông điệp của commit gần nhất.

## 2. Cấu hình `.gitignore`

Tạo file `.gitignore` với nội dung:

```gitignore
credentials.txt
```

Sau khi cấu hình, Git sẽ bỏ qua `credentials.txt` trong những lần theo dõi và commit tiếp theo.

## 3. Gỡ file khỏi Git cache

Do `credentials.txt` đã được commit trước đó nên chỉ thêm vào `.gitignore` là chưa đủ.

Sử dụng lệnh:

```bash
git rm --cached credentials.txt
```

Lệnh trên chỉ gỡ file khỏi Git index/cache và **không xóa file vật lý khỏi thư mục làm việc**.

Kiểm tra trạng thái:

```bash
git status
```

Kết quả mong đợi: `credentials.txt` không còn xuất hiện dưới dạng file cần commit hoặc file bị modified.

## 4. Sửa commit gần nhất bằng Amend

Sử dụng:

```bash
git commit --amend -m "chore: ignore sensitive credentials"
```

Lệnh `--amend` thay thế commit gần nhất bằng một commit mới có nội dung/thông điệp đã được chỉnh sửa.

## 5. Kiểm tra lịch sử commit

Sử dụng:

```bash
git log -n 1
```

Kết quả:

```text
commit <commit-id>
Author: <author>
Date: <date>

    chore: ignore sensitive credentials
```

Thông điệp commit gần nhất đã được sửa thành công.

## 6. Kết luận

* Đã tạo `.gitignore` để bỏ qua `credentials.txt`.
* Đã sử dụng `git rm --cached credentials.txt` để gỡ file khỏi Git cache.
* File `credentials.txt` vẫn được giữ lại trên máy tính.
* Đã sử dụng `git commit --amend` để sửa thông điệp commit gần nhất.
