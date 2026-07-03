---
name: client-reply
description: Hỗ trợ soạn tin nhắn/email trả lời khách hàng trong các tình huống thường gặp (sau khi gửi báo cáo, nhắc phản hồi, nhắc bổ sung thông tin, gửi proposal/báo giá, nhắc nạp ngân sách quảng cáo) với giọng văn chuyên nghiệp, lịch sự, chủ động. Dùng khi người dùng cần soạn/kiểm tra tin nhắn gửi khách hàng, hoặc cần lưu kết quả làm việc bằng Git khi được yêu cầu.
---

# Client Reply

## Mục đích

Skill này giúp Claude hỗ trợ soạn các tin nhắn/email trả lời khách hàng thường gặp trong công việc Digital Marketing, đảm bảo:

- Giọng văn chuyên nghiệp, lịch sự, chủ động, đúng chuẩn giao tiếp với khách hàng.
- Nội dung phù hợp với từng tình huống cụ thể (sau báo cáo, nhắc phản hồi, nhắc tài liệu, gửi proposal, nhắc ngân sách...).
- Luôn có hướng xử lý và lời kêu gọi hành động (CTA) rõ ràng, không đổ lỗi cho khách hàng.
- Có checklist tự kiểm tra trước khi gửi để tránh sai sót về giọng văn, chính tả.

Ngoài ra, Skill cũng hướng dẫn cách dùng Git CLI để lưu lại kết quả làm việc **khi người dùng chủ động yêu cầu**.

## Khi nào nên dùng Skill này

- Khi người dùng cần soạn tin nhắn/email trả lời khách sau khi gửi báo cáo quảng cáo.
- Khi cần nhắc khách phản hồi vì đã im lặng vài ngày.
- Khi cần nhắc khách bổ sung thông tin/tài liệu còn thiếu.
- Khi cần soạn email gửi proposal và báo giá cho khách.
- Khi cần nhắc khách nạp thêm ngân sách quảng cáo.
- Khi người dùng cần rà soát lại một tin nhắn/email đã soạn trước khi gửi (QA giọng văn).
- Khi người dùng yêu cầu **lưu hoặc quản lý kết quả làm việc bằng Git** (xem `docs/git-cli.md`).

## Cách sử dụng các tài nguyên trong Skill

Không cần đọc hết mọi file — chỉ đọc file phù hợp với tác vụ đang làm:

- **Trả lời khách sau khi gửi báo cáo**: đọc `templates/report-reply.md`, tham khảo `examples/sample-report-reply.md`.
- **Nhắc khách phản hồi khi im lặng vài ngày**: đọc `templates/follow-up.md`, tham khảo `examples/sample-follow-up.md`.
- **Nhắc khách bổ sung thông tin/tài liệu**: đọc `templates/reminder.md`.
- **Gửi proposal và báo giá**: đọc `templates/proposal-email.md`.
- **Nhắc khách nạp thêm ngân sách quảng cáo**: đọc `templates/budget-reminder.md`.
- **Kiểm tra chất lượng tin nhắn trước khi gửi**: đọc `checklist/qa-checklist.md` và rà soát theo từng mục.
- **Cần định hướng giọng văn/phong cách giao tiếp**: đọc `docs/tone-of-voice.md`.
- **Người dùng yêu cầu lưu kết quả bằng Git**: đọc `docs/git-cli.md` để biết cách hướng dẫn/thực hiện đúng quy trình.

Luôn ưu tiên đọc file tương ứng trước khi soạn nội dung, thay vì tự suy đoán cấu trúc hoặc giọng văn.

## Quy trình gợi ý khi soạn tin nhắn/email gửi khách

1. Xác định đúng tình huống (sau báo cáo / nhắc phản hồi / nhắc tài liệu / proposal / nhắc ngân sách) để chọn đúng template.
2. Nếu chưa chắc về giọng văn phù hợp, đọc `docs/tone-of-voice.md` trước khi soạn.
3. Đọc template tương ứng trong `templates/`, điền thông tin cụ thể của khách hàng/tình huống. Với các tình huống có ví dụ mẫu (report-reply, follow-up), tham khảo thêm file trong `examples/` để hình dung mức độ chi tiết phù hợp.
4. Rà soát nội dung theo `checklist/qa-checklist.md` trước khi xem là hoàn tất.
5. Nếu người dùng yêu cầu lưu lại nội dung đã soạn (hoặc kết quả công việc khác) bằng Git, làm theo hướng dẫn trong `docs/git-cli.md` — chỉ thực hiện khi có yêu cầu rõ ràng, không tự động chạy.

## Lưu ý về văn phong

- Luôn giữ giọng văn lịch sự, chuyên nghiệp, chủ động; không đổ lỗi cho khách hàng hay bên thứ ba.
- Mọi tin nhắn cần có **hướng xử lý cụ thể** và **CTA rõ ràng** ở cuối, không để khách hàng phải đoán bước tiếp theo.
- Không hứa hẹn những điều chưa chắc chắn (kết quả, thời gian xử lý...) khi chưa có cơ sở.
