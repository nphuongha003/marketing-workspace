# Ví dụ nhiệm vụ — Client Support Agent

## Yêu cầu

> "Khách hàng yêu cầu gửi proposal triển khai Google Ads."

## Cách Agent xử lý

1. **Nhận yêu cầu hoặc kết quả từ Performance Marketing Agent**: ghi nhận yêu cầu khách hàng cần proposal triển khai Google Ads. Nếu Performance Marketing Agent đã lập kế hoạch quảng cáo (mục tiêu, ngân sách, KPI, timeline) từ trước, Client Support Agent lấy kết quả đó làm đầu vào; nếu chưa có, cần yêu cầu Performance Marketing Agent lập kế hoạch trước (xem `docs/collaboration.md`).
2. **Xác định mục tiêu giao tiếp**: đây là tình huống soạn **proposal mới** gửi khách hàng.
3. **Chọn Skill phù hợp**: dùng Skill **`proposal-generator`** để xây dựng proposal hoàn chỉnh (thông tin khách hàng, hiện trạng, mục tiêu, chiến lược, KPI, timeline, ngân sách, deliverables) và báo giá đi kèm.
4. **Soạn nội dung**: điền proposal theo `templates/proposal-template.md` và báo giá theo `templates/quotation-template.md` của Skill `proposal-generator`, dựa trên kế hoạch Google Ads đã có.
5. **Kiểm tra giọng văn**: rà soát theo `checklist/qa-checklist.md` của `proposal-generator` (đủ mục tiêu, KPI, timeline, ngân sách, CTA, không placeholder, không sai chính tả).
6. **Trả kết quả (giai đoạn 1)**: bàn giao proposal và báo giá hoàn chỉnh.

## Giai đoạn tiếp theo (sau khi đã có báo cáo hiệu quả chiến dịch)

- Nếu chiến dịch Google Ads đã triển khai và Performance Marketing Agent đã gửi báo cáo phân tích (dùng Skill `ads-report`), khi cần soạn email gửi khách kèm báo cáo đó, Agent sẽ:
  1. Xác định mục tiêu giao tiếp mới: đây là tình huống **trả lời khách sau khi gửi báo cáo**.
  2. Chọn Skill phù hợp: chuyển sang dùng Skill **`client-reply`** (template `report-reply.md`) để soạn email/tin nhắn gửi khách kèm báo cáo.
  3. Kiểm tra giọng văn theo `checklist/qa-checklist.md` và `docs/tone-of-voice.md` của `client-reply`.
  4. Trả kết quả: nội dung email/tin nhắn sẵn sàng gửi khách hàng.

## Tóm tắt lựa chọn Skill theo từng giai đoạn

| Giai đoạn | Tình huống | Skill sử dụng |
|---|---|---|
| Trước khi triển khai (gửi proposal Google Ads) | Cần tạo proposal + báo giá | `proposal-generator` |
| Sau khi đã có báo cáo hiệu quả chiến dịch | Cần soạn email/tin nhắn gửi kèm báo cáo | `client-reply` |
