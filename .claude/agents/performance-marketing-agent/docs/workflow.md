# Workflow xử lý nhiệm vụ — Performance Marketing Agent

Workflow tổng quát từ lúc nhận yêu cầu đến khi bàn giao kết quả:

```
1. Nhận yêu cầu
        ↓
2. Xác định mục tiêu
        ↓
3. Chọn Skill phù hợp
        ↓
4. Thực hiện phân tích hoặc lập kế hoạch
        ↓
5. Trả kết quả
```

## Bước 1 — Nhận yêu cầu

- Tiếp nhận yêu cầu công việc (từ người dùng trực tiếp, hoặc được chuyển tiếp từ agent/quy trình khác).
- Ghi nhận các thông tin đầu vào có sẵn: khách hàng, ngân sách, dữ liệu quảng cáo (nếu có), mục tiêu đã nêu.

## Bước 2 — Xác định mục tiêu

- Làm rõ nhiệm vụ thuộc loại nào:
  - **Lập kế hoạch cho chiến dịch mới** (chưa có dữ liệu thực tế chạy quảng cáo), hoặc
  - **Phân tích/đánh giá chiến dịch đã có dữ liệu** (đã chạy quảng cáo, cần báo cáo/insight/recommendation/đánh giá KPI).
- Nếu thông tin đầu vào chưa đủ để xác định mục tiêu (ví dụ thiếu ngân sách, thiếu số liệu), hỏi lại trước khi tiếp tục.

## Bước 3 — Chọn Skill phù hợp

- Nếu là chiến dịch mới, chưa có số liệu thực tế → dùng Skill `campaign-planner` để lập kế hoạch.
- Nếu đã có dữ liệu quảng cáo (số liệu người dùng cung cấp hoặc từ Google Sheets) → dùng Skill `ads-report` để phân tích và sinh báo cáo/recommendation.
- Một số nhiệm vụ có thể cần dùng nối tiếp cả hai Skill (ví dụ: lập kế hoạch trước bằng `campaign-planner`, sau khi chiến dịch chạy có dữ liệu thì dùng `ads-report` để đánh giá) — xem ví dụ minh hoạ tại `examples/sample-task.md`.

## Bước 4 — Thực hiện phân tích hoặc lập kế hoạch

- Tuân theo đúng quy trình nội bộ của Skill đã chọn (đọc template, đối chiếu ví dụ, áp dụng checklist QA của Skill đó trước khi xem là hoàn tất).
- Đảm bảo mọi số liệu, nhận xét, recommendation đều có căn cứ rõ ràng; không tự suy đoán khi thiếu dữ liệu quan trọng.

## Bước 5 — Trả kết quả

- Bàn giao kết quả ở dạng có thể sử dụng ngay: kế hoạch quảng cáo, báo cáo phân tích, hoặc bảng đánh giá KPI.
- Nếu nhiệm vụ tiếp theo là giao tiếp với khách hàng (gửi proposal, trả lời khách, nhắc ngân sách...), chuyển kết quả cho Client Support Agent theo mô tả tại `docs/collaboration.md` thay vì tự soạn nội dung gửi khách.
