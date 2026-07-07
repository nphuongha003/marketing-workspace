---
name: campaign-planner
description: Hỗ trợ xây dựng kế hoạch triển khai chiến dịch Digital Marketing (Google Ads, Facebook Ads, hoặc kết hợp cả hai) — từ mục tiêu, đối tượng, KPI, phân bổ ngân sách đến timeline và recommendation. Dùng khi khách hàng cần proposal, chuẩn bị báo giá, lập kế hoạch chạy quảng cáo, hoặc cần lập KPI theo ngân sách.
---

# Campaign Planner

## Mục đích

Skill này hỗ trợ xây dựng **kế hoạch triển khai chiến dịch Digital Marketing** — giúp Claude lập kế hoạch quảng cáo có cấu trúc, gắn mục tiêu với KPI và ngân sách cụ thể, trước khi chiến dịch được triển khai thực tế.

## Khi nào nên sử dụng

- Khi khách hàng cần proposal và cần một kế hoạch triển khai làm nền tảng nội dung.
- Khi cần chuẩn bị báo giá dựa trên kế hoạch phân bổ ngân sách theo kênh.
- Khi cần lập kế hoạch chạy quảng cáo mới (chưa có dữ liệu thực tế).
- Khi cần lập KPI dự kiến tương ứng với một mức ngân sách cụ thể.

## Skill có thể hỗ trợ

- **Google Ads** (Search, Display, Shopping...).
- **Facebook Ads** (Conversion, Traffic, Awareness, Remarketing...).
- **Google Ads + Facebook Ads kết hợp** — khi chiến dịch cần phối hợp nhiều kênh trong cùng một kế hoạch.

## Cách sử dụng các tài nguyên trong Skill

Không cần đọc hết mọi file — chỉ đọc file phù hợp với tác vụ đang làm:

- **Lập kế hoạch chiến dịch mới**: đọc `templates/campaign-plan.md` để lấy cấu trúc tổng thể.
- **Phân bổ ngân sách chi tiết theo kênh**: đọc `templates/budget-allocation.md`.
- **Lên timeline triển khai theo tuần**: đọc `templates/timeline.md`.
- **Cần hiểu framework lập kế hoạch**: đọc `docs/planning-framework.md` trước khi bắt đầu lập kế hoạch.
- **Cần giải thích hoặc tra cứu ý nghĩa KPI**: đọc `docs/kpi-reference.md`.
- **Cần ví dụ cụ thể**: tham khảo `examples/sample-google-ads.md` (kế hoạch chạy Google Ads) hoặc `examples/sample-facebook-ads.md` (kế hoạch chạy Facebook Ads).
- **Kiểm tra chất lượng kế hoạch trước khi bàn giao**: đọc `checklist/qa-checklist.md` và rà soát theo từng mục.

Luôn ưu tiên đọc file tương ứng trước khi tạo nội dung, thay vì tự suy đoán cấu trúc, benchmark hoặc định nghĩa KPI.

## Quy trình lập kế hoạch

1. **Phân tích mục tiêu**: xác định mục tiêu chính của chiến dịch (traffic/lead/conversion/awareness) và bối cảnh yêu cầu từ khách hàng.
2. **Phân tích khách hàng**: xác định đối tượng mục tiêu (nhân khẩu học, hành vi, insight) và ngành hàng liên quan.
3. **Xác định KPI**: đọc `docs/kpi-reference.md` để chọn đúng KPI phù hợp với mục tiêu, sau đó ước tính KPI dự kiến dựa trên benchmark ngành hoặc số liệu lịch sử (nếu có).
4. **Phân bổ ngân sách**: dùng `templates/budget-allocation.md` để chia ngân sách theo kênh (Google Search, Google Display, Facebook, Remarketing), có lý do rõ ràng gắn với mục tiêu.
5. **Đề xuất timeline**: dùng `templates/timeline.md` để lên kế hoạch triển khai theo tuần.
6. **Đưa ra recommendation**: tổng hợp thành kế hoạch hoàn chỉnh theo `templates/campaign-plan.md`, nêu rõ đề xuất và các lưu ý/rủi ro đi kèm; rà soát theo `checklist/qa-checklist.md` trước khi bàn giao.

## Lưu ý về văn phong

- KPI đề xuất phải luôn đi kèm ghi chú là **ước tính dựa trên benchmark**, không phải cam kết chắc chắn.
- Phân bổ ngân sách cần có lý do rõ ràng, gắn với mục tiêu chiến dịch, không chia đều một cách máy móc.
- Nếu thiếu thông tin quan trọng (ngành hàng, mục tiêu cụ thể, ngân sách), chủ động hỏi lại thay vì tự giả định để lập kế hoạch.
