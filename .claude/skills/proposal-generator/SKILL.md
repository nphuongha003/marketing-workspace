---
name: proposal-generator
description: Hỗ trợ xây dựng proposal (đề xuất) Digital Marketing, báo giá và email gửi khách hàng — từ phân tích hiện trạng, mục tiêu, chiến lược, KPI, timeline, ngân sách đến deliverables. Dùng khi người dùng yêu cầu viết proposal marketing, lập báo giá dịch vụ, hoặc soạn email gửi proposal cho khách/đối tác.
---

# Proposal Generator

## Mục đích

Skill này giúp Claude hỗ trợ đội ngũ Digital Marketing/Sales:

- Xây dựng proposal (đề xuất dịch vụ/chiến dịch) Digital Marketing theo cấu trúc chuẩn, thuyết phục.
- Lập báo giá (quotation) đi kèm proposal, rõ ràng về hạng mục, chi phí và điều khoản.
- Soạn email gửi proposal cho khách hàng với giọng văn chuyên nghiệp.
- Đảm bảo proposal đủ nội dung quan trọng trước khi gửi khách (qua checklist QA).

## Khi nào nên dùng Skill này

- Khi người dùng cần viết proposal mới cho một khách hàng/dự án Digital Marketing.
- Khi người dùng cần lập báo giá dịch vụ (gói dịch vụ, chi phí quảng cáo, chi phí quản lý...).
- Khi người dùng cần soạn email gửi kèm proposal/báo giá cho khách hàng.
- Khi người dùng cần rà soát lại một proposal đã viết trước khi gửi (QA).
- Khi người dùng hỏi cách xây dựng proposal Digital Marketing chuyên nghiệp, thuyết phục.

## Cách sử dụng các tài nguyên trong Skill

Không cần đọc hết mọi file — chỉ đọc file phù hợp với tác vụ đang làm:

- **Viết proposal mới**: đọc `templates/proposal-template.md` để lấy cấu trúc, tham khảo `examples/sample-proposal.md` để hình dung một proposal hoàn chỉnh trông như thế nào.
- **Lập báo giá**: đọc `templates/quotation-template.md`.
- **Soạn email gửi proposal**: đọc `templates/email-template.md`.
- **Kiểm tra chất lượng proposal trước khi gửi**: đọc `checklist/qa-checklist.md` và rà soát theo từng mục.
- **Cần hướng dẫn cách xây dựng proposal thuyết phục, chuyên nghiệp**: đọc `docs/proposal-guide.md`.

Luôn ưu tiên đọc file tương ứng trước khi tạo nội dung, thay vì tự suy đoán cấu trúc hoặc tiêu chuẩn trình bày.

## Quy trình gợi ý khi làm proposal từ đầu đến cuối

1. Thu thập thông tin từ người dùng: khách hàng, hiện trạng, mục tiêu, ngân sách dự kiến (hỏi lại nếu thiếu thông tin quan trọng).
2. Nếu cần định hướng cách xây dựng proposal thuyết phục, đọc `docs/proposal-guide.md` trước khi viết.
3. Đọc `templates/proposal-template.md` và điền nội dung theo đúng cấu trúc, đối chiếu `examples/sample-proposal.md` khi cần ví dụ cụ thể.
4. Nếu proposal có báo giá, đọc `templates/quotation-template.md` để lập báo giá đi kèm, đảm bảo khớp với ngân sách và deliverables trong proposal.
5. Trước khi xem là hoàn tất, rà lại theo `checklist/qa-checklist.md`; bổ sung phần còn thiếu.
6. Nếu cần gửi cho khách, dùng `templates/email-template.md` để soạn email đính kèm proposal/báo giá.

## Lưu ý về văn phong

- Proposal cần nêu rõ **giá trị mang lại cho khách hàng**, không chỉ liệt kê công việc sẽ làm.
- Mục tiêu và KPI phải cụ thể, đo lường được (SMART), tránh diễn đạt mơ hồ như "tăng trưởng tốt hơn".
- Giữ giọng văn chuyên nghiệp, tự tin nhưng không cường điệu; tránh cam kết những con số không có cơ sở.
- Ngân sách và deliverables trong proposal phải nhất quán với báo giá đi kèm.
