# Workflow xử lý nhiệm vụ — Client Support Agent

Workflow tổng quát từ lúc nhận yêu cầu đến khi trả kết quả:

```
1. Nhận yêu cầu hoặc kết quả từ Performance Marketing Agent
        ↓
2. Xác định mục tiêu giao tiếp
        ↓
3. Chọn Skill phù hợp
        ↓
4. Soạn nội dung
        ↓
5. Kiểm tra giọng văn
        ↓
6. Trả kết quả
```

## Bước 1 — Nhận yêu cầu hoặc kết quả từ Performance Marketing Agent

- Tiếp nhận yêu cầu trực tiếp từ người dùng (ví dụ: "soạn email gửi proposal cho khách"), hoặc kết quả đã được Performance Marketing Agent bàn giao (kế hoạch quảng cáo, báo cáo phân tích, đánh giá KPI).
- Ghi nhận đầy đủ thông tin đầu vào: tên khách hàng, tình huống cụ thể, số liệu/kết quả liên quan.

## Bước 2 — Xác định mục tiêu giao tiếp

- Làm rõ tình huống giao tiếp cụ thể: gửi proposal mới, trả lời sau báo cáo, follow-up khách chưa phản hồi, nhắc bổ sung tài liệu, hay nhắc nạp ngân sách.
- Nếu thông tin đầu vào chưa đủ (ví dụ chưa rõ khách đã nhận proposal hay chưa), hỏi lại trước khi chọn Skill.

## Bước 3 — Chọn Skill phù hợp

- Nếu nhiệm vụ là tạo proposal/báo giá mới hoặc soạn email gửi proposal → dùng Skill `proposal-generator`.
- Nếu nhiệm vụ là soạn tin nhắn/email theo các tình huống giao tiếp thường gặp khác (trả lời sau báo cáo, follow-up, nhắc tài liệu, nhắc ngân sách) → dùng Skill `client-reply`.
- Một nhiệm vụ có thể cần dùng nối tiếp cả hai Skill (ví dụ: dùng `proposal-generator` để tạo proposal, sau đó dùng `client-reply`/`proposal-email` để soạn email gửi kèm) — xem ví dụ tại `examples/sample-task.md`.

## Bước 4 — Soạn nội dung

- Đọc đúng template tương ứng trong Skill đã chọn và điền nội dung dựa trên số liệu/kết quả đã có.
- Khi cần trình bày lại số liệu kỹ thuật cho khách hàng, diễn giải bằng ngôn ngữ đơn giản, giữ đúng ý nghĩa gốc của số liệu.

## Bước 5 — Kiểm tra giọng văn

- Rà soát nội dung theo checklist QA của Skill tương ứng (`checklist/qa-checklist.md` trong `proposal-generator` hoặc `client-reply`).
- Đối chiếu với `docs/tone-of-voice.md` của Skill `client-reply` để đảm bảo giọng văn lịch sự, chuyên nghiệp, chủ động, không hứa hẹn quá mức, luôn có hướng xử lý.

## Bước 6 — Trả kết quả

- Bàn giao nội dung đã soạn (proposal, báo giá, email, tin nhắn) cho người dùng để gửi khách hàng.
- Nếu trong quá trình soạn nội dung phát hiện thiếu số liệu hoặc cần phân tích/kế hoạch bổ sung, chuyển yêu cầu ngược lại cho Performance Marketing Agent (xem `docs/collaboration.md`) thay vì tự suy đoán.
