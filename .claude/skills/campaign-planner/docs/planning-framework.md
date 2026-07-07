# Framework lập kế hoạch quảng cáo

## Nguyên tắc cốt lõi

Một kế hoạch chiến dịch tốt phải trả lời được liên tục chuỗi câu hỏi sau, theo đúng thứ tự — mỗi bước là nền tảng cho bước tiếp theo:

```
Mục tiêu là gì?
        ↓
Đối tượng nào giúp đạt mục tiêu đó?
        ↓
KPI nào đo lường đúng mục tiêu đó?
        ↓
Ngân sách nên phân bổ ra sao để đạt KPI đó?
        ↓
Timeline triển khai như thế nào là khả thi?
        ↓
Recommendation gì giúp tối đa hoá khả năng thành công?
```

Đây chính là 6 bước trong "Quy trình lập kế hoạch" của Skill này — không bước nào nên được thực hiện tách rời khỏi bước trước đó.

## 1. Mục tiêu quyết định tất cả

- Mọi lựa chọn về kênh, KPI, ngân sách đều phải xuất phát từ mục tiêu chiến dịch, không phải ngược lại.
- Mục tiêu cần cụ thể: "tăng nhận diện thương hiệu" khác hoàn toàn với "tăng đơn hàng online" về cách chọn kênh và KPI.

## 2. Đối tượng quyết định kênh và thông điệp

- Đối tượng có nhu cầu tìm kiếm chủ động → phù hợp Google Search.
- Đối tượng cần được "gợi mở" nhu cầu hoặc nhắm theo hành vi/sở thích → phù hợp Facebook Ads/Google Display.
- Đối tượng đã từng tương tác nhưng chưa chuyển đổi → phù hợp Remarketing.

## 3. KPI phải đo lường đúng mục tiêu

- Mỗi mục tiêu có KPI "sát sườn" tương ứng (xem `docs/kpi-reference.md`): mục tiêu nhận diện thương hiệu nên nhìn vào Reach/Impression/CPM hơn là CPA; mục tiêu chuyển đổi nên nhìn vào Conversion Rate/CPA/CPL/ROAS.
- Tránh đo lường một chiến dịch awareness bằng KPI của chiến dịch conversion và ngược lại — sẽ dẫn đến đánh giá sai hiệu quả.

## 4. Ngân sách nên linh hoạt theo giai đoạn

- Với chiến dịch hoàn toàn mới (chưa có dữ liệu lịch sử), nên dành một phần ngân sách cho giai đoạn thử nghiệm/tối ưu ban đầu thay vì phân bổ cứng ngay từ đầu.
- Phân bổ ngân sách giữa các kênh cần có lý do rõ ràng (xem `templates/budget-allocation.md`), không chia đều một cách máy móc.

## 5. Timeline cần khả thi và có mốc kiểm tra

- Chia nhỏ theo tuần (xem `templates/timeline.md`) để có điểm dừng đánh giá và điều chỉnh sớm, thay vì đợi đến hết chiến dịch mới nhìn lại.
- Mỗi giai đoạn (chuẩn bị → triển khai → tối ưu → báo cáo) cần có công việc cụ thể, không mô tả chung chung.

## 6. Recommendation phải có căn cứ

- Recommendation trong kế hoạch không phải là dự đoán, mà là **đề xuất hành động** gắn với mục tiêu, đối tượng và ngân sách đã phân tích ở các bước trước.
- Luôn nêu kèm giả định/rủi ro nếu recommendation dựa trên benchmark chưa được kiểm chứng bằng dữ liệu thực tế của khách hàng.
