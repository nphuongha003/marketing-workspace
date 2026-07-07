# Ví dụ nhiệm vụ — Performance Marketing Agent

## Yêu cầu

> "Khách hàng muốn chạy Google Ads với ngân sách 100 triệu."

## Cách Agent xử lý

1. **Nhận yêu cầu**: ghi nhận yêu cầu — khách hàng muốn chạy Google Ads, ngân sách 100.000.000đ. Chưa có dữ liệu quảng cáo thực tế nào (chưa từng chạy chiến dịch).
2. **Xác định mục tiêu**: đây là nhiệm vụ **lập kế hoạch cho chiến dịch mới**, chưa phải phân tích dữ liệu đã có.
3. **Chọn Skill phù hợp**: vì chưa có số liệu thực tế, Agent dùng Skill **`campaign-planner`** trước tiên để xây dựng kế hoạch quảng cáo (mục tiêu, cấu trúc chiến dịch, phân bổ ngân sách, KPI kỳ vọng, timeline sơ bộ) cho ngân sách 100 triệu.
4. **Thực hiện lập kế hoạch**: Agent hỏi lại các thông tin cần thiết còn thiếu (nếu có) như ngành hàng, mục tiêu chiến dịch (traffic/lead/conversion), đối tượng mục tiêu... rồi hoàn thiện kế hoạch theo quy trình của `campaign-planner`.
5. **Trả kết quả (giai đoạn 1)**: bàn giao kế hoạch quảng cáo cho Client Support Agent để đưa vào proposal gửi khách hàng.

## Giai đoạn tiếp theo (sau khi chiến dịch đã chạy và có dữ liệu)

- Khi chiến dịch đã triển khai và có dữ liệu thực tế (impression, click, conversion...), nếu người dùng yêu cầu đánh giá hiệu quả hoặc lên báo cáo, Agent sẽ:
  1. Xác định mục tiêu mới: đây là nhiệm vụ **phân tích/đánh giá chiến dịch đã có dữ liệu**.
  2. Chọn Skill phù hợp: chuyển sang dùng Skill **`ads-report`** để phân tích số liệu, sinh insight/recommendation và đánh giá KPI so với kế hoạch đã lập ở bước trước.
  3. Trả kết quả: bàn giao báo cáo phân tích cho Client Support Agent để soạn phản hồi/báo cáo gửi khách hàng.

## Tóm tắt lựa chọn Skill theo từng giai đoạn

| Giai đoạn | Có dữ liệu thực tế? | Skill sử dụng |
|---|---|---|
| Trước khi chạy chiến dịch (lập kế hoạch ngân sách 100 triệu) | Không | `campaign-planner` |
| Sau khi chiến dịch đã chạy và có số liệu | Có | `ads-report` |
