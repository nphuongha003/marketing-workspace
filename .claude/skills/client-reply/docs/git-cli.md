# Hướng dẫn dùng Git CLI để lưu kết quả làm việc

## Nguyên tắc quan trọng

- Skill này **không tự động chạy Git CLI**.
- Chỉ sử dụng các lệnh Git khi **người dùng chủ động yêu cầu** lưu lại hoặc quản lý kết quả làm việc (ví dụ: "lưu lại giúp mình", "commit file này", "đẩy lên repo").
- Không tự ý commit hoặc push khi người dùng chỉ đang nhờ soạn nội dung (tin nhắn, báo cáo, proposal...) mà chưa yêu cầu lưu bằng Git.
- Trước khi chạy các lệnh có ảnh hưởng đến remote (`git push`), luôn xác nhận lại với người dùng phạm vi thay đổi sẽ được đẩy lên.

## Các lệnh cơ bản

### 1. `git status`

Kiểm tra trạng thái hiện tại của thư mục làm việc: file nào đã thay đổi, file nào chưa được theo dõi (untracked).

```
git status
```

Dùng lệnh này đầu tiên để biết chính xác những gì sẽ được lưu lại, tránh add nhầm file không liên quan.

### 2. `git add`

Đưa file thay đổi vào staging area (chuẩn bị commit).

```
git add <đường-dẫn-file>
```

- Ưu tiên add từng file/thư mục cụ thể theo đúng nội dung người dùng yêu cầu lưu, tránh dùng `git add .` một cách tuỳ tiện nếu có file không liên quan trong thư mục.

### 3. `git commit`

Lưu lại các thay đổi đã staging thành một commit, kèm mô tả ngắn gọn về nội dung thay đổi.

```
git commit -m "Mô tả ngắn gọn nội dung đã thay đổi"
```

- Nội dung commit message nên mô tả rõ đã thay đổi/thêm gì (ví dụ: "Thêm báo cáo quảng cáo tháng 6 cho khách hàng ABC").

### 4. `git push`

Đẩy các commit đã lưu ở local lên remote repository.

```
git push
```

- Chỉ thực hiện khi người dùng yêu cầu rõ ràng là muốn đẩy lên remote (không chỉ lưu local).
- Nếu chưa rõ nhánh (branch) hoặc remote đích, hỏi lại người dùng trước khi thực hiện.

## Quy trình gợi ý khi người dùng yêu cầu "lưu lại bằng Git"

1. Chạy `git status` để xác nhận những file nào đã thay đổi.
2. Xác nhận với người dùng (nếu cần) những file nào nên được lưu.
3. Chạy `git add` cho đúng các file liên quan.
4. Chạy `git commit` với message mô tả rõ ràng nội dung thay đổi.
5. Chỉ chạy `git push` nếu người dùng yêu cầu đẩy lên remote.
